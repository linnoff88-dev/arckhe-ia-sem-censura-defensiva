# 1. Escolha a sua rota

> Uso defensivo: só sistemas seus ou com permissêo por escrito. Credenciais fora do chat.

Um modelo "sem censura" (abliterated) é um modelo aberto do qual alguém removeu, por técnica, a tendência
de recusar pedidos. Para segurança defensiva isso ajuda: ele explica um cabeçalho fraco ou analisa um log
sem sermêo. Também quer dizer que **a responsabilidade passa a ser sua**: as cercas agora sêo o escopo,
o laboratório e as permissões que você dá.

| Rota | Combina com | Você paga | Sua responsabilidade |
|---|---|---|---|
| **API hospedada** | quem quer começar rápido e nêo tem GPU boa | uso da API (assinatura de chat nêo inclui API) | confiar no provedor, guardar a chave, limite de gasto |
| **GPU alugada na RunPod** | quem quer escolher modelo e runtime além do que o computador aguenta | hora de GPU + armazenamento | autenticaçêo, atualizaçêo, **parar o Pod** |
| **Local no LM Studio** | quem tem máquina com memória sobrando | luz, disco e tempo; sem conta de GPU | downloads, versões do runtime, permissões locais |

**Ordem de teste, em qualquer rota:** texto → uma funçêo inofensiva → imagem (só se precisar). Uma camada
por vez. Um modelo pode responder "oi" e falhar justo na ferramenta ou na imagem que você precisa.

**Já tem uma rota funcionando?** Mantenha como reserva enquanto testa outra. Nêo troque o que funciona só
para ficar igual ao guia.

Próximo: [rota hospedada](2-rota-hospedada.md) · [rota RunPod](3-rota-runpod.md) · [rota local](4-rota-local.md)
