# MinaDeploy

## Project Overview

This project provides a quick way to deploy a Mina blockchain node using Docker Compose. It supports custom key, port, and parameter configuration, making it easy for developers and operators to start and manage a Mina node with one command.

## Prerequisites

- Docker
- Docker Compose
- Recommended OS: Linux/macOS/WSL2

## Quick Start

### 1. Clone the Repository
```bash
git clone <your-repo-url>
cd minadeploy
```

### 2. Configure Environment Variables

Create a `.env` file in the project root directory. Example:
```env
IMAGE=minaprotocol/mina-daemon:3.1.0-ae112d3-bullseye-mainnet
P2P_PORT=8302
METRICS_PORT=6060
MINA_PRIVKEY_PASS=your_password
RUNDIR=/absolute/path/to/minadeploy
COINBASE_RECEIVER=B62qxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```
- `IMAGE`: Mina node image name and tag
- `P2P_PORT`: P2P network port
- `METRICS_PORT`: Metrics port
- `MINA_PRIVKEY_PASS`: Wallet private key password
- `RUNDIR`: Absolute path to the project (for key mounting)
- `COINBASE_RECEIVER`: Address to receive block rewards

### 3. Prepare Your Key

Place your Mina wallet private key file (e.g., `my-wallet`) in the `keys/` directory. Make sure the `RUNDIR` path in your `.env` file is correct.

> Example: `keys/my-wallet`. See `keys/my-wallet.example` for reference.

### 4. Start the Mina Node

```bash
docker compose up -d
```

### 5. View Logs

```bash
docker compose logs -f
```

## Directory Structure

```
minadeploy/
├── docker-compose.yaml   # Docker Compose configuration
├── keys/                # Directory for wallet keys
│   └── my-wallet.example
└── README.md            # Usage documentation
```

## FAQ

1. **What if the ports are already in use?**
   - Change `P2P_PORT` and `METRICS_PORT` in your `.env` file.
2. **Key permission issues?**
   - Ensure `keys/my-wallet` has permission 600 and the mount path is correct.
3. **How to stop the node?**
   - Run `docker-compose down`.

## References
- [Mina Protocol Documentation](https://docs.minaprotocol.com/)
- [Docker Documentation](https://docs.docker.com/)