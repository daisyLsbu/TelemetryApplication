# TelemetryApplication

> A lightweight, self-contained Python telemetry agent for host and container resource monitoring — designed to be deployed independently or used as a reusable building block in larger distributed systems.

---

## Overview

**TelemetryApplication** is a minimal HTTP-based telemetry agent built with Python and Flask. Deployed on any host you want to observe, it exposes a clean REST API that returns real-time resource metrics for the machine itself, any Docker containers running on it, and network round-trip times to other hosts.

The agent is intentionally simple and decoupled — it has no dependencies on the systems that consume its data, making it straightforward to integrate as a data collection layer in any monitoring, observability, or orchestration pipeline.

---

## Features

- **Host resource metrics** — CPU, memory, disk, and network utilisation via `psutil`
- **Container metrics** — per-container resource data via the Docker Stats API
- **Network RTT measurement** — round-trip time from this host to a configurable list of other hosts
- **Combined endpoint** — host and container data in a single API response
- **Configurable port** — pass any port number at startup
- **Lightweight** — no database, no state, no overhead; just expose and serve

---

## API Endpoints

| Method | Endpoint       | Description                                              |
|--------|----------------|----------------------------------------------------------|
| GET    | `/`            | Health check / welcome message                          |
| GET    | `/devicedetails` | CPU, memory, disk, and network stats for this host     |
| GET    | `/containers`  | Resource metrics for all running Docker containers       |
| GET    | `/combined`    | Host stats and container stats in a single response      |
| POST   | `/rttData`     | RTT from this host to a list of hosts (JSON body)        |

### RTT request body format

```json
{
  "hosts": ["192.168.1.10", "192.168.1.11", "192.168.1.12"]
}
```
---

## Getting Started
**Deploy this on:** every host node in your network.
This project showcases how to use the `psutil`
library to send metrics from your applications to a monitoring server written
in any language.

1. Download the `setup.sh` script and copy it to the location on your Linux machine where you want the application to run.
2. Execute the setup script:
```bash
   ./setup.sh
```
3. Navigate into the application directory:
```bash
   cd TelemetryApplication
   chmod +x scripts/deploy.sh
   chmod +x scripts/build.sh
```

4. Run the application using **one** of the following options:
    - **Option A — Use the deploy script:**  source scripts/deploy.sh
    - **Option B — Use Build then run:** source scripts/build.sh ./scripts/run.sh 5002
    -  **Option C — Manual execution:**
      Run the commands from `build.sh` and `run.sh` individually, one at a time.

   
   
  
   

### check troubleshoot file

Or follow the steps below:

### Prerequisites

- Python 3.8+
- Docker Engine (required only if using the `/containers` or `/combined` endpoints)

### Installation

```bash
git clone https://github.com/daisyLsbu/TelemetryApplication.git
cd TelemetryApplication
git pull 
python3 -m venv venv
conda deactivate
source venv/bin/activate
python3 -m pip install --upgrade pip
pip install -r requirement.txt```

### Running the agent

```bash
python app.py <port>
# Example:
python app.py 5000
```

The agent will be available at `http://<host-ip>:<port>`.
#example: http://127.0.0.1:5002
## Folder structure
The Script folder has all the script required for running this. 
app.py and dockerstat.py are main files - use which ever required
psutil and rtt is supporting code
requirement.txt - package detail - used in script
start with trouble shoot file if you want detail on how to debug and use the application

## Used In

This agent has been used as **Part 1 — the data collection layer** in the following project in this account:

### [reactiveAndPredictiveMigration](https://github.com/daisyLsbu/reactiveAndPredictiveMigration)

---
