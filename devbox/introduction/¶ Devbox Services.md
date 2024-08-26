---
tags: 
  - devbox
title: "Devbox Services: Managing Daemon Applications with process-compose"
date: 2024-08-01
description: An overview of Devbox Services, which uses process-compose to manage daemon applications in a non-containerized environment
authors:
  - bievh
---
## Process Compose

Process Compose is a simple and flexible scheduler and orchestrator to manage non-containerized applications.It is highly recommended when you don't want to deal with docker files, volume definitions, networks and docker registries. As `docker-compose.yml`, you can define `process-compose.yml` in your root directory of your project. For example: 

```yaml
version: "0.5"

processes:
  postgresql:
    command: |
      if ! grep -q "shared_preload_libraries = 'timescaledb'" $PGDATA/postgresql.conf; then
        echo "shared_preload_libraries = 'timescaledb'" >> $PGDATA/postgresql.conf
      fi
      pg_ctl start -o "-k $PGHOST"
    is_daemon: true
    shutdown: 
      command: "pg_ctl stop -m fast"
    availability:
      restart: "always"
    readiness_probe:
      exec:
        command: "pg_isready"
        
  telegram-bot:
    command: |
      cd telegram-bot
      make install
      make dev
    availability:
      restart: "always"    
    depends_on:
      postgresql:
        condition: process_healthy    
    readiness_probe:
      http_get:
        host: 127.0.0.1
        scheme: http
        path: "/healthz"
        port: 5001
      initial_delay_seconds: 5
      period_seconds: 10
      timeout_seconds: 5
      success_threshold: 1
      failure_threshold: 3
```

## Break it down
This configuration sets up a development environment where PostgreSQL (with TimescaleDB extension) and a Telegram bot are run and managed together. The PostgreSQL process is set up first, and once it's healthy, the Telegram bot process starts. Both processes are configured to restart if they stop, and have readiness probes to check their health status.


### Processes

The file defines two processes: `postgresql` and `telegram-bot`.

#### PostgreSQL Process

```yaml
postgresql:
  command: |
    if ! grep -q "shared_preload_libraries = 'timescaledb'" $PGDATA/postgresql.conf; then
      echo "shared_preload_libraries = 'timescaledb'" >> $PGDATA/postgresql.conf
    fi
    pg_ctl start -o "-k $PGHOST"
  is_daemon: true
  shutdown: 
    command: "pg_ctl stop -m fast"
  availability:
    restart: "always"
  readiness_probe:
    exec:
      command: "pg_isready"
```

- **command**: A shell script that:
  - Checks if `timescaledb` is already in the `postgresql.conf` file.
  - If not, adds it to the configuration.
  - Starts PostgreSQL with a specific socket directory (`$PGHOST`).
- **is_daemon**: Set to `true`, indicating this process runs continuously.
- **shutdown**: Specifies how to stop the process (`pg_ctl stop -m fast`).
- **availability**: Set to restart "always" if the process stops.
- **readiness_probe**: Uses `pg_isready` to check if PostgreSQL is ready to accept connections.

#### Telegram Bot Process

```yaml
telegram-bot:
  command: |
    cd telegram-bot
    make install
    make dev
  availability:
    restart: "always"    
  depends_on:
    postgresql:
      condition: process_healthy    
  readiness_probe:
    http_get:
      host: 127.0.0.1
      scheme: http
      path: "/healthz"
      port: 5001
    initial_delay_seconds: 5
    period_seconds: 10
    timeout_seconds: 5
    success_threshold: 1
    failure_threshold: 3
```

- **command**: A series of shell commands to:
  - Change to the `telegram-bot` directory.
  - Run `make install` to install dependencies.
  - Run `make dev` to start the bot in development mode.
- **availability**: Set to restart "always" if the process stops.
- **depends_on**: Specifies that this process depends on the `postgresql` process being healthy before starting.
- **readiness_probe**: Checks the health of the bot by:
  - Making an HTTP GET request to `http://127.0.0.1:5001/healthz`.
  - Defining various parameters for the health check (initial delay, frequency, timeout, etc.).

## Devbox Services 
In the Devbox, you do not need to interact directly to process-compose. You just only need to use some `services` CLI as following.

- `devbox services ls` - List available services
- `devbox services restart` - Restarts service. If no service is specified, restarts all services
- `devbox services start` - Starts service. If no service is specified, starts all services
- `devbox services stop` - Stops service. If no service is specified, stops all services
