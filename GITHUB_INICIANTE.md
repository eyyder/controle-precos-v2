# 🚀 Guia GitHub para Iniciantes (Passo a Passo)

Se você é novo no GitHub, este guia vai te ajudar de forma bem simples!

---

## 📋 O que é GitHub?

GitHub é um site onde você armazena seu código na nuvem. É como um "Google Drive" para programadores. Você pode:
- Guardar seu projeto online
- Compartilhar com outras pessoas
- Colaborar em equipe
- Ter histórico de todas as mudanças

---

## 🎯 Passo 1: Criar Conta no GitHub

1. Acesse [github.com](https://github.com)
2. Clique em **"Sign up"** (canto superior direito)
3. Preencha:
   - **Email**: seu email
   - **Password**: uma senha forte
   - **Username**: seu nome de usuário (ex: `seu-nome-aqui`)
4. Clique em **"Create account"**
5. Verifique seu email e confirme a conta

✅ **Pronto! Você tem uma conta GitHub!**

---

## 📁 Passo 2: Criar um Repositório

Um repositório é uma "pasta" no GitHub onde seu projeto fica armazenado.

1. Acesse [github.com](https://github.com) (já logado)
2. Clique no ícone **"+"** (canto superior direito)
3. Clique em **"New repository"**
4. Preencha:
   - **Repository name**: `controle-precos`
   - **Description**: "Sistema de gerenciamento de preços de produtos"
   - **Visibility**: Escolha **"Public"** (qualquer um pode ver) ou **"Private"** (só você)
   - **Initialize this repository with**: Deixe desmarcado
5. Clique em **"Create repository"**

✅ **Seu repositório foi criado!**

Você verá uma página com instruções. Copie a URL que aparece, será algo como:
```
https://github.com/seu-usuario/controle-precos.git
```

---

## 💻 Passo 3: Instalar Git no Seu Computador

Git é o programa que você usa para enviar código para o GitHub.

### Windows:
1. Acesse [git-scm.com](https://git-scm.com)
2. Clique em **"Download for Windows"**
3. Execute o instalador
4. Clique em **"Next"** em todas as telas
5. Clique em **"Finish"**

### Mac:
1. Abra o Terminal
2. Cole: `xcode-select --install`
3. Pressione Enter e aguarde

### Linux:
```bash
sudo apt-get install git
```

✅ **Git instalado!**

---

## 🔑 Passo 4: Configurar Git (Uma Vez)

Abra o **Terminal** (ou **Command Prompt** no Windows) e execute:

```bash
git config --global user.name "Seu Nome"
git config --global user.email "seu-email@example.com"
```

Substitua:
- `Seu Nome` pelo seu nome real
- `seu-email@example.com` pelo email da sua conta GitHub

✅ **Git configurado!**

---

## 📤 Passo 5: Enviar Projeto para GitHub

Agora vamos enviar o projeto!

### No Terminal/Command Prompt:

1. **Navegue até a pasta do projeto:**
```bash
cd /home/ubuntu/controle-precos
```

2. **Verifique se git está inicializado:**
```bash
git status
```

Se aparecer algo como "On branch main", está tudo certo. Se não, execute:
```bash
git init
```

3. **Adicione o repositório do GitHub:**
```bash
git remote add origin https://github.com/SEU-USUARIO/controle-precos.git
```

⚠️ **Importante:** Substitua `SEU-USUARIO` pelo seu username do GitHub!

4. **Verifique se foi adicionado:**
```bash
git remote -v
```

Deve aparecer duas linhas com a URL que você copiou.

5. **Envie o projeto:**
```bash
git push -u origin main
```

Pode pedir seu **username** e **password** do GitHub. Digite e pressione Enter.

✅ **Projeto enviado para GitHub!**

---

## 🔍 Passo 6: Verificar no GitHub

1. Acesse [github.com](https://github.com)
2. Clique no seu repositório **"controle-precos"**
3. Você deve ver todos os arquivos do projeto!

✅ **Sucesso! Seu projeto está no GitHub!**

---

## 🧪 Passo 7: Testar Clonando em Outro Local

Vamos testar se tudo funciona clonando o projeto:

1. **Abra uma nova pasta:**
```bash
mkdir ~/teste-github
cd ~/teste-github
```

2. **Clone o repositório:**
```bash
git clone https://github.com/SEU-USUARIO/controle-precos.git
cd controle-precos
```

3. **Instale as dependências:**
```bash
pnpm install
```

4. **Configure as variáveis de ambiente:**
```bash
# Copie o arquivo de exemplo
cp ENVIRONMENT.md .env

# Edite o arquivo .env com suas credenciais
# (Você pode usar um editor de texto)
```

5. **Inicie o servidor:**
```bash
pnpm dev
```

6. **Acesse no navegador:**
```
http://localhost:5173
```

✅ **Tudo funcionando!**

---

## 📝 Passo 8: Fazer Mudanças e Enviar Novamente

Quando você fizer mudanças no projeto:

1. **Veja o que mudou:**
```bash
git status
```

2. **Adicione as mudanças:**
```bash
git add .
```

3. **Crie um "commit" (salve as mudanças):**
```bash
git commit -m "Descrição do que você mudou"
```

Exemplo:
```bash
git commit -m "Adicionar novo produto ao banco de dados"
```

4. **Envie para GitHub:**
```bash
git push origin main
```

✅ **Mudanças enviadas!**

---

## 🎓 Termos Importantes

| Termo | Significado |
|-------|------------|
| **Repository** | Pasta do projeto no GitHub |
| **Clone** | Copiar um projeto do GitHub para seu computador |
| **Commit** | Salvar mudanças com uma mensagem |
| **Push** | Enviar mudanças para GitHub |
| **Pull** | Baixar mudanças do GitHub |
| **Branch** | Uma "versão" do projeto (padrão é "main") |
| **Remote** | Conexão com o repositório no GitHub |

---

## ❓ Dúvidas Comuns

### "Erro: permission denied"
**Solução:** Verifique se você está logado no GitHub e se o username está correto.

### "Erro: fatal: not a git repository"
**Solução:** Você não está na pasta correta. Execute:
```bash
cd /home/ubuntu/controle-precos
```

### "Erro: rejected ... (fetch first)"
**Solução:** Execute:
```bash
git pull origin main
git push origin main
```

### "Como compartilhar com outra pessoa?"
**Solução:** 
1. Vá em **Settings** do repositório
2. Clique em **Collaborators**
3. Adicione o email da pessoa

---

## 🎉 Parabéns!

Você agora sabe como:
- ✅ Criar uma conta GitHub
- ✅ Criar um repositório
- ✅ Enviar código para GitHub
- ✅ Clonar e testar o projeto
- ✅ Fazer mudanças e enviar novamente

**Próximos passos:**
1. Compartilhe o link do repositório com sua equipe
2. Faça mudanças e pratique enviando para GitHub
3. Leia mais em [github.com/features/actions](https://github.com/features/actions) para aprender sobre automação

---

## 📚 Recursos Úteis

- [GitHub Docs](https://docs.github.com) - Documentação oficial
- [Git Cheat Sheet](https://github.github.com/training-kit/downloads/github-git-cheat-sheet.pdf) - Comandos rápidos
- [YouTube - Git para Iniciantes](https://www.youtube.com/results?search_query=git+para+iniciantes) - Vídeos tutoriais

---

**Dúvidas? Releia este guia ou procure ajuda online!** 🚀
