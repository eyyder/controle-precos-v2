# 📤 Como Publicar no GitHub (Com Sincronização)

Guia passo a passo para publicar seu site no GitHub mantendo sincronizado com o Manus!

---

## 🎯 Resumo Rápido

Você vai ter **DOIS sites funcionando**:
- **Site 1:** Manus (já está online: `precosapp-mzq8rzqc.manus.space`)
- **Site 2:** GitHub (você vai criar agora)

**Ambos compartilham o MESMO banco de dados** = Tudo sincronizado!

---

## 📋 Passo 1: Criar Repositório no GitHub

1. Acesse [github.com](https://github.com)
2. Clique no **"+"** (canto superior direito)
3. Clique em **"New repository"**
4. Preencha:
   - **Repository name:** `mercearia-do-loirinho`
   - **Description:** "Sistema de controle de preços"
   - **Visibility:** Public (qualquer um vê) ou Private (só você)
5. Clique em **"Create repository"**

✅ **Repositório criado!**

---

## 📦 Passo 2: Enviar o Arquivo ZIP

1. **Baixe o arquivo** `controle-precos.zip` que você recebeu
2. **No GitHub**, clique em **"Add file"** > **"Upload files"**
3. **Arraste o ZIP** para a caixa (ou clique para selecionar)
4. Clique em **"Commit changes"**

✅ **Arquivo enviado!**

---

## 🗂️ Passo 3: Extrair o ZIP (Opcional)

Se quiser ver os arquivos no GitHub:

1. Clique no arquivo `controle-precos.zip`
2. Clique em **"..."** (três pontinhos)
3. Clique em **"Delete"** (para remover o ZIP depois de extrair)

Ou deixe o ZIP lá mesmo, não faz diferença.

---

## 🔐 Passo 4: Adicionar Banco de Dados Compartilhado

Este é o passo **MAIS IMPORTANTE** para sincronização!

### 4.1: Obter a URL do Banco Manus

1. Acesse o painel de gerenciamento do **Manus**
2. Vá em **Settings** > **Database**
3. Você verá algo como:
   ```
   Host: seu-host.tidb.cloud
   Port: 4000
   Username: seu-usuario
   Password: sua-senha
   Database: seu-banco
   ```

4. **Construa a URL:**
   ```
   mysql://seu-usuario:sua-senha@seu-host.tidb.cloud:4000/seu-banco
   ```

⚠️ **Guarde essa URL em um local seguro!**

### 4.2: Adicionar no GitHub

1. No GitHub, vá em **Settings** (engrenagem)
2. Clique em **"Secrets and variables"** > **"Actions"**
3. Clique em **"New repository secret"**
4. Preencha:
   - **Name:** `DATABASE_URL`
   - **Value:** (Cole a URL que você copiou)
5. Clique em **"Add secret"**

✅ **Banco de dados compartilhado configurado!**

---

## 🚀 Passo 5: Publicar o Site (Escolha Uma Opção)

Agora você precisa publicar o site GitHub em um serviço. Escolha uma:

### **Opção A: Vercel (Recomendado - Mais Fácil)**

1. Acesse [vercel.com](https://vercel.com)
2. Clique em **"Sign up"** (ou login se já tem conta)
3. Clique em **"Import Project"**
4. Clique em **"Import Git Repository"**
5. Selecione seu repositório `mercearia-do-loirinho`
6. Clique em **"Import"**
7. **Configure as variáveis de ambiente:**
   - Clique em **"Environment Variables"**
   - Adicione: `DATABASE_URL` = (a URL do banco)
8. Clique em **"Deploy"**

✅ **Site publicado! Você receberá um link como:** `https://mercearia-do-loirinho.vercel.app`

### **Opção B: Netlify**

1. Acesse [netlify.com](https://netlify.com)
2. Clique em **"Sign up"** (ou login)
3. Clique em **"Add new site"** > **"Import an existing project"**
4. Conecte seu GitHub
5. Selecione `mercearia-do-loirinho`
6. Configure as variáveis de ambiente
7. Clique em **"Deploy"**

### **Opção C: GitHub Pages (Mais Simples)**

1. No GitHub, vá em **Settings**
2. Clique em **"Pages"**
3. Em **"Source"**, selecione **"main"**
4. Clique em **"Save"**

✅ **Site publicado em:** `https://seu-usuario.github.io/mercearia-do-loirinho`

---

## ✅ Verificar Se Está Sincronizado

### Teste 1: Adicionar Produto no Manus
1. Acesse o site **Manus**
2. Clique em **"+ NOVO PRODUTO"**
3. Adicione um produto qualquer
4. Acesse o site **GitHub** (Vercel/Netlify)
5. **O produto deve aparecer lá também!**

### Teste 2: Editar Produto no GitHub
1. Acesse o site **GitHub**
2. Clique em um produto
3. Clique em **"Editar"**
4. Mude o preço
5. Acesse o site **Manus**
6. **A mudança deve aparecer lá também!**

Se aparecer, **está funcionando perfeitamente!** 🎉

---

## 📱 Usar os Dois Sites

Agora você pode:

- ✅ **Usar o Manus** no celular para adicionar produtos no supermercado
- ✅ **Usar o GitHub** no computador para análises
- ✅ **Compartilhar o Manus** com sua esposa
- ✅ **Tudo sincronizado automaticamente!**

---

## 🔗 Links Importantes

| O Quê | Link |
|-------|------|
| Site Manus | `precosapp-mzq8rzqc.manus.space` |
| Repositório GitHub | `https://github.com/seu-usuario/mercearia-do-loirinho` |
| Site GitHub (Vercel) | `https://mercearia-do-loirinho.vercel.app` |
| Painel Manus | Acesse no gerenciador |

---

## ⚠️ Importante

- ✅ **Não compartilhe a URL do banco** (tem sua senha!)
- ✅ **Faça backup regularmente** (Manus já faz automaticamente)
- ✅ **Teste em um site antes de fazer em produção**
- ✅ **Mantenha a senha do banco segura**

---

## 🆘 Problemas?

### "O site GitHub não vê os produtos"
- Verifique se a `DATABASE_URL` está correta
- Verifique se o banco está acessível
- Reinicie o site

### "Mudanças não sincronizam"
- Aguarde alguns segundos
- Atualize a página (F5)
- Verifique se ambos usam a mesma `DATABASE_URL`

### "Erro de conexão com banco"
- Verifique username e password
- Verifique se o usuário tem permissão
- Teste a URL manualmente

---

## 🎉 Parabéns!

Você agora tem:
- ✅ Site Manus funcionando
- ✅ Site GitHub funcionando
- ✅ Ambos sincronizados
- ✅ Tudo pronto para usar!

---

**Próximo passo:** Compartilhe os links com sua esposa e comecem a usar! 🚀

---

**Última atualização:** Março 2026
