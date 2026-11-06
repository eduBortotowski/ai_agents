# Onde encontrar cada informação

Cada fato do README precisa ter origem no repositório. Esta tabela indica onde procurar.

| Informação | Onde procurar |
|---|---|
| Nome e descrição | `package.json` (`name`, `description`), `pyproject.toml`, README existente, `angular.json` |
| Versões de linguagem e frameworks | `package.json`, `requirements.txt`, `pyproject.toml`, `.nvmrc`, `.python-version`, `Dockerfile` (imagem base), `runtime.txt` |
| Comandos de execução e build | `scripts` do `package.json`, `Makefile`, `manage.py`, `docker-compose.yml`, `Dockerfile` (`CMD`/`ENTRYPOINT`) |
| Variáveis de ambiente | `.env.example`, `settings.py` (`os.environ`, `env(...)`, `config(...)`), `environment.ts`, `docker-compose.yml`, workflows de CI |
| Rotas e telas (App) | `app.routes.ts`, `*-routing.module.ts`, `src/app/` |
| Endpoints (API) | `urls.py`, `views.py`/`viewsets`, `serializers.py`, rotas do framework; schema OpenAPI, se existir |
| Autenticação | `settings.py` (`REST_FRAMEWORK`, `SIMPLE_JWT`), guards e interceptors do frontend |
| Modelo de dados | `models.py`, migrations, schemas, entidades |
| Integrações externas | clients HTTP, SDKs em `requirements.txt`/`package.json`, URLs em configs |
| Comunicação entre serviços | `docker-compose.yml`, brokers/filas, clients de outros serviços |
| Testes | `pytest.ini`, `tox.ini`, `*.spec.ts`, `tests/`, `karma.conf.js`, `jest.config.*` |
| Qualidade de código | `ruff.toml`, `.flake8`, `.eslintrc*`, `.prettierrc*`, `mypy.ini`, `.pre-commit-config.yaml` |
| Deploy | `Dockerfile`, `docker-compose*.yml`, `.github/workflows/`, `.gitlab-ci.yml`, `nginx.conf`, scripts de deploy |
| Licença | arquivo `LICENSE`, campo `license` nos manifestos |
| Autores e contato | `package.json` (`author`), `pyproject.toml` (`authors`), README existente |
| Contribuição | `CONTRIBUTING.md`, templates de PR/issue, `.github/` |

## Regras de uso
- Se a informação não estiver em nenhuma dessas fontes, **não a inclua**. Deixe um `TODO` ou omita a seção condicional.
- Se duas fontes divergem (ex.: README diz uma versão, manifesto diz outra), vale o manifesto.
- Prefira o `.env.example` para listar variáveis. Se não existir, derive do código e do compose, sem inventar descrições. Descreva apenas o que o código mostra.