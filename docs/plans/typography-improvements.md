# Plano: Melhorar a Tipografia do Tema

## Resumo

Melhorar a tipografia do site usando **Public Sans**, uma escala tipográfica harmoniosa (Major Third 1.25), e ajustes de espaçamento para maior legibilidade.

## Estado Atual

- **Fontes**: Sistema (browser default via PaperMod)
- **Variáveis**: Definidas em `assets/css/core/theme-vars.css`
- **Escala atual**: Inconsistente (h3 quase igual ao corpo, h4-h6 menores que o corpo)
- **Line-height**: 1.45 (ligeiramente apertado para leitura longa)

## Abordagem Escolhida

**Public Sans** + alterações completas:
- Fonte desenvolvida pelo U.S. Web Design System
- Neutra, moderna e muito legível
- Open source (SIL Open Font License)
- Self-hosted para melhor privacidade e performance

## Implementação

### 1. Descarregar Public Sans
- Obter ficheiros WOFF2 de https://github.com/uswds/public-sans/releases
- Pesos: 400 (Regular), 500 (Medium), 600 (SemiBold), 700 (Bold)
- Colocar em `static/fonts/`

### 2. Criar `assets/css/extended/typography.css`
- `@font-face` para Public Sans (4 pesos)
- Font smoothing (`-webkit-font-smoothing: antialiased`)
- Aplicar Public Sans ao body com fallback para system fonts
- Monospace font stack para código

### 3. Atualizar `assets/css/core/theme-vars.css`
Nova escala Major Third (1.25), base 18px:

| Variável | Valor | Uso |
|----------|-------|-----|
| `--text-xs` | 11px | Captions, footer |
| `--text-sm` | 14px | Metadata, secondary |
| `--text-base` | 18px | Body text |
| `--text-lg` | 22px | h4, lead |
| `--text-xl` | 28px | h3 |
| `--text-2xl` | 35px | h2 |
| `--text-3xl` | 44px | h1 |

Novas variáveis de line-height e letter-spacing:
- `--leading-tight`: 1.25 (headings)
- `--leading-normal`: 1.5 (body)
- `--tracking-tighter`: -0.02em (large headings)
- `--tracking-wide`: 0.025em (small caps)

### 4. Atualizar `assets/css/common/post-single.css`
- Aplicar nova escala aos headings h1-h6
- Adicionar letter-spacing negativo a headings grandes
- Melhorar margens verticais

### 5. Atualizar outros ficheiros
- `post-entry.css`: Títulos de entradas
- `profile-mode.css`: Título do perfil

## Ficheiros a Criar/Modificar

1. `static/fonts/` (criar diretório com ficheiros WOFF2)
2. `assets/css/extended/typography.css` (criar)
3. `assets/css/core/theme-vars.css` (editar)
4. `assets/css/common/post-single.css` (editar)
5. `assets/css/common/post-entry.css` (editar)
6. `assets/css/common/profile-mode.css` (editar)

## Verificação

1. Executar `hugo server`
2. Verificar páginas:
   - Homepage (profile)
   - Lista de posts
   - Post individual com todos os níveis de heading
3. Testar dark mode
4. Verificar em diferentes larguras de ecrã
