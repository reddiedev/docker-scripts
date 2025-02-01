# Assorted Docker Scripts

a set of commonly used docker scripts

## Deploy Postgres via Docker CLI

```bash
docker run --name <name> -p 5432:5432 -e POSTGRES_PASSWORD=<password> --restart unless-stopped -d postgres
```

## Deploy Discord Bot via Docker CLI

```bash
docker build . --tag <username>/<image>
docker run -d --name <app> --env-file ./.env <username>/<image>
```

### Deploy OpenWebUI with Ollama

```bash
docker run -d -p 3001:8080 -e OLLAMA_KEEP_ALIVE=24h --gpus=all -v ollama:/root/.ollama -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:ollama
docker pull ghcr.io/open-webui/open-webui:ollama
docker rm -f open-webui
```
