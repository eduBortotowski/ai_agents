---
name: code-quality-review
description: Valida o código contra as boas práticas da linguagem adotada (Python/Django, TypeScript/Angular, SQL e outras) e aponta falhas ou incompatibilidades com guias oficiais como PEP 8 e o Angular Style Guide. Use em revisões de qualidade ou quando pedirem para checar se o código segue as boas práticas da linguagem.
---

# Revisão de qualidade e boas práticas da linguagem

## Pré-requisito
Execute antes a skill `project-recon` para saber as linguagens e as configs de qualidade do projeto.

## Princípios
1. **Boas práticas têm fonte.** Só reporte desvios apoiados em guias oficiais ou consagrados (PEP 8, Angular Style Guide etc.). Nada de preferência pessoal.
2. **Respeite o projeto.** As configs existentes (`ruff`, `flake8`, `eslint`, `prettier`, `mypy`, `tsconfig`) são a referência.
3. **Foque no que importa:** correção, manutenção, desempenho e segurança. Não gaste o relatório com estilo que um formatador resolve.
4. **Agrupe padrões recorrentes:** reporte uma vez, com a contagem e 2 ou 3 exemplos.

## Referências por linguagem (carregue só as que se aplicam)
- Python / Django / DRF: `references/python-django.md`
- TypeScript / JavaScript / Angular: `references/typescript-angular.md`
- Outras linguagens e SQL: `references/other-languages.md`

## Qualidade geral (todas as linguagens)
- Existência e cobertura de testes, sobretudo em regras de negócio e autenticação.
- Tratamento de erros consistente; logs úteis sem dados sensíveis.
- Dependências não usadas, `TODO`/`FIXME` críticos, código comentado em excesso.
- README e instruções de ambiente suficientes para rodar o projeto com segurança.

## Severidade
Alto (bug provável ou risco à manutenção), Médio (dívida técnica relevante), Baixo (melhoria).

## Formato de cada achado
`[SEVERIDADE] Título` · Local (`arquivo:linha`, ou contagem + exemplos) · Boa prática de referência (ex.: PEP 8) · Por que importa · Como corrigir.