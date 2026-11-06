# Python / Django / DRF

## Estilo e documentação
- PEP 8 (nomes, imports, tamanho de linha conforme a config do projeto), PEP 257 (docstrings).
- `import *`, imports circulares, código morto.

## Tipagem
- Type hints (PEP 484) em funções públicas; `Any` abusivo; consistência com `mypy`/`pyright` configurado.

## Armadilhas clássicas
- Argumentos mutáveis como padrão (`def f(x=[])`).
- `except:` genérico ou `except Exception: pass`.
- Comparação com `None` usando `==`.
- Variáveis globais mutáveis; shadowing de built-ins (`id`, `type`, `list`).

## Idiomático
- Context managers (`with`) para arquivos e conexões.
- `pathlib` em vez de concatenar caminhos.
- f-strings, comprehensions, `logging` em vez de `print`.
- `enum`/`dataclass` quando fizer sentido.

## Estrutura
- Funções e classes longas, responsabilidades misturadas, duplicação, complexidade ciclomática alta.

## Django / DRF
- Consultas N+1 (faltando `select_related`/`prefetch_related`).
- Regra de negócio em views/serializers em vez de camada de serviço/model.
- Settings sem separação por ambiente.
- Migrations ausentes ou editadas à mão.
- `Meta` mal definido; ausência de testes.

## Ferramentas a recomendar
`ruff` (ou `flake8` + `black` + `isort`), `mypy`, `bandit`, `pip-audit`, `pytest` com cobertura.