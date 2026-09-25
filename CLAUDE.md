# CLAUDE.md — LAVALMA

Site gerado pelo **SF (Site Factory)** em 15/04/2026. Migrado para o modelo Cloudflare + Supabase em 25/09/2026.

## Contexto do Site

**Nome:** LAVALMA
**Nicho:** Moda e Beleza
**Keywords:** Bem vindo ao Lava Alma o refugio para os amantes da beleza
**Paleta de cores:** gold | **Fonte:** poppins

Bem-vindo ao Lava Alma, o refúgio para os amantes da beleza ética e sustentável. Em nosso universo de cosméticos e belezas veganos, acreditamos que é possível alcançar a exuberância sem sacrificar a natureza ou os animais. Cada produto que oferecemos é cuidadosamente selecionado e formulado para realçar sua beleza única, enquanto preserva o equilíbrio ecológico do nosso planeta. Nossa paixão pela beleza consciente é evidente em cada etapa da jornada do Lava Alma. Escolhemos ingredientes éticos, livres de crueldade e de origem vegetal, garantindo que nenhum animal sofra em prol da nossa beleza. Buscamos nutrir a alma e a autoestima de nossos clientes, oferecendo uma experiência de bem-estar e conexão com a natureza.

## Componentes visuais usados

| Seção | Variante |
|-------|----------|
| Header | Header-I |
| Hero | Hero-I |
| Features | Features-J |
| About Section | About-B |
| Posts | Posts-H |
| Footer | Footer-I |
| Página Sobre | Sobre-A |
| Página Contato | Contato-C |

## Estrutura do projeto

```
src/
  sections/        # Layout escolhido pelo SF — Header, Hero, Features, About, Posts, Footer, Sobre, Contato
  data/            # JSONs com todo o conteúdo editável
  lib/             # supabase.ts (cliente) e posts.ts (getPosts/getPostBySlug)
  components/      # Seo.astro (meta tags + JSON-LD)
  pages/           # Rotas Astro (index, sobre, contato, blog, privacidade, termos, [...slug])
  layouts/         # BaseLayout com fonte e cores dinâmicas
  styles/          # global.css com variáveis CSS de cor
public/
  images/          # hero.jpg, about.jpg, sobre.jpg
```

## O que editar

### Textos e conteúdo
- **`src/data/home.json`** — hero (título, subtítulo, botão), features (título, items), about section (título, desc, stats), posts
- **`src/data/sobre.json`** — conteúdo completo da página Sobre (hero, texto, missão)
- **`src/data/contato.json`** — título, subtítulo, email, tempo de resposta
- **`src/data/siteConfig.json`** — nome, slug, email, redes sociais, menu (título/descrição/OG/JSON-LD derivam daqui)

### Imagens
Imagens já estão em `public/images/` (via Pexels). Para substituir, mantenha os mesmos nomes de arquivo:
- `hero.jpg` — imagem de fundo do Hero (e og:image padrão)
- `about.jpg` — imagem da seção About (home)
- `sobre.jpg` — imagem de fundo da página Sobre

### Posts do blog
Os posts NÃO ficam mais em markdown local. São carregados do Supabase (tabela `network_posts`, filtrados por `domain = lavalma.com.br`).
- `src/lib/posts.ts` — `getPosts()` e `getPostBySlug()`; `formatContentToHtml()` converte markdown → HTML.
- Sem painel admin. Novos posts/posts editados entram pela plataforma 8links e publicam automaticamente (via Git/CF).

### Cores
Variáveis em `src/styles/global.css`: `--color-primary`, `--color-accent`, `--color-dark`.

## SEO

- `src/components/Seo.astro` injetado pelo `BaseLayout`: title, description, canonical, OG, Twitter, `name="robots"`, JSON-LD (WebSite nas páginas estáticas, BlogPosting nos artigos).
- `src/pages/robots.txt.ts` e `src/pages/sitemap.xml.ts` gerados dinamicamente (sitemap inclui posts com lastmod).

## Deploy

```bash
bun install
bun run build
# Publicar no Cloudflare: a pasta dist/ é servida como Worker (adaptador @astrojs/cloudflare)
# Envs opcionais no CF: SUPABASE_URL e SUPABASE_ANON_KEY (fallbacks embutidos no código)
```