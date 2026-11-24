# IA sem censura, do jeito certo â€” seu prÃ³prio modelo para seguranÃ§a defensiva

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="48" />
  <p><strong>Arckhé AI</strong></p>
</div>


[![IA sem censura, do jeito certo](guia/assets/banner.jpg)](https://linnoff88-dev.github.io/

**ðŸ‡§ðŸ‡· [PortuguÃªs](README.md) Â· ðŸ‡ºðŸ‡¸ [English](README.en.md) Â· ðŸ‡ªðŸ‡¸ [EspaÃ±ol](README.es.md)**

## O que Ã©

Este Ã© um kit gratuito do ARCKHÉ, em portuguÃªs, para quem estuda seguranÃ§a e quer um modelo de IA aberto que
nÃ£o recuse perguntas tÃ©cnicas â€” os chamados modelos *abliterated*, dos quais a recusa foi removida. Ele
mostra como ligar esse modelo ao DeepSeek Harness (um agente de cÃ³digo aberto) por uma API, por uma GPU
alugada na RunPod ou pelo LM Studio no seu computador. Traz prompts prontos, scripts que provam se texto,
ferramenta e imagem funcionam, um laboratÃ³rio falso para treinar e uma guarda que para a GPU ociosa. VocÃª
precisa de um assistente que leia arquivos, Python 3.10+ e, conforme a rota, uma conta de API ou de GPU â€” e
de permissÃ£o para tudo o que for testar.

## ðŸ“– Guia de uso

Guia completo (landing + passo a passo): **https://linnoff88-dev.github.io/

## âš ï¸ Uso defensivo

**SÃ³ sistemas seus ou com permissÃ£o por escrito do dono.** Escopo registrado antes do primeiro pedido,
laboratÃ³rio sintÃ©tico primeiro, checagens nÃ£o destrutivas, prova proporcional, credenciais fora do chat e do
git. Modelo baixado roda primeiro sem ferramentas; o isolamento Ã© do sistema operacional e do contÃªiner â€”
prompt nÃ£o Ã© cerca. Endpoint local sÃ³ em `127.0.0.1`; endpoint na nuvem sempre com autenticaÃ§Ã£o. Na RunPod,
pare o Pod e confira **EXITED**: o armazenamento ainda cobra. Regras completas em
[`kit/USO-DEFENSIVO.md`](kit/USO-DEFENSIVO.md).

## As trÃªs rotas

| Rota | Combina com | VocÃª paga | Prompts |
|---|---|---|---|
| API hospedada (ex.: Venice, Abliteration, OrcaRouter) | comeÃ§ar rÃ¡pido, sem GPU | uso da API | 01 â†’ 02 â†’ 03 â†’ 09 (Venice: 01 â†’ 10 â†’ 03 â†’ 09) |
| GPU alugada na RunPod | escolher modelo e runtime | hora de GPU + armazenamento | 01 â†’ 04 â†’ 05 â†’ 06 â†’ 03 â†’ 09 |
| Local no LM Studio | mÃ¡quina com memÃ³ria sobrando | luz, disco, tempo | 01 â†’ 07 â†’ 08 â†’ 03 â†’ 09 |

Modelos de exemplo (conferidos em 26/10/2026; mudam): local **Huihui Qwen3.6 35B-A3B abliterated GGUF Q4_K**
(~21,7 GB + projetor de visÃ£o ~0,9 GB); nuvem **Huihui Qwen3.5 9B abliterated Q6_K** com projetor de visÃ£o.

### Rota Venice (DeepSeek sem filtro, sem GPU)

A Venice serve modelos sem filtro prontos por uma API no padrÃ£o OpenAI (`https://api.venice.ai/api/v1`). Comece pelo
`deepseek-v4-1-flash-1017-uncensored` (US$ 0,33 / 1,32 por 1M tokens, contexto de 1M, modo Private). Coloque sÃ³ o crÃ©dito
que aceita gastar: o crÃ©dito prÃ©-pago Ã© o teto. O modelo sem filtro trabalha numa pasta separada e o seu Claude Code ou
Codex, pela assinatura, revisa antes de vocÃª copiar para o projeto real. Passo a passo:
[`kit/guias/2b-rota-venice.md`](kit/guias/2b-rota-venice.md) Â· prompt [`10-conectar-venice.txt`](kit/prompts/10-conectar-venice.txt).
PreÃ§os lidos na documentaÃ§Ã£o pÃºblica em 09/11/2026; rota ainda nÃ£o testada com conta pelo ARCKHÉ.

## O processo, do inÃ­cio ao fim

Quem faz: ðŸ§  vocÃª numa sessÃ£o com o assistente Â· âš™ï¸ script do kit Â· ðŸ¤– agente/modelo.

| # | Passo | Comando / arquivo | Quem faz |
|---|---|---|---|
| 1 | Ler as regras | [`kit/USO-DEFENSIVO.md`](kit/USO-DEFENSIVO.md) | ðŸ§  |
| 2 | Conferir a mÃ¡quina | `python3 kit/scripts/doutor.py` | âš™ï¸ |
| 3 | Rodar os testes offline | `python3 -m unittest discover -s kit/testes -v` | âš™ï¸ |
| 4 | LaboratÃ³rio + checagem com escopo | `python3 kit/scripts/laboratorio.py` e `python3 kit/scripts/checagem_segura.py --lab-local-autorizado` | âš™ï¸ |
| 5 | Corrigir e retestar | `laboratorio.py --corrigido` + a mesma checagem â†’ `"achados": []` | âš™ï¸ |
| 6 | Escolher a rota | [`kit/guias/1-escolha-da-rota.md`](kit/guias/1-escolha-da-rota.md) | ðŸ§  |
| 7 | Entregar o kit ao assistente | pedido de [`kit/CONFIGURA-COM-ASSISTENTE.md`](kit/CONFIGURA-COM-ASSISTENTE.md) | ðŸ§  â†’ ðŸ¤– |
| 8 | Instalar/ligar o modelo pela rota | prompts 01, 02 / 04-05 / 07-08 em [`kit/prompts/`](kit/prompts/) (custo sempre aprovado antes) | ðŸ¤–, aprovado por ðŸ§  |
| 9 | Provar texto, funÃ§Ã£o e imagem | `python3 kit/scripts/checa_endpoint.py --base-url ... --modelo ... --funcao --imagem kit/exemplos/teste-visao.png` | âš™ï¸ |
| 10 | Dar ferramentas (Playwright, Firecrawl, Nuclei) | prompt 03 + `kit/config/dsh-mcp.exemplo.yml` + `kit/exemplos/nuclei-cabecalhos-lab.yaml` sÃ³ no laboratÃ³rio | ðŸ¤–, conferido por ðŸ§  |
| 11 | RunPod: guarda ociosa | `python3 kit/scripts/guarda_ociosa.py --upstream ... --ocioso 900` (simulaÃ§Ã£o â†’ parada real com ID e nome) | âš™ï¸ + ðŸ§  confere EXITED |
| 12 | Seu app, com escopo escrito | prompt 09 + cÃ³pia preenchida de `kit/exemplos/escopo-autorizado.exemplo.json` | ðŸ§  â†’ ðŸ¤– |

### Onde ficam o guia e o vÃ­deo deste repositÃ³rio

| PeÃ§a | Onde | Quem faz |
|---|---|---|
| Guia (PT/EN/ES) | `guia/index.html`, `guia/en/`, `guia/es/` â†’ https://linnoff88-dev.github.io/ | ðŸ§  sessÃ£o ARCKHÉ â†’ âš™ï¸ GitHub Pages via Actions |
| VÃ­deo explicativo | MP4 fora do repo; release `video-v1.0.0` + player em `videos/` â†’ https://linnoff88-dev.github.io/ | âš™ï¸ `python3 scripts/publica.py` |

## Estrutura

```
kit/
â”œâ”€â”€ COMECE-AQUI.md Â· USO-DEFENSIVO.md Â· CONFIGURA-COM-ASSISTENTE.md
â”œâ”€â”€ guia-rapido.pdf  o kit inteiro em PDF para ler e imprimir (`python3 scripts/gera_pdf.py` refaz)
â”œâ”€â”€ prompts/      01..09 (cada um com o bloco FRONTEIRAS) + TODOS-OS-PROMPTS.md
â”œâ”€â”€ guias/        1 escolha da rota Â· 2 hospedada Â· 3 runpod Â· 4 local Â· 5 ferramentas
â”‚                 6 seguranÃ§a do modelo Â· 7 custo runpod Â· 8 problemas comuns
â”œâ”€â”€ config/       .env.exemplo Â· campos-do-provedor.json Â· dsh-mcp.exemplo.yml Â· mcp.exemplo.json Â· modelos-de-exemplo.json
â”œâ”€â”€ scripts/      doutor Â· checa_endpoint Â· laboratorio Â· checagem_segura Â· guarda_ociosa Â· comum Â· gera_imagem_teste
â”œâ”€â”€ testes/       test_kit.py (offline, 127.0.0.1)
â”œâ”€â”€ exemplos/     escopo de exemplo Â· relatÃ³rio de achados Â· template Nuclei passivo Â· teste-visao.png
â””â”€â”€ verificacao/  STATUS.md Â· checklist.md
guia/       pÃ¡gina de uso (PT, en/, es/)
videos/     player do vÃ­deo explicativo
scripts/    publica.py (sobe o vÃ­deo como release e gera o player)
```

## Status (26/10/2026)

- **Testado pelo ARCKHÉ:** os 25 testes offline dos scripts e o ciclo laboratÃ³rio â†’ achado â†’ correÃ§Ã£o pela linha de comando.
- **Observado, nÃ£o repetido nesta versÃ£o:** modelo local Q4_K no LM Studio â€” texto âœ”, funÃ§Ã£o âœ”, **imagem âœ˜** naquele runtime.
- **NÃ£o testado:** provedor pago, GPU na RunPod, parada real de Pod, Harness/MCPs/Nuclei instalados. Dependem da sua conta.

Detalhes em [`kit/verificacao/STATUS.md`](kit/verificacao/STATUS.md). Nada aqui Ã© certificaÃ§Ã£o de seguranÃ§a.

## LicenÃ§a

[MIT](LICENSE) â€” texto, prompts, scripts e exemplos do ARCKHÉ. DeepSeek Harness, LM Studio, RunPod, Nuclei,
Playwright, Firecrawl e os modelos citados sÃ£o de seus autores, cada um com os seus termos.

---

ConteÃºdo aberto e gratuito do **[ARCKHÉ AI](https://ARCKHÉ AI)**.

---

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="32" />
  <p><strong>Arckhé AI</strong></p>
</div>