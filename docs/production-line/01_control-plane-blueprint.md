# Control-Plane Blueprint

## Objective

Run DevOps Stage 0 as a controlled ops line instead of a loose chat-driven effort.

## System Layers

### 1. Direction Layer

Actor: human operator

Responsibilities:

- confirm provider, domain, and username
- approve gate closures
- resolve blockers such as domain control or checker-key availability

### 2. Control Layer

Actor: conductor/orchestrator

Responsibilities:

- convert directives into task packets
- assign lane type, scope, and green level
- keep delivery state current

### 3. Lane Layer

Recommended lane families:

- `control`
- `provisioning`
- `hardening`
- `nginx`
- `ssl`
- `proof`

### 4. Verification Layer

Responsibilities:

- run declared checks
- determine whether the lane achieved its green level

### 5. Proof Layer

Responsibilities:

- update trackers and logs
- preserve command, config, and live-domain evidence

## Canonical Artifacts

- lane board
- task packet
- delivery state
- lane closeout
- sign-off log
