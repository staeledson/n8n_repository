# n8n com FFmpeg

Repositório mínimo para rodar **n8n** com **FFmpeg** usando Docker (PostgreSQL + n8n customizado).

## Estrutura

```
.
├── docker-compose.yml    # Stack n8n + PostgreSQL
├── docker/
│   └── n8n/
│       └── Dockerfile    # n8n oficial + FFmpeg (Alpine)
├── .env.example
└── README.md
```

## Deploy no Portainer

1. **Stacks** → **Add stack** → **Build method:** Repository
2. **Repository URL:** `https://github.com/SEU_USUARIO/SEU_REPO_N8N.git`
3. **Compose path:** `docker-compose.yml`
4. **Environment variables:** adicione as variáveis (veja `.env.example`). Obrigatórias:
   - `N8N_DB_PASSWORD`
   - `N8N_BASIC_AUTH_PASSWORD`
5. **Deploy the stack**

Acesse: `http://IP_DA_VPS:5678`

## Deploy via linha de comando

```bash
git clone https://github.com/SEU_USUARIO/SEU_REPO_N8N.git
cd SEU_REPO_N8N
cp .env.example .env
# Edite .env com suas senhas
docker compose up -d --build
```

## Variáveis de ambiente

| Variável | Obrigatória | Descrição |
|----------|-------------|-----------|
| `N8N_DB_PASSWORD` | Sim | Senha do PostgreSQL |
| `N8N_BASIC_AUTH_PASSWORD` | Sim | Senha de login do n8n |
| `N8N_DB_USER` | Não (default: n8n) | Usuário do banco |
| `N8N_DB_NAME` | Não (default: n8n_db) | Nome do banco |
| `N8N_HOST` | Não | IP ou domínio (ex: n8n.seudominio.com) |
| `N8N_PORT` | Não (5678) | Porta no host |
| `N8N_PROTOCOL` | Não (http) | http ou https |
| `N8N_BASIC_AUTH_USER` | Não (admin) | Usuário de login do n8n |

## Verificar FFmpeg

No container n8n, execute:

```bash
ffmpeg -version
```

## Licença

Uso livre.
