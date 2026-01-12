# Plano: Configurar Site Hugo no GitHub Pages

## Objetivo
Configurar um site baseado em Hugo usando o template `pmichaillat/hugo-website`, implementado no GitHub Pages em `cboone.github.io`.

---

## Decisoes Confirmadas

| Aspecto | Escolha |
|---------|---------|
| **Nome** | Christopher Boone |
| **Seccoes** | Notes, Projects |
| **Links Sociais** | GitHub, LinkedIn, Instagram (+ outros a definir) |
| **Foto** | Sim (adicionar depois) |
| **Tema** | Auto com toggle (detecta preferencia do sistema) |
| **Branch principal** | main |

---

## Passos de Implementacao

### Fase 0: Renomear Branch

1. **Renomear branch master para main**
   - Utilizador fara esta alteracao manualmente
   - Actualizar default branch no GitHub se necessario

### Fase 1: Copiar Template

2. **Clonar o template temporariamente e copiar ficheiros**
   ```bash
   # Clonar template para pasta temporaria
   git clone --depth 1 https://github.com/pmichaillat/hugo-website /tmp/claude/hugo-website

   # Copiar ficheiros relevantes para o repositorio
   cp -r /tmp/claude/hugo-website/.github .
   cp -r /tmp/claude/hugo-website/archetypes .
   cp -r /tmp/claude/hugo-website/assets .
   cp -r /tmp/claude/hugo-website/content .
   cp -r /tmp/claude/hugo-website/layouts .
   cp -r /tmp/claude/hugo-website/static .
   cp /tmp/claude/hugo-website/config.yml .

   # Adicionar tema PaperMod como submodulo
   git submodule add https://github.com/adityatelange/hugo-PaperMod themes/PaperMod
   ```

### Fase 2: Configuracao Inicial

3. **Atualizar `config.yml`**
   ```yaml
   baseURL: "https://cboone.github.io/"
   title: "Christopher Boone"

   # Menu
   menu:
     main:
       - name: Notes
         url: /notes/
         weight: 1
       - name: Projects
         url: /projects/
         weight: 2

   # Tema com toggle
   params:
     defaultTheme: auto
     disableThemeToggle: false

   # Links sociais
   socialIcons:
     - name: github
       url: "https://github.com/cboone"
     - name: linkedin
       url: "https://linkedin.com/in/..."
     - name: instagram
       url: "https://instagram.com/..."
   ```

4. **Verificar workflow do GitHub Actions**
   - Confirmar que esta configurado para branch `main`

### Fase 3: Conteudo Inicial

5. **Limpar conteudo de exemplo e criar estrutura**
   - Remover conteudo de exemplo do template
   - Criar `content/notes/` - notas e posts
   - Criar `content/projects/` - paginas de projectos

6. **Configurar pagina inicial**
   - Placeholder para foto (adicionar depois)
   - Texto de apresentacao (opcional)

### Fase 4: Configuracao do GitHub Pages

7. **Configurar GitHub Pages no repositorio**
   - Settings > Pages > Source: GitHub Actions

8. **Fazer push e verificar deploy**
   - Confirmar que o workflow executa com sucesso
   - Verificar site em https://cboone.github.io

---

## Ficheiros Criticos a Modificar

| Ficheiro | Descricao |
|----------|-----------|
| `config.yml` | Configuracao principal do Hugo |
| `.github/workflows/hugo.yml` | Workflow de deploy |
| `content/notes/_index.md` | Pagina de listagem de notas |
| `content/projects/_index.md` | Pagina de listagem de projectos |
| `static/picture.png` | Foto de perfil (adicionar depois) |

---

## Verificacao

1. Executar `hugo server` localmente e verificar em `localhost:1313`
2. Fazer push e confirmar que o GitHub Action executa com sucesso
3. Aceder a https://cboone.github.io e verificar o site

---

## Notas

- O template usa o tema PaperMod modificado para contexto academico
- O workflow actual usa Hugo v0.147.2
- Suporta LaTeX/MathJax para formulas matematicas
- Sintaxe de codigo com realce automatico

---

## Informacao Adicional Necessaria Durante Implementacao

Durante a implementacao, vou precisar de:
- URL do perfil LinkedIn
- URL do perfil Instagram
- Outros links sociais a adicionar (se houver)
- Texto de apresentacao para a pagina inicial (opcional - pode ser adicionado depois)
- Caminho para a foto de perfil (quando estiver pronta)
