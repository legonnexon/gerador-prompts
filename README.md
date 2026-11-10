# Gerador de prompts para ComfyUI

Duas páginas HTML independentes (sem build, sem dependências locais):

- `gerador-comfyui.html`: gerador de prompts aleatórios no formato de 4 blocos (qualidade, personagem, roupa, cenário), com envio direto ao ComfyUI.
- `jogo.html`: retratos de personagens do jogo (expressões, enquadramento, fundo) e character sheet para criadores 3D, com a mesma integração.

Basta abrir os arquivos no navegador. O ComfyUI precisa estar rodando (padrão `http://127.0.0.1:8188`) e ser iniciado com `--enable-cors-header "*"`. Para a prévia ao vivo das imagens, use também `--preview-method auto`.

## Gerador

- Personagem (garota, garoto, sorteio ou favorita), raça, cenário e enquadramento. Roupa e pose respeitam o enquadramento: num retrato só entram acessórios da cabeça e do pescoço.
- LoRAs escolhidos da lista do ComfyUI, com força, tags de ativação e posição de cada tag no prompt. Lista compartilhada com o jogo.
- Perfil de configurações por checkpoint (Avançado): steps, CFG, sampler, scheduler, clip skip, tamanhos, denoise do hires, prompt de qualidade e negativo. Ao trocar o modelo, o perfil troca junto. Tem preset do Velvette-XL V4.
- Seed aleatória ou fixa; uma seed só identifica a imagem inteira.
- Fila de 1, 3, 6 ou 12 imagens, com progresso ao vivo por WebSocket, prévia e posição na fila.
- Imagem → tags: extrai as tags de uma imagem com o WD14 Tagger e monta o prompt.
- Visualizador: favoritar, copiar prompt e seed, Variar, Hires fix (arruma rosto e mãos da imagem pronta) e Upscale (Fiel, só 4x-UltraSharp, ou Com detalhes).
- Backup (engrenagem): exporta e importa num arquivo `.json` as favoritas, LoRAs, perfis, personagens do jogo, negativos e históricos.

## Jogo

- Personagens com aparência, roupa e LoRA próprio; importa favoritas do gerador.
- Uma imagem por expressão marcada, com prompt por enquadramento (rosto, retrato, busto, meio corpo).
- Character sheet (3D) com Flux 2 Klein 4B: usa a imagem da personagem como referência e redesenha nas vistas pedidas (corpo, pose T ou rosto). Upscale 2x fiel nas folhas.

## Requisitos no ComfyUI

- Checkpoint SDXL/Illustrious (padrão: `waiIllustriousSDXL_v170`), `4x-UltraSharp`, LoRA `dmd2_sdxl_4step_lora_fp16` e os nodes Power Lora Loader (rgthree) e Ultimate SD Upscale.
- Imagem → tags: custom node WD14 Tagger (pysssss), que precisa do pacote `onnxruntime` no Python do ComfyUI.
- Character sheet: `flux-2-klein-4b-fp8`, `qwen3_4b_fp8_scaled` e `flux2-vae`.

As configurações ficam no armazenamento do navegador. Use o backup antes de limpar os dados dele ou de trocar de navegador.

## Como contribuir

- Achou um bug ou teve uma ideia? Abra uma [issue](../../issues) contando o que aconteceu, qual página (gerador ou jogo) e, se tiver, a mensagem que apareceu no topo da tela.
- Quer mudar algo? Faça um fork, altere o HTML e mande um pull request explicando o que mudou e como testou.
- O projeto não tem build nem dependências: cada página é um arquivo HTML só. As duas páginas repetem parte do código (LoRAs, checkpoint, envio ao ComfyUI); ao mudar uma dessas partes, confira se a outra página precisa da mesma mudança.
- As ideias que ainda não foram feitas estão no [TODO.md](TODO.md).

## Créditos

- Preset do Velvette-XL: prompt de qualidade, negativo e configurações recomendadas pelo autor do modelo na [página do Civitai](https://civitai.com/models/1972843).
- Modelos e nodes usados pelos workflows pertencem aos respectivos autores: WAI-Illustrious, 4x-UltraSharp, DMD2, rgthree (Power Lora Loader), Ultimate SD Upscale, WD14 Tagger (pysssss) e Flux 2 Klein (Black Forest Labs).

## Licença

[MIT](LICENSE): pode usar, modificar e distribuir, desde que mantenha o aviso de copyright.
