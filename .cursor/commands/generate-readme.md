# Gerar ou atualizar o README.md do projeto

Gere ou atualize o `README.md` da raiz do projeto, seguindo o template padrão. Se o usuário informou instruções adicionais após o comando, repasse-as ao subagente.

1. Use o subagente `technical-docs-writer` para analisar o projeto inteiro e gravar o `README.md`.
2. Quando ele terminar, apresente ao usuário o resumo final: modo (criado ou atualizado), tipo detectado, seções incluídas e omitidas, o que foi preservado, corrigido ou removido, e as pendências (`TODO`).
3. Não altere nenhum outro arquivo. Sugira ao usuário revisar o diff do `README.md` antes de commitar.