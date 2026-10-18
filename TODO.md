# TODO

## Feito
- LoRAs escolhidos pelo usuário (gerador e jogo.html), em Estilo > Seus LoRAs:
  - Botão "Adicionar LoRA" busca a lista no ComfyUI só ao clicar (/models/loras, com /object_info/LoraLoader de reserva), seletor com busca, mostra até 80 por vez.
  - Só os LoRAs escolhidos aparecem: checkbox, força (0 a 2), tags de ativação, botão remover.
  - Sem LoRAs fixos: Smooth Booster, Dramatic Lighting e os de estilo saíram do app; tudo passa pela lista (seção LoRAs). Imagens antigas do histórico mantêm os LoRAs com que foram feitas em Variar e Upscale.
  - Minimizar e expandir cada LoRA (seta ao lado do ×).
  - Lista salva no navegador e compartilhada entre gerador e jogo. ComfyUI fora do ar: usa a última lista salva.
  - Enviados como lora_1, lora_2... no Power Lora Loader.
  - Variar e Upscale reusam os LoRAs da imagem; Mesma seed usa os ligados agora.
- Tags de ativação:
  - Lê os metadados do arquivo (/view_metadata/loras): trigger phrase e ss_tag_frequency. Sugere até 15 tags, sem as genéricas e as que o app já sorteia.
  - Campo para digitar ou colar várias tags com vírgula (ex.: palavras-gatilho do Civitai).
  - Cada tag tem um seletor de posição (Início, Personagem, Roupa, Cenário), com classificação automática.
  - Modo "Só o fundo": tags de Personagem e Roupa não entram.
- jogo.html: LoRA do personagem no editor; entra sempre com aquele personagem, somando às tags dele.

## Ideias para depois
- Etiqueta de tipo do LoRA (personagem, estilo, detalhe...) por palpite: descartado por enquanto.
- Buscar as palavras-gatilho no Civitai pelo hash do arquivo.
- Mostrar no chip do personagem (jogo) quando ele tem LoRA.
