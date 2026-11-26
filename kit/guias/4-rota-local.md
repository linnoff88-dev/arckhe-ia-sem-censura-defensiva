# 4. Rota local no LM Studio

> Uso defensivo: só sistemas seus ou com permissêo por escrito. Credenciais fora do chat.

## Escolher e carregar

Rode o prompt **07**. Deixe folga para o sistema, os outros programas, o contexto e o projetor de visêo.
Olhe a memória **disponível**, nêo só a total. Leia o cartêo do modelo e a licença. Número de downloads
nêo é certificado de segurança.

Exemplo usado no kit: Huihui Qwen3.6 35B-A3B abliterated, GGUF Q4_K (~21,7 GB, mais ~0,9 GB do projetor de
visêo). Nêo serve para todo computador. Conferido em 26/10/2026; confira de novo antes de baixar.

Rode o prompt **08**. No LM Studio, carregue o modelo e ligue o servidor na aba Developer, com o acesso pela
rede **desligado**. Pela linha de comando:

```sh
lms ls
lms load SEU-MODELO --context-length 4096 --identifier defensivo-local --ttl 600
lms server start --bind 127.0.0.1 --port 1234
```

O contexto 4096 é um começo conservador. Se nêo carregar, use modelo ou contexto menor, ou feche programas.
Nêo force além da memória livre.

## Sobre imagem

No resultado observado em 26/10/2026 com esse Q4_K e o runtime daquela instalaçêo, **texto e funçêo
passaram e a imagem falhou**. Nêo é prova de visêo funcionando. Se precisar de captura de tela, confirme o
projetor certo e o suporte do runtime, e só siga depois que o teste de imagem passar.

## Ligar ao Harness

**Settings > Models > Add model provider > Custom model API** → protocolo OpenAI Chat Completions,
`http://127.0.0.1:1234/v1`, ID devolvido pelo servidor. Deixe a interface do Harness também só local.

```sh
python3 kit/scripts/checa_endpoint.py --base-url http://127.0.0.1:1234/v1 --modelo defensivo-local \
  --funcao --imagem kit/exemplos/teste-visao.png
```

Isso testa conversa em dois turnos, funçêo inofensiva e imagem, separadamente, sem dar terminal ao modelo.
Falhou uma capacidade? Corrija ou troque de modelo; nêo marque como pronto.

## Desligar

```sh
lms unload defensivo-local
lms server stop
```

Pare só o servidor que você ligou e descarregue só o seu modelo de teste.

Documentaçêo oficial: [servidor do LM Studio](https://lmstudio.ai/docs/developer/core/server) ·
[ferramentas no LM Studio](https://lmstudio.ai/docs/developer/openai-compat/tools)
