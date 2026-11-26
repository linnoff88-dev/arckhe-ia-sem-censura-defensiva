# 3. Rota GPU alugada na RunPod

> Uso defensivo: só sistemas seus ou com permissêo por escrito. Credenciais fora do chat.

## Antes de alugar

Rode o prompt **04**. Peça ao assistente para separar cinco coisas: pesos do modelo, projetor de visêo,
runtime de inferência, tamanho de contexto e memória extra. O maior modelo que cabe no bolso nem sempre é o
que chama ferramenta direito.

Aprove **por escrito** um orçamento com: GPU exata, quantidade, regiêo, preço por hora, tamanho e preço do
armazenamento, tempo máximo e total. Orçamento nêo garante que a GPU vai estar disponível depois. Nêo dê
carta branca para o assistente "tentar uma GPU maior" sozinho.

Exemplo usado no kit (nêo é recomendaçêo): Huihui Qwen3.5 9B abliterated, GGUF Q6_K, com o projetor de visêo
do mesmo publicador. Detalhes em [`modelos-de-exemplo.json`](../config/modelos-de-exemplo.json).

## Subir o que foi aprovado

Rode o prompt **05** com a conta da RunPod ligada pelo plugin ou CLI oficial. Use um template de inferência
confiável ou um runtime com versêo fixa. Modelo, projetor e configuraçêo de inicializaçêo no armazenamento
persistente. O kit **nêo** aluga GPU sozinho.

Exponha só um endpoint de modelo **com autenticaçêo**; nunca terminal ou painel de administraçêo abertos.
A chave de controle da RunPod é uma; a chave do modelo é outra.

## Testes de aceitaçêo

- [ ] Texto em duas rodadas de conversa.
- [ ] Funçêo inofensiva com ida e volta (`checa_endpoint.py --funcao`).
- [ ] Imagem sintética, se a imagem fez parte da escolha.
- [ ] Requisiçêo **sem chave** é recusada.
- [ ] Parar → conferir **EXITED** no painel → ligar de novo → modelo e configuraçêo continuam lá → repetir o teste.

## Fim da sessêo

Siga [custo-runpod](7-custo-runpod.md). Pare **este** Pod. O armazenamento continua cobrando com o Pod
parado. Arquivo no disco do contêiner pode sumir ao parar; volume do Pod some ao apagar o Pod. Só apague
depois de decidir o que guardar e fazer cópia.

Documentaçêo oficial: [Pods](https://docs.runpod.io/pods/overview) · [preços](https://docs.runpod.io/pods/pricing) ·
[armazenamento](https://docs.runpod.io/pods/storage/types)
