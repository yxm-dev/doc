---
title: "lec/dev/notes"
subtitle: "Vim: Portabilidade"
---

Lembre-se que todo sistema operacional possui um software base chamado de *kernel*. É ele que conecta os
diferentes componentes físicos do computador (os hardwares) e faz a transcrição entre os comandos que passamos
ao computador e o que o hardware deve executar. Além do kernel, alguns sistemas operacionais fazem uso de um
*shell*, que funciona como uma `CLI` para o kernel. Como comentamos em um texto anterior ([aqui](vim-o-que)),
esse é o caso, por exemplo, do `Unix` e de seus derivados.

Na década de 60, quando o primeiro `Unix` foi lançado, o kernel e o shell de todos os sistemas operacionais
eram escritos um uma linguagem do tipo *assembly*, as quais são mais fortemente dependentes das propriedades
hardware. Isso significa que um software desenvolvido em uma linguagem assembly pode "não funcionar" em outro
computador com um mesmo sistema operacional, mas hardwares com propriedades diferentes. Em outras palavras, um
software desenvolvido em uma linguagem assembly peca no quesito portabilidade.

No início da década de 70, uma linguagem de alto nível, chamada `C`, foi desenvolvida com enfoque na
portabilidade. Em 1971 o kernel do `Unix` começou a ser reescrito em `C` e a transcrição foi finalizada em
1972. No entanto, a primeira versão entregue ao público com um kernel em `C` foi a de 1979. Nesse meio tempo,
iniciou-se a transcrição do shell do `Unix`, dando origem ao conhecido `Bash`, que passou a ser entregue nas
versões a partir de `1989`.

O editor de texto `Ed`, da década de 60, era escrito em linguagens assembly. Seu sucessor `Ex`, que veio na
década de 70, já nasceu escrito em `C`. Foi justamente na versão de 1979 que `Vi` foi lançado pela primeira
vez ao público. Portanto, ele surgiu quando:

1. o kernel do `Unix` já estava escrito em `C` e pronto para ser lançado;
2. seu predecessor `Ed` era escrito em `C`;
3. o shell `Sh` estava em evolução para dar origem ao `Bash`.

Nessa situação apresenta-se de forma natural a escolha de desenvolver `Vim` em `C` ao invés de escrevê-lo na
linguagem shell `Sh`, a qual passava por uma fase de transição. Ter sido escrita em `C` foi crucial para a
portabilidade de `Vim`. Se fosse escrito em `Bash`, isso teoria o tornado menos adaptável a diferentes
sistemas operacionais.


