# n8n local Docker stack (WSL / Docker Desktop)

Quick start

1. Copy the example env and edit secrets:

```powershell
cd n8n
cp .env.example .env
# edit .env with a text editor
```

2. Start the stack:

```powershell
docker compose -f docker-compose.yaml up -d
```

3. Verify services:

```powershell
docker compose -f docker-compose.yaml ps
docker compose -f docker-compose.yaml logs -f n8n
```

4. Access UIs:
- n8n: http://localhost:5678 (basic auth if enabled)
- pgAdmin: http://localhost:5050
- MinIO Console: http://localhost:9001

5. Verify Ollama connectivity from WSL or a container:

```bash
curl http://host.docker.internal:11434/v1/models
```

6. Stop and remove containers (preserve volumes):

```powershell
docker compose -f docker-compose.yaml down
```

Notes
- The Compose file uses named Docker volumes for persistence.
- If Ollama runs on the Windows host, `host.docker.internal:11434` is the default address for containers.
- To enable distributed `queue` mode in n8n, you'll need to set `EXECUTIONS_PROCESS=queue` and provide a Redis endpoint; the compose includes a Redis service to make that switch easier later.
