# 📤 Guia de Upload no GitHub

Este documento explica como fazer upload do projeto para o GitHub e testá-lo.

## Pré-requisitos

- Conta no GitHub
- Git instalado no seu computador
- Acesso ao repositório (público ou privado)

## Passo 1: Criar Repositório no GitHub

1. Acesse [GitHub](https://github.com)
2. Clique em "New" (novo repositório)
3. Preencha os dados:
   - **Repository name**: `controle-precos`
   - **Description**: "Sistema de gerenciamento de preços de produtos"
   - **Visibility**: Escolha "Public" ou "Private"
   - **Initialize repository**: Deixe desmarcado
4. Clique em "Create repository"

## Passo 2: Preparar o Projeto Localmente

```bash
cd /home/ubuntu/controle-precos

# Inicializar git (se não estiver inicializado)
git init

# Adicionar remote do GitHub
git remote add origin https://github.com/seu-usuario/controle-precos.git

# Verificar status
git status
```

## Passo 3: Configurar .gitignore

O projeto já deve ter um `.gitignore`. Verifique se contém:

```
node_modules/
dist/
.env
.env.local
.DS_Store
*.log
.manus-logs/
backup-*.json
```

## Passo 4: Fazer Commit e Push

```bash
# Adicionar todos os arquivos
git add .

# Criar commit inicial
git commit -m "Initial commit: Controle de Preços v1.0"

# Push para GitHub (substitua 'main' se usar outra branch)
git branch -M main
git push -u origin main
```

## Passo 5: Testar no GitHub

### Opção A: Clonar em Outro Local

```bash
# Em outro diretório
git clone https://github.com/seu-usuario/controle-precos.git
cd controle-precos

# Instalar dependências
pnpm install

# Configurar variáveis de ambiente
cp ENVIRONMENT.md .env
# Edite .env com suas credenciais

# Executar migrations
pnpm drizzle-kit generate
pnpm drizzle-kit migrate

# Iniciar servidor
pnpm dev
```

### Opção B: Usar GitHub Codespaces (Recomendado)

1. Acesse seu repositório no GitHub
2. Clique em "Code" > "Codespaces" > "Create codespace on main"
3. Aguarde o ambiente ser criado
4. No terminal do Codespaces:

```bash
pnpm install
pnpm dev
```

5. Clique no link fornecido para acessar a aplicação

## Passo 6: Atualizar Código

Quando fizer mudanças localmente:

```bash
# Ver mudanças
git status

# Adicionar mudanças
git add .

# Commit
git commit -m "Descrição das mudanças"

# Push
git push origin main
```

## Estrutura do Repositório

```
controle-precos/
├── README.md              # Documentação principal
├── ENVIRONMENT.md         # Guia de variáveis de ambiente
├── GITHUB.md              # Este arquivo
├── package.json           # Dependências
├── tsconfig.json          # Configuração TypeScript
├── vite.config.ts         # Configuração Vite
├── tailwind.config.js     # Configuração Tailwind
├── client/                # Frontend
├── server/                # Backend
├── drizzle/               # Banco de dados
├── scripts/               # Scripts auxiliares
└── .gitignore             # Arquivos ignorados pelo Git
```

## Checklist Antes de Fazer Push

- [ ] Todos os testes passam: `pnpm test`
- [ ] Sem erros TypeScript: `pnpm check`
- [ ] Sem erros de build: `pnpm build`
- [ ] `.env` não está commitado
- [ ] `node_modules/` não está commitado
- [ ] `dist/` não está commitado
- [ ] README.md está atualizado
- [ ] Backup de dados foi feito

## Comandos Úteis

### Verificar Histórico

```bash
git log --oneline
```

### Ver Mudanças Não Commitadas

```bash
git diff
```

### Reverter Mudanças

```bash
git checkout -- arquivo.ts
```

### Criar Branch para Feature

```bash
git checkout -b feature/nova-funcionalidade
git push origin feature/nova-funcionalidade
```

## Colaboração

Se outras pessoas vão contribuir:

1. Vá em Settings > Collaborators
2. Adicione os colaboradores
3. Eles podem fazer clone e push

## CI/CD (Opcional)

Para automatizar testes e build, crie `.github/workflows/ci.yml`:

```yaml
name: CI

on: [push, pull_request]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: pnpm/action-setup@v2
      - uses: actions/setup-node@v2
        with:
          node-version: '22'
          cache: 'pnpm'
      - run: pnpm install
      - run: pnpm test
      - run: pnpm build
```

## Troubleshooting

### Erro: "fatal: not a git repository"

```bash
git init
git remote add origin https://github.com/seu-usuario/controle-precos.git
```

### Erro: "permission denied"

Verifique suas credenciais do GitHub:

```bash
git config --global user.name "Seu Nome"
git config --global user.email "seu-email@example.com"
```

### Erro: "rejected ... (fetch first)"

```bash
git pull origin main
git push origin main
```

## Próximos Passos

1. ✅ Fazer push para GitHub
2. ✅ Testar clonando em outro local
3. ✅ Compartilhar link com sua equipe
4. ✅ Configurar CI/CD (opcional)
5. ✅ Documentar mudanças futuras

## Dúvidas?

Consulte a [documentação oficial do Git](https://git-scm.com/doc) ou [GitHub Docs](https://docs.github.com).

---

**Última atualização**: Março 2026
