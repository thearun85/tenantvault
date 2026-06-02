# TenantVault

A secrets management API demonstrating bank-grade tenant isolation.

Each tenant gets its own KMS encryption key. A secret belonging to 
Tenant A cannot be read by Tenant B — enforced at the API level, 
the database level, and the KMS level independently.

## The core idea

Before building a cloud IDE, you need to answer one question:
where do tenant secrets live, and how do you guarantee isolation?
TenantVault is that answer.

## Stack

- FastAPI — API framework
- Postgres — tenant metadata and audit log
- DynamoDB Local — encrypted secret storage
- LocalStack KMS — envelope encryption (one key per tenant)
- Docker Compose — local infrastructure

## Quick start

    docker compose up -d
    pip install -r requirements.txt
    python main.py

## Status

- [x] Local infrastructure (Postgres + LocalStack KMS)
- [ ] Tenant provisioning
- [ ] Secrets CRUD with envelope encryption
- [ ] Tenant isolation test
- [ ] Audit log
