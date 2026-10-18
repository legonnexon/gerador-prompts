# TODO

## LoRAs escolhidos pelo usuário (gerador e jogo.html)
Inspirado no Power Lora Loader do ComfyUI: nada é carregado por padrão.
- Botão "Adicionar LoRA": só ao clicar o app busca a lista no ComfyUI (/object_info/LoraLoader) e abre um seletor com busca por nome. Não monta lista fixa na abertura, para não pesar com 10, 20 ou 30+ LoRAs.
- O app mostra só os LoRAs que o usuário selecionou. Cada um com: checkbox, força, tags de ativação e botão remover.
- O botão de buscar pode ser repetido a qualquer momento para ver LoRAs novos (substitui a ideia de "botão atualizar").
- Salvar a seleção no navegador (localStorage). Lista do ComfyUI em cache só para o seletor.
- Smooth Booster e Dramatic Lighting continuam fixos na seção Estilo.
- Vários LoRAs ao mesmo tempo (lora_N extras no Power Lora Loader).
- jogo.html: ligar um LoRA (com força e tags) a um personagem, ex.: Evelyn.

## Tags de ativação dos LoRAs
- Ao escolher um LoRA, ler só os metadados dele (/view_metadata/loras?filename=...), em especial ss_tag_frequency, e sugerir as tags mais frequentes como chips clicáveis. Ignorar tags genéricas (1girl, solo etc.) e as que o app já conhece.
- Campo de tags por LoRA, salvo no navegador.
- Opcional: colar as palavras-gatilho da página do Civitai.
- Aviso "sem tags conhecidas" quando o LoRA não tiver metadados.

## Onde cada tag do LoRA entra no prompt
Cada LoRA tem tipos de tag diferentes (pose, iluminação, proporção, estilo, personagem). Plano híbrido:
- Classificação automática: se a tag já existe numa lista do app (poses, iluminação, câmera, cabelo, roupa etc.), vai para o bloco dessa lista. Palavras-chave (ex.: lighting/light = cena, pose/sitting/standing = personagem, nome de artista/style = início). Se não casar com nada, vai para o início do bloco do personagem.
- Um seletor pequeno por tag (Início / Personagem / Roupa / Cenário), sempre editável e lembrado para o LoRA.
- Tags de estilo artístico e de personagem vão logo depois do bloco de qualidade.
