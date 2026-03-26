# 🔄 Sincronização: Manus + GitHub (Dois Sites, Um Banco de Dados)

Este guia explica como ter **dois sites funcionando simultaneamente** que compartilham o **mesmo banco de dados**. Qualquer mudança em um site aparece no outro automaticamente!

---

## 🎯 Como Funciona

```
┌─────────────────────────────────────────────────┐
│          BANCO DE DADOS ÚNICO (MySQL)           │
│  (Armazena todos os produtos, histórico, etc)   │
└─────────────────────────────────────────────────┘
         ↑                              ↑
         │                              │
    ┌────┴────┐                  ┌─────┴─────┐
    │   MANUS │                  │  GITHUB   │
    │  (Site 1)│                  │  (Site 2) │
    └─────────┘                  └───────────┘
```

**Resultado:**
- Você adiciona um produto no **Manus** → Aparece no **GitHub**
- Você edita um produto no **GitHub** → Aparece no **Manus**
- Você exclui um produto em qualquer lugar → Desaparece dos dois
- **Tudo sincronizado automaticamente!**

---

## 📋 Passo 1: Obter Informações do Banco de Dados Manus

Seu site Manus já tem um banco de dados funcionando. Você precisa das informações de conexão:

### Onde encontrar:

1. Acesse o painel de gerenciamento do Manus
2. Vá em **Settings** > **Database**
3. Você verá informações como:
   ```
   Host: seu-host.tidb.cloud
   Port: 4000
   Username: seu-usuario
   Password: sua-senha
   Database: seu-banco
   ```

4. **Copie a URL de conexão completa:**
   ```
   mysql://usuario:senha@host:4000/banco
   ```

⚠️ **IMPORTANTE:** Guarde essa URL em um local seguro!

---

## 📋 Passo 2: Preparar o Arquivo ZIP para GitHub

O arquivo ZIP que você vai enviar para GitHub já tem a estrutura correta. Você só precisa:

1. Baixar o arquivo `controle-precos.zip`
2. Enviar para GitHub (conforme o guia anterior)

---

## 🚀 Passo 3: Publicar no GitHub (Com Sincronização)

Depois que você enviar o ZIP para GitHub e extrair os arquivos:

1. **Vá para o repositório no GitHub**
2. **Clique em "Settings"** (engrenagem)
3. **Clique em "Secrets and variables"** > **"Actions"**
4. **Clique em "New repository secret"**
5. **Adicione a variável:**
   - **Name:** `DATABASE_URL`
   - **Value:** `mysql://usuario:senha@host:4000/banco` (a URL que você copiou)
6. **Clique em "Add secret"**

✅ **Pronto! GitHub agora tem acesso ao mesmo banco de dados!**

---

## 🔗 Passo 4: Conectar o GitHub ao Seu Banco

Quando você publicar o site GitHub (usando Vercel, Netlify ou outro serviço):

1. **Configure a variável de ambiente:**
   ```
   DATABASE_URL=mysql://usuario:senha@host:4000/banco
   ```

2. **O site GitHub vai usar o MESMO banco que o Manus**

3. **Tudo fica sincronizado!**

---

## ✅ Verificar Se Está Funcionando

### No Manus:
1. Adicione um novo produto
2. Vá para o site GitHub
3. **O produto deve aparecer lá também!**

### No GitHub:
1. Edite um produto
2. Vá para o site Manus
3. **A mudança deve aparecer lá também!**

Se aparecer, está funcionando perfeitamente! 🎉

---

## ⚠️ Cuidados Importantes

### Não Faça Isso:

❌ **Não compartilhe a URL do banco de dados** com ninguém (tem sua senha!)
❌ **Não mude o banco de dados** sem avisar (pode quebrar os dois sites)
❌ **Não delete o banco** (os dois sites param de funcionar)

### Faça Isso:

✅ **Faça backup regularmente** (o Manus já faz automaticamente)
✅ **Teste mudanças em um site antes de fazer em produção**
✅ **Mantenha a URL do banco segura**

---

## 🆘 Problemas Comuns

### "O site GitHub não vê os produtos do Manus"

**Solução:**
1. Verifique se a `DATABASE_URL` está correta
2. Verifique se o banco está acessível de fora (firewall)
3. Reinicie o site GitHub

### "Mudanças no GitHub não aparecem no Manus"

**Solução:**
1. Aguarde alguns segundos (pode ter delay)
2. Atualize a página do Manus (F5)
3. Verifique se ambos estão usando a mesma `DATABASE_URL`

### "Erro: 'Access denied for user'"

**Solução:**
1. Verifique se o username e password estão corretos
2. Verifique se o usuário tem permissão no banco
3. Teste a conexão manualmente

---

## 📊 Estrutura de Dados Compartilhada

Ambos os sites compartilham as mesmas tabelas:

```
Banco de Dados
├── users (usuários)
├── products (produtos)
├── purchaseHistory (histórico de compras)
├── priceAlerts (alertas de preço)
└── categories (categorias)
```

Qualquer mudança em qualquer tabela aparece nos dois sites!

---

## 🔄 Fluxo de Trabalho Recomendado

1. **Desenvolvimento:** Use o site Manus (mais rápido)
2. **Testes:** Teste mudanças no GitHub
3. **Produção:** Ambos funcionam sincronizados
4. **Backup:** O Manus faz automaticamente

---

## 📱 Usar em Múltiplos Dispositivos

Com a sincronização, você pode:

- ✅ Usar o **Manus no celular** para adicionar produtos
- ✅ Usar o **GitHub no computador** para fazer análises
- ✅ Compartilhar o **Manus com sua esposa** para editar juntos
- ✅ **Tudo sincronizado automaticamente!**

---

## 🎯 Próximos Passos

1. **Obter a URL do banco de dados** do Manus
2. **Enviar o ZIP para GitHub**
3. **Adicionar a variável DATABASE_URL** no GitHub
4. **Publicar o site GitHub**
5. **Testar a sincronização**

---

## 📞 Suporte

Se tiver dúvidas sobre sincronização, me avise! Estou aqui para ajudar! 🚀

---

**Última atualização:** Março 2026
