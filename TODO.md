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

## A fazer

### Aviso de LoRA não encontrado (prevenção de erros)
- Quando detectar: antes de enviar (comparando com a lista do ComfyUI) e quando o ComfyUI recusar o prompt (erro 400, "value not in list").
- Como aparece: janela de aviso no centro da tela, com fundo escurecido (mesmo visual do visualizador de imagem), listando os arquivos que não existem mais.
  - Botões: "Remover da lista" (em cada LoRA ou todos) e "Fechar".
  - Nada é enviado enquanto o aviso estiver aberto. Depois de fechar, GENERATE gera sem os LoRAs com problema.
- LoRA com problema na lista:
  - Fica desabilitado: sem checkbox, sem controle de força e sem sugestões de tags.
  - Mostra um símbolo de atenção amarelo e "Não encontrado no ComfyUI".
  - Mantém o botão × para remover e um link "Verificar de novo" (caso o arquivo volte para a pasta).
  - As tags e a força ficam guardadas: se o arquivo voltar, o LoRA volta ao normal sozinho na próxima verificação.
  - Não é enviado ao ComfyUI enquanto estiver com problema.
- Imagens antigas: Variar, Upscale e Mesma seed também passam pela verificação.
- Mesmo tratamento para o checkpoint (item abaixo).

### Escolher o checkpoint (modelo base)
Pensado para ser simples de usar:
- Linha fixa no topo da seção LoRAs: "Modelo: <nome curto>" com um botão Trocar. Sem lista aberta o tempo todo.
- Trocar abre o mesmo seletor com busca dos LoRAs (lista lida do ComfyUI só ao clicar).
- No topo do seletor: os modelos usados recentemente (últimos 3 a 5), para trocar rápido.
- Nome curto na tela (sem pasta e extensão); nome completo ao passar o mouse.
- Padrão: o checkpoint que já está no workflow; botão "Voltar ao padrão".
- Salvo no navegador e compartilhado entre gerador e jogo.
- Cada imagem guarda o checkpoint usado; Variar e Upscale usam o da imagem; Mesma seed usa o escolhido agora.
- Checkpoint ausente: mesmo aviso do item anterior.

## Ideias para depois
- Etiqueta de tipo do LoRA (personagem, estilo, detalhe...) por palpite: descartado por enquanto.
- Buscar as palavras-gatilho no Civitai pelo hash do arquivo.
- Mostrar no chip do personagem (jogo) quando ele tem LoRA.
- Misturas de LoRAs salvas com nome; comparar forças lado a lado; mostrar os LoRAs de cada imagem no visualizador (com "Usar estes LoRAs"); backup das configurações em arquivo.
