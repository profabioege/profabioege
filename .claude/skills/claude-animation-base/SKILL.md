---
name: claude-animation-base
description: Faz desenhos animados curtos pintados à mão (aquarela, traço que "ferve", 2D chapado, sem texto) com p5.js + p5.brush, estrelando o personagem Clawd (31 emoções, vistas, chapéus, danças) ou qualquer personagem novo. Use quando o usuário pedir um desenho animado, cartoon, animação pintada à mão, animação do Clawd, vídeo animado com personagem, curta animado ou "claude animation base". Não use para vídeos de produto/lançamento com UI (use hyperframes) nem para B-roll de colagem (use gbro-collage-broll).
license: MIT (kit de John Heibel, github.com/JohnHeibel/ClaudeAnimationBase)
---

# Claude Animation Base

Kit para animar desenhos pintados à mão com p5.js e p5.brush. O kit completo está em `kit/` ao lado
deste arquivo. As regras, o fluxo de trabalho e a API inteira estão em `kit/ANIMATION_GUIDE.md`.

## Passo a passo

1. **Crie a pasta do vídeo copiando o kit.** Nunca edite `kit/` dentro da skill: ele é o modelo.
   Se o usuário não disser onde, use `videos/<AAAA-MM-DD>-<titulo-curto>/` na raiz do projeto.
   ```bash
   cp -r <pasta-desta-skill>/kit <pasta-do-video>
   cd <pasta-do-video> && npm install
   ```
2. **Leia `ANIMATION_GUIDE.md` inteiro** antes de desenhar qualquer coisa. Olhe também
   `docs/emotions.jpg` e `docs/views.jpg`.
3. **Siga o guia:** storyboard primeiro, depois construa plano a plano em `src/scenes/` (registre cada
   arquivo de cena em `studio.html`), confira o próprio trabalho com contact sheets e strips, e por fim
   renderize `out/video.mp4`.
4. **Entregue** o MP4 e um resumo curto do storyboard.

O usuário decide **o quê**; o guia decide **como**. Se o usuário pedir algo que o guia proíbe
(por exemplo, uma legenda), faça o que o usuário pediu.

## Renderizar em uma sessão na nuvem do Claude Code (sem GPU)

Aqui não há GPU, então passe sempre `--soft-gl` e aponte para o Chromium já instalado:

```bash
node render.mjs --sheet=0.5,1,2 --soft-gl --chrome=/opt/pw-browsers/chromium-1243/chrome-linux64/chrome --out=out/check/a.jpg
node render.mjs --clip --soft-gl --chrome=/opt/pw-browsers/chromium-1243/chrome-linux64/chrome --out=out/video.mp4
```

Se esse caminho não existir, procure com `find /opt/pw-browsers -name chrome -type f`. No computador do
usuário o `render.mjs` encontra o Chrome sozinho.

Sem GPU, os preenchimentos de aquarela (`fill`) são lentos: segundos por quadro. Para rascunhos, ou
se a renderização ficar lenta demais, avise o usuário e ofereça trocar esses preenchimentos por
`wash` chapado, como o próprio README do kit recomenda.

## Requisitos

Node.js, Chrome/Chromium e ffmpeg. `npm install` baixa p5, p5.brush e puppeteer-core.
