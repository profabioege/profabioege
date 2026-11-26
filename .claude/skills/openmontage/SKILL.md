---
name: openmontage
description: Produz vídeos completos com o OpenMontage (github.com/OpenMontageInc/OpenMontage), um estúdio de produção agêntico com 12 pipelines (explicativo animado, documentário com footage real, trailer, curta animado, vitrine 3D em Blender, filme de produto, vídeo a partir de uma referência do YouTube/Reels/TikTok), pesquisa, roteiro, narração, música, legendas e autorrevisão. Use quando o usuário pedir "OpenMontage", "com o OpenMontage", ou quiser um vídeo produzido de ponta a ponta a partir de uma ideia ou de um vídeo de referência e aceitar o fluxo do OpenMontage. Não use quando o usuário nomear outra ferramenta (Remotion, HyperFrames, motion-design, claude-animation-base).
---

# OpenMontage (ponte)

O OpenMontage é um aplicativo inteiro, não uma skill avulsa: as skills dele dependem das pipelines, das
ferramentas Python e do compositor Remotion que estão no repositório dele. Esta skill só baixa o
aplicativo para dentro do projeto e entrega o controle ao guia oficial.

## 1. Obter o aplicativo

Pasta: `openmontage/` na raiz deste projeto (está no `.gitignore`; nunca faça commit dela).

```bash
git clone --depth 1 https://github.com/OpenMontageInc/OpenMontage.git openmontage
```

Se a pasta já existir, atualize com `git -C openmontage pull --ff-only`. Se o clone falhar, avise o
usuário e pare.

## 2. Instalar (uma vez por sessão; demora alguns minutos)

```bash
cd openmontage && make setup
```

Sem `make`: siga o README do OpenMontage ("Sem `make`?"). Pré-requisitos: Python 3.10+, FFmpeg e
Node.js 22.23.4+. Rode a instalação em segundo plano quando puder e avise o usuário que ela está
acontecendo. Não instale software de sistema sem avisar.

## 3. Entregar o controle

Trabalhe de dentro de `openmontage/` e **leia `openmontage/AGENT_GUIDE.md` inteiro antes de qualquer
outra coisa**: ele define a primeira ação (onboarding, vídeo de referência ou pipeline), a "Rule Zero"
(toda produção passa por uma pipeline de `pipeline_defs/`) e os portões de aprovação. As skills que ele
cita estão em `openmontage/skills/`, `openmontage/.agents/skills/` e `openmontage/.claude/skills/`; leia-as
pelo caminho, porque elas não aparecem na lista de skills deste projeto.

Enquanto estiver neste fluxo, as regras do `AGENT_GUIDE.md` valem sobre as das outras skills de vídeo
deste projeto.

## Custos e chaves

- Todas as chaves de API são opcionais (`openmontage/.env`, a partir de `.env.example`). Sem chaves, o
  OpenMontage usa só ferramentas gratuitas e locais. Mais chaves = mais ferramentas (geração de
  imagem/vídeo, vozes), e essas cobram por uso.
- **Antes de qualquer geração paga, mostre a estimativa de custo e espere o "ok" do usuário.**
- Nunca peça para o usuário colar chaves no chat. Neste ambiente na nuvem, chaves são cadastradas como
  credenciais do ambiente.

## Entrega

Os vídeos ficam dentro de `openmontage/` (o guia diz onde). Informe o caminho completo do arquivo final.
Licença do OpenMontage: AGPL-3.0.
