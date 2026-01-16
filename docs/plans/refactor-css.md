# Plano: Refatoração CSS

Refatorar os 19 ficheiros CSS (~1.600 linhas) para melhorar estrutura e organização, mantendo os estilos visuais iguais.

## Problemas Identificados

| Problema | Ficheiros Afetados |
|----------|-------------------|
| `0px` redundante (deve ser `0`) | main.css, profile-mode.css, search.css |
| `box-shadow: 0 0px 0` inútil | post-single.css (L400, L448) |
| `border-radius: 6px` literal (deve usar variável) | notice.css, header.css, terms.css |
| `font-weight` inconsistente (literal vs variável) | post-single.css, archive.css |
| Cores RGB hardcoded | scroll-bar.css |
| Linhas em branco duplicadas | post-single.css |
| Espaçamento irregular | post-single.css, 404.css |
| Media queries sem documentação | zmedia.css |
| Classes com underscore | profile-mode.css (`.profile_inner`), post-single.css (`.i18n_list`) |

---

## Fase 1: Correções Cosméticas (Risco Zero)

### 1.1 Normalizar `0px` para `0`

- `assets/css/common/main.css:32` — `10px 14px 10px 0px` → `10px 14px 10px 0`
- `assets/css/common/profile-mode.css:39` — `6px 12px 6px 0px` → `6px 12px 6px 0`
- `assets/css/common/search.css` — `top: 0px` → `top: 0`, `left: 0px` → `left: 0`

### 1.2 Remover linhas em branco duplicadas

- `assets/css/common/post-single.css` — linhas 37, 342, 384, 428

### 1.3 Normalizar espaçamento

- `assets/css/common/post-single.css:90` — espaço extra antes de `;`
- `assets/css/common/post-single.css:239` — espaços extras antes de `*/`

---

## Fase 2: Remoção de Código Morto (Baixo Risco)

### 2.1 Remover box-shadow sem efeito visual

Uma sombra `0 0px 0` não é visível — pode ser removida ou substituída por `none`.

- `assets/css/common/post-single.css:400` — `.anchor` hover
- `assets/css/common/post-single.css:448` — footnotes hover

---

## Fase 3: Consolidação de Variáveis (Médio Risco)

### 3.1 Adicionar variável para border-radius secundário

Em `assets/css/core/theme-vars.css`:

```css
--radius-sm: 6px;
```

Atualizar:
- `assets/css/extended/notice.css:5`
- `assets/css/common/header.css:35`
- `assets/css/common/terms.css:11`

### 3.2 Adicionar variáveis para font-weight

Em `assets/css/core/theme-vars.css`:

```css
--normal: 400;
--bold: 700;
```

Atualizar em `assets/css/common/post-single.css`:
- L137: `font-weight: 700` → `font-weight: var(--bold)`
- L270: `font-weight: bold` → `font-weight: var(--bold)`
- L277: `font-weight: normal` → `font-weight: var(--normal)`
- L398: `font-weight: 700` → `font-weight: var(--bold)`

Atualizar em `assets/css/common/archive.css`:
- L39: `font-weight: normal` → `font-weight: var(--normal)`

### 3.3 Adicionar variáveis para cores de scrollbar

Em `assets/css/core/theme-vars.css`:

```css
--scrollbar-thumb: rgb(113, 113, 117);
--scrollbar-thumb-hover: rgb(163, 163, 165);
--scrollbar-gist-border: rgb(255, 255, 255);
--scrollbar-gist-thumb: rgb(173, 173, 173);
--scrollbar-gist-thumb-hover: rgb(112, 112, 112);
```

Atualizar `assets/css/includes/scroll-bar.css` para usar estas variáveis.

---

## Fase 4: Documentação (Risco Zero)

### 4.1 Documentar media queries

Em `assets/css/core/zmedia.css`, adicionar comentários explicativos:

```css
/* Mobile: <=768px - reduce gaps, scale profile image */
/* Tablet: <=900px - adjust top-link position */
/* Narrow: <=340px - allow share buttons overflow */
/* Accessibility: prefers-reduced-motion */
```

### 4.2 Melhorar comentários de variáveis legacy

Em `assets/css/core/theme-vars.css`, expandir o comentário existente para explicar que são mantidas para compatibilidade.

---

## Fase 5: Renomeação de Classes (Alto Risco)

Requer alterações simultâneas em CSS e templates Hugo.

| Classe Atual | Nova Classe | Ficheiro CSS |
|--------------|-------------|--------------|
| `.profile_inner` | `.profile-inner` | profile-mode.css |
| `.i18n_list` | `.i18n-list` | post-single.css |

**Processo:**
1. Pesquisar templates: `grep -r "profile_inner\|i18n_list" layouts/`
2. Atualizar CSS e templates simultaneamente
3. Testar páginas afetadas

---

## Ficheiros Críticos

- `assets/css/core/theme-vars.css` — adicionar novas variáveis
- `assets/css/common/post-single.css` — maior ficheiro, mais correções
- `assets/css/common/profile-mode.css` — classe underscore, valor 0px
- `assets/css/includes/scroll-bar.css` — cores hardcoded
- `assets/css/core/zmedia.css` — adicionar documentação

---

## Verificação

Após cada fase, verificar:

1. **Build:** `hugo --gc --minify`
2. **Servidor local:** `hugo server --disableFastRender`
3. **Temas:** light mode e dark mode
4. **Responsividade:** 340px, 768px, 900px, desktop
5. **Páginas:** homepage, post, archive, tags, 404, search
6. **Componentes:** code blocks, TOC, notice boxes, scrollbars
