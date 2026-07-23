# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## O que é este repositório

Repositório especial de perfil do GitHub (`rogerio-silva/rogerio-silva` — nome do repo igual ao do usuário). O `README.md` da raiz é renderizado automaticamente na página <https://github.com/rogerio-silva>.

Não há código-fonte, build, testes nem dependências. O conteúdo total é:

- `README.md` — a página de perfil
- `img/` — banner (`github-profile.png`), foto (`profile.png`) e ícones de redes sociais (`ins.png`, `lin.png`, `blu.png`, `you.png`, `fac.png`)

Publicar = commitar e dar push em `main`. Não existe pipeline de CI ou etapa de deploy.

## Estrutura do README

Conteúdo visível, nessa ordem: banner → identidade (professor/pesquisador/extensionista no IFG, doutor pelo PPGCC-UFG em 2025) → badges acadêmicos (Lattes, Scholar, ORCID, e-mail) → *Onde me encontrar* → *Pesquisa* (tabela de repos autorais) → *Publicações selecionadas* → *Material de aula* → `<details>` com a versão em inglês → *Ferramentas* → *Estatísticas*.

A bio aparece em dois lugares: no cabeçalho em português e dentro do `<details>` "In English". Ao mudar titulação ou vínculo, atualize **os dois**.

No fim do arquivo há um bloco grande comentado em HTML marcado como **ARQUIVO HISTÓRICO** — versões anteriores do perfil. **Preserve esse bloco** ao editar; ao reativar algo dali, mova para fora do comentário em vez de duplicar.

## Estatísticas e badges

- Provedores em uso e verificados funcionando: `streak-stats.demolab.com`, `github-readme-activity-graph.vercel.app`, `img.shields.io`. Todos via `<picture>` com `prefers-color-scheme` para funcionar nos temas claro e escuro do GitHub.
- Os cards do **`github-readme-stats` estão comentados**: a instância pública responde `503 DEPLOYMENT_PAUSED`. Só reative com um deploy próprio na Vercel (o comentário no README explica). Não descomente apontando para o domínio público.
- `github-profile-trophy.vercel.app` responde `402` — não usar.
- Antes de adicionar qualquer badge/card novo, faça `curl -s -o /dev/null -w '%{http_code}' <url>` — esses serviços gratuitos caem com frequência e um card quebrado fica visível na home do perfil.

## Pendências conhecidas

- `img/profile.png` (288 KB) e `img/github-profile.png` (863 KB) não são mais referenciados — o banner atual é `img/hero-rogerio-silva.png`.
- O banner ainda tem 1,8 MB. Já passou por otimização PNG sem perda (`oxipng` nível 6 + zopfli, −7,4%); é conteúdo fotográfico, então o PNG não comprime muito mais. WebP lossless daria 1,46 MB (−26 %, pixels idênticos) se valer a troca de formato.
- Campos do perfil no GitHub (fora deste repo): `bio` está como `"."` e `blog` está vazio.

## Otimizar imagens

Não há otimizador de PNG instalado no sistema (`oxipng`/`optipng`/`pngquant` ausentes) e o `sudo` pede senha. A rota sem root é o wheel `pyoxipng`:

```bash
uv venv .venv && uv pip install --python .venv/bin/python pyoxipng pillow
```

Use `strip=StripChunks.safe()` e sempre confirme que os pixels não mudaram comparando o SHA-256 de `Image.open(p).convert('RGBA').tobytes()` antes e depois.

## Convenções ao editar

- Ícones sociais usam imagens locais de `img/` em sintaxe `[![Alt](img/x.png)](url)`; o bloco comentado usa SVGs remotos. Ao adicionar novos links visíveis, siga o padrão local.
- Caminhos de imagem são relativos (`img/...`) e funcionam tanto no GitHub quanto em clones locais — não troque por URLs absolutas.
- Verifique o resultado renderizando o Markdown (ex.: `gh browse` após o push) — não há preview local configurado.
- Mensagens de commit no histórico são curtas e em inglês (`Update README.md`, `Updating info`, `Fix LinkedIn link format in README.md`).
