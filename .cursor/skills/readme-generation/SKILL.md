---
name: readme-generation
description: Gera ou atualiza o README.md de um projeto a partir da análise do repositório, seguindo obrigatoriamente o template padrão de README. Detecta o tipo (App, API ou Microserviço), cria o README se não existir ou atualiza o existente preservando o conteúdo autoral válido. Use quando pedirem para criar, atualizar, revisar ou padronizar a documentação do projeto.
---

# Geração e atualização de README

## Pré-requisito
Execute antes a skill `project-recon`. Mapeamento de tipos:
- Frontend → **App**
- Backend/API → **API**
- Microserviços → **Microserviço**
- Misto (ex.: frontend + backend no mesmo repositório) → um **único README na raiz**, subdividindo Stack, Instalação e Uso por parte (frontend, backend).

## Fonte da verdade do formato
O formato é definido **exclusivamente** em `references/readme-template.md`. Leia-o por inteiro antes de escrever. Ordem e títulos das seções são fixos.

## Princípios
1. **Não invente nada.** Documente só o que você confirmou no repositório. Se não achou, a seção condicional é removida, ou a informação essencial fica como pendência (ver passo 5).
2. **Código é a verdade.** Se o README existente contradiz o código, vale o código.
3. **Nunca exponha segredos.** Somente nomes de variáveis e exemplos fictícios. Sem credenciais, tokens, IPs ou hosts internos.
4. **Conciso e objetivo, com senioridade e clareza.** Frases curtas, sem adjetivos de marketing, sem repetir o óbvio.
5. **Um único README principal** na raiz, com toda a documentação.

## Passos

### 1. Reconhecimento
Rode `project-recon`: tipo, linguagens, frameworks, infraestrutura e configs de qualidade.

### 2. Modo de operação
Procure `README.md` na raiz.
- **Não existe:** modo **criar**.
- **Existe:** modo **atualizar**. Leia-o inteiro antes de qualquer alteração.

### 3. Coleta de evidências
Use `references/evidence-sources.md` para saber onde achar cada informação (comandos, versões, variáveis, rotas, testes, deploy). Anote a origem de cada fato.

### 4. Redação
Preencha o template conforme o tipo detectado:
- Aplique as seções obrigatórias e só as condicionais cujas condições você comprovou.
- Use os blocos específicos do tipo (App, API ou Microserviço) descritos no template.
- Idioma: português (pt-BR), a menos que o README existente esteja em outro idioma (nesse caso, mantenha o idioma dele).

**Regras do modo atualizar:**
- **Preserve** o que for autoral e continuar válido: descrição do projeto, badges, imagens e capturas de tela, licença, contatos.
- **Corrija** o que estiver desatualizado (comandos, versões, variáveis, caminhos), conferindo no código.
- **Reorganize** o conteúdo existente na ordem e nos títulos do template.
- Conteúdo válido que não tem seção no template vai para `## Informações adicionais`, no final, sem ser apagado.
- Remova apenas o que for comprovadamente falso ou obsoleto, e liste isso no resumo final.

### 5. Informações que não dá para inferir
Se algo essencial não puder ser confirmado (ex.: propósito de negócio, contato), não preencha por suposição. Deixe `<!-- TODO: <o que falta> -->` na seção correspondente e liste os TODOs no resumo final.

### 6. Validação antes de gravar
- Todo comando citado existe (script em `package.json`, `Makefile`, `manage.py`, compose etc.).
- Toda variável de ambiente citada aparece no código, no `.env.example` ou no compose.
- Todo caminho citado existe. Todo endpoint citado existe nas rotas.
- Versões batem com os manifestos.
- Nenhum valor real de segredo.
- Nenhum placeholder `<...>` ou comentário de instrução do template sobrando (exceto os `TODO`).
- Seções na ordem do template.

### 7. Gravação
Grave `README.md` na raiz, **completo** (o arquivo inteiro, não trechos). Não altere nenhum outro arquivo.

## Resumo final (mensagem ao usuário)
- Modo (criado ou atualizado) e tipo detectado
- Seções incluídas e seções omitidas (com o motivo)
- Se atualizado: o que foi preservado, o que foi corrigido e o que foi removido
- Pendências (`TODO`) e o que não foi possível verificar