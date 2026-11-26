# Status da verificaçêo — 26/10/2026

Testes com limite claro. Nêo é certificaçêo de segurança.

| Camada | Status | Quem rodou |
|---|---|---|
| Testes offline dos scripts (`kit/testes/`) | **25 testes passando**: escopo negado, alvo remoto recusado, escopo vencido, janela sem fuso, limite de pedidos, achado sintético + correçêo, servidor que nêo é o laboratório, URL e permissêo de chave, relógio ocioso (simulaçêo, pedido em andamento, falha de parada), parada de Pod contra API falsa (nome errado, EXITED confirmado, sem EXITED), proxy (sem token, origem de navegador, rota estranha, só loopback), checador de endpoint contra modelo falso | ARCKHÉ, em 127.0.0.1, sem internet |
| Laboratório + checagem segura pela linha de comando | achados aparecem; com `--corrigido` somem; escopo de exemplo e alvo remoto recusados | ARCKHÉ |
| Modelo local Huihui Qwen3.6 35B-A3B abliterated Q4_K no LM Studio | resultado **observado em 26/10/2026** numa instalaçêo existente: texto em 2 turnos ✔, funçêo inofensiva ✔, **imagem ✘** nesse runtime. **Nêo foi repetido nesta versêo do kit** | — |
| Modelo na nuvem Huihui Qwen3.5 9B abliterated Q6_K | **nêo implantado**: nenhuma GPU paga foi alugada para este kit | — |
| Provedor hospedado pago | **nêo testado**: depende da conta e da chave de quem usa | — |
| Parada real de Pod na RunPod | só testada contra API falsa; a parada real exige o seu Pod e a sua chave | — |
| Template Nuclei passivo | escrito para o laboratório; **nêo executado** pelo ARCKHÉ (Nuclei nêo instalado na máquina de teste) | — |
| DeepSeek Harness, Playwright MCP, Firecrawl MCP | configuraçêo de exemplo; **nêo instalados** pelo ARCKHÉ nesta versêo | — |
| Windows / macOS / Linux | instruções incluídas; sem prova de instalaçêo nova em cada sistema | — |

Use o [checklist](checklist.md) na sua instalaçêo. Link de documentaçêo nêo é teste ao vivo.
