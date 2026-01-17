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

## Workflow de Verificação Visual

### Screenshots de Baseline (Fase 0)

Antes de qualquer alteração, capturar screenshots de referência:

**Páginas a capturar (light mode e dark mode):**
1. Homepage (profile mode)
2. Página de lista de posts (ex: /llms/)
3. Post individual com código (ex: um post com syntax highlighting)
4. Página de arquivo (/archives/)
5. Página 404
6. Post com notice blocks (se existir)

**Armazenamento:**
- Diretório: `docs/screenshots/`
- Naming: `fase-0-[página]-[tema].png` (ex: `fase-0-homepage-light.png`)
- Fazer commit dos screenshots de baseline antes de iniciar Fase 1

### Verificação por Fase

Após cada fase:
1. Tirar novos screenshots das mesmas páginas
2. Naming: `fase-N-[página]-[tema].png`
3. Comparar visualmente com screenshots anteriores
4. Fazer commit dos novos screenshots
5. **Parar e informar o utilizador**
6. **Aguardar confirmação explícita para continuar**

### Limpeza Final

Após confirmação de que o plano está completo:
- Eliminar screenshots intermédios (manter apenas baseline e final)
- Aguardar confirmação do utilizador antes de eliminar

## Fases de Implementação

### Fase 0: Screenshots de Baseline
1. Iniciar hugo server
2. Capturar screenshots de todas as páginas de referência (light + dark)
3. Guardar em `docs/screenshots/`
4. Fazer commit
5. **Parar e aguardar confirmação**

### Fase 1: Fundação (risco baixo)
1. Criar `base/variables.css` — copiar de theme-vars.css
2. Criar `base/reset.css` — copiar de core/reset.css
3. Criar `base/typography.css` — fundir declarações de fontes
4. Criar `base/scrollbar.css` — mover de includes/scroll-bar.css
5. Atualizar head.html para usar novos caminhos base/
6. Capturar screenshots fase-1
7. Comparar com baseline
8. Fazer commit
9. **Parar e aguardar confirmação**

### Fase 2: Componentes de Layout (risco médio)
1. Criar `components/layout.css` — fundir header + footer + main
2. Criar `components/cards.css` — fundir post-entry, profile-mode, terms, 404
3. Atualizar head.html
4. Capturar screenshots fase-2
5. Comparar com fase-1
6. Fazer commit
7. **Parar e aguardar confirmação**

### Fase 3: Componentes de Conteúdo (risco médio)
1. Criar `components/content.css` — extrair de post-single.css
2. Criar `components/code.css` — fundir código de post-single + main + chroma
3. Criar `components/navigation.css` — extrair TOC, paginação + archive + search
4. Atualizar head.html
5. Capturar screenshots fase-3
6. Comparar com fase-2
7. Fazer commit
8. **Parar e aguardar confirmação**

### Fase 4: Refatoração de Notice (risco baixo)
1. Adicionar variáveis de cor de notice a `base/variables.css`
2. Refatorar `components/notice.css` para usar variáveis
3. Capturar screenshots fase-4
4. Comparar com fase-3
5. Fazer commit
6. **Parar e aguardar confirmação**

### Fase 5: Limpeza de Variáveis (risco médio)
1. Substituir variáveis legacy pelos equivalentes modernos em todo o código
2. Remover variáveis legacy de variables.css
3. Capturar screenshots fase-5
4. Comparar com fase-4
5. Fazer commit
6. **Parar e aguardar confirmação**

### Fase 6: Limpeza Final (risco baixo)
1. Eliminar diretórios antigos (core/, common/, extended/, includes/)
2. Simplificação final de head.html
3. Capturar screenshots finais
4. Comparar com baseline (devem ser idênticos)
5. Fazer commit
6. **Parar e aguardar confirmação final**

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

## Checklist de Verificação Visual

Após cada fase, confirmar em cada screenshot:
- [ ] Layout geral mantido
- [ ] Cores e contrastes corretos
- [ ] Tipografia sem alterações
- [ ] Espaçamentos preservados
- [ ] Dark mode funcional
- [ ] Elementos interativos visíveis

## Resultado Esperado

| Métrica | Antes | Depois |
|---------|-------|--------|
| Ficheiros | 19 | 10 |
| Diretórios | 4 | 2 |
| Linhas (estimado) | 1.701 | ~1.400 |
| Ficheiro maior | 448 linhas | ~220 linhas |
| Variáveis legacy | 8 | 0 |
