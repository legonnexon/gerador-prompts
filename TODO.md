# TODO

## Versão 1.0 (feito)
- LoRAs escolhidos pelo usuário (gerador e jogo.html), na seção LoRAs:
  - Botão "Adicionar LoRA" busca a lista no ComfyUI só ao clicar (/models/loras, com /object_info/LoraLoader de reserva), seletor com busca, mostra até 80 por vez.
  - Só os LoRAs escolhidos aparecem: checkbox, força (0 a 2), tags de ativação, botão remover, minimizar e arrastar para reordenar.
  - Sem LoRAs fixos: tudo passa pela lista. Imagens antigas do histórico mantêm os LoRAs com que foram feitas.
  - Lista salva no navegador e compartilhada entre gerador e jogo. ComfyUI fora do ar: usa a última lista salva.
  - Enviados como lora_1, lora_2... no Power Lora Loader.
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
- Checkpoint: linha "Modelo" no topo da seção LoRAs com Trocar e Voltar ao padrão; seletor com busca e "Usados recentemente"; salvo e compartilhado entre as páginas; cada imagem guarda o modelo usado.
- Visualizador mostra os LoRAs e forças de cada imagem (faixa no topo).
- Progresso ao vivo por WebSocket em cada card (etapa, porcentagem, prévia e posição na fila). O limite de 10 min só vale quando o job some da fila.
- Upscale da imagem pronta: Fiel (só 4x-UltraSharp) ou Com detalhes (Ultimate SD Upscale, denoise 0.15).
- Hires fix da imagem pronta no visualizador: 1,5x o tamanho base, no máximo 2,4 MP, denoise ajustável (padrão 0.30).
- Imagem → tags com o WD14 Tagger: arrastar, colar ou escolher a imagem; sensibilidade e modelo ajustáveis.
- Seção Avançado: seed fixa e Copiar seed (uma seed só: hires e tile usam seed+1 e seed+2).
- Perfis por checkpoint no gerador (steps, CFG, sampler, scheduler, clip skip, tamanhos, denoise do hires, prompt de qualidade e negativo), com preset do Velvette-XL V4.
- Roupa e pose respeitam o enquadramento no gerador; prompt por enquadramento nos retratos do jogo.
- Character sheet (3D) no jogo com Flux 2 Klein 4B, modelos de instrução e upscale 2x fiel.
- Backup das configurações em arquivo .json (exportar e importar).

## Versão 2 (ideias, sem pressa)
- Perfis por checkpoint também no jogo (hoje ele usa os valores do WAI).
- LoRAs de estilo no Flux do character sheet (precisa de LoRAs feitos para o Flux 2 Klein), ou repintar a folha no estilo do app com o Illustrious.
- Vistas separadas no character sheet (frente, lado e costas em arquivos próprios).
- Buscar as palavras-gatilho no Civitai pelo hash do arquivo.
- Mostrar no chip do personagem (jogo) quando ele tem LoRA.
- Misturas de LoRAs salvas com nome; comparar forças lado a lado.
- Etiqueta de tipo do LoRA (personagem, estilo, detalhe...) por palpite: descartado por enquanto.
