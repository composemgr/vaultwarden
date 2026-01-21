## 👋 Welcome to vaultwarden 🚀

Vaultwarden - Unofficial Bitwarden compatible password manager server

## 📋 Description

Vaultwarden is an alternative implementation of the Bitwarden server API written in Rust. Lightweight, fast, and compatible with all official Bitwarden clients (mobile, desktop, browser extensions).

## 🚀 Services

- **app**: Vaultwarden server (`vaultwarden/server:latest`)

## 📦 Installation

### Using curl
```shell
curl -q -LSsf "https://raw.githubusercontent.com/composemgr/vaultwarden/main/docker-compose.yaml" | docker compose -f - up -d
```

### Using git
```shell
git clone "https://github.com/composemgr/vaultwarden" ~/.local/srv/docker/vaultwarden
cd ~/.local/srv/docker/vaultwarden
docker compose up -d
```

### Using composemgr
```shell
composemgr install vaultwarden
```

## 🔧 Configuration

### Environment Variables

```shell
# Core Settings
TZ=America/New_York
DOMAIN=https://${BASE_HOST_NAME}

# Features
SENDS_ALLOWED=true
SIGNUPS_ALLOWED=false              # Disable after creating accounts
SIGNUPS_VERIFY=true
INVITATIONS_ALLOWED=true
TRASH_AUTO_DELETE_DAYS=30
ORG_GROUPS_ENABLED=true
ORG_EVENTS_ENABLED=true
ORG_CREATION_USERS=all

# Admin Panel
ADMIN_TOKEN=changeme_admin_token    # Generate with: openssl rand -base64 48

# SMTP
SMTP_HOST=172.17.0.1
SMTP_PORT=587
SMTP_FROM=vaultwarden@${BASE_DOMAIN_NAME}
SMTP_SECURITY=starttls
SMTP_FROM_NAME=Vaultwarden
INVITATION_ORG_NAME=Vaultwarden
```

## 🌐 Access

- **Web Vault**: http://172.17.0.1:59090
- **Admin Panel**: http://172.17.0.1:59090/admin
- **Must use HTTPS** in production (reverse proxy required)

## 📂 Volumes

- `./rootfs/data/vaultwarden` - Database and attachments

## 🔐 Security

- **HTTPS required**: Clients won't connect without valid TLS
- **Disable signups**: After creating accounts
- **Strong admin token**: Use `openssl rand -base64 48`
- **Enable 2FA**: For all accounts
- **Email verification**: Configure SMTP
- **Regular backups**: Critical for password data

## 🔍 Logging

```shell
docker compose logs -f app
```

## 🛠️ Management

```shell
docker compose up -d
docker compose down
docker compose pull && docker compose up -d
```

## 🔄 Backup

```shell
# Backup data directory (includes SQLite DB)
tar -czf vaultwarden-backup-$(date +%Y%m%d).tar.gz rootfs/data/vaultwarden
```

## 📋 Requirements

- Docker Engine 20.10+
- Docker Compose V2+
- **HTTPS reverse proxy** (required for clients)
- Valid TLS certificate

## 🤝 Author

🤖 casjay: [Github](https://github.com/casjay) 🤖  
🦄 composemgr: [Github](https://github.com/composemgr) 🦄
