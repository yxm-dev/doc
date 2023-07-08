---
title: "lec/dev/notes"
subtitle: "O que é Vim?"
author: "yxm"
---

Origens
----------

No início da história dos sistemas operacionais encontra-se o `Unix`, desenvolvido pela Bell Labs na década de
60 que vinha acompanhado de um editor de texto chamado `Ed`, uma abreviação de *editor*. No início da década
de 70 `Ed` foi substituído por uma versão mais moderna, denominada `Ex` (vindo de *extended*). Nessa época
tudo tinha uma interface `CLI` (*command line interface*) e, portanto, tudo funcionava diretamente por linhas
de comando. Com o `Ex` não era diferente.

Com o avanço da tecnologia passaram a ser desenvolvidas aplicações `TUI` (*terminal-based user interface*).
Apesar de não serem `CLI`, as aplicações `TUI` também são realizadas dentro de um terminal. No final da década
de 70, a Unix substituiu `Ex` e passou a utilizar um editor de texto `TUI` chamado `Vi`: uma abreviação de
*visual*, em menção ao fato da mudança de linhas de comando para uma interface visual.

Os sistemas operacionais `Unix` não eram open-source. Por outro lado, eram muito visados devido
a sua portabilidade (veja a nota abaixo), o que motivou muitas pessoas a se debruçarem sobre o problema
de construir versões open-source de aplicações do `Unix`. Por exemplo, o kernel do `Linux` surgiu da tentativa
de reproduzir, em formato open-source, o kernel do `Minix`, uma das versões do `Unix`. O mesmo ocorreu com o
editor de texto `Vi`.

Com efeito, em 1991 Bram Moolenaar desenvolveu um software que se propunha a ser uma versão open-source do
`Vi`. Ele o chamou de `Vim`, um acrônimo para "Vi IMitation".  Contudo, `Vim` acabou sendo desenvolvido como
um fork muito mais elaborado que `Vi` e muito mais cheio de ferramentas, levando-se à substituição do
significado do acrônimo `Vim` por "Vi IMproved". Ao longo dos anos, `Vim` desenvolveu-se focado na
simplicidade, na modularidade e na customização.

Características
-----------------

`Vim` foi desenvolvido em linguagem `C` sendo independente do shell utilizado no `Unix`. Isso
possibilitou que versões de `Vim` para diferentes sistemas operacionais fossem lançadas. Uma linguagem de
script chamada `Vimscript` foi desenvolvida para padronizar e favorecer a criação de módulos, aqui chamados de
`plugins`.

Uma das características marcantes do `Vi` é o uso de *keybinds*: trata-se do mapeamento de padrões de teclas
do teclado em ações, o que a execução de comandos mais simples, rápida e customizável. Tal característica
manteve-se viva e predominante no `Vim`.

`gvim`
--------------

Ainda na década de 80 começaram a surgir as primeiras aplicações `GUI` em computadores `Macintosh` e `Windows 1.0`.
Sem deixar o ar minimalista, em 1998 uma versão `GUI` do `Vim` foi lançada, sendo chamada de `gVim`.

`Conclusão`
---------------

Assim, `Vim` é:

* um editor de texto criado em 1991 como fork de um editor de texto que existe desde a década de 70, o que o
  torna extremamente estável e muito bem testado;
* um software open-source e multiplataforma, com versões para `Linux`, `Windows`, `MacOS`, etc.
* originalmente desenvolvido no formato `TUI`, mas possui também uma versão `GUI` bastante minimalista,
  chamada de `gVim`;
* extensível, admitindo uma série de plugins que o agregam funcionalidades;
* totalmente customizável.
