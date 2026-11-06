# Revisão completa de segurança e qualidade

Faça uma revisão completa do projeto. O escopo é o que o usuário informar após o comando (pasta, módulo ou diff). Se nada for informado, use o projeto inteiro.

1. Lance **em paralelo** os subagentes `security-reviewer` e `code-quality-reviewer`, passando o escopo no prompt de cada um.
2. Quando ambos terminarem, consolide em **um único relatório**, nesta ordem:
   - Resumo executivo (tipo de projeto, stack, nota de risco de segurança, nota de qualidade, os 3 pontos mais urgentes no total)
   - Achados de segurança
   - Segredos, variáveis de ambiente e higiene do repositório (com o bloco de `.gitignore` recomendado)
   - Achados de qualidade e boas práticas da linguagem
   - Plano de ação priorizado (segurança Crítico/Alto primeiro, depois qualidade relevante)
3. **Não altere nenhum arquivo.** Ao final, pergunte se o usuário quer aplicar as correções, começando pelas de maior severidade.