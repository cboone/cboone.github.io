# Plano: Consolidação e Refatoração do CSS

## Resumo

Reorganizar 19 ficheiros CSS (1.701 linhas) numa estrutura mais simples com 10 ficheiros em 2 diretórios. Eliminar a hierarquia core/common/extended/includes herdada do PaperMod, consolidar ficheiros pequenos, dividir o grande post-single.css, e substituir valores hardcoded por variáveis CSS.

## Estado Atual

```
assets/css/
├── core/           4 ficheiros (theme-vars, reset, zmedia, license)
├── common/         10 ficheiros (header, footer, main, post-single, ...)
├── extended/       2 ficheiros (notice, typography)
└── includes/       3 ficheiros (chroma-styles, chroma-mod, scroll-bar)
```

**Problemas identificados:**
- Estrutura de diretórios não serve propósito (editamos todos os ficheiros)
- 8 variáveis legacy «PaperMod compatibility» desnecessárias
- Ficheiros muito pequenos (404.css: 12 linhas, terms.css: 19 linhas)
- post-single.css demasiado grande (448 linhas, mistura concerns)
- Valores hardcoded que deviam ser variáveis

## Nova Estrutura Proposta

```
assets/css/
├── base/
│   ├── variables.css    (de theme-vars + cores de notice)
│   ├── reset.css        (movido, sem alterações)
│   ├── typography.css   (fundido: extended/typography + tipografia de reset)
│   └── scrollbar.css    (renomeado de includes/scroll-bar.css)
├── components/
│   ├── layout.css       (fundido: header + footer + main)
│   ├── content.css      (extraído: tipografia de posts, listas, blockquotes)
│   ├── code.css         (fundido: blocos de código + chroma-styles + chroma-mod)
│   ├── navigation.css   (fundido: paginação, TOC, archive, search)
│   ├── cards.css        (fundido: post-entry, profile-mode, terms, 404)
│   └── notice.css       (refatorado com variáveis CSS)
└── responsive.css       (movido de core/zmedia.css)
```

## Ordem de Carregamento

```
variables → reset → typography → scrollbar → components/* → responsive
```

A licença será incluída como comentário no topo de variables.css.

## Ficheiros Críticos a Modificar

- `layouts/partials/head.html` — atualizar pipeline de recursos
- `assets/css/core/theme-vars.css` — fonte para variables.css
- `assets/css/common/post-single.css` — dividir em content.css, code.css, navigation.css
- `assets/css/extended/notice.css` — refatorar cores para usar variáveis

## Fases de Implementação

### Fase 1: Fundação (risco baixo)
1. Criar `base/variables.css` — copiar de theme-vars.css
2. Criar `base/reset.css` — copiar de core/reset.css
3. Criar `base/typography.css` — fundir declarações de fontes
4. Criar `base/scrollbar.css` — mover de includes/scroll-bar.css
5. Atualizar head.html para usar novos caminhos base/
6. **Testar:** verificar que não há alterações visuais

### Fase 2: Componentes de Layout (risco médio)
7. Criar `components/layout.css` — fundir header + footer + main
8. Criar `components/cards.css` — fundir post-entry, profile-mode, terms, 404
9. Atualizar head.html
10. **Testar:** verificar homepage, páginas de lista, página 404

### Fase 3: Componentes de Conteúdo (risco médio)
11. Criar `components/content.css` — extrair de post-single.css
12. Criar `components/code.css` — fundir código de post-single + main + chroma
13. Criar `components/navigation.css` — extrair TOC, paginação + archive + search
14. Atualizar head.html
15. **Testar:** verificar posts, syntax highlighting, TOC, arquivo

### Fase 4: Refatoração de Notice (risco baixo)
16. Adicionar variáveis de cor de notice a `base/variables.css`
17. Refatorar `components/notice.css` para usar variáveis
18. **Testar:** verificar os 12 tipos de notice em ambos os temas

### Fase 5: Limpeza de Variáveis (risco médio)
19. Substituir variáveis legacy pelos equivalentes modernos em todo o código
20. Remover variáveis legacy de variables.css
21. **Testar:** revisão visual completa

### Fase 6: Limpeza Final (risco baixo)
22. Eliminar diretórios antigos (core/, common/, extended/, includes/)
23. Simplificação final de head.html
24. **Testar:** teste completo do site

## Variáveis Legacy a Migrar

| Variável Legacy | Substituir por |
|-----------------|----------------|
| `--entrysize` | `--text-sm` |
| `--footersize` | `--text-xs` |
| `--h1size` | `--text-2xl` |
| `--headersize` | `--text-base` |
| `--homesize` | `--text-base` |
| `--lineclamp` | valor inline (8) |
| `--lineheight` | `--leading-normal` |
| `--marginleft` | valor inline (26px) |
| `--textsize` | `--text-base` |

## Verificação

Após cada fase, verificar:
- [ ] Homepage (profile mode) renderiza corretamente
- [ ] Páginas de lista de posts
- [ ] Páginas de post individual: headings, code blocks, tabelas, imagens
- [ ] Páginas de arquivo
- [ ] Funcionalidade de pesquisa
- [ ] Blocos de notice (12 tipos, ambos os temas)
- [ ] Toggle de dark mode funciona
- [ ] Comportamento responsivo em mobile
- [ ] Syntax highlighting (temas light e dark)
- [ ] TOC expand/collapse
- [ ] Scrollbar styling

## Resultado Esperado

| Métrica | Antes | Depois |
|---------|-------|--------|
| Ficheiros | 19 | 10 |
| Diretórios | 4 | 2 |
| Linhas (estimado) | 1.701 | ~1.400 |
| Ficheiro maior | 448 linhas | ~220 linhas |
| Variáveis legacy | 8 | 0 |
