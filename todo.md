# Controle de Preços - TODO

## Backend & Database
- [x] Schema de banco de dados (produtos, histórico, alertas, usuários)
- [x] Migrations SQL aplicadas
- [x] APIs tRPC: CRUD de produtos
- [x] APIs tRPC: histórico de compras
- [x] APIs tRPC: alertas de variação de preço
- [x] API tRPC: importação em massa de produtos
- [x] Testes unitários das APIs (14 testes passando)

## Frontend - Estética Blueprint
- [x] Configurar tema com paleta azul royal profundo e padrão de grade
- [x] Componentes base com linhas brancas e marcadores técnicos
- [x] Tipografia sans-serif branca em negrito
- [x] Layout responsivo mobile-first

## Frontend - Funcionalidades
- [x] Página de listagem de produtos com busca rápida
- [x] Autocompletar/lista suspensa para busca de produtos
- [x] Página de cadastro de novo produto
- [x] Página de visualização de histórico de preços por produto
- [x] Página de histórico de compras (todas as transações)
- [x] Página de alertas de variação de preço
- [x] Página de importação em massa (upload de arquivo)
- [x] Página de categorias/variações de produtos

## Funcionalidades Avançadas
- [x] Atualização em tempo real de preços (via tRPC queries)
- [x] Cálculo automático de variação percentual de preço
- [x] Geração automática de alertas quando variação > X%
- [x] Compartilhamento de acesso entre múltiplos usuários (via autenticação Manus)
- [x] Sincronização de dados entre dispositivos

## Testes & Deploy
- [x] Testes de fluxos completos
- [x] Otimização de performance mobile
- [x] Importação de 206 produtos do arquivo Excel
- [ ] Checkpoint final e publicação do site

## Melhorias Solicitadas
- [x] Adicionar função de excluir produtos com confirmação
- [x] Melhorar registro de datas (createdAt, updatedAt)
- [x] Mostrar data de alteração na interface

## Funcionalidades em Desenvolvimento
- [x] Exportar relatório em PDF com preços e histórico

## Sistema de Backup
- [x] Criar serviço de backup com exportação em JSON
- [x] Implementar agendador de backup diário (executa às 2:00 AM)
- [x] Adicionar API para download e restauração
- [x] Criar página de gerenciamento de backups
- [x] Adicionar botão de backups na página inicial

## Listagem e Análise de Produtos
- [x] Criar API para calcular estatísticas de preços (mín, máx, último)
- [x] Desenvolver página de listagem completa de produtos
- [x] Mostrar margem de lucro em todas as visualizações
- [x] Implementar exportação em Excel com análise de preços
- [x] Adicionar botão de listagem na página inicial


## Integração Google Drive
- [x] Configurar autenticação OAuth com Google Drive (googleapis)
- [x] Implementar upload automático de backups para Google Drive
- [x] Adicionar funcionalidade de download manual
- [x] Criar interface para gerenciar backups na nuvem
- [x] Página de gerenciamento com upload/download/delete de backups


## Bugs a Corrigir
- [x] PDF de listagem não lista todos os 267 produtos (agora lista em múltiplas páginas)
- [x] Download de backup não está funcionando (corrigido)


## Bugs Críticos Reportados
- [x] Download de backup não funciona no celular (corrigido com fetch direto)
- [x] Backup não está sendo criado/salvo (corrigido import ESM)
- [x] Adicionar preço de venda na listagem de produtos (adicionado coluna VENDA)


## Bugs em Investigação
- [x] Download de backup ainda não funciona (corrigido com rota Express direto)


## Novas Funcionalidades
- [x] Implementar função de editar produtos (página completa com formulário)

## Backup Automático para GitHub
- [ ] Criar exportação automática de dados para GitHub (JSON diário)
- [ ] Adicionar botão de backup manual para GitHub na interface

## Redesign UX Mobile (Supermercado)
- [x] Redesenhar página inicial: busca dominante no topo, sem menu poluído
- [x] Busca fuzzy: ignorar acentos, maiúsculo/minúsculo (cafe = café = CAFÉ)
- [x] Resultados da busca mostram preço custo, venda e margem inline
- [x] Comparador de preço em tempo real na página do produto (variação ao digitar)
- [x] Separar ferramentas (PDF, Backup, Importar) em menu secundário (engrenagem)
- [x] Barra de navegação inferior fixa com atalhos principais
- [x] Histórico de compras mostra nome do produto (não só ID)

## Margens Sugeridas por Categoria
- [x] Criar tabela de margens sugeridas no banco de dados
- [x] Popular com margens típicas de mercearia de bairro
- [x] Integrar sugestão de margem no formulário de novo produto
- [x] Integrar sugestão de margem no formulário de edição de produto
- [x] Criar página de gerenciamento de margens sugeridas

## Melhorias v3
- [x] Corrigir sugestão de margem no formulário de novo produto
- [x] Adicionar campo para editar nome do produto no formulário de edição
- [x] Implementar botão "Clonar Produto" na página de detalhes do produto

## Alertas de Margem Abaixo do Recomendado (SEBRAE)
- [x] Criar lógica de avaliação de margem por categoria com referências SEBRAE
- [x] Componente de alerta reutilizável (MarginWarning)
- [x] Alerta na página de detalhes do produto
- [x] Alerta nos resultados da busca rápida
- [x] Painel de produtos com margem crítica na tela inicial

## Relatório de Margem por Categoria
- [x] Página de relatório de margem por categoria
- [x] Exportação Excel do relatório por categoria
- [x] Verificação de prontidão para GitHub

## Auditoria e Correção do Cálculo de Margem
- [x] Auditar todas as ocorrências do cálculo de margem no código
- [x] Corrigir inconsistências e padronizar fórmula: ((venda - custo) / venda) * 100

## Atualização das Regras de Preços (tabela personalizada)
- [x] Atualizar marginEvaluator.ts com 8 categorias + regra padrão personalizadas
- [x] Atualizar banco de dados de margens sugeridas com novos valores
