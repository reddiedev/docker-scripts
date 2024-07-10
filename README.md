# Assorted Docker Scripts
a set of commonly used docker scripts

## Deploy Postgres via Docker CLI
```bash
docker run --name <name> -p 5432:5432 -e POSTGRES_PASSWORD=<password> -d postgres
```