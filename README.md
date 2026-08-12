# LP — Manual do Corte · Lu Carrilho

Landing page de vendas do curso **Manual do Corte**, em HTML/CSS/JS puro (arquivo único, sem build e sem dependências).

## Estrutura

```
lp-manual-do-corte-lu-carrilho/
├── index.html      ← a página inteira (CSS e JS inline)
├── .nojekyll       ← publica os arquivos diretamente no GitHub Pages
├── images/         ← favicon e imagens adicionais do projeto
│   └── figma/      ← assets exportados do layout do Figma
└── README.md
```

## Assets

O hero oficial está em `images/hero-image.png` e o selo vetorial de garantia em `images/7-dias-vetor.svg`. As fotos editoriais, curvas, ícones e demais elementos gráficos do layout estão em `images/figma/`; nenhum deles depende dos links temporários do Figma.

A faixa de resultados no meio da página mantém os cinco cartões rosa existentes no layout. Caso as fotos sejam adicionadas depois, use `images/resultado-1.jpg` até `images/resultado-5.jpg` nos blocos `.proof-slot` indicados no `index.html`.

O favicon vetorial está em `images/favicon.svg`.

## Pendências de conteúdo (antes de publicar)

- [ ] **Valor da parcela** — o botão de preço mostra `12x de R$` com o marcador rosa "Ver na Hotmart". Substituir pelo valor real (procure por `class="pend"` no HTML).
- [ ] **Divergência de valor total** — a Dobra 6 fecha em **R$772,00** e a Dobra 8 em **R$839,00**. Está assim na copy original. Definir qual é o correto.
- [ ] **Link do checkout** — o botão de compra está com `href="#"` e o atributo `data-checkout`. Trocar pela URL da Hotmart:
  ```bash
  grep -n 'data-checkout' index.html
  ```
- [ ] **Pixel / tag de conversão** — inserir antes de `</head>` se a campanha for rodar em mídia paga.

## Sistema visual

- **Fundos** alternados entre rosa-claro `#FFEFF9` e azul profundo `#171337`
- **Destaques** rosa `#FDCEEC` / `#E7C4D9` e lilás `#DCDBFF`
- Transições orgânicas, cards editoriais e assets exportados diretamente do Figma

Breakpoints: 1000px / 760px / 480px. Respeita `prefers-reduced-motion`.

### Tipografia — regra de uso

Cada família tem um papel fixo. Não misturar:

| Família | Onde usar |
|---|---|
| **Playfair Display** | Todos os títulos (h1–h4), perguntas do FAQ |
| **Fraunces** | Só citações (`.quotes`, `.display-copy`) e a camada de preços |
| **Manrope** | Corpo de texto, botões, labels |

A escala de títulos vem dos tokens no `:root` e é ancorada na H1 do hero — **nada na página pode ser maior que `--t-h1`**, com uma única exceção deliberada: `.price-main` (o preço final), que é o clímax da oferta.

```
--t-h1  34 → 47.8px    --t-h3  24 → 31px
--t-h2  30 → 43px      --t-h4  18 → 21px
--t-num 28 → 38px  (totais de preço)
```

Ao criar uma seção nova, **não declare `font-size` nem `font-family` no título** — use `<h2>`/`<h3>` e deixe os tokens agirem. Se precisar controlar a quebra de linha, ajuste o `max-width` em `ch` (nunca abaixo de ~20ch, senão o título espreme e vira uma coluna estreita de muitas linhas).

## Publicação

O projeto é publicado diretamente pelo GitHub Pages a partir da branch `main`. Não há passo de build.

Também pode ser hospedado no cPanel: basta enviar `index.html` e a pasta `images/` para `public_html/` ou para o subdiretório do site.
