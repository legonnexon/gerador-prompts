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
- Aviso de arquivo não encontrado:
  - Antes de enviar, confere LoRAs e checkpoint com a lista do ComfyUI (cache de 15 s, refeito antes de acusar falta). Também lê o erro 400 "value not in list".
  - Janela no centro com "Remover da lista" (ou "Voltar ao padrão" para o modelo) e "Fechar". Nada é enviado; lotes param no primeiro aviso.
  - LoRA ausente na lista: só alerta amarelo, "Verificar de novo" e ×; não é enviado; volta ao normal se o arquivo reaparecer.
  - Imagens antigas (Variar/Upscale) também são verificadas; o aviso sugere Mesma seed.
- Checkpoint: linha "Modelo" no topo da seção LoRAs com Trocar e Voltar ao padrão; seletor com busca e "Usados recentemente"; salvo e compartilhado entre as páginas; cada imagem guarda o modelo usado. Visual em teste.
- Visualizador mostra os LoRAs e forças de cada imagem (faixa no topo); "Usar estes LoRAs" substitui a lista atual pela mistura daquela imagem.

## Ideias para depois
- Etiqueta de tipo do LoRA (personagem, estilo, detalhe...) por palpite: descartado por enquanto.
- Buscar as palavras-gatilho no Civitai pelo hash do arquivo.
- Mostrar no chip do personagem (jogo) quando ele tem LoRA.
- Misturas de LoRAs salvas com nome; comparar forças lado a lado; backup das configurações em arquivo.
