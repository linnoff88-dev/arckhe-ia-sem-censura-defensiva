# IA sem censura, do jeito certo ê¢â¬â seu prêÂ³prio modelo para seguranêÂ§a defensiva

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="48" />
  <p><strong>Arckhé AI</strong></p>
</div>


[![IA sem censura, do jeito certo](guia/assets/banner.jpg)](https://linnoff88-dev.github.io/

**ê°Å¸â¡Â§ê°Å¸â¡Â· [PortuguêÂªs](README.md) êÂ· ê°Å¸â¡Âºê°Å¸â¡Â¸ [English](README.en.md) êÂ· ê°Å¸â¡Âªê°Å¸â¡Â¸ [EspaêÂ±ol](README.es.md)**

## O que êÂ©

Este êÂ© um kit gratuito do ARCKHê, em portuguêÂªs, para quem estuda seguranêÂ§a e quer um modelo de IA aberto que
nêÂ£o recuse perguntas têÂ©cnicas ê¢â¬â os chamados modelos *abliterated*, dos quais a recusa foi removida. Ele
mostra como ligar esse modelo ao DeepSeek Harness (um agente de cêÂ³digo aberto) por uma API, por uma GPU
alugada na RunPod ou pelo LM Studio no seu computador. Traz prompts prontos, scripts que provam se texto,
ferramenta e imagem funcionam, um laboratêÂ³rio falso para treinar e uma guarda que para a GPU ociosa. VocêÂª
precisa de um assistente que leia arquivos, Python 3.10+ e, conforme a rota, uma conta de API ou de GPU ê¢â¬â e
de permissêÂ£o para tudo o que for testar.

## ê°Å¸ââ Guia de uso

Guia completo (landing + passo a passo): **https://linnoff88-dev.github.io/

## ê¢Å¡Â ê¯Â¸Â Uso defensivo

**SêÂ³ sistemas seus ou com permissêÂ£o por escrito do dono.** Escopo registrado antes do primeiro pedido,
laboratêÂ³rio sintêÂ©tico primeiro, checagens nêÂ£o destrutivas, prova proporcional, credenciais fora do chat e do
git. Modelo baixado roda primeiro sem ferramentas; o isolamento êÂ© do sistema operacional e do contêÂªiner ê¢â¬â
prompt nêÂ£o êÂ© cerca. Endpoint local sêÂ³ em `127.0.0.1`; endpoint na nuvem sempre com autenticaêÂ§êÂ£o. Na RunPod,
pare o Pod e confira **EXITED**: o armazenamento ainda cobra. Regras completas em
[`kit/USO-DEFENSIVO.md`](kit/USO-DEFENSIVO.md).

## As trêÂªs rotas

| Rota | Combina com | VocêÂª paga | Prompts |
|---|---|---|---|
| API hospedada (ex.: Venice, Abliteration, OrcaRouter) | comeêÂ§ar rêÂ¡pido, sem GPU | uso da API | 01 ê¢â â 02 ê¢â â 03 ê¢â â 09 (Venice: 01 ê¢â â 10 ê¢â â 03 ê¢â â 09) |
| GPU alugada na RunPod | escolher modelo e runtime | hora de GPU + armazenamento | 01 ê¢â â 04 ê¢â â 05 ê¢â â 06 ê¢â â 03 ê¢â â 09 |
| Local no LM Studio | mêÂ¡quina com memêÂ³ria sobrando | luz, disco, tempo | 01 ê¢â â 07 ê¢â â 08 ê¢â â 03 ê¢â â 09 |

Modelos de exemplo (conferidos em 26/10/2026; mudam): local **Huihui Qwen3.6 35B-A3B abliterated GGUF Q4_K**
(~21,7 GB + projetor de visêÂ£o ~0,9 GB); nuvem **Huihui Qwen3.5 9B abliterated Q6_K** com projetor de visêÂ£o.

### Rota Venice (DeepSeek sem filtro, sem GPU)

A Venice serve modelos sem filtro prontos por uma API no padrêÂ£o OpenAI (`https://api.venice.ai/api/v1`). Comece pelo
`deepseek-v4-1-flash-1017-uncensored` (US$ 0,33 / 1,32 por 1M tokens, contexto de 1M, modo Private). Coloque sêÂ³ o crêÂ©dito
que aceita gastar: o crêÂ©dito prêÂ©-pago êÂ© o teto. O modelo sem filtro trabalha numa pasta separada e o seu Claude Code ou
Codex, pela assinatura, revisa antes de vocêÂª copiar para o projeto real. Passo a passo:
[`kit/guias/2b-rota-venice.md`](kit/guias/2b-rota-venice.md) êÂ· prompt [`10-conectar-venice.txt`](kit/prompts/10-conectar-venice.txt).
PreêÂ§os lidos na documentaêÂ§êÂ£o pêÂºblica em 09/11/2026; rota ainda nêÂ£o testada com conta pelo ARCKHê.

## O processo, do inêÂ­cio ao fim

Quem faz: ê°Å¸Â§Â  vocêÂª numa sessêÂ£o com o assistente êÂ· ê¢Å¡â¢ê¯Â¸Â script do kit êÂ· ê°Å¸Â¤â agente/modelo.

| # | Passo | Comando / arquivo | Quem faz |
|---|---|---|---|
| 1 | Ler as regras | [`kit/USO-DEFENSIVO.md`](kit/USO-DEFENSIVO.md) | ê°Å¸Â§Â  |
| 2 | Conferir a mêÂ¡quina | `python3 kit/scripts/doutor.py` | ê¢Å¡â¢ê¯Â¸Â |
| 3 | Rodar os testes offline | `python3 -m unittest discover -s kit/testes -v` | ê¢Å¡â¢ê¯Â¸Â |
| 4 | LaboratêÂ³rio + checagem com escopo | `python3 kit/scripts/laboratorio.py` e `python3 kit/scripts/checagem_segura.py --lab-local-autorizado` | ê¢Å¡â¢ê¯Â¸Â |
| 5 | Corrigir e retestar | `laboratorio.py --corrigido` + a mesma checagem ê¢â â `"achados": []` | ê¢Å¡â¢ê¯Â¸Â |
| 6 | Escolher a rota | [`kit/guias/1-escolha-da-rota.md`](kit/guias/1-escolha-da-rota.md) | ê°Å¸Â§Â  |
| 7 | Entregar o kit ao assistente | pedido de [`kit/CONFIGURA-COM-ASSISTENTE.md`](kit/CONFIGURA-COM-ASSISTENTE.md) | ê°Å¸Â§Â  ê¢â â ê°Å¸Â¤â |
| 8 | Instalar/ligar o modelo pela rota | prompts 01, 02 / 04-05 / 07-08 em [`kit/prompts/`](kit/prompts/) (custo sempre aprovado antes) | ê°Å¸Â¤â, aprovado por ê°Å¸Â§Â  |
| 9 | Provar texto, funêÂ§êÂ£o e imagem | `python3 kit/scripts/checa_endpoint.py --base-url ... --modelo ... --funcao --imagem kit/exemplos/teste-visao.png` | ê¢Å¡â¢ê¯Â¸Â |
| 10 | Dar ferramentas (Playwright, Firecrawl, Nuclei) | prompt 03 + `kit/config/dsh-mcp.exemplo.yml` + `kit/exemplos/nuclei-cabecalhos-lab.yaml` sêÂ³ no laboratêÂ³rio | ê°Å¸Â¤â, conferido por ê°Å¸Â§Â  |
| 11 | RunPod: guarda ociosa | `python3 kit/scripts/guarda_ociosa.py --upstream ... --ocioso 900` (simulaêÂ§êÂ£o ê¢â â parada real com ID e nome) | ê¢Å¡â¢ê¯Â¸Â + ê°Å¸Â§Â  confere EXITED |
| 12 | Seu app, com escopo escrito | prompt 09 + cêÂ³pia preenchida de `kit/exemplos/escopo-autorizado.exemplo.json` | ê°Å¸Â§Â  ê¢â â ê°Å¸Â¤â |

### Onde ficam o guia e o vêÂ­deo deste repositêÂ³rio

| PeêÂ§a | Onde | Quem faz |
|---|---|---|
| Guia (PT/EN/ES) | `guia/index.html`, `guia/en/`, `guia/es/` ê¢â â https://linnoff88-dev.github.io/ | ê°Å¸Â§Â  sessêÂ£o ARCKHê ê¢â â ê¢Å¡â¢ê¯Â¸Â GitHub Pages via Actions |
| VêÂ­deo explicativo | MP4 fora do repo; release `video-v1.0.0` + player em `videos/` ê¢â â https://linnoff88-dev.github.io/ | ê¢Å¡â¢ê¯Â¸Â `python3 scripts/publica.py` |

## Estrutura

```
kit/
ê¢âÅê¢ââ¬ê¢ââ¬ COMECE-AQUI.md êÂ· USO-DEFENSIVO.md êÂ· CONFIGURA-COM-ASSISTENTE.md
ê¢âÅê¢ââ¬ê¢ââ¬ guia-rapido.pdf  o kit inteiro em PDF para ler e imprimir (`python3 scripts/gera_pdf.py` refaz)
ê¢âÅê¢ââ¬ê¢ââ¬ prompts/      01..09 (cada um com o bloco FRONTEIRAS) + TODOS-OS-PROMPTS.md
ê¢âÅê¢ââ¬ê¢ââ¬ guias/        1 escolha da rota êÂ· 2 hospedada êÂ· 3 runpod êÂ· 4 local êÂ· 5 ferramentas
ê¢ââ                 6 seguranêÂ§a do modelo êÂ· 7 custo runpod êÂ· 8 problemas comuns
ê¢âÅê¢ââ¬ê¢ââ¬ config/       .env.exemplo êÂ· campos-do-provedor.json êÂ· dsh-mcp.exemplo.yml êÂ· mcp.exemplo.json êÂ· modelos-de-exemplo.json
ê¢âÅê¢ââ¬ê¢ââ¬ scripts/      doutor êÂ· checa_endpoint êÂ· laboratorio êÂ· checagem_segura êÂ· guarda_ociosa êÂ· comum êÂ· gera_imagem_teste
ê¢âÅê¢ââ¬ê¢ââ¬ testes/       test_kit.py (offline, 127.0.0.1)
ê¢âÅê¢ââ¬ê¢ââ¬ exemplos/     escopo de exemplo êÂ· relatêÂ³rio de achados êÂ· template Nuclei passivo êÂ· teste-visao.png
ê¢ââê¢ââ¬ê¢ââ¬ verificacao/  STATUS.md êÂ· checklist.md
guia/       pêÂ¡gina de uso (PT, en/, es/)
videos/     player do vêÂ­deo explicativo
scripts/    publica.py (sobe o vêÂ­deo como release e gera o player)
```

## Status (26/10/2026)

- **Testado pelo ARCKHê:** os 25 testes offline dos scripts e o ciclo laboratêÂ³rio ê¢â â achado ê¢â â correêÂ§êÂ£o pela linha de comando.
- **Observado, nêÂ£o repetido nesta versêÂ£o:** modelo local Q4_K no LM Studio ê¢â¬â texto ê¢Åâ, funêÂ§êÂ£o ê¢Åâ, **imagem ê¢ÅË** naquele runtime.
- **NêÂ£o testado:** provedor pago, GPU na RunPod, parada real de Pod, Harness/MCPs/Nuclei instalados. Dependem da sua conta.

Detalhes em [`kit/verificacao/STATUS.md`](kit/verificacao/STATUS.md). Nada aqui êÂ© certificaêÂ§êÂ£o de seguranêÂ§a.

## LicenêÂ§a

[MIT](LICENSE) ê¢â¬â texto, prompts, scripts e exemplos do ARCKHê. DeepSeek Harness, LM Studio, RunPod, Nuclei,
Playwright, Firecrawl e os modelos citados sêÂ£o de seus autores, cada um com os seus termos.

---

ConteêÂºdo aberto e gratuito do **[ARCKHê AI](https://ARCKHê AI)**.

---

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="32" />
  <p><strong>Arckhé AI</strong></p>
</div>