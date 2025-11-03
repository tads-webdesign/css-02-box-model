# Tutorial CSS: Box Model para Iniciantes

Este tutorial completo sobre CSS Box Model foi criado para ajudar iniciantes a entender os conceitos fundamentais de layout e espaçamento em CSS.

## Sumário

1. [O que é o Box Model](#1-o-que-é-o-box-model)
   - [Componentes do Box Model](#componentes-do-box-model)
   - [Exemplo Visual](#exemplo-visual)
2. [Propriedades de Dimensão](#2-propriedades-de-dimensão)
   - [Width e Height](#width-e-height)
   - [Box-sizing](#box-sizing)
3. [Propriedades de Borda](#3-propriedades-de-borda)
   - [Border-width](#border-width)
   - [Border-style](#border-style)
   - [Border-color](#border-color)
   - [Shorthand da Border](#shorthand-da-border)
4. [Propriedades de Espaçamento](#4-propriedades-de-espaçamento)
   - [Margin](#margin)
   - [Padding](#padding)
   - [Notação Individual e Shorthand](#notação-individual-e-shorthand)
5. [Propriedades Display](#5-propriedades-display)
   - [Block](#block)
   - [Inline](#inline)
   - [Inline-block](#inline-block)
6. [Exemplo Prático: Criando Cards](#6-exemplo-prático-criando-cards)
7. [Exemplo Prático: Layout com Box Model](#7-exemplo-prático-layout-com-box-model)
8. [Dicas e Boas Práticas](#8-dicas-e-boas-práticas)

---

## 1. O que é o Box Model

O Box Model (Modelo de Caixa) é um conceito fundamental do CSS que define como os elementos HTML são renderizados na página. Cada elemento é tratado como uma caixa retangular composta por quatro áreas:

### Componentes do Box Model

1. **Content (Conteúdo)**: A área onde o texto e imagens aparecem
2. **Padding (Preenchimento)**: Espaço transparente entre o conteúdo e a borda
3. **Border (Borda)**: Uma linha ao redor do padding e conteúdo
4. **Margin (Margem)**: Espaço transparente fora da borda, separando o elemento de outros

```
+----------------------------------+
|           MARGIN                 |
|  +--------------------------+    |
|  |        BORDER            |    |
|  |  +-------------------+   |    |
|  |  |     PADDING       |   |    |
|  |  |  +------------+   |   |    |
|  |  |  |  CONTENT   |   |   |    |
|  |  |  +------------+   |   |    |
|  |  +-------------------+   |    |
|  +--------------------------+    |
+----------------------------------+
```

### Exemplo Visual

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    .box-exemplo {
      width: 200px;
      height: 100px;
      padding: 20px;
      border: 5px solid #3498db;
      margin: 30px;
      background-color: #ecf0f1;
    }
  </style>
</head>
<body>
  <div class="box-exemplo">
    Este é o conteúdo da caixa
  </div>
</body>
</html>
```

**Resultado:**
- Content: 200px × 100px
- Padding: 20px em todos os lados
- Border: 5px sólida azul
- Margin: 30px ao redor
- **Largura total**: 200 + (20×2) + (5×2) + (30×2) = 310px
- **Altura total**: 100 + (20×2) + (5×2) + (30×2) = 210px

---

## 2. Propriedades de Dimensão

### Width e Height

As propriedades `width` e `height` definem a largura e altura do conteúdo do elemento.

```css
/* Valores fixos */
.elemento {
  width: 300px;
  height: 200px;
}

/* Valores percentuais */
.elemento-responsivo {
  width: 100%;
  height: 50%;
}

/* Valores automáticos */
.elemento-auto {
  width: auto;  /* Ajusta ao conteúdo */
  height: auto;
}

/* Valores máximos e mínimos */
.elemento-limitado {
  width: 100%;
  max-width: 1200px;
  min-width: 320px;
  min-height: 100px;
}
```

**Exemplo prático:**

```html
<style>
  .container {
    width: 80%;
    max-width: 800px;
    height: auto;
    margin: 0 auto;
    background-color: #f8f9fa;
  }
</style>

<div class="container">
  <p>Este container tem largura responsiva com limite máximo</p>
</div>
```

### Box-sizing

A propriedade `box-sizing` controla como as dimensões totais são calculadas.

```css
/* Padrão: content-box */
.content-box {
  box-sizing: content-box;
  width: 200px;
  padding: 20px;
  border: 5px solid black;
  /* Largura total = 200 + 40 + 10 = 250px */
}

/* Recomendado: border-box */
.border-box {
  box-sizing: border-box;
  width: 200px;
  padding: 20px;
  border: 5px solid black;
  /* Largura total = 200px (padding e border incluídos) */
}
```

**Dica importante:** É comum usar `box-sizing: border-box` em todos os elementos:

```css
* {
  box-sizing: border-box;
}
```

**Exemplo comparativo:**

```html
<style>
  .exemplo-content {
    box-sizing: content-box;
    width: 200px;
    padding: 20px;
    border: 3px solid #e74c3c;
    background-color: #fadbd8;
    margin-bottom: 20px;
  }
  
  .exemplo-border {
    box-sizing: border-box;
    width: 200px;
    padding: 20px;
    border: 3px solid #27ae60;
    background-color: #d5f4e6;
  }
</style>

<div class="exemplo-content">content-box: largura final maior</div>
<div class="exemplo-border">border-box: largura final = 200px</div>
```

---

## 3. Propriedades de Borda

### Border-width

Define a espessura da borda.

```css
.borda-fina {
  border-width: 1px;
}

.borda-media {
  border-width: 3px;
}

.borda-grossa {
  border-width: 10px;
}

/* Valores por lado */
.borda-variada {
  border-top-width: 2px;
  border-right-width: 4px;
  border-bottom-width: 6px;
  border-left-width: 8px;
}

/* Shorthand com 4 valores (topo, direita, baixo, esquerda) */
.borda-short {
  border-width: 2px 4px 6px 8px;
}
```

### Border-style

Define o estilo da linha da borda.

```css
.borda-solida {
  border-style: solid;  /* Linha sólida */
}

.borda-tracejada {
  border-style: dashed;  /* Linha tracejada */
}

.borda-pontilhada {
  border-style: dotted;  /* Linha pontilhada */
}

.borda-dupla {
  border-style: double;  /* Linha dupla */
}

.borda-groove {
  border-style: groove;  /* Efeito 3D entalhado */
}

.borda-ridge {
  border-style: ridge;  /* Efeito 3D elevado */
}

.borda-inset {
  border-style: inset;  /* Efeito 3D inserido */
}

.borda-outset {
  border-style: outset;  /* Efeito 3D projetado */
}

.sem-borda {
  border-style: none;  /* Sem borda */
}
```

**Exemplo visual:**

```html
<style>
  .exemplo-estilos div {
    width: 150px;
    padding: 10px;
    margin: 10px;
    border-width: 4px;
    display: inline-block;
  }
  
  .estilo-solid { border-style: solid; border-color: #3498db; }
  .estilo-dashed { border-style: dashed; border-color: #e74c3c; }
  .estilo-dotted { border-style: dotted; border-color: #2ecc71; }
  .estilo-double { border-style: double; border-color: #f39c12; }
</style>

<div class="exemplo-estilos">
  <div class="estilo-solid">Solid</div>
  <div class="estilo-dashed">Dashed</div>
  <div class="estilo-dotted">Dotted</div>
  <div class="estilo-double">Double</div>
</div>
```

### Border-color

Define a cor da borda.

```css
/* Cor única para todos os lados */
.borda-azul {
  border-color: #3498db;
}

/* Cores diferentes por lado */
.borda-colorida {
  border-top-color: red;
  border-right-color: green;
  border-bottom-color: blue;
  border-left-color: yellow;
}

/* Usando diferentes formatos de cor */
.cores-variadas {
  border-color: rgb(255, 0, 0);        /* RGB */
  border-color: rgba(255, 0, 0, 0.5);  /* RGB com transparência */
  border-color: #ff0000;                /* Hexadecimal */
  border-color: hsl(0, 100%, 50%);     /* HSL */
}
```

### Shorthand da Border

Você pode definir largura, estilo e cor em uma única linha:

```css
/* Sintaxe: border: [width] [style] [color]; */
.borda-completa {
  border: 2px solid #3498db;
}

/* Bordas individuais */
.bordas-diferentes {
  border-top: 3px solid red;
  border-right: 2px dashed green;
  border-bottom: 4px dotted blue;
  border-left: 1px solid yellow;
}

/* Borda arredondada */
.borda-arredondada {
  border: 2px solid #9b59b6;
  border-radius: 10px;
}

/* Arredondar cantos específicos */
.cantos-customizados {
  border: 2px solid #e67e22;
  border-top-left-radius: 20px;
  border-top-right-radius: 5px;
  border-bottom-right-radius: 20px;
  border-bottom-left-radius: 5px;
}
```

**Exemplo completo:**

```html
<style>
  .card-borda {
    width: 250px;
    padding: 20px;
    border: 3px solid #3498db;
    border-radius: 15px;
    background-color: white;
    box-shadow: 0 4px 6px rgba(0,0,0,0.1);
  }
</style>

<div class="card-borda">
  <h3>Card com Borda Estilizada</h3>
  <p>Borda sólida azul com cantos arredondados</p>
</div>
```

---

## 4. Propriedades de Espaçamento

### Margin

A margem é o espaço externo ao redor do elemento, criando distância entre elementos.

```css
/* Margem igual em todos os lados */
.margem-uniforme {
  margin: 20px;
}

/* Margem vertical e horizontal */
.margem-vh {
  margin: 20px 40px;  /* vertical horizontal */
}

/* Margem topo, horizontal, baixo */
.margem-3-valores {
  margin: 10px 20px 30px;  /* topo | esquerda/direita | baixo */
}

/* Margem em cada lado (sentido horário) */
.margem-4-valores {
  margin: 10px 20px 30px 40px;  /* topo direita baixo esquerda */
}
```

**Propriedades individuais:**

```css
.margem-individual {
  margin-top: 10px;
  margin-right: 20px;
  margin-bottom: 30px;
  margin-left: 40px;
}

/* Valores especiais */
.centralizar {
  width: 800px;
  margin: 0 auto;  /* Centraliza horizontalmente */
}

.margem-negativa {
  margin-top: -10px;  /* Sobrepõe elementos */
}

.sem-margem {
  margin: 0;
}
```

### Padding

O padding é o espaço interno entre o conteúdo e a borda do elemento.

```css
/* Padding igual em todos os lados */
.padding-uniforme {
  padding: 20px;
}

/* Padding vertical e horizontal */
.padding-vh {
  padding: 20px 40px;  /* vertical horizontal */
}

/* Padding topo, horizontal, baixo */
.padding-3-valores {
  padding: 10px 20px 30px;  /* topo | esquerda/direita | baixo */
}

/* Padding em cada lado (sentido horário) */
.padding-4-valores {
  padding: 10px 20px 30px 40px;  /* topo direita baixo esquerda */
}
```

**Propriedades individuais:**

```css
.padding-individual {
  padding-top: 10px;
  padding-right: 20px;
  padding-bottom: 30px;
  padding-left: 40px;
}
```

### Notação Individual e Shorthand

```css
/* FORMA LONGA (individual) */
.elemento-longo {
  margin-top: 10px;
  margin-right: 20px;
  margin-bottom: 10px;
  margin-left: 20px;
  
  padding-top: 15px;
  padding-right: 30px;
  padding-bottom: 15px;
  padding-left: 30px;
}

/* FORMA CURTA (shorthand) - EQUIVALENTE */
.elemento-curto {
  margin: 10px 20px;      /* vertical horizontal */
  padding: 15px 30px;     /* vertical horizontal */
}

/* Exemplos de shorthand */
.exemplo-1 {
  margin: 20px;           /* todos os lados = 20px */
}

.exemplo-2 {
  margin: 20px 40px;      /* vertical=20px, horizontal=40px */
}

.exemplo-3 {
  margin: 10px 20px 30px; /* topo=10px, horizontal=20px, baixo=30px */
}

.exemplo-4 {
  margin: 10px 20px 30px 40px; /* topo, direita, baixo, esquerda */
}
```

**Exemplo prático com margin e padding:**

```html
<style>
  .container-espacamento {
    width: 600px;
    margin: 40px auto;
    padding: 0;
    background-color: #ecf0f1;
  }
  
  .item-espacamento {
    margin: 20px;
    padding: 30px;
    background-color: white;
    border: 2px solid #3498db;
  }
</style>

<div class="container-espacamento">
  <div class="item-espacamento">
    Item com margin de 20px (espaço externo) e padding de 30px (espaço interno)
  </div>
  <div class="item-espacamento">
    Outro item com o mesmo espaçamento
  </div>
</div>
```

**Diferença entre Margin e Padding:**

```html
<style>
  .demo-margin {
    margin: 30px;
    padding: 10px;
    background-color: #e8f5e9;
    border: 2px solid #4caf50;
  }
  
  .demo-padding {
    margin: 10px;
    padding: 30px;
    background-color: #e3f2fd;
    border: 2px solid #2196f3;
  }
</style>

<div class="demo-margin">
  Margin alta (30px), padding baixo (10px)
  O espaço VERDE está fora da borda
</div>

<div class="demo-padding">
  Margin baixa (10px), padding alto (30px)
  O espaço AZUL está dentro da borda
</div>
```

---

## 5. Propriedades Display

A propriedade `display` controla como um elemento é exibido na página.

### Block

Elementos `block` ocupam toda a largura disponível e começam em uma nova linha.

```css
.elemento-block {
  display: block;
  width: 100%;  /* Ocupa toda a largura */
  margin: 10px 0;
}
```

**Características:**
- Ocupa toda a largura disponível por padrão
- Começa em uma nova linha
- Aceita propriedades de largura e altura
- Exemplos naturais: `<div>`, `<p>`, `<h1>-<h6>`, `<section>`, `<article>`

**Exemplo:**

```html
<style>
  .bloco {
    display: block;
    width: 300px;
    padding: 20px;
    margin: 10px 0;
    background-color: #3498db;
    color: white;
  }
</style>

<div class="bloco">Bloco 1 - Ocupa linha inteira</div>
<div class="bloco">Bloco 2 - Nova linha</div>
<div class="bloco">Bloco 3 - Mais uma linha</div>
```

### Inline

Elementos `inline` ocupam apenas o espaço necessário e ficam na mesma linha.

```css
.elemento-inline {
  display: inline;
  /* width e height NÃO funcionam */
  /* margin-top e margin-bottom NÃO funcionam */
  padding: 5px 10px;  /* Apenas horizontal tem efeito visual completo */
  margin: 0 5px;      /* Apenas horizontal funciona */
}
```

**Características:**
- Ocupa apenas o espaço necessário para o conteúdo
- Fica na mesma linha que outros elementos inline
- NÃO aceita width e height
- margin e padding verticais não afetam o layout
- Exemplos naturais: `<span>`, `<a>`, `<strong>`, `<em>`, `<img>`

**Exemplo:**

```html
<style>
  .texto-inline {
    display: inline;
    padding: 5px 10px;
    margin: 0 5px;
    background-color: #e74c3c;
    color: white;
  }
</style>

<p>
  Este é um parágrafo com 
  <span class="texto-inline">elemento inline</span> que fica 
  <span class="texto-inline">na mesma linha</span> do texto.
</p>
```

### Inline-block

Combina características de `block` e `inline`.

```css
.elemento-inline-block {
  display: inline-block;
  width: 150px;      /* Aceita width */
  height: 100px;     /* Aceita height */
  padding: 10px;     /* Funciona completamente */
  margin: 10px;      /* Funciona completamente */
  vertical-align: top;  /* Alinhamento vertical */
}
```

**Características:**
- Fica na mesma linha (como inline)
- Aceita width e height (como block)
- margin e padding funcionam em todas as direções
- Ideal para criar layouts de grade simples
- Usado para botões, cards lado a lado, galerias

**Exemplo comparativo:**

```html
<style>
  .container-display {
    background-color: #f8f9fa;
    padding: 20px;
    margin-bottom: 20px;
  }
  
  .box-block {
    display: block;
    width: 150px;
    height: 80px;
    padding: 10px;
    margin: 10px;
    background-color: #3498db;
    color: white;
  }
  
  .box-inline {
    display: inline;
    width: 150px;      /* NÃO funciona */
    height: 80px;      /* NÃO funciona */
    padding: 10px;
    margin: 10px 10px; /* Só horizontal */
    background-color: #e74c3c;
    color: white;
  }
  
  .box-inline-block {
    display: inline-block;
    width: 150px;
    height: 80px;
    padding: 10px;
    margin: 10px;
    background-color: #2ecc71;
    color: white;
  }
</style>

<div class="container-display">
  <h4>Display: Block</h4>
  <div class="box-block">Box 1</div>
  <div class="box-block">Box 2</div>
</div>

<div class="container-display">
  <h4>Display: Inline (width/height ignorados)</h4>
  <span class="box-inline">Box 1</span>
  <span class="box-inline">Box 2</span>
  <span class="box-inline">Box 3</span>
</div>

<div class="container-display">
  <h4>Display: Inline-Block (melhor dos dois)</h4>
  <div class="box-inline-block">Box 1</div>
  <div class="box-inline-block">Box 2</div>
  <div class="box-inline-block">Box 3</div>
</div>
```

**Tabela Comparativa:**

| Propriedade | Block | Inline | Inline-Block |
|-------------|-------|--------|--------------|
| Nova linha | Sim | Não | Não |
| Width/Height | Sim | Não | Sim |
| Margin vertical | Sim | Não | Sim |
| Padding vertical | Sim | Parcial* | Sim |
| Uso comum | Containers | Texto | Botões, Cards |

*Padding vertical em inline existe mas não afeta o layout dos elementos adjacentes.

---

## 6. Exemplo Prático: Criando Cards

Vamos criar um sistema de cards responsivo usando o Box Model:

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Cards com Box Model</title>
  <style>
    /* Reset básico */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    
    body {
      font-family: Arial, sans-serif;
      background-color: #f5f5f5;
      padding: 40px 20px;
    }
    
    .container {
      max-width: 1200px;
      margin: 0 auto;
    }
    
    .titulo-principal {
      text-align: center;
      margin-bottom: 40px;
      color: #2c3e50;
    }
    
    /* Container dos cards */
    .cards-container {
      display: block;
      margin: -10px; /* Compensa o margin dos cards */
    }
    
    /* Card individual */
    .card {
      display: inline-block;
      width: calc(33.333% - 20px);
      margin: 10px;
      padding: 0;
      background-color: white;
      border-radius: 8px;
      box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
      overflow: hidden;
      vertical-align: top;
      transition: transform 0.3s, box-shadow 0.3s;
    }
    
    .card:hover {
      transform: translateY(-5px);
      box-shadow: 0 4px 16px rgba(0, 0, 0, 0.2);
    }
    
    /* Imagem do card */
    .card-imagem {
      width: 100%;
      height: 200px;
      background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
      display: block;
      margin: 0;
      padding: 60px 20px;
      text-align: center;
      color: white;
      font-size: 24px;
      font-weight: bold;
    }
    
    /* Conteúdo do card */
    .card-conteudo {
      padding: 20px;
    }
    
    .card-titulo {
      margin: 0 0 15px 0;
      padding: 0;
      font-size: 22px;
      color: #2c3e50;
      border-bottom: 2px solid #3498db;
      padding-bottom: 10px;
    }
    
    .card-descricao {
      margin: 0 0 20px 0;
      padding: 0;
      line-height: 1.6;
      color: #7f8c8d;
    }
    
    .card-botao {
      display: inline-block;
      padding: 10px 20px;
      margin: 0;
      background-color: #3498db;
      color: white;
      text-decoration: none;
      border-radius: 4px;
      border: 2px solid #3498db;
      transition: all 0.3s;
    }
    
    .card-botao:hover {
      background-color: white;
      color: #3498db;
    }
    
    /* Tags/Labels */
    .card-tags {
      margin: 15px 0 0 0;
      padding: 15px 0 0 0;
      border-top: 1px solid #ecf0f1;
    }
    
    .tag {
      display: inline-block;
      padding: 5px 12px;
      margin: 0 5px 5px 0;
      background-color: #ecf0f1;
      color: #7f8c8d;
      border-radius: 20px;
      font-size: 12px;
    }
    
    /* Variações de cores */
    .card.azul .card-imagem {
      background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    }
    
    .card.verde .card-imagem {
      background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
    }
    
    .card.laranja .card-imagem {
      background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);
    }
    
    /* Responsividade */
    @media (max-width: 768px) {
      .card {
        width: calc(50% - 20px);
      }
    }
    
    @media (max-width: 480px) {
      .card {
        width: calc(100% - 20px);
      }
    }
  </style>
</head>
<body>
  <div class="container">
    <h1 class="titulo-principal">Galeria de Cards com Box Model</h1>
    
    <div class="cards-container">
      <!-- Card 1 -->
      <div class="card azul">
        <div class="card-imagem">
          Card 1
        </div>
        <div class="card-conteudo">
          <h2 class="card-titulo">Box Model Básico</h2>
          <p class="card-descricao">
            Aprenda os fundamentos do Box Model: content, padding, border e margin.
            Essencial para qualquer desenvolvedor web.
          </p>
          <a href="#" class="card-botao">Saiba Mais</a>
          <div class="card-tags">
            <span class="tag">CSS</span>
            <span class="tag">Básico</span>
            <span class="tag">Layout</span>
          </div>
        </div>
      </div>
      
      <!-- Card 2 -->
      <div class="card verde">
        <div class="card-imagem">
          Card 2
        </div>
        <div class="card-conteudo">
          <h2 class="card-titulo">Propriedades Display</h2>
          <p class="card-descricao">
            Entenda as diferenças entre block, inline e inline-block.
            Controle como seus elementos são exibidos.
          </p>
          <a href="#" class="card-botao">Saiba Mais</a>
          <div class="card-tags">
            <span class="tag">Display</span>
            <span class="tag">Intermediário</span>
          </div>
        </div>
      </div>
      
      <!-- Card 3 -->
      <div class="card laranja">
        <div class="card-imagem">
          Card 3
        </div>
        <div class="card-conteudo">
          <h2 class="card-titulo">Box-sizing</h2>
          <p class="card-descricao">
            Descubra como box-sizing: border-box simplifica cálculos de layout
            e torna seu CSS mais previsível.
          </p>
          <a href="#" class="card-botao">Saiba Mais</a>
          <div class="card-tags">
            <span class="tag">Box-sizing</span>
            <span class="tag">Dica</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</body>
</html>
```

**Pontos importantes do exemplo:**

1. **Reset com box-sizing**: `box-sizing: border-box` facilita o cálculo das dimensões
2. **Cards inline-block**: Permite criar grid sem flexbox/grid
3. **Padding estruturado**: Espaçamento interno consistente
4. **Margin para espaçamento**: Distância entre cards
5. **Border-radius**: Bordas arredondadas modernas
6. **Box-shadow**: Profundidade e hierarquia visual
7. **Hover effects**: Feedback visual interativo

---

## 7. Exemplo Prático: Layout com Box Model

Vamos criar um layout completo de página usando apenas Box Model:

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Layout com Box Model</title>
  <style>
    /* Reset e configurações globais */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      line-height: 1.6;
      color: #333;
    }
    
    /* Header */
    .header {
      background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
      color: white;
      padding: 20px 0;
      border-bottom: 5px solid #5568d3;
    }
    
    .header-container {
      max-width: 1200px;
      margin: 0 auto;
      padding: 0 20px;
    }
    
    .logo {
      display: inline-block;
      font-size: 28px;
      font-weight: bold;
      margin: 0;
      padding: 10px 0;
    }
    
    .nav {
      display: inline-block;
      float: right;
      margin: 0;
      padding: 10px 0;
    }
    
    .nav a {
      display: inline-block;
      color: white;
      text-decoration: none;
      padding: 10px 20px;
      margin: 0 5px;
      border-radius: 4px;
      transition: background-color 0.3s;
    }
    
    .nav a:hover {
      background-color: rgba(255, 255, 255, 0.2);
    }
    
    /* Hero Section */
    .hero {
      background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
      color: white;
      padding: 80px 20px;
      text-align: center;
      border-bottom: 5px solid #e04458;
    }
    
    .hero h1 {
      margin: 0 0 20px 0;
      font-size: 48px;
    }
    
    .hero p {
      margin: 0 0 30px 0;
      font-size: 20px;
      max-width: 600px;
      margin-left: auto;
      margin-right: auto;
    }
    
    .btn {
      display: inline-block;
      padding: 15px 40px;
      background-color: white;
      color: #f5576c;
      text-decoration: none;
      border-radius: 30px;
      font-weight: bold;
      border: 3px solid white;
      transition: all 0.3s;
    }
    
    .btn:hover {
      background-color: transparent;
      color: white;
    }
    
    /* Main Content */
    .main-container {
      max-width: 1200px;
      margin: 0 auto;
      padding: 60px 20px;
    }
    
    /* Seção de recursos */
    .recursos {
      margin-bottom: 60px;
    }
    
    .secao-titulo {
      text-align: center;
      margin: 0 0 40px 0;
      padding: 0 0 20px 0;
      font-size: 36px;
      color: #2c3e50;
      border-bottom: 3px solid #3498db;
    }
    
    .recursos-grid {
      margin: -15px;
    }
    
    .recurso-item {
      display: inline-block;
      width: calc(25% - 30px);
      margin: 15px;
      padding: 30px 20px;
      background-color: #f8f9fa;
      border: 2px solid #e9ecef;
      border-radius: 8px;
      text-align: center;
      vertical-align: top;
      transition: all 0.3s;
    }
    
    .recurso-item:hover {
      border-color: #3498db;
      transform: translateY(-5px);
      box-shadow: 0 5px 15px rgba(0,0,0,0.1);
    }
    
    .recurso-icone {
      display: block;
      width: 80px;
      height: 80px;
      margin: 0 auto 20px auto;
      background-color: #3498db;
      border-radius: 50%;
      line-height: 80px;
      font-size: 36px;
      color: white;
    }
    
    .recurso-item h3 {
      margin: 0 0 15px 0;
      color: #2c3e50;
    }
    
    .recurso-item p {
      margin: 0;
      color: #7f8c8d;
      line-height: 1.6;
    }
    
    /* Seção de conteúdo com sidebar */
    .content-section {
      margin-bottom: 60px;
    }
    
    .content-main {
      display: inline-block;
      width: calc(66.666% - 20px);
      margin-right: 20px;
      padding: 30px;
      background-color: white;
      border: 1px solid #dee2e6;
      border-radius: 8px;
      vertical-align: top;
    }
    
    .content-main h2 {
      margin: 0 0 20px 0;
      padding: 0 0 15px 0;
      border-bottom: 2px solid #3498db;
      color: #2c3e50;
    }
    
    .content-main p {
      margin: 0 0 15px 0;
      text-align: justify;
    }
    
    .sidebar {
      display: inline-block;
      width: calc(33.333% - 20px);
      padding: 0;
      vertical-align: top;
    }
    
    .sidebar-widget {
      margin-bottom: 20px;
      padding: 20px;
      background-color: #f8f9fa;
      border: 1px solid #dee2e6;
      border-radius: 8px;
    }
    
    .sidebar-widget h3 {
      margin: 0 0 15px 0;
      padding: 0 0 10px 0;
      border-bottom: 2px solid #6c757d;
      color: #2c3e50;
    }
    
    .sidebar-widget ul {
      list-style: none;
      margin: 0;
      padding: 0;
    }
    
    .sidebar-widget li {
      padding: 10px 0;
      border-bottom: 1px solid #dee2e6;
    }
    
    .sidebar-widget li:last-child {
      border-bottom: none;
    }
    
    .sidebar-widget a {
      color: #3498db;
      text-decoration: none;
      transition: color 0.3s;
    }
    
    .sidebar-widget a:hover {
      color: #2980b9;
    }
    
    /* Footer */
    .footer {
      background-color: #2c3e50;
      color: white;
      padding: 40px 0;
      border-top: 5px solid #34495e;
    }
    
    .footer-container {
      max-width: 1200px;
      margin: 0 auto;
      padding: 0 20px;
    }
    
    .footer-coluna {
      display: inline-block;
      width: calc(33.333% - 20px);
      margin: 0 10px;
      padding: 0;
      vertical-align: top;
    }
    
    .footer h4 {
      margin: 0 0 20px 0;
      padding: 0 0 10px 0;
      border-bottom: 2px solid #3498db;
    }
    
    .footer p {
      margin: 0 0 15px 0;
      line-height: 1.6;
    }
    
    .footer ul {
      list-style: none;
      margin: 0;
      padding: 0;
    }
    
    .footer li {
      margin: 0 0 10px 0;
    }
    
    .footer a {
      color: #ecf0f1;
      text-decoration: none;
      transition: color 0.3s;
    }
    
    .footer a:hover {
      color: #3498db;
    }
    
    .copyright {
      text-align: center;
      margin-top: 30px;
      padding-top: 30px;
      border-top: 1px solid #34495e;
      color: #95a5a6;
    }
    
    /* Responsividade */
    @media (max-width: 992px) {
      .recurso-item {
        width: calc(50% - 30px);
      }
      
      .content-main,
      .sidebar {
        width: 100%;
        margin-right: 0;
        margin-bottom: 20px;
      }
      
      .footer-coluna {
        width: 100%;
        margin: 0 0 30px 0;
      }
    }
    
    @media (max-width: 768px) {
      .nav {
        float: none;
        display: block;
        text-align: center;
        margin-top: 20px;
      }
      
      .hero h1 {
        font-size: 32px;
      }
      
      .recurso-item {
        width: calc(100% - 30px);
      }
    }
  </style>
</head>
<body>
  <!-- Header -->
  <header class="header">
    <div class="header-container">
      <div class="logo">MeuSite</div>
      <nav class="nav">
        <a href="#">Início</a>
        <a href="#">Sobre</a>
        <a href="#">Serviços</a>
        <a href="#">Contato</a>
      </nav>
    </div>
  </header>
  
  <!-- Hero Section -->
  <section class="hero">
    <h1>Aprenda CSS Box Model</h1>
    <p>
      Domine os conceitos fundamentais de layout web com nosso guia completo
      sobre Box Model, margins, padding e borders.
    </p>
    <a href="#" class="btn">Começar Agora</a>
  </section>
  
  <!-- Main Content -->
  <main class="main-container">
    <!-- Seção de Recursos -->
    <section class="recursos">
      <h2 class="secao-titulo">Principais Conceitos</h2>
      <div class="recursos-grid">
        <div class="recurso-item">
          <div class="recurso-icone">📦</div>
          <h3>Content</h3>
          <p>A área principal onde seu conteúdo é exibido</p>
        </div>
        <div class="recurso-item">
          <div class="recurso-icone">🎨</div>
          <h3>Padding</h3>
          <p>Espaço interno entre conteúdo e borda</p>
        </div>
        <div class="recurso-item">
          <div class="recurso-icone">🖼️</div>
          <h3>Border</h3>
          <p>Moldura ao redor do elemento</p>
        </div>
        <div class="recurso-item">
          <div class="recurso-icone">↔️</div>
          <h3>Margin</h3>
          <p>Espaço externo entre elementos</p>
        </div>
      </div>
    </section>
    
    <!-- Conteúdo com Sidebar -->
    <section class="content-section">
      <div class="content-main">
        <h2>Entendendo o Box Model</h2>
        <p>
          O Box Model é um dos conceitos mais importantes no CSS. Cada elemento HTML
          é tratado como uma caixa retangular, composta por quatro áreas distintas:
          content, padding, border e margin.
        </p>
        <p>
          Compreender como essas áreas funcionam é essencial para criar layouts
          precisos e responsivos. O content contém seu texto e imagens, o padding
          adiciona espaço interno, a border cria uma moldura visual, e a margin
          estabelece distância entre elementos.
        </p>
        <p>
          Com a propriedade box-sizing: border-box, você pode simplificar
          significativamente seus cálculos de layout, fazendo com que width e height
          incluam padding e border automaticamente.
        </p>
        <p>
          Este conhecimento é fundamental para qualquer desenvolvedor web e serve
          como base para técnicas mais avançadas de layout como Flexbox e Grid.
        </p>
      </div>
      
      <aside class="sidebar">
        <div class="sidebar-widget">
          <h3>Links Úteis</h3>
          <ul>
            <li><a href="#">Documentação MDN</a></li>
            <li><a href="#">CSS Tricks</a></li>
            <li><a href="#">W3Schools</a></li>
            <li><a href="#">Can I Use</a></li>
          </ul>
        </div>
        
        <div class="sidebar-widget">
          <h3>Recursos</h3>
          <ul>
            <li><a href="#">Cheat Sheet</a></li>
            <li><a href="#">Exemplos</a></li>
            <li><a href="#">Exercícios</a></li>
            <li><a href="#">Quiz</a></li>
          </ul>
        </div>
        
        <div class="sidebar-widget">
          <h3>Sobre</h3>
          <p>
            Este tutorial foi criado para ajudar iniciantes a dominar
            o CSS Box Model de forma prática e objetiva.
          </p>
        </div>
      </aside>
    </section>
  </main>
  
  <!-- Footer -->
  <footer class="footer">
    <div class="footer-container">
      <div class="footer-coluna">
        <h4>Sobre Nós</h4>
        <p>
          Somos apaixonados por ensinar desenvolvimento web e ajudar
          pessoas a realizarem seus sonhos na tecnologia.
        </p>
      </div>
      
      <div class="footer-coluna">
        <h4>Links Rápidos</h4>
        <ul>
          <li><a href="#">Início</a></li>
          <li><a href="#">Tutoriais</a></li>
          <li><a href="#">Blog</a></li>
          <li><a href="#">Contato</a></li>
        </ul>
      </div>
      
      <div class="footer-coluna">
        <h4>Contato</h4>
        <ul>
          <li>Email: contato@exemplo.com</li>
          <li>Tel: (11) 1234-5678</li>
          <li>São Paulo, Brasil</li>
        </ul>
      </div>
      
      <div class="copyright">
        © 2024 Tutorial CSS. Todos os direitos reservados.
      </div>
    </div>
  </footer>
</body>
</html>
```

**Elementos chave deste layout:**

1. **Header fixo**: Com logo e navegação usando inline-block
2. **Hero section**: Banner principal com gradiente e CTA
3. **Grid de recursos**: 4 itens usando inline-block e calc()
4. **Layout duas colunas**: Conteúdo principal (66%) + Sidebar (33%)
5. **Footer em colunas**: Informações organizadas em 3 colunas
6. **Box-sizing global**: Facilita todos os cálculos
7. **Responsividade**: Media queries para diferentes tamanhos de tela
8. **Transições**: Efeitos suaves em hovers
9. **Hierarquia visual**: Usando margins, paddings e borders estrategicamente

---

## 8. Dicas e Boas Práticas

### 1. Use box-sizing: border-box

```css
/* Aplicar em todos os elementos */
*, *::before, *::after {
  box-sizing: border-box;
}
```

**Por quê?** Torna o cálculo de dimensões muito mais intuitivo.

### 2. Reset de Margins e Paddings

```css
* {
  margin: 0;
  padding: 0;
}
```

**Por quê?** Diferentes navegadores têm estilos padrão diferentes.

### 3. Centralize Containers

```css
.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}
```

**Por quê?** Cria um layout responsivo e centrado.

### 4. Use Margin para Espaçamento Externo

```css
/* BOM */
.elemento {
  margin-bottom: 20px;
}

/* EVITE padding no pai apenas para espaçar filhos */
```

### 5. Use Padding para Espaçamento Interno

```css
/* BOM */
.card {
  padding: 20px;
}

/* Cria respiração entre conteúdo e bordas */
```

### 6. Margens Negativas com Cuidado

```css
.elemento {
  margin-top: -20px;  /* Sobrepõe elementos acima */
}
```

**Cuidado!** Pode quebrar o layout se usado incorretamente.

### 7. Colapso de Margens

```css
/* Margens verticais adjacentes se sobrepõem */
.elemento1 {
  margin-bottom: 30px;
}

.elemento2 {
  margin-top: 20px;
}

/* Espaço total = 30px (não 50px!) */
```

**Solução:** Use apenas margin-bottom OU margin-top, não ambos.

### 8. Evite Larguras Fixas Quando Possível

```css
/* BOM - Responsivo */
.elemento {
  width: 100%;
  max-width: 800px;
}

/* EVITE - Rígido */
.elemento {
  width: 800px;
}
```

### 9. Shorthand Inteligente

```css
/* Quando todos os lados são iguais */
.elemento {
  margin: 20px;  /* Mais limpo que especificar 4 vezes */
}

/* Quando vertical e horizontal são diferentes */
.elemento {
  padding: 20px 40px;  /* vertical horizontal */
}
```

### 10. Unidades Relativas para Espaçamento

```css
.elemento {
  padding: 1.5rem;   /* Relativo ao tamanho da fonte */
  margin: 2em 0;     /* Relativo ao tamanho da fonte do elemento */
}
```

### 11. Debug com Bordas Temporárias

```css
/* Durante desenvolvimento */
* {
  border: 1px solid red;
}

/* Ajuda a visualizar o box model de cada elemento */
```

### 12. Organize seu CSS

```css
/* Ordem lógica das propriedades */
.elemento {
  /* Display e Box Model */
  display: block;
  width: 300px;
  height: 200px;
  padding: 20px;
  border: 1px solid black;
  margin: 10px;
  
  /* Visual */
  background-color: white;
  color: black;
  
  /* Texto */
  font-size: 16px;
  line-height: 1.6;
  
  /* Outros */
  transition: all 0.3s;
}
```

### 13. Teste em Diferentes Navegadores

- Chrome DevTools: F12 → Computed → Visualização do Box Model
- Firefox Developer Tools: Similar ao Chrome
- Safari Web Inspector: Também mostra o Box Model

### 14. Use DevTools para Experimentar

1. Abra o inspetor (F12)
2. Selecione um elemento
3. Na aba "Computed", veja o box model visual
4. Edite valores em tempo real

### 15. Comentários Úteis

```css
/* === SECTION: Cards === */
.card {
  /* O padding interno garante respiro ao conteúdo */
  padding: 20px;
  
  /* Margin inferior cria espaçamento entre cards */
  margin-bottom: 20px;
}
```

---

## Conclusão

O Box Model é a fundação do layout CSS. Dominar seus conceitos permite criar interfaces profissionais e responsivas. Lembre-se:

- **Content**: Onde seu conteúdo vive
- **Padding**: Respiro interno
- **Border**: Definição visual
- **Margin**: Espaçamento externo
- **Box-sizing**: Seu melhor amigo para cálculos
- **Display**: Controla o comportamento do elemento

Continue praticando, experimente diferentes combinações e use as ferramentas de desenvolvedor do navegador para entender melhor como cada propriedade afeta seus elementos!

---

## Recursos Adicionais

- [MDN Web Docs - Box Model](https://developer.mozilla.org/pt-BR/docs/Learn/CSS/Building_blocks/The_box_model)
- [CSS Tricks - Box Sizing](https://css-tricks.com/box-sizing/)
- [W3Schools - CSS Box Model](https://www.w3schools.com/css/css_boxmodel.asp)

**Licença**: Este tutorial está sob a licença GNU GPL v3.
