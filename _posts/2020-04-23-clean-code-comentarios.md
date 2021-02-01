---
layout: post
title:  "[Clean Code] Comentários"
date:   2020-04-23
---

Notas de estudo do livro *Clean Code* de Robert C. Martin.  
*Capítulo 4 - Comentários*

Neste capítulo, Uncle Bob fala como usar comentários da forma correta.

Comentários são um mal necessário, se nossas linguagens de programação fossem expressivas o suficiente ou se tivéssemos o dom de nos expressarmos corretamente com ela, não precisaríamos de comentários.   
Quando se encontrar em uma situação que sentir a necessidade de criar um comentário, avalie se não tem como se expressar através do código em si.   
Comentários podem gerar uma grande confusão, já que códigos mudam e evoluem. São movidos de um lado para o outro, se bifurcam, se reproduzem, se unem novamente… e os comentários nem sempre acompanham essas mudanças.

## Comentários compensam um código ruim

Não gaste tempo criando comentários para explicar o código, gaste tempo melhorando o código.  
Explique-se no código.   
Em muitos casos, explicar-se no código é apenas nomear a função com o que você escreveria no comentário.   

Exemplo:

`// verifica se o funcionário tem direito a todos os benefícios
if ((employee.flags && HOURLY_FLAG) && (employee.age > 65))`

Pode ser substitído por:

`if (employee.isEligleForFullBenefits())`

## Comentários bons

### Comentários legais

Por questões legais as vezes precisamos adicionar comentários. Por exemplo, quando adicionamos informações sobre direitos autorais e autoria no início de um arquivo.   

### Comentários informativos

Um exemplo de comentário informativo é explicar o que um código Regex faz, já que é bem difícil de entendê-lo dependendo da sua complexidade.   
Mas ainda assim o ideal seria criar uma classe com o propósito deste código, que pode ser por exemplo, converter formatos de datas e horas.   

### Alerta sobre consequências

As vezes é útil alertar outros programadores sobre certas consequências como tempo de execução, ou avisar que alguma thread não é segura.   

### Comentários TODO

Comentários TODOS devem ser evitados, mas se for necessário deixar um código incompleto, ou que deve ser melhorado posteriormente por algum motivo muito especial (evite ao máximo deixar para depois!), comentários TODO são cabíveis.   

### Javadocs e APIS públicas

Se estiver escrevendo uma API pública, uma boa documentação deve ser feita, mas apenas se for uma API pública! Não faça isso para qualquer projeto.

### Comentários ruins

A maioria dos comentários são ruins! Aqui vão alguns exemplos: 
- Murmúrios, comentários que são esquecidos e deixados para trás.
- Comentários redundantes, que explicam o que o código já está explicando.
- Comentários enganadores, que dizem que um método retorna algo, mas esse algo só é retornado se uma condição ser verdadeira. Portando o programador pode chamar esse método esperando um retorno que pode nunca chegar.
- Comentários longos que parecem diários, é muito difícil manter esse comentário atualizado caso o código mude, sem falar que ele toma a atenção que deveria estar no código e pode confundir o programador.
- Comentários ruidosos que não trazem nenhuma informação nova ou relevante. Evite o comentário se é possível gerar uma função com um nome explicativo.
- Comentários com marcadores de posição como `// Header`, `// Ações`, etc. Defina isso em tags id por exemplo, se for `HTML`, ou em nomes de classes, funções ou arquivos. Crie uma boa estrutura de projeto.
- Comentários ao lado de chaves de fechamento, indicando que é o final de uma função. Se sentir a necessidade de adicionar esse comentário, é provavelmente porque a função está muito grande, tente diminuí-la.
- Crédito e autoria, a não ser que seja requisitado.
- Código comentado, isso gera acúmulo de lixo na codebase além de deixar outros programadores inseguros para excluí-lo.

## Conclusão

Houve um tempo em que era uma boa prática encher o código de comentários, mas hoje isso é vista como bagunça. Invista o seu tempo em criar um código legível.


