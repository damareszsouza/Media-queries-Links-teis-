# Media-queries-Links-teis-
Praticas FrontEnd Curso Desenvolvimento Web


Media queries (Links úteis)
Tipos de mídias:

all – todos os dispositivos

aural – sintetizadores de voz

braille – leitores de Braille

embossed – impressoras de Braille

handheld – dispositivos de mão. Por exemplo: celulares com telas pequenas.

print – impressoras convencionais

projection – apresentações de slides

screen – monitores coloridas

tty – teleimpressores e terminais

tv – televisores

Exemplo de utilização:

<link rel="stylesheet" media="print" href="print.css" /> 

Exemplos de resoluções de telas:

￼320 pixels – Smartphones no modo retrato.

480 pixels – Smartphones no modo paisagem.

600 pixels – Tablets pequenos. Ex: Amazon Kindle (600×800)

￼768 pixels – Tablets maiores em modo retrato. Ex: iPad (768×1024)

1024 pixels – Tablets maiores em modo paisagem, monitores antigos.

￼1200 pixels – Monitores wide.

Links de media queries no Bootstrap:

https://getbootstrap.com/docs/4.1/layout/overview/

Exemplos de utilização media queries:

@media (min-width: 576px) { ... }


Visão geral
Componentes e opções para o layout do seu projeto Bootstrap, incluindo empacotamento de contêineres, um poderoso sistema de grade, um objeto de mídia flexível e classes de utilitário responsivas.

Containers
Os contêineres são o elemento de layout mais básico no Bootstrap e são necessários ao usar nosso sistema de grade padrão . Escolha entre um contêiner responsivo de largura fixa (o que significa que max-widthmuda a cada ponto de interrupção) ou largura fluida (o que significa que é 100%largo o tempo todo).

Embora os contêineres possam ser aninhados, a maioria dos layouts não requer um contêiner aninhado.

cópia de
<div class="container">
  <!-- Content here -->
</div>
Use .container-fluidpara um contêiner de largura total, abrangendo toda a largura da viewport.

cópia de
<div class="container-fluid">
  ...
</div>
Pontos de interrupção responsivos
Como o Bootstrap foi desenvolvido para ser móvel primeiro, usamos um punhado de consultas de mídia para criar pontos de interrupção sensatos para nossos layouts e interfaces. Esses pontos de interrupção são baseados principalmente nas larguras mínimas da viewport e nos permitem aumentar a escala dos elementos à medida que a viewport muda.

O Bootstrap usa principalmente os seguintes intervalos de consulta de mídia - ou pontos de interrupção - em nossos arquivos Sass de origem para nosso layout, sistema de grade e componentes.

cópia de
// Extra small devices (portrait phones, less than 576px)
// No media query since this is the default in Bootstrap

// Small devices (landscape phones, 576px and up)
@media (min-width: 576px) { ... }

// Medium devices (tablets, 768px and up)
@media (min-width: 768px) { ... }

// Large devices (desktops, 992px and up)
@media (min-width: 992px) { ... }

// Extra large devices (large desktops, 1200px and up)
@media (min-width: 1200px) { ... }
Como escrevemos nosso CSS de origem em Sass, todas as nossas consultas de mídia estão disponíveis via mixins Sass:

cópia de
@include media-breakpoint-up(xs) { ... }
@include media-breakpoint-up(sm) { ... }
@include media-breakpoint-up(md) { ... }
@include media-breakpoint-up(lg) { ... }
@include media-breakpoint-up(xl) { ... }

// Example usage:
@include media-breakpoint-up(sm) {
  .some-class {
    display: block;
  }
}
Ocasionalmente, usamos consultas de mídia que vão na outra direção (o tamanho da tela fornecido ou menor ):

cópia de
// Extra small devices (portrait phones, less than 576px)
@media (max-width: 575.98px) { ... }

// Small devices (landscape phones, less than 768px)
@media (max-width: 767.98px) { ... }

// Medium devices (tablets, less than 992px)
@media (max-width: 991.98px) { ... }

// Large devices (desktops, less than 1200px)
@media (max-width: 1199.98px) { ... }

// Extra large devices (large desktops)
// No media query since the extra-large breakpoint has no upper bound on its width
Observe que, como os navegadores atualmente não oferecem suporte a consultas de contexto de intervalo , contornamos as limitações de min-prefixos max-e viewports com larguras fracionárias (o que pode ocorrer sob certas condições em dispositivos de alta dpi, por exemplo) usando valores com maior precisão para essas comparações .

Mais uma vez, essas consultas de mídia também estão disponíveis via mixins Sass:

cópia de
@include media-breakpoint-down(xs) { ... }
@include media-breakpoint-down(sm) { ... }
@include media-breakpoint-down(md) { ... }
@include media-breakpoint-down(lg) { ... }
Há também consultas de mídia e mixins para segmentar um único segmento de tamanhos de tela usando as larguras mínima e máxima do ponto de interrupção.

cópia de
// Extra small devices (portrait phones, less than 576px)
@media (max-width: 575.98px) { ... }

// Small devices (landscape phones, 576px and up)
@media (min-width: 576px) and (max-width: 767.98px) { ... }

// Medium devices (tablets, 768px and up)
@media (min-width: 768px) and (max-width: 991.98px) { ... }

// Large devices (desktops, 992px and up)
@media (min-width: 992px) and (max-width: 1199.98px) { ... }

// Extra large devices (large desktops, 1200px and up)
@media (min-width: 1200px) { ... }
Essas consultas de mídia também estão disponíveis via mixins Sass:

cópia de
@include media-breakpoint-only(xs) { ... }
@include media-breakpoint-only(sm) { ... }
@include media-breakpoint-only(md) { ... }
@include media-breakpoint-only(lg) { ... }
@include media-breakpoint-only(xl) { ... }
Da mesma forma, as consultas de mídia podem abranger várias larguras de ponto de interrupção:

cópia de
// Example
// Apply styles starting from medium devices and up to extra large devices
@media (min-width: 768px) and (max-width: 1199.98px) { ... }
O mixin do Sass para segmentar o mesmo intervalo de tamanho de tela seria:

cópia de
@include media-breakpoint-between(md, xl) { ... }
índice Z
Vários componentes do Bootstrap utilizam z-index, a propriedade CSS que ajuda a controlar o layout fornecendo um terceiro eixo para organizar o conteúdo. Utilizamos uma escala de índice z padrão no Bootstrap que foi projetada para navegar adequadamente em camadas, dicas de ferramentas e popovers, modais e muito mais.

Esses valores mais altos começam em um número arbitrário, alto e específico o suficiente para evitar conflitos. Precisamos de um conjunto padrão deles em nossos componentes em camadas - dicas de ferramentas, popovers, navbars, menus suspensos, modais - para que possamos ser razoavelmente consistentes nos comportamentos. Não há razão para não termos usado 100+ ou 500+.

Não encorajamos a personalização desses valores individuais; se você alterar um, provavelmente precisará alterar todos eles.

cópia de
$zindex-dropdown:          1000 !default;
$zindex-sticky:            1020 !default;
$zindex-fixed:             1030 !default;
$zindex-modal-backdrop:    1040 !default;
$zindex-modal:             1050 !default;
$zindex-popover:           1060 !default;
$zindex-tooltip:           1070 !default;
Para lidar com bordas sobrepostas em componentes (por exemplo, botões e entradas em grupos de entrada), usamos z-indexvalores baixos de um dígito de 1, 2e 3para os estados padrão, hover e ativo. Ao passar o mouse/focar/ativo, trazemos um elemento específico para o primeiro plano com um z-indexvalor mais alto para mostrar sua borda sobre os elementos irmãos.
