---
layout: post
categories: cool
title: Clean Code - Nomes significativos
---

Notas de estudo do livro *Clean Code* de Robert C. Martin.  
*Capítulo 2 - Nomes significativos*

Uma das coisas que mais fazemos quando programamos é nomear. Nomeamos classes, funções, variáveis, entre outra coisas. Já que fazemos muito isso, é importante que façamos bem.

## Use nomes que revelem seu propósito

Escolher bons nomes leva tempo, mas economiza mais. Portanto, cuide de seus nomes e troque-os quando encontrar melhores.
O nome de uma variável, função ou classe deve lhe dizer porque existe, como faz e como é usado. Se um nome requer comentário, ele não revela seu propósito.

Exemplos de nomes ruins: *a*, *list*, *n1*, *getThem()*.  
Exemplos de nomes bons: *age*, *names*, *month*, *getAges()*.

## Evite informações erradas

Devemos evitar palavras cujos significados podem se desviar daqueles que desejamos. Por exemplo, nunca utilize a variável *accountList* a menos que essa variável seja uma *List* (palavra específica de muitas linguagens de programação) de verdade. Se não for o caso, utilize outros nomes como *accountGroup* ou apenas *accounts*.

## Faça distinções significativas

Suponhamos que temos os métodos *getActiveAccount()* e *getActiveAccountInfo()*, como saber qual chamar? Também não há como distinguir *moneyAccount* de *money* ou *customerInfo* de *customer*. Faça distinções de uma forma que o leitor compreenda as diferenças. Se começamos a nomear as coisas de forma parecida, temos que reavaliar se o design do código está da forma que deveria ser.

## Use nomes pronunciáveis

Uma das coisas que fazemos como desenvolvedores, é discutir com outros o nosso código. Precisamos usar nomes pronunciáveis para fazer isso de uma forma melhor. Isso importa porque a programação dentro do ambiente de mercado, querendo ou não, é uma atividade social.

## Use nomes passíveis de busca

Nomes que possuem apenas uma letra ou números são difíceis de buscar em um código longo. Uma busca pela variável *a* por exemplo, em qualquer IDE, retornaria milhares de resultados dependendo do tamanho do código.

## Evite codificações e prefixos de variáveis membro

Nomes codificados raramente são pronunciáveis, além de ser fácil escrevê-los incorretamente. Exemplos de nomes ruins: *m_dsc*, *IShapeFactory* e *phoneString*.  
*IShapeFactory* é um exemplo muito seguido hoje em dia para interfaces, mas não tem porque enfeitar o nome, o que interessa é que ela é uma *ShapeFactory*, não precisa incluir o *I*. Para a implementação, posso usar o nome *ShapeFactoryImp*.

## Evite o mapeamento mental

Certamente um contador de iterações pode ser chamado de *i*, *j* ou *k*, pois isso já se tornou uma convenção, desde que seu escopo seja pequeno e não houver outros nomes que possam entrar em conflito. Mas no geral, um nome de uma letra só é uma escolha ruim. Dificilmente você vai lembrar que um *r* minúsculo é uma versão da url sem o host, muito menos outro programador que está mantendo o seu código.

## Nomes de classes

Classes e objetos devem ter nomes com substantivo, como *Customer*, *Account* e *AddressParser*. Não use verbos.

## Nomes de métodos

Os nomes de métodos devem ter verbos como *save()* e *deletePage()*. Devem-se nomear métodos de acesso, alteração e autenticação segundo seus valores e adicionar os prefixos *get*, *set* e *is* (padrão *javabean*). Exemplo: *geUser()*, *setUser()* e *isAdmin()*.

## Não dê uma de espertinho

Se os nomes forem muito "espertinhos", apenas pessoas com o mesmo senso de humor irão entender.

## Selecione uma palavra por conceito

Escolha uma palavra por cada conceito abstrato e fique com ela. Por exemplo, é confuso ter *get*, *fetch* e *retrieve* como métodos equivalentes de classes diferentes. Da mesma forma é confuso ter um *controller*, um *manager* e um *driver*.

## Não faça trocadilhos

Evite usar a mesma palavra para dois propósitos. Por exemplo, você pode ter várias classes com o método *add()*, contanto que as listas de parâmetros e os valores retornados dos diversos métodos *add()* sejam semanticamente equivalentes. Se não for o caso, use *append()* ou *insert()*.

## Use nomes a partir do domínio da solução

São programadores que lerão o seu código. Portanto, está liberado usar nomes relativos da área. Nâo é prudente colocar um nome a partir do domínio do problema, pois o programador precisaria consultar o cliente todo o tempo para entender o significado de um nome. Por exemplo, o nome *AccountVisitor* significa o bastante para um programador familiarizado com o padrão *visitor*.

**Use nomes de domínios do problema** somente quando não houver uma solução *a la programador*, pois pelo menos ele poderá consultar o cliente.

## Adicione um contexto significativo

Há poucos nomes que são significativos por si só. Imagine as variáveis *street*, *houseNumber*, *city* e *state*. Vistas juntas, fica claro que se trata de um endereço. Mas com a variável *state* sozinha, ficaria mais difícil de entender do que se trata, *state* pode ser várias coisas. A solução ideal nesse caso, é ter um objeto *Address*, mas se isso não for possível, pode-se abrir uma exceção e usar o prefixo *addr*, ficando *addrState*.

## Não adicione contextos desnecessários

Em uma aplicação chamada *Gas Station Deluxe* (GSD), seria uma péssima ideia adicionar o prefixo GSD em todas as classes. Isso dificultaria a busca (se eu pesquisar *G* por exemplo, apareceria uma lista enorme com todas as classes). Os nomes *accountAddress* e *customerAddress* são bons para instâncias de classes, mas péssimos para as classes mesmo, a classe deve ser apenas *Address*.

## Conclusão

Não tenha receio de renomear as coisas por temer a opinião de outros desenvolvedores. Desenvolvedores profissionais ficam agradecidos quando o código muda para melhor. De qualquer forma, na maioria das vezes, não memorizamos os nomes de métodos e classes. Use qualquer dica acima e note como o código ficará mais legível.