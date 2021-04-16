---
layout: post
categories: development portuguese
title: Clean Code - Funções
---

Notas de estudo do livro *Clean Code* de Robert C. Martin.  
*Capítulo 3 - Funções*

Neste capítulo, Uncle Bob nos ensina como uma boa função deve ser estruturada. 

## Pequenas

A primeira regra é que as funções (métodos) devem ser pequenas e fazer apenas uma coisa, nunca ultrapasse as 20 linhas. 
No cenário ideal, cada função tem 2, 3 ou 4 linhas e possui uma obviedade transparente. Cada uma conta uma história e leva você a próxima em uma ordem atraente.
Blocos dentro de instruções if, else, etc. devem conter apenas uma linha, de preferencia uma chamada de função, pois essa função pode receber um nome descritivo.

## Um nível de abstração por função

O código deve ser lido de cima pra baixo como uma narrativa, cada função deve ser seguida por outra, no proximo nível de abstração. Ou seja, queremos ler o programa como se fosse uma serie de parágrafos, descrevendo o nível atual de abstração e fazendo referencia ao proximo nível.

## Instruções switch

Devemos evitar, pois é quase impossível criar uma instrução switch pequena. Se não pudermos evitar, vamos garantir que cada switch esta em uma classe de baixo nível e nunca é repetido, para garantir isso podemos usar polimorfismo.`
## Use nomes descritivos

Para usar nomes descritivos, é importante seguir a regra de ter métodos pequenos e que só ficam uma coisa, assim fica fácil nomear o método. Não tem problema se o nome for grande, um nome grande e descritivo é melhor que um comentário longo e descritivo. Seja consistente nos nomes, use os mesmos verbis, frases e substantivos nos nomes das funções, isso vai manter um padrão r vai facilitar a leitura e manutenção do código.

## Parâmetros de funções

A quantidade ideal de parâmetros de uma função é 0, depois 1 e depois 2. Deve-se evitar um método com 3 parâmetros. Se tiver mais que 3, deve-se ter um motivo muito especial para usa-lo. É melhor instanciar um objeto do que passa-lo por parâmetro. Pois assim fica mais fácil de entender o que esta acontecendo. Os parâmetros são mais difíceis ainda do ponto de vista de testes, deve-se escrever muitos casos de teste para se certificar que todas as combinações dos parâmetros estão cobertas. Parâmetros booleanos devem ser evitados sempre, se a função possui um parâmetros booleano, significa que existem duas possibilitas, ou seja, ela está fazendo mais de uma coisa.

Passar um objeto para reduzir o numero de paramentos é uma coisa boa. Se passamos muitas variáveis por parâmetros, temos que prestar atenção se não estamos passando parte de um conceito que mereça uma classe.

A regra para a criação de bons nomes de funções e parâmetros é utilizar um verbo e um substantivo para os parâmetros, por exemplo `writeField(name)`.

## Evite efeitos colaterais

Ou seja, evite funções que prometem fazer uma coisa mas acabam fazendo muito mais, como modificar variáveis da própria classe. Se uma função se chama `checkPassword()`, não faça ela iniciar uma sessão ou qualquer outra coisa após saber o resultado, apenas retorne o valor booleano.

## Separação comando-consulta

As funções devem fazer ou responder algo,  ou seja, ou ela altera o estado de um objeto (set) ou retorna a informação dele (get). Fazer os dois viola a regra de responsabilidade única de uma função.

## Prefira exceções a retorno de códigos de erro

Utilize exceções e não logs para avisar de um erro e separe um bloco `try/catch` em sua própria função, isso mantem separado o processamento normal do código e o tratamento do erro. Uma função que trata erro, não deve fazer mais nada.

## Evite repetição

A duplicação pode ser a raiz de todo o mal no software. A duplicação amontoa e bagunça o código. Se existem trechos de código fazendo a mesma coisa, é um sinal que a estrutura do programa pode estar com problemas. Avalie como a orientação a objetos pode ser usada para resolver o problema.

> Criar um software é como qualquer outro tipo de escrita. Ao escrever um artigo, você primeiro coloca seus pensamentos no papel e depois os organiza de modo que fiquem fáceis de ler. O primeiro rascunho pode ficar desastroso e desorganizado, então você, reestrutura e refina até que ele fique como voce deseja.
