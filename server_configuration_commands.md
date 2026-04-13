# Create hngdevops user and grant sudo privileges
sudo adduser hngdevops --gecos "HNG DevOps User" --disabled-password
sudo usermod -aG sudo hngdevops
sudo mkdir -p /home/hngdevops/.ssh
sudo cp /home/hngdevops-operator/.ssh/authorized_keys /home/hngdevops/.ssh/authorized_keys # Assuming you used hngdevops-operator to add the key
sudo chown -R hngdevops:hngdevops /home/hngdevops/.ssh
sudo chmod 700 /home/hngdevops/.ssh
sudo chmod 600 /home/hngdevops/.ssh/authorized_keys

# Configure sudoers for hngdevops
echo 'hngdevops ALL=(root) NOPASSWD:/usr/sbin/sshd,/usr/sbin/ufw' | sudo tee /etc/sudoers.d/hngdevops

# Harden SSH
sudo sed -i 's/^PermitRootLogin yes/PermitRootLogin no/' /etc/ssh/sshd_config
sudo sed -i 's/^#PasswordAuthentication yes/PasswordAuthentication no/' /etc/ssh/sshd_config
sudo sed -i 's/^PasswordAuthentication yes/PasswordAuthentication no/' /etc/ssh/sshd_config
sudo systemctl reload sshd

# Configure UFW
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow 22/tcp
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
sudo ufw --force enable

# Install Nginx
sudo apt update
sudo apt install -y nginx

# Create Nginx content files
sudo mkdir -p /var/www/api
echo '<h1>HNGI14 Stage 0 - Kelechi Uba</h1>' | sudo tee /var/www/html/index.html
echo '{"message":"HNGI14 Stage 0","track":"DevOps","username":"Kelechi Uba"}' | sudo tee /var/www/api/index.json

# Configure Nginx
sudo tee /etc/nginx/sites-available/default <<EOF
server {
    listen 80;
    listen [::]:80;
    server_name _;

    # Redirect HTTP to HTTPS (Certbot will handle this later)
    # return 301 https://\$host\$request_uri;

    root /var/www/html;
    index index.html index.htm index.nginx-debian.html;

    location / {
        try_files \$uri \$uri/ =404;
    }

    location = /api {
        alias /var/www/api/index.json;
        default_type application/json;
        add_header Content-Type application/json always;
    }
}
EOF

sudo nginx -t
sudo systemctl reload nginx

# Install Certbot and obtain Let's Encrypt SSL
sudo snap install core
sudo snap refresh core
sudo snap install --classic certbot
sudo ln -s /snap/bin/certbot /usr/bin/certbot

# IMPORTANT: Before running the next command, ensure your domain's A record points to 34.135.216.230
# Replace 'your_domain.com' with your actual domain name
# sudo certbot --nginx -d your_domain.com --non-interactive --agree-tos -m your_email@example.com

