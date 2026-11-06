---
name: secrets-and-repo-hygiene
description: Procura segredos e variáveis de ambiente fixadas no código e identifica arquivos e pastas que não deveriam ser commitados, gerando o bloco de .gitignore recomendado. Use em revisões de segurança, antes de commits e deploys, ou quando suspeitarem de credenciais expostas.
---

# Segredos e higiene do repositório

## Regras
- Nunca reproduza um segredo completo. Mascare (`AKIA****************XYZ`).
- Diferencie segredo real de valor fictício (`changeme`, `your-key-here`, `.env.example`, testes).
- Se um segredo já está versionado: **revogar e rotacionar**. Adicionar ao `.gitignore` não remove do histórico.

## Passo 1: segredos no código e nas configs
Procure em código, `Dockerfile` (`ENV`/`ARG`), `docker-compose`, workflows de CI, configs e coleções de API (Postman/Insomnia):
- Padrões: `password=`, `secret`, `token`, `api_key`, `Bearer `, `BEGIN PRIVATE KEY`, `AKIA`, `ghp_`, `sk-`, URLs com `user:senha@`.
- Arquivos reais versionados: `.env`, `.env.local`, `.env.production`, `environment.prod.ts` com chaves reais.
- **Frontend:** tudo que vai para o bundle é público. Chave secreta em `environment.ts` ou em `VITE_*`/`NEXT_PUBLIC_*`/`REACT_APP_*` conta como exposta.
- Verifique se existe `.env.example` sem valores reais.

## Passo 2: o que está rastreado
- `git ls-files` para ver o que já está versionado.
- Se possível, histórico: `git log -p -S"termo"`, ou `gitleaks`/`trufflehog` se disponíveis.

## Passo 3: `.gitignore` e `.dockerignore`
Compare o que existe com a lista em `references/gitignore-recommended.md` e entregue **somente o que falta**, em bloco pronto para copiar. Para itens sensíveis já rastreados, indique `git rm --cached <arquivo>` como recomendação (não execute).

## Saída
- Lista de segredos/variáveis fixadas (local, confiança, o que migrar para variável de ambiente)
- Arquivos que não deveriam estar versionados
- Bloco de `.gitignore` recomendado
- Recomendações de `.dockerignore`