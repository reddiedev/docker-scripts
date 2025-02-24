# Assorted Docker Scripts

a set of commonly used docker scripts

## Deploy Postgres via Docker CLI

```bash
docker run --name <name> -v pg_data:/var/lib/postgresql/data -p 5432:5432 -e POSTGRES_PASSWORD=<password> --restart unless-stopped -d postgres

pg_dump -U user -h host -p port -d database -Fc -x -f file.dump
pg_restore -U user -h host -p port -d database --no-owner -1 file.dump
```

## Deploy Discord Bot via Docker CLI

```bash
docker build . --tag <username>/<image>
docker run -d --name <app> --env-file ./.env <username>/<image>
```

## Deploy Ollama

```bash
docker run -d --gpus=all -v ollama:/root/.ollama -e OLLAMA_HOST=0.0.0.0 -e OLLAMA_KEEP_ALIVE=24h -p 11434:11434 --name ollama ollama/ollama
```

## Deploy Open-webui

```bash
docker run -d -p 3001:8080 -v open-webui:/app/backend/data -e OLLAMA_BASE_URL=http://127.0.0.1:11434 --network=host --name open-webui ghcr.io/open-webui/open-webui:main

```

### Deploy OpenWebUI with Ollama

```bash
docker run -d -p 3001:8080 -e OLLAMA_KEEP_ALIVE=24h --gpus=all -v ollama:/root/.ollama -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:ollama
docker pull ghcr.io/open-webui/open-webui:ollama
docker rm -f open-webui
```

### Deploy Redis

```bash
docker run -d --name <name> -v <loc>:/data -p 6379:6379 -e REDIS_ARGS="--requirepass mypassword" redis/redis-stack-server:latest
```
