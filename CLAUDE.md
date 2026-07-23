# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## O que é este repositório

Repositório especial de perfil do GitHub (`rogerio-silva/rogerio-silva` — nome do repo igual ao do usuário). O `README.md` da raiz é renderizado automaticamente na página <https://github.com/rogerio-silva>.

Não há código-fonte, build, testes nem dependências. O conteúdo total é:

- `README.md` — a página de perfil
- `img/` — banner (`github-profile.png`), foto (`profile.png`) e ícones de redes sociais (`ins.png`, `lin.png`, `blu.png`, `you.png`, `fac.png`)

Publicar = commitar e dar push em `main`. Não existe pipeline de CI ou etapa de deploy.

## Estrutura do README

Conteúdo visível, nessa ordem: banner → identidade (professor IFG / doutorando PPGCC-UFG / NumbERS Lab) + badge ORCID → *Pesquisa* (tabela de repos autorais) → *Publicações selecionadas* → *Material de aula* → `<details>` com a versão em inglês → *Ferramentas* → *Estatísticas* → *Onde me encontrar*.

No fim do arquivo há um bloco grande comentado em HTML marcado como **ARQUIVO HISTÓRICO** — versões anteriores do perfil. **Preserve esse bloco** ao editar; ao reativar algo dali, mova para fora do comentário em vez de duplicar.

## Estatísticas e badges

- Provedores em uso e verificados funcionando: `streak-stats.demolab.com`, `github-readme-activity-graph.vercel.app`, `img.shields.io`. Todos via `<picture>` com `prefers-color-scheme` para funcionar nos temas claro e escuro do GitHub.
- Os cards do **`github-readme-stats` estão comentados**: a instância pública responde `503 DEPLOYMENT_PAUSED`. Só reative com um deploy próprio na Vercel (o comentário no README explica). Não descomente apontando para o domínio público.
- `github-profile-trophy.vercel.app` responde `402` — não usar.
- Antes de adicionar qualquer badge/card novo, faça `curl -s -o /dev/null -w '%{http_code}' <url>` — esses serviços gratuitos caem com frequência e um card quebrado fica visível na home do perfil.

## Pendências conhecidas

- `img/profile.png` (288 KB) não é referenciado por nada.
- `img/github-profile.png` tem 863 KB — candidato a otimização (`oxipng`/WebP).
- Campos do perfil no GitHub (fora deste repo): `bio` está como `"."` e `blog` está vazio.

## Convenções ao editar

- Ícones sociais usam imagens locais de `img/` em sintaxe `[![Alt](img/x.png)](url)`; o bloco comentado usa SVGs remotos. Ao adicionar novos links visíveis, siga o padrão local.
- Caminhos de imagem são relativos (`img/...`) e funcionam tanto no GitHub quanto em clones locais — não troque por URLs absolutas.
- Verifique o resultado renderizando o Markdown (ex.: `gh browse` após o push) — não há preview local configurado.
- Mensagens de commit no histórico são curtas e em inglês (`Update README.md`, `Updating info`, `Fix LinkedIn link format in README.md`).
