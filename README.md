# Ansible-web-stack
Automate provisioning and deployment of a Nginx + Gunicorn + Flask + PostgreSQL web stack using best practices.

## Features

- Role-based, idempotent Ansible layout
- Zero-downtime deployment via rolling update
- Ansible Vault for secrets
- Environment-specific variables
- Handlers, templates, health checks
- UFW firewall
- CI/CD linting with GitHub Actions

## Quick Start

1. **Clone this repo**
2. **Install dependencies**
   ```bash
   pip install ansible ansible-lint
   ansible-galaxy collection install -r requirements.yml
   ```
3. **Encrypt secrets**
   ```bash
   ansible-vault encrypt vault.yml
   ```
4. **Edit your inventory and group_vars as needed**
5. **Run provisioning**
   ```bash
   ansible-playbook -i inventory/dev site.yml --ask-vault-pass
   ```
6. **Deploy new app version**
   ```bash
   ansible-playbook -i inventory/dev deploy.yml --ask-vault-pass
   ```
7. **CI/CD**
   - Linting and syntax checks run on each PR/commit.

## Structure

- `roles/` — Ansible Galaxy-style roles (nginx, app, db, security, common)
- `group_vars/` — Environment-specific vars
- `vault.yml` — Encrypted secrets (DB password)
- `inventory/` — Static inventory (dev/staging/prod)
- `site.yml` — Complete provisioning
- `deploy.yml` — Rolling deploy for app updates

## Extend

- Add more roles (monitoring, certbot, etc)
- Use dynamic inventory for cloud
- Add Molecule tests
