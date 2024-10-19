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