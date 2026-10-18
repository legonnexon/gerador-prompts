# Gerador de prompts para ComfyUI

Duas páginas HTML independentes (sem build, sem dependências locais):

- `gerador-comfyui.html`: gerador de prompts aleatórios no formato de 4 blocos, com envio direto ao ComfyUI, galeria, favoritos, slots (3/6/12), negativo editável e LoRAs ajustáveis.
- `jogo.html`: retratos de personagens do jogo (expressões, enquadramento, fundo), com a mesma integração.

Basta abrir os arquivos no navegador. O ComfyUI precisa estar rodando (padrão `http://127.0.0.1:8188`) com `--enable-cors-header` se a página for aberta de outra origem.
