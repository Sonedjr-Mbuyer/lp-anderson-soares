# CLAUDE.md — Diretrizes de Design para LPs Imobiliárias de Alto Padrão

> Este arquivo define o padrão de qualidade visual e técnico para todas as landing pages criadas neste projeto. Leia e siga rigorosamente antes de escrever qualquer linha de código.

---

## 1. IDENTIDADE VISUAL

### Paleta de Cores
Nunca use azul como cor de destaque padrão. A paleta deve partir do próprio empreendimento. Para imobiliário de alto padrão, o ponto de partida é:

- Cor primária: verde-musgo escuro, petróleo profundo ou chumbo quente — nunca preto puro (#000)
- Cor de destaque: dourado envelhecido, champagne ou areia quente — nunca amarelo genérico
- Fundo: branco off-white (#F9F7F3 ou similar), nunca branco puro (#FFF) como fundo principal
- Nunca use gradientes coloridos. Se usar gradiente, apenas escuro-para-transparente sobre imagem.

### Tipografia
- Títulos (display): fontes serifadas com personalidade — Cormorant Garamond, Playfair Display, DM Serif Display ou similar. Nunca use a mesma fonte em título e corpo.
- Corpo: fonte sans-serif limpa e contemporânea — DM Sans, Inter (com moderação), Outfit.
- Nunca use font-weight 700 em tudo. Varie: títulos principais em 700, subtítulos em 400 italic, corpo em 300 ou 400.
- Tamanho de título hero: mínimo clamp(40px, 6vw, 80px). Títulos grandes criam impacto imediato.
- Letter-spacing em eyebrows e labels: 2px a 4px, uppercase, font-size 10-12px.

### Formas e Bordas
- Border-radius: 0px ou 2px máximo em elementos de destaque. Bordas arredondadas genéricas são o sinal mais claro de design padrão de IA.
- Nunca use border-radius > 8px, exceto em avatares circulares.
- Prefira ângulos retos, proporções áureas e assimetria controlada.

---

## 2. LAYOUT E ESTRUTURA

### Princípios Fundamentais
- **Hierarquia visual clara**: cada seção tem UM elemento principal que domina. Nunca distribua atenção igualmente entre vários elementos.
- **Respiração**: use padding generoso. Seções apertadas comunicam baixo padrão.
- **Assimetria intencional**: grids 5/7, 4/8, 3/9 são mais sofisticados que 6/6.
- **Âncoras visuais**: cada seção deve ter um elemento que "prende o olho" — uma imagem dominante, um número grande, uma citação em destaque.

### Grid
- Use CSS Grid nativo, nunca frameworks de grid externos.
- Varie o grid entre seções — não use o mesmo layout em duas seções seguidas.
- Quebre o container ocasionalmente: imagens que sangram até a borda da tela criam sensação premium.

### Seção Hero
- Sempre full-viewport (min-height: 100vh).
- Imagem de fundo com overlay escuro gradiente — nunca cor sólida sobre imagem.
- Texto alinhado à esquerda com formulário à direita (em desktop).
- O hero deve comunicar em 3 segundos: o produto, quem está vendendo e o próximo passo.

---

## 3. IMAGENS E MÍDIA

### Tratamento de Imagens — PRIORITÁRIO
Este é o elemento que mais diferencia uma LP premium de uma LP genérica.

- **Nunca use `object-fit: cover` sem considerar o `object-position`**. Posicione a imagem intencionalmente para mostrar o elemento mais impactante (vista, fachada, área de lazer).
- **Imagens hero**: sempre full-bleed (largura 100vw), nunca dentro de container com padding.
- **Imagens de seção**: alterne entre full-bleed, contained e sangria parcial (imagem que ultrapassa o container em 20-30%).
- **Parallax sutil**: aplique `transform: translateY()` via scroll em imagens hero para sensação de profundidade. Máximo 20% de deslocamento.
- **Aspect ratios**: use proporções cinematográficas em imagens de destaque (16:9, 21:9) e retratos em 3:4 ou 4:5 para interiores.
- **Lightbox**: galeria sempre com lightbox funcional, navegação por teclado e swipe em mobile.
- **Lazy loading**: todas as imagens abaixo do fold com `loading="lazy"`.

### Vídeo e Animação
- Se houver vídeo, use como background do hero com `autoplay muted loop playsinline`.
- Nunca use GIFs — prefira vídeos MP4 ou CSS animations.

---

## 4. ANIMAÇÕES E INTERATIVIDADE

### Filosofia
Animação serve à narrativa, não à exibição. Cada animação deve ter uma razão de existir.

### O que usar
- **Scroll reveal**: elementos entram suavemente ao scrollar — `opacity: 0 → 1` + `translateY(30px → 0)` com `transition: 0.6s ease`. Use Intersection Observer, nunca bibliotecas pesadas.
- **Parallax em imagens hero**: deslocamento sutil que cria profundidade.
- **Hover em cards**: `translateY(-4px)` + `box-shadow` suave. Nunca zoom brusco.
- **Números animados**: contadores que sobem ao entrar na viewport (para seções de estatísticas).
- **Cursor personalizado**: em projetos premium, um cursor dot customizado eleva a percepção de qualidade.
- **Sticky header**: transparente no topo, escurece e compacta ao scrollar.

### O que NUNCA usar
- Animações de entrada em bounce ou elásticas
- Rotações desnecessárias
- Parallax em texto (prejudica leitura)
- Animações que disparam sem scroll (distração imediata)
- Transições acima de 0.8s (percebidas como lentas)

---

## 5. COPY E MICROCOPY

### Tom de Voz para Imobiliário de Alto Padrão
- Sofisticado, direto, sem exageros.
- Nunca use: "incrível", "perfeito", "sonho", "oportunidade única", "não perca".
- Prefira: "projetado para", "entregue em", "a poucos metros de", "planejado com".
- Headlines: afirmações sobre estilo de vida, não sobre o produto. Ex: "Viver bem tem um endereço" > "Apartamento com 3 quartos na Av. Rio Branco".
- CTAs: específicos e com baixo atrito. "Agendar visita" > "Saiba mais". "Receber tabela de preços" > "Solicitar informações".

### Estrutura de Copy por Seção
1. **Hero**: promessa principal + localização + CTA imediato
2. **Números**: 3-4 dados que validam o produto (metragem, andares, unidades, % vendido)
3. **Sobre o empreendimento**: story, não lista de features
4. **Corretor**: autoridade + proximidade + CTA direto
5. **Lazer/Diferenciais**: benefício emocional primeiro, feature depois
6. **Galeria**: sem texto — as imagens falam
7. **Localização**: contexto de vida, não apenas endereço
8. **Formulário**: eliminar fricção — promessa de retorno rápido, sem spam

---

## 6. PERFORMANCE E CÓDIGO

### HTML
- Semântico: `<header>`, `<main>`, `<section>`, `<article>`, `<footer>` nos lugares certos.
- IDs em todas as seções para navegação por âncora.
- Meta tags completas: title, description, og:image, og:title para compartilhamento social.

### CSS
- Variáveis CSS (`:root`) para TODAS as cores, fontes e espaçamentos — nunca valores hardcoded espalhados.
- Mobile-first: escreva o CSS base para mobile e use `@media (min-width: 768px)` para desktop.
- Sem frameworks CSS externos (Bootstrap, Tailwind). CSS puro e limpo.
- Nunca duplique seletores. Organize em blocos: reset → variáveis → layout → componentes → seções → responsivo.

### JavaScript
- Vanilla JS apenas. Sem jQuery, sem bibliotecas desnecessárias.
- Intersection Observer para scroll animations — nunca scroll event listener direto.
- Debounce em eventos de resize e scroll.
- Formulário: validação inline (não só no submit), máscara de telefone, feedback visual.

### Responsivo
- Breakpoints: 480px (mobile pequeno), 768px (tablet), 1024px (desktop), 1440px (wide).
- Imagens hero: altura mínima 100svh em mobile (usar svh, não vh, para evitar problema de barra de endereço).
- Formulário: ocupa largura total em mobile, nunca campos cortados.
- Menu mobile: hamburger com overlay escuro, animação suave.
- Fonte mínima: 16px em corpo para mobile — nunca menor.

---

## 7. ELEMENTOS QUE CARACTERIZAM "DESIGN PADRÃO DE IA" — EVITAR SEMPRE

Os itens abaixo são sinais imediatos de que a página foi gerada por IA sem critério. Nunca os use sem justificativa explícita:

- ❌ Cards com sombra `box-shadow: 0 4px 6px rgba(0,0,0,0.1)` em grid 3x uniforme
- ❌ Seção de "features" com ícones SVG genéricos + título + 2 linhas de texto em grid 3 colunas
- ❌ Botões com border-radius: 8px ou 50px (pill)
- ❌ Gradiente de hero em azul ou roxo
- ❌ Seção de depoimentos com foto redonda + nome + estrelinhas amarelas
- ❌ Footer com 4 colunas de links + redes sociais em grid uniforme
- ❌ Animação de "fade in from bottom" em TODOS os elementos da página
- ❌ Paleta azul (#3B82F6) + branco + cinza como identidade visual
- ❌ Inter ou Roboto como única fonte em toda a página
- ❌ Numeração 01 / 02 / 03 em seções que não são sequenciais
- ❌ "Por que nos escolher?" como título de seção
- ❌ Placeholder de imagem cinza com ícone de câmera

---

## 8. CHECKLIST ANTES DE ENTREGAR

Antes de considerar qualquer arquivo finalizado, confirme:

- [ ] A página carrega sem erros no console
- [ ] Todas as seções têm IDs para navegação
- [ ] O formulário valida campos e tem máscara de telefone
- [ ] As imagens têm `alt` descritivo
- [ ] Scroll animations funcionam ao rolar a página
- [ ] Header fica sticky e muda ao scrollar
- [ ] Botão de WhatsApp flutuante está visível em mobile
- [ ] A página é navegável sem mouse (Tab + Enter)
- [ ] Nenhuma imagem está cortada ou distorcida
- [ ] Os textos placeholder estão claramente marcados com comentários `<!-- TODO: substituir -->`
- [ ] As variáveis CSS estão centralizadas e comentadas em português
- [ ] O arquivo tem menos de 2000 linhas (se mais, propor separação em arquivos)
