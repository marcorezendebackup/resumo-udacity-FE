# Introdução ao foco
Nesta sessão, faleremos sobre foco e como gerencia-lo. Foco se refere ao controle da tela do computador que recebe entrada do teclado e do arquivo colado (clipboard). Conhecemos bem o foco das caixas de texto. Para escrever nelas, clicamos com o mouse. A ação de clicar  na caixa de texto é o foco. Ao pressionar Tab, o foco passa para a proxima caixa de texto ou controle disponivel.

Alguns usuarios manipulam o computador só com o teclado ou com algum outro tipo de aparelho de entrada. Para eles, o foco é muito importante, é a forma primaria de acessar coisas na tela. Por isso, o checklist WebAIM diz na [seção 2.1.1](https://webaim.org/standards/wcag/checklist#sc2.1.1) que a funcionalidade da pagina deve estar disponivel no teclado, a não ser para algo que não dê para realizar nele, como um desenho à mão livre ou algo do tipo. Essa funcionalidade atende tanto para pessoas com deficiencia motora quanto para usuarios que preferem usar somente o teclado.

# O que é foco?
Quando um elemento está focado, ele geralmente é indicado por um anel de foco. O estilo do anel depende do navegador e do estilo aplicado pelo autor da pagina. O usuario controla qual elemento focar usando o teclado. Pressionando Tab o foco segue adiante, pressionando Shift + Tab o foco retorna.

Usando Tab em paginas que se adquam ao foco, como Wikipedia vemos, que o foco segue uma ordem. Esta ordem é chamada ordem Tab. Garantir que o aplicativo tenha uma ordem logica é um passo importante.

Elementos HTML interativos como os de entrada, os de botões e os de selecioanar são implicitamente focaveis. Eles são inseridos automaticamente na ordem Tab e possuem manipuladores de evento no teclado.

# A ordem no DOM é importante
Trabalhar com elementos nativos é otimo para o comportamento de foco, pois eles são inseridos automaticamente na ordem Tab a partir da posição deles no DOM. Por exemplo:

HTML:

```
<button>Eu devo</button>
<button>ser focado</button>
<button>por ultimo</button>

```

OUTPUT:

```
{Eu devo} {ser focado} {por ultimo}

```

Como a ordem Tab corresponde à ordem da DOM, ao pressionar a tecla Tab, o primeiro botão ({Eu devo}) de foco recebe a indicação em volta. É importante notar que a utilização do CSS pode fazer as coisas aparecerem em um ordem na tela, mas existirem em outra ordem no DOM. Por exemplo:

HTML:

```
<button style="float: right;">Eu devo</button>
<button>ser focado</button>
<button>por ultimo</button>

```

OUTPUT:

```
{por ultimo} {ser focado} {Eu devo}

```

Isso mudará a ordem visual dos botões, mas a ordem continua a mesma, ou seja, pressionando Tab, a ordem de foco será a mesma do exemplo anterior. Por isso, tenha cuidado ao utilizar CSS para alterar o posicionamento dos elementos na tela. O checklist WebAIM diz na [seção 1.3.2](https://webaim.org/standards/wcag/checklist#sc1.3.2) que leitura e ordem de navegação determinadas na ordem do codigo devem ser logicas e intuitivas no aplicativo.

# Utilizando Tabindex
Elementos nativos são automaticamente inseridos na ordem Tab e são muito convenientes. Mas há situações nas quais devemos alterar a ordem Tab para componentes sem um analog nativo, como menu dropdown nativo, ou para algo fora da tela que só estará em foco quando ele aparecer, como, por exemplo, uma janela de modal.

Para estes casos, usaremos o atributo tabindex. Ele pode ser aplicado a qualquer elemento HTML e usa uma gama de valores numericos. Um tabindex de '-1' significa que o elemento não estará na ordem Tab, mas pode ser focado programaticamente via JavaScript com o método `focus()` do elemento. Isso pode ser util para conteudo oculto que aparece na tela em resposta a um evento. Quando este conteudo é exibido, podemos chamar o metodo focus que direcionará futuros eventos do teclado a ele. Exemplo:

```
document.querySelector('#modal').focus()

```

Um tabindex igual a zero adicionará o elemento à ordem Tab natural, e o elemento será focado ao chamar o método focus. Por ebody {
    background-color: #F0F0F0;
    font-size: 0.9em;
    padding-bottom: 70px;
}

#footer {
    background-color: #D1D1D1;
    bottom: 0;
    height: 40px;
    left: 0;
    overflow: hidden;
    padding-left: 5px;
    position: fixed;
    right: 0;
}

.button {
    cursor: pointer;
}

.box {
    background-color: #FFFFFF;
    border-color: #D1D1D1;
    border-style: solid;
    border-width: 1px;
    margin-left: auto;
    margin-right: auto;
    margin-top: 35px;
    width: 60%;
}

.popup {
    display: none;
    height: 21%;
    left: 35%;
    position: fixed;
    top: 35%;
    width: 30%;
}

.logo {
    float: left;
    left: 5px;
    position: relative;
    top: 5px;
    z-index: 10;
}

.title {
    background-image: url('/css/custom-theme1/images/ui-bg_dots-small_40_ebebeb_2x2.png');
    background-repeat: repeat;
    border-bottom-color: #CFCFCF;
    border-bottom-style: solid;
    border-bottom-width: 1px;
    color: #000;
    font-size: 110%;
    padding: 5px 0 5px 30px;
}

.content {
    margin: 15px 0 0 10px;
}

.formLine {
    height: 35px;
    margin: -5px 0 5px 0;
    overflow: hidden;
    white-space: nowrap;
    width: 99%;
}

.input {
    max-width: 10%!important;
    width: 10%;
}

.formLabel {
    padding-top: -10px;
    text-align: right;
    width: 80%;
}

.inputLabel {
    float: left;
    font-weight: bold;
    margin-top: 5px;
    padding: 0 1em;
    text-align: right;
    width: 15%;
}

.rule {
    color: red;
    font-weight: bold;
}

.deleteButton {
    cursor: pointer;
    position: relative;
    user-select: none;
}

tr>td:first-child {
    width: 20%;
}

#addRule {
    float: right;
    margin-right: 0;
    margin-top: 0;
}

#addRule span {
    vertical-align: text-top;
}

#submitDiv {
    float: right;
    margin-right: 5px;
    margin-top: 5px;
}

#submitButton {
    height: 30px;
    margin-bottom: 5px;
    margin-top: 5px;
    padding-bottom: 5px;
    padding-top: 5px;
    right: 0;
    user-select: none;
}

.helper {
    border-bottom: 1px dotted #9e9e9e;
    color: #9e9e9e;
    cursor: help;
}

.help_subject {
    font-size: 90%;
    color: #ff0033;
}

A:link {
    color: #000;
    text-decoration: none;
}

A:visited {
    color: #000;
    text-decoration: none;
}

A:active {
    color: #000;
    text-decoration: none;
}                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   body {
    margin: 0;
    padding: 0;
    background-color: #FFF;
    font-size: 0.9em;
    font-family: 'Open Sans', sans-serif;
    font-size: 75%;
    cursor: default;
    user-select: none;
}

h1 {
    color: rgb(92, 97, 102);
    font-size: 150%;
    font-weight: normal;
    line-height: 1;
}

#navigation {
    position: fixed;
    left: 0;
    width: 160px;
    height: 100%;
    padding-top: 15px;
    background-color: #FFF;
    background-color: #F7F7F7;
    border-right-width: 1px;
    border-right-style: solid;
    border-right-color: #E3E3E3;
    z-index: 1;
}

#navigation>h1 {
    margin-left: 5px;
}

#navigation>ul {
    list-style-type: none;
    margin: 0;
    padding: 0;
}

#navigation li {
    -webkit-border-start: 6px solid transparent;
    -webkit-padding-start: 18px;
    user-select: none;
    color: #999;
    cursor: pointer;
    line-height: 17px;
    margin: 5px 0;
}

#navigation li:hover {
    color: #777;
}

#navigation li.selected {
    -webkit-border-start-color: rgb(78, 87, 100);
    color: rgb(70, 78, 90);
    font-weight: bold;
}

#maincontent {
    position: fixed;
    width: 100%;
    height: 100%;
    margin: 0;
    padding: 0;
    background-color: #F7F7F7;
    border: none;
}

.box {
    margin-left: 180px;
    padding-top: 15px;
    padding-right: 15px;
}

.box h1 {
    color: #000;
    margin-top: 10px;
    margin-left: -10px;
    font-size: 200%;
}

.section-title {
    margin-top: 0px;
    margin-left: -10px;
    margin-bottom: 10px;
    font-size: 110%;
    font-weight: bold;
}

.section-title:first-of-type {
    margin-top: 10px;
}

.button {
    cursor: pointer;
}

.formLine {
    height: 30px;
}

.checker>span {
    margin-top: -2px !important;
}

A:link, A:visited, A:active, .link_like {
    color: #4183C4;
    cursor: pointer;
    text-decoration: none;
    font-weight: bold;
}

.linkify {
    cursor: pointer;
}

.linkify:hover {
    color: #4D4D4D;
}

.helper {
    border-bottom: 1px dotted #9e9e9e !important;
    color: #9e9e9e !important;
    cursor: pointer !important;
    text-decoration: none !important;
}

hr {
    margin: 10px 0 10px -15px;
    border-top-color: #E3E3E3;
    border-top-style: solid;
    border-width: 1px 0 0 0;
}

.template {
    display: none !important;
}

.table {
    padding-left: 0px;
    width: 100%;
    display: table;
    border-collapse: separate;
    border-spacing: 0px;
}

.table_row {
    width: 100%;
    display: table-row;
    vertical-align: middle
}

.header div {
    padding-left: 0px !important;
    font-weight: bold;
}

.table_row div {
    height: 30px;
    padding-right: 10px;
    display: table-cell;
    text-align: left;
    vertical-align: middle;
}

.fa {
    font-size: 1.2em;
    line-height: 20px;
}                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          #tabs {
    overflow: hidden;
    width: 100%;
    margin: 0;
    padding: 0;
    list-style: none;
}

#tabs ul {
    background-color: transparent !important;
    background-image: none !important;
}

#tabs li {
    float: left;
    margin: 0 -15px 0 0;
}

#tabs a {
    float: left;
    position: relative;
    padding: 0 40px;
    height: 0;
    line-height: 30px;
    text-transform: uppercase;
    text-decoration: none;
    color: #fff;
    border-right: 30px solid transparent;
    border-bottom: 30px solid #3D3D3D;
    border-bottom-color: #777;
    opacity: .3;
    filter: alpha(opacity=30);
}

#tabs a:hover, #tabs a:focus {
    border-bottom-color: #2ac7e1;
    opacity: 1;
    filter: alpha(opacity=100);
}

#tabs a:focus {
    outline: 0;
}

#tabs #current {
    z-index: 3;
    border-bottom-color: #3d3d3d;
    opacity: 1;
    filter: alpha(opacity=100);
}                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       INDX( 	 �,{           (   0  �       c                     ��    � x f     ��    y ���x>�c3��x>�c3��x>�c3��x>�                        f o n t - a w e s o m e - 4 . 6 . 3   ��    ' h R     ��    y  �x>�6��x>�6��x>�6��x>�                        o p e n s a n s       ��    d h X     ��    y pO�x>� �����v�x>�>n�x>�       �               o p t i o n s . c s s -�    � � l     ��    y ˮ�x>� ����G����x>�4��x>�       �
               o p t i o n s _ m a i n _ p a g e .  s s     n�    | x h     ��    y X\�x>� �0d��G��x>���x>�h      e               p o p u p - a c c o r d i o n . c s s K�    \ p ^     ��    y �Հ�x>� B�������x>����x>�       i               p o p u p - t a b s . c s s   ��    L h T     ��    y du��x>� nô��dÕ�x>�����x>�        �              	 p o p u p . c s s     ��    � h V     ��    y ����x>�����x>�����x>�����x>�                       
 s m o o t h n e s s   ��    � x h     ��    y [��x>� ־˓��	���x>�n��x>� 0     �)               u n i f o r m . d e f a u l t . c s s                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           