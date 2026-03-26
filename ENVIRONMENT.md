# 🔐 Variáveis de Ambiente

Este documento descreve todas as variáveis de ambiente necessárias para executar o projeto.

## Configuração Básica

### Banco de Dados

```env
DATABASE_URL=mysql://usuario:senha@localhost:3306/controle_precos
```

**Formatos suportados:**
- MySQL: `mysql://usuario:senha@host:porta/banco`
- TiDB: `mysql://usuario:senha@tidb-host:4000/banco`

### Autenticação

```env
JWT_SECRET=sua_chave_secreta_muito_segura_aqui
```

Gere uma chave forte com:
```bash
openssl rand -base64 32
```

## OAuth (Autenticação Externa)

Se você está usando um provedor OAuth:

```env
VITE_APP_ID=seu_app_id_aqui
OAUTH_SERVER_URL=https://seu-oauth-server.com
VITE_OAUTH_PORTAL_URL=https://seu-oauth-portal.com
```

## Proprietário da Aplicação

```env
OWNER_NAME=Seu Nome Completo
OWNER_OPEN_ID=seu_open_id_unico
```

## Google Drive (Backup em Nuvem)

Para sincronizar backups com Google Drive:

### 1. Criar Pasta no Google Drive

1. Acesse [Google Drive](https://drive.google.com)
2. Crie uma nova pasta chamada "Controle de Preços Backups"
3. Copie o ID da pasta da URL: `https://drive.google.com/drive/folders/FOLDER_ID`

### 2. Criar Service Account

1. Acesse [Google Cloud Console](https://console.cloud.google.com)
2. Crie um novo projeto
3. Ative a API do Google Drive
4. Crie uma Service Account
5. Gere uma chave JSON
6. Compartilhe a pasta do Google Drive com o email da service account

### 3. Configurar Variáveis

```env
GOOGLE_DRIVE_FOLDER_ID=seu_folder_id_aqui
GOOGLE_SERVICE_ACCOUNT_EMAIL=seu-email@seu-projeto.iam.gserviceaccount.com
GOOGLE_PRIVATE_KEY=sua_chave_privada_json_aqui
```

## Aplicação

```env
VITE_APP_TITLE=Controle de Preços
VITE_APP_LOGO=https://seu-dominio.com/logo.png
```

## Analytics (Opcional)

```env
VITE_ANALYTICS_WEBSITE_ID=seu_website_id
VITE_ANALYTICS_ENDPOINT=https://seu-analytics-endpoint.com
```

## APIs Internas (Manus)

Se você está usando as APIs internas do Manus:

```env
VITE_FRONTEND_FORGE_API_URL=https://api.manus.im
VITE_FRONTEND_FORGE_API_KEY=sua_chave_publica_aqui
BUILT_IN_FORGE_API_URL=https://api.manus.im
BUILT_IN_FORGE_API_KEY=sua_chave_privada_aqui
```

## Ambiente

```env
NODE_ENV=development
PORT=3000
```

## Exemplo Completo (.env)

```env
# Banco de Dados
DATABASE_URL=mysql://root:password@localhost:3306/controle_precos

# Autenticação
JWT_SECRET=abc123def456ghi789jkl012mno345pqr

# OAuth
VITE_APP_ID=app_123456789
OAUTH_SERVER_URL=https://oauth.example.com
VITE_OAUTH_PORTAL_URL=https://oauth-portal.example.com

# Proprietário
OWNER_NAME=João Silva
OWNER_OPEN_ID=user_123456

# Google Drive
GOOGLE_DRIVE_FOLDER_ID=1ABC123DEF456GHI789
GOOGLE_SERVICE_ACCOUNT_EMAIL=backup@projeto.iam.gserviceaccount.com
GOOGLE_PRIVATE_KEY={"type":"service_account",...}

# Aplicação
VITE_APP_TITLE=Controle de Preços
VITE_APP_LOGO=https://example.com/logo.png

# Ambiente
NODE_ENV=development
PORT=3000
```

## Validação

Para verificar se todas as variáveis estão configuradas corretamente, execute:

```bash
pnpm dev
```

Se houver erro de variável faltante, você verá uma mensagem clara indicando qual variável está faltando.

## Segurança

⚠️ **IMPORTANTE:**
- Nunca commit `.env` no Git
- Use `.env.example` como template
- Mantenha `JWT_SECRET` seguro
- Não compartilhe `GOOGLE_PRIVATE_KEY` ou `BUILT_IN_FORGE_API_KEY`
- Em produção, use variáveis de ambiente do servidor (não arquivo `.env`)

## Troubleshooting

### Erro: "DATABASE_URL is not set"
- Verifique se `.env` existe na raiz do projeto
- Confirme que `DATABASE_URL` está definido
- Reinicie o servidor: `pnpm dev`

### Erro: "Failed to connect to database"
- Verifique se MySQL/TiDB está rodando
- Confirme credenciais em `DATABASE_URL`
- Teste conexão: `mysql -u usuario -p -h localhost`

### Erro: "Google Drive sync failed"
- Verifique `GOOGLE_DRIVE_FOLDER_ID`
- Confirme que a service account tem acesso à pasta
- Verifique `GOOGLE_PRIVATE_KEY` está em formato correto
