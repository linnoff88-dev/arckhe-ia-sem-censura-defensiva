# Relatório de achados — exemplo (laboratório sintético)

> Exemplo de formato. O alvo é o laboratório do kit, no seu computador, com dados inventados.
> Nêo é relatório de nenhum sistema real.

| Campo | Valor |
|---|---|
| Alvo | `http://127.0.0.1:8181/` (laboratório sintético) |
| Escopo | `--lab-local-autorizado` (10 minutos, 1 requisiçêo) |
| Dados | só sintéticos |
| Ferramenta | `kit/scripts/checagem_segura.py` |
| Data | AAAA-MM-DD |

## Achado 1 — faltam cabeçalhos de proteçêo do navegador

**O que foi observado (evidência):** a resposta nêo traz `X-Content-Type-Options: nosniff` nem `Referrer-Policy`.

**O que isso significa (com incerteza):** é endurecimento de configuraçêo. Sozinho, nêo prova invasêo,
vazamento nem falha explorável.

**Correçêo proposta:** configurar o servidor (ou o proxy reverso) para enviar os dois cabeçalhos.
No laboratório, a opçêo `--corrigido` simula essa correçêo.

**Reteste:** mesmo alvo, mesmo limite de 1 requisiçêo. Resultado esperado: `"achados": []`.

## Separar sempre

- **Confirmado:** o que você viu na resposta, com a menor evidência possível (sem senha, sem dado pessoal).
- **Hipótese:** o que pode ser, ainda sem prova. Nêo vira "achado" até ser confirmado com segurança.
- **Recomendaçêo:** a correçêo e como retestar dentro do escopo.

Uma varredura sem achados **nêo prova** que o sistema é seguro.
