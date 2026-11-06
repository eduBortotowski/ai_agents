---
name: project-recon
description: Reconhece um projeto antes de qualquer análise. Detecta se é Frontend, Backend, Microserviços ou misto, identifica linguagens, frameworks, gerenciador de dependências, Docker, CI/CD e configurações de qualidade existentes. Use sempre como primeira etapa de uma revisão de segurança ou de qualidade.
---

# Reconhecimento de projeto

## Quando usar
Primeira etapa de qualquer revisão. Nada de achados antes de concluir isto.

## Passos
1. Mapeie a árvore de diretórios (2 a 3 níveis) e os arquivos de configuração da raiz.
2. Detecte o **tipo** pelos sinais abaixo e registre a justificativa:
   - **Frontend:** `package.json` com Angular/React/Vue/Svelte/Next, `angular.json`, `vite.config`, sem servidor de aplicação próprio, build gerando estáticos.
   - **Backend/API:** `manage.py`/`settings.py` (Django), `requirements.txt`/`pyproject.toml` com Flask/FastAPI, `pom.xml`/`build.gradle`, Express/Nest; rotas, models, serializers, migrations.
   - **Microserviços:** vários serviços independentes, `docker-compose` com múltiplos serviços de aplicação, gateway, filas/mensageria, manifests Kubernetes/Helm.
   - **Misto:** trate cada parte separadamente.
3. Liste **linguagens e frameworks predominantes** (definem quais checklists carregar), gerenciador de dependências e lockfiles.
4. Localize Dockerfiles, `docker-compose`, CI/CD (`.github/workflows`, `.gitlab-ci.yml`) e ambientes (dev, homologação, produção).
5. Verifique se é repositório Git e se há `.gitignore`/`.dockerignore`.
6. Localize configurações de qualidade já existentes: `ruff`, `flake8`, `black`, `mypy`, `eslint`, `prettier`, `tsconfig`, testes.

## Saída (bloco curto, em Markdown)
- Tipo detectado e por quê
- Linguagens/frameworks
- Infra e CI/CD encontrados
- Configs de qualidade existentes
- Escopo analisado