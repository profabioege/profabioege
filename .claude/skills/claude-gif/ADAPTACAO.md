# Adaptações feitas neste projeto

Origem: https://github.com/AgriciDaniel/claude-gif (commit 7bb7e47, licença MIT, ver LICENSE).

O original é instalado em `~/.claude/skills/`. Aqui as skills ficam no repositório, em
`.claude/skills/`, porque as sessões na nuvem apagam a pasta pessoal a cada sessão. Mudanças:

| Original | Aqui | Motivo |
|---|---|---|
| `~/.claude/skills/claude-gif/...` | `.claude/skills/claude-gif/...` | caminho relativo à raiz do projeto |
| `~/.video-skill/bin/python3` | `python3` | o ambiente Python vinha de outra skill do autor; instale `pip install Pillow numpy` |
| `~/Documents/gif_output` | `gif_output/` (na raiz do projeto) | pasta que o usuário consegue abrir |

## Partes que dependem de skills que não estão instaladas

- `claude-gif-generate` (GIF a partir de vídeo de IA) chama `~/.claude/skills/veo/scripts/generate.py`,
  de uma skill `veo` que não faz parte deste repositório. Sem ela, esse modo não funciona: avise o
  usuário e ofereça gerar o vídeo de outra forma (por exemplo, pela Higgsfield, se estiver conectada)
  e depois converter com `claude-gif-convert`.
- O modo de sequência de imagens por IA em `claude-gif-convert` chama
  `~/.claude/skills/claude-video/scripts/image_generate.py`, também ausente.

Os demais modos (create com Remotion, convert, optimize, edit) funcionam com ffmpeg, gifsicle,
ImageMagick, Python (Pillow, numpy) e Node.
