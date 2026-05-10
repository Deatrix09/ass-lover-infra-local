# rag-infra

Infrastructure and deployment configuration for the RAG system.

## Repository Structure

```
rag-infra/
├── docker-compose.prod.yaml    ← Full stack (Docker Compose)
├── k8s/                        ← Kubernetes manifests
│   ├── namespace.yaml
│   ├── backend/
│   ├── frontend/
│   ├── postgres/
│   ├── qdrant/
│   └── ingress.yaml
└── DEPLOYMENT.md               ← Detailed deployment guide
```

## Prerequisites

Clone all required repos **side by side**:

```bash
git clone https://github.com/Deatrix09/firecrawl-main
git clone https://github.com/Deatrix09/ass-lover-backend-local
git clone https://github.com/Deatrix09/ass-lover-frontend-local
git clone https://github.com/Deatrix09/ass-lover-infra-local
```

Expected directory structure:

```
project/
├── firecrawl-main/
├── ass-lover-backend-local/
├── ass-lover-frontend-local/
└── ass-lover-infra-local/         ← run commands from here
```

## Quick Start (Docker Compose)

```bash
cd rag-infra

# First time: set your GitHub org in docker-compose.prod.yaml
#   image: ghcr.io/Deatrix09/ass-lover-backend-local:latest
#   image: ghcr.io/Deatrix09/ass-lover-frontend-local:latest

# Pull images and start all services
docker compose -f docker-compose.prod.yaml up -d

# View logs
docker compose -f docker-compose.prod.yaml logs -f backend
```

## Image Tags

After merging to `main` in `rag-backend` or `rag-frontend`, GitHub Actions auto-publishes:

- `ghcr.io/Deatrix09/ass-lover-backend-local:latest`
- `ghcr.io/Deatrix09/ass-lover-frontend-local:latest`

To deploy a specific version, use the commit SHA tag:

```yaml
image: ghcr.io/Deatrix09/ass-lover-backend-local:sha-abc1234
```

## Kubernetes

See [DEPLOYMENT.md](DEPLOYMENT.md) for full Kubernetes setup guide.
