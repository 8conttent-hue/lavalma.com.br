# CLAUDE.md — LAVALMA

Site gerado pelo **SF (Site Factory)** em 15/04/2026.

## Contexto do Site

**Nome:** LAVALMA
**Nicho:** Moda e Beleza
**Keywords:** Bem vindo ao Lava Alma o refugio para os amantes da beleza
**Paleta de cores:** gold | **Fonte:** poppins

Bem-vindo ao Lava Alma, o refúgio para os amantes da beleza ética e sustentável. Em nosso universo de cosméticos e belezas veganos, acreditamos que é possível alcançar a exuberância sem sacrificar a natureza ou os animais. Cada produto que oferecemos é cuidadosamente selecionado e formulado para realçar sua beleza única, enquanto preserva o equilíbrio ecológico do nosso planeta. Nossa paixão pela beleza consciente é evidente em cada etapa da jornada do Lava Alma. Escolhemos ingredientes éticos, livres de crueldade e de origem vegetal, garantindo que nenhum animal sofra em prol da nossa beleza. Além disso, nossas embalagens são ecologicamente corretas, feitas com materiais recicláveis ou biodegradáveis, contribuindo para a redução do impacto ambiental. No Lava Alma, acreditamos que a beleza vai além da aparência. Buscamos nutrir a alma e a autoestima de nossos clientes, oferecendo uma experiência de bem-estar e conexão com a natureza. Nossos produtos são uma celebração da individualidade e da diversidade, pois acreditamos que a verdadeira beleza está na autenticidade de cada pessoa. Junte-se a nós nessa jornada de transformação consciente da indústria da beleza. Explore nossa ampla gama de cosméticos, desde maquiagens que realçam seus traços únicos até produtos para cuidados pessoais que mimam sua pele e cabelo. Sinta-se confiante ao saber que sua escolha eco-friendly está fazendo a diferença para um futuro mais sustentável. Sinta-se bem, sinta-se belo, sinta-se em harmonia com a natureza. Descubra a beleza que transcende o espelho. Descubra o Lava Alma.



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
  content/blog/    # Posts em Markdown
  pages/           # Rotas Astro (index, sobre, contato, blog, privacidade, termos)
  layouts/         # BaseLayout com fonte e cores dinâmicas
  styles/          # global.css com variáveis CSS de cor
public/
  images/          # hero.jpg, about.jpg, blog/*.jpg — inseridos automaticamente via Pexels
```

## O que editar

### Textos e conteúdo
- **`src/data/home.json`** — hero (título, subtítulo, botão), features (título, items), about section (título, desc, stats), posts
- **`src/data/sobre.json`** — conteúdo completo da página Sobre (hero, texto, missão)
- **`src/data/contato.json`** — título, subtítulo, email, tempo de resposta
- **`src/data/siteConfig.json`** — nome, slug, email, redes sociais, menu

### Imagens
Imagens já estão em `public/images/` (via Pexels). Para substituir, mantenha os mesmos nomes de arquivo:
- `hero.jpg` — imagem de fundo do Hero
- `about.jpg` — imagem da seção About (home)
- `sobre.jpg` — imagem de fundo da página Sobre
- `blog/{slug}.jpg` — imagens dos posts

### Posts do blog
Arquivos em `src/content/blog/`. Ajuste o tom de voz, adicione dados específicos do nicho e personalize conforme a identidade do site.

### Cores
Variáveis em `src/styles/global.css`: `--color-primary`, `--color-accent`, `--color-dark`.

## Deploy

```bash
bun install
bun run build
# Faça upload da pasta dist/ para Netlify, Vercel ou hosting estático
```
