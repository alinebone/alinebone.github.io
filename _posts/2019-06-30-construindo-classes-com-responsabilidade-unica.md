---
layout: post
title:  "Construindo classes com responsabilidade única"
date:   2014-06-30
---

*Practical Object-Oriented Design in Ruby, Sandi Metz.  
Chapter 2 - Design classes with single responsability*

Se um projeto tem sucesso, existe uma possibilidade enorme dele precisar ser atualizado, por isso é fundamental que o código seja fácil de mudar.

Sandi Metz, autora de *Practical Object-Oriented Design in Ruby* usa um acróstico com a palavra TRUE para definir como um código deve ser:

**T**ransparent  
**R**easonable  
**U**sable  
**E**xemplary

*Transparent*: significa que as consequências de uma mudança no código devem ser óbvias.  
*Reasonable*: o custo de uma mudança deve ser proporcional aos seus benefícios.   
*Usable*: o código existente deve continuar sendo usável após as alterações, mesmo em contextos novos e inesperados.  
*Exemplary*: o código deve encorajar os outros a manter a qualidade.

O primeiro passo para criar um código TRUE é usar o princípio da reponsabilidade única, que diz que uma classe deve fazer a menor coisa útil possível. 

Quando estamos desenvolvendo uma aplicação, procuramos substantivos candidatos a serem classes. São candidatos os substantivos que possuem atributos e comportamentos, como a marcha de uma bicicleta. Uma classe *marcha* teria correntes e engrenagens (atributos), e proporção (comportamento). Se quiser incluir o cálculo do tamanho da marcha nesta classe, teremos que incluir o tamanho da roda e do pneu.

Para um programa crescer, ele precisa ser modificado para ser fácil de trabalhar no futuro.
Aplicações fáceis de mudar são aplicações fáceis de reutilizar.

As classes devem ser como blocos com propósito específico e que vamos mantendo conforme a necessidade. A classe que contém mais de um propósito é difícel de ser reutilizada.

Dica: Tratar métodos com quetões para ver se ele está certo:
*Hey, [nome da classe], qual o seu [nome do método]?*

Se quando desrevermos a classe, usarmos a palavra "e", ela provavelmente tem mais de uma responsabilidade. Se usarmos a palavra "ou", ela tem mais de uma responsabilidade e elas não são nem relacionadas.

Exemplos de descrição para a classe marcha:
- Calcular a proporção entre rodas dentadas
- Calcula o efeito que a marcha tem uma uma bicicleta

Se não tenho certeza sobre a responsabilidade de uma classe, devo aguardar até ter mais informações, pois a tendência é que o próximo desenvolvedor replique o meu design ou reuse minha classe.
Portanto, faça o código com cuidado e seja crítico com o código dos outros.

Dependa de comportamento, não de dados:
- Encapsule as variáveis em métodos de acesso (get). Se eu referenciar essa variável em 10 lugares e precisar mudar o que ela significa, fica mais fácil fazer isso modificando ou implementando minha versão do método.
- Utilizar *single responsability* também em outros lugares, como métodos. O objetivo é deixar o código fácil de mudar, e não pequeno. Refatorar o método para que ele tenha responsabilidade única traz vantagens como:
	- Fica mais fácil entender se uma classe tem responsabilidade única
	- Evita comentários explicando o que o método faz
	- Encoraja o reuso do método
	- Métodos pequenos são mais fáceis de mover para outra classe, caso necessário

- Se encontrar responsabilidades extras em uma classe que ainda não podem ser removidas, isole-as, usando ferramentas como o stect do Ruby.