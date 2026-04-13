# Nginx Contract

## Root Route

- path: `/`
- method: `GET`
- behavior: serve a static HTML page
- requirement: the HNG username must be visible as page text

## API Route

- path: `/api`
- method: `GET`
- status: `200`
- content-type: `application/json`
- body:

```json
{
  "message": "HNGI14 Stage 0",
  "track": "DevOps",
  "username": "<exact-hng-username>"
}
```

The `username` value must match the registered HNG username exactly, including case.
