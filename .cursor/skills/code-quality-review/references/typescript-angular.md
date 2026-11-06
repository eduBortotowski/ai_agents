# TypeScript / JavaScript / Angular

## Tipagem
- `strict` desativado no `tsconfig`.
- Uso de `any`, asserções `as` sem necessidade, `@ts-ignore` sem justificativa.

## JavaScript moderno
- `var` em vez de `const`/`let`; `==` em vez de `===`.
- Promises sem tratamento de erro; `async/await` sem `try/catch`; callbacks aninhados.

## Angular / RxJS
- Subscriptions sem cancelamento (use `async` pipe, `takeUntilDestroyed` ou equivalente).
- `subscribe` aninhado.
- Lógica pesada no template; ausência de `trackBy`/`track` em listas.
- `ChangeDetectionStrategy.OnPush` ausente onde faz diferença.
- Componentes grandes demais; serviços com múltiplas responsabilidades.
- Formulários não tipados.
- Ausência de lazy loading.
- Interceptors para auth/erros ausentes.

## Ferramentas a recomendar
`eslint` (com `angular-eslint`/`typescript-eslint`), `prettier`.