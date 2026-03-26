# 📊 Controle de Preços - Sistema de Gerenciamento de Custos e Vendas

Sistema web mobile-first para controle de preços de custo e venda de produtos de supermercado, com histórico de compras, alertas automáticos e backup em nuvem.

## 🎯 Funcionalidades

- ✅ **Cadastro de Produtos**: Adicione produtos com preço de custo, venda e quantidade
- ✅ **Busca Rápida**: Autocompletar para encontrar produtos rapidamente
- ✅ **Histórico de Compras**: Registre cada compra com data, preço e quantidade
- ✅ **Análise de Preços**: Veja mínimo, máximo e último preço pago por produto
- ✅ **Margem de Lucro**: Cálculo automático de margem em tempo real
- ✅ **Alertas de Variação**: Notificações quando preço varia mais de 10%
- ✅ **Exportação em PDF**: Relatórios de listagem e detalhes de produtos
- ✅ **Exportação em Excel**: Análise de dados em planilha
- ✅ **Backup Automático**: Backup diário com sincronização Google Drive
- ✅ **Edição de Produtos**: Atualize dados de produtos facilmente
- ✅ **Exclusão de Produtos**: Remova produtos com confirmação
- ✅ **Interface Mobile-First**: Otimizada para uso no celular
- ✅ **Autenticação Compartilhada**: Múltiplos usuários acessam os mesmos dados
- ✅ **Estética Blueprint**: Design técnico profissional com tema azul royal
- ✅ **Busca Inteligente**: Ignora acentos e maiúsculas (cafe = café = CAFÉ)
- ✅ **Margens Sugeridas por Categoria**: 20 categorias pré-configuradas com referências SEBRAE/ABRAS/CNC
- ✅ **Alertas de Margem SEBRAE**: Alerta automático quando margem está abaixo do recomendado para a categoria
- ✅ **Comparador de Preço em Tempo Real**: Variação percentual e margem projetada ao digitar novo preço no atacado
- ✅ **Clonar Produto**: Duplicar produto com preços copiados para nova marca/variação
- ✅ **Relatório de Margem por Categoria**: Visão consolidada com distribuição e exportação Excel

## 🚀 Quick Start

### Pré-requisitos

- Node.js 22.13.0+
- pnpm 10.4.1+
- MySQL/TiDB (banco de dados)

### Instalação

1. **Clone o repositório**
```bash
git clone https://github.com/seu-usuario/controle-precos.git
cd controle-precos
```

2. **Instale as dependências**
```bash
pnpm install
```

3. **Configure variáveis de ambiente**
```bash
cp .env.example .env
# Edite .env com suas credenciais
```

4. **Execute as migrations do banco de dados**
```bash
pnpm drizzle-kit generate
pnpm drizzle-kit migrate
```

5. **Inicie o servidor de desenvolvimento**
```bash
pnpm dev
```

6. **Acesse a aplicação**
```
http://localhost:5173
```

## 📁 Estrutura do Projeto

```
controle-precos/
├── client/                 # Frontend React + Vite
│   ├── src/
│   │   ├── pages/         # Páginas da aplicação
│   │   ├── components/    # Componentes reutilizáveis
│   │   ├── lib/           # Utilitários e configurações
│   │   └── index.css      # Estilos globais (Tailwind)
│   └── index.html         # HTML principal
├── server/                 # Backend Express + tRPC
│   ├── routers.ts         # Definição das APIs tRPC
│   ├── db.ts              # Funções de banco de dados
│   ├── backup-service.ts  # Serviço de backup
│   └── pdf-generator.ts   # Geração de PDFs
├── drizzle/               # Schema e migrations do banco
│   └── schema.ts          # Definição das tabelas
├── scripts/               # Scripts auxiliares
│   └── import-products.mjs # Importação em massa de produtos
└── package.json           # Dependências do projeto
```

## 🔧 Configuração

### Variáveis de Ambiente

Crie um arquivo `.env` na raiz do projeto:

```env
# Banco de dados
DATABASE_URL=mysql://usuario:senha@localhost:3306/controle_precos

# Autenticação
JWT_SECRET=sua_chave_secreta_aqui

# OAuth (se usando autenticação externa)
VITE_APP_ID=seu_app_id
OAUTH_SERVER_URL=https://seu-oauth-server.com
VITE_OAUTH_PORTAL_URL=https://seu-oauth-portal.com

# Google Drive (para backup)
GOOGLE_DRIVE_FOLDER_ID=seu_folder_id_aqui
GOOGLE_SERVICE_ACCOUNT_EMAIL=seu-email@seu-projeto.iam.gserviceaccount.com
GOOGLE_PRIVATE_KEY=sua_chave_privada_aqui

# Proprietário
OWNER_NAME=Seu Nome
OWNER_OPEN_ID=seu_open_id
```

## 📱 Páginas Principais

### 🏠 Home
- Busca rápida de produtos (fuzzy, sem acento)
- Estatísticas (total de produtos, alertas pendentes)
- Painel de produtos com margem crítica/baixa
- Acesso rápido a todas as funcionalidades via barra inferior

### 📦 Listagem de Produtos
- Visualização de todos os produtos
- Filtros por nome
- Ordenação por margem de lucro
- Exportação em Excel

### 📊 Detalhes do Produto
- Preço de custo e venda
- Histórico de compras
- Registro de nova compra
- Edição e exclusão de produto

### 📈 Histórico de Compras
- Todas as transações registradas
- Data, quantidade e preço
- Filtros por período

### ⚠️ Alertas de Preço
- Produtos com variação de preço > 10%
- Detalhes da variação
- Data da última compra

### 💾 Backups
- Backup local automático (diário às 2:00 AM)
- Sincronização com Google Drive
- Download manual de backups
- Histórico de 30 dias

### ➕ Novo Produto
- Cadastro de novo produto
- Preço de custo e venda
- Quantidade inicial

### 📥 Importar Produtos
- Upload de arquivo CSV
- Importação em massa
- Validação de dados

### ✨ Margens Sugeridas
- 20 categorias de mercearia pré-configuradas
- Detecção automática por palavras-chave no nome do produto
- Sugestão de preço de venda ao cadastrar produto
- Gerenciamento de categorias e percentuais

### 📊 Relatório de Margens
- Visão consolidada por categoria
- Distribuição: crítico / baixo / aceitável / bom
- Exportação Excel com resumo e produtos com problema

## 🧪 Testes

Execute os testes unitários:

```bash
pnpm test
```

Testes cobrem:
- Autenticação e logout
- CRUD de produtos
- Histórico de compras
- Cálculo de alertas
- Geração de PDFs

## 📦 Build para Produção

```bash
pnpm build
pnpm start
```

## 🔐 Segurança

- Autenticação via OAuth
- Proteção de rotas com `protectedProcedure`
- Validação de entrada com Zod
- Senhas de banco de dados em variáveis de ambiente
- HTTPS obrigatório em produção

## 🐛 Troubleshooting

### Erro de conexão com banco de dados
- Verifique se MySQL/TiDB está rodando
- Confirme `DATABASE_URL` em `.env`
- Execute migrations: `pnpm drizzle-kit migrate`

### Servidor não inicia
- Limpe cache: `rm -rf node_modules/.vite`
- Reinstale dependências: `pnpm install`
- Reinicie: `pnpm dev`

### Backup não sincroniza com Google Drive
- Verifique credenciais do Google Service Account
- Confirme `GOOGLE_DRIVE_FOLDER_ID` correto
- Verifique permissões da pasta no Google Drive

## 📚 Documentação Adicional

- [Drizzle ORM](https://orm.drizzle.team/)
- [tRPC](https://trpc.io/)
- [React 19](https://react.dev/)
- [Tailwind CSS 4](https://tailwindcss.com/)
- [Express.js](https://expressjs.com/)

## 🤝 Contribuindo

1. Faça um fork do projeto
2. Crie uma branch para sua feature (`git checkout -b feature/AmazingFeature`)
3. Commit suas mudanças (`git commit -m 'Add some AmazingFeature'`)
4. Push para a branch (`git push origin feature/AmazingFeature`)
5. Abra um Pull Request

## 📄 Licença

Este projeto está licenciado sob a Licença MIT - veja o arquivo LICENSE para detalhes.

## 👨‍💼 Autor

Desenvolvido com ❤️ para gerenciamento eficiente de preços em supermercados.

## 📞 Suporte

Para dúvidas ou problemas, abra uma issue no repositório GitHub.

---

**Versão**: 2.0.0  
**Última atualização**: Março 2026
