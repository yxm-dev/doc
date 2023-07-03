---
title: "lec/dev/notes/"
subtitle: "Por que Vim?"
author: "yxm"
---

Anteriormente contamos um pouco sobre a história de `Vim` ([aqui](vim-o-que), e falamos sobre uma de
suas principais características: a *portabilidade* ([aqui](vim-portabilidade)). Neste texto gostaria de
comentar o porque de minha escolha de `Vim` como meu editor. Obviamente a portabilidade é um peso a favor. No
entanto, o verdadeiro motivo está relacionado com minha maneira de ver o mundo. 

Caminhos
---------

Quando preciso tomar uma
atitude em relação à adquirir algo ou algum serviço, a primeira coisa que penso é:

* eu realmente preciso disso?

Isso me leva a questionar minhas *reais necessidades* e o papel do produto/serviço dentro delas. Existem dois
caminhos a se tomar:

* buscar produtos/serviços que com certeza cobrem as necessidades, mas sem se preocupar se outras coisas
  desnecessárias também estão sendo cobertas;
* buscar produtos/serviços que com certeza cobrem as necessidades, mas que cobrem apenas elas.

Noto algumas diferenças entre as abordagens:

* O primeiro caminho:
    - fornece uma condição *suficiente* para a solução das necessidades, mas por cobrir coisas além, não é uma
      condição necessária;
    - é baseado em *generalidade*: cobre-se tudo o que é possível, de modo que a mesma solução (os mesmos
      produtos/serviços) cobrem as necessidades de várias pessoas;
    - não é construtivista: o que importa é cobrir as necessidades, sem se importar com a maneira em que isso
      é feito.
      
* O segundo caminho:
    - fornece uma condição *necessária e suficiente* para a solução das necessidades;
    - é baseado em *customização*: cobre-se as necessidades de uma pessoa em específico;
    - é construtivista: preocupa-se com a construção da solução em cada uma de suas etapas, não só com a
      solução final. 

É uma escolha pessoal, mas sempre prefiro o segundo caminho. Eu passo grande parte do meu dia na frente do
computador utilizando um editor de texto. Então, não seria diferente com respeito à escolha deste.

Vantagens e Desvantagens
--------------------------

Mas, quais são as vantagens e desvantagens de se seguir cada caminho? Decidir se um fato é uma desvantagem e
desvantagem é algo bastante pessoal, mas segue o meu ponto de vista:

* O primeiro caminho é mais rápido e mais simples. Ele também é "estável" com respeito a novas necessidades:
  se um dia você precisar de algo novo, provavelmente a solução já estará lá.
* Como desvantagem, se é obrigado a carregar o peso referente às soluções das necessidades que você ainda não
  possui ou que nem irá possuir um dia.
  
* O segundo caminho demanda tempo: é preciso analisar real necessidade de cada questão para então buscar pelas
  soluções que contemplem a elas, tentando minimizar features desnecessárias. 
* Além disso, é preciso um esforço
  diário para manter tudo em ordem: caso uma nova necessidade apareça, o processo de análise e busca e
  otimização de soluções precisará recomeçar.
* Como vantagem, tem-se uma solução limpa, simples e leve que cobre exatamente o que se precisa.

Por que `Vim`?
--------------

Mas, por que `Vim`? Ora, ele segue exatamente a filosofia do segundo caminho. Em contrapartida, as IDEs padrões
seguem a filosofia do primeiro caminho e, portanto, vão na contramão do que acredito. No fim, tenho a garantia
de conseguir rodar meus arquivos em diferentes computadores:

* de diferentes OS, devido à *portabilidade*
* mesmo com pouco recursos, já que a solução minimiza o seu uso.

Seguindo por outra argumentação: uma questão importante para mim é que `Vim` roda dentro de um terminal: é uma
aplicação TUI. Para cumprir esse requisito existem poucas soluções disponíveis, sendo Nano a mais conhecida
delas. O problema é que Nano não possui modularidade suficiente para possibilitar a adequação a todas as
minhas necessidades atuais. 

Esse é outro ponto forte sobre `Vim`: a *modularidade*. Recorde que, como comentamos em um texto anterior
([aqui](https://www.linkedin.com/feed/update/urn:li:activity:7065364501587517440/?updateEntityUrn=urn%3Ali%3Afs_feedUpdate%3A%28V2%2Curn%3Ali%3Aactivity%3A7065364501587517440%29)),
`Vim` é escrito em `C` e possui sua própria linguagem de script (o `Vim Script`), o que torna viável a construção
de extensões para ele. Além disso, existem inúmeras extensões já disponíveis por aí que podem ser anexadas a
sua configuração de forma simples.

`NeoVim`
----------

Mas, e o `NeoVim`? Bem, isso é assunto para outro texto. O que já adianto é que não senti a necessidade de migrar
do `Vim` e só o farei se tal necessidade aparecer um dia e não puder ser realizada dentro do `Vim`.

