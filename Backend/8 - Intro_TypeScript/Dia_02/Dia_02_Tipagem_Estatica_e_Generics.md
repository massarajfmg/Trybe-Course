
# Introdução - Tipagem Estática e Generics

## O que vamos aprender?

Hoje você continuará aprendendo sobre o maior diferencial do **Typescript** em relação ao Javascript: o seu sistema de tipos. Irá aprofundar seus conhecimentos sobre a tipagem estática, conhecer novos tipos, **Type Assertion** e os *Generics*, que te ajudarão na reutilização de código.

### Você será capaz de:

- Declarar tipos em coleções, *Arrays* e **Tuplas**;
- Declarar variáveis de tipos objeto do **TypeScript**;
- Compreender o que são *Type Aliases*;
- Compreender o que é uma **Classe**;
- Compreender o que é uma **Interface**;
- Compreender o que são **Type Assertion** e *Generics*;
- Estruturar um *model* que usa os conceitos aprendidos.

## Por que isso é importante?

Aprofundar o nosso conhecimento em uma tecnologia é sempre ótimo. Conhecer todas as ferramentas que ela pode proporcionar, assim como suas vantagens e limitações, nos torna pessoas desenvolvedoras cada vez melhores.

Não poderia ser de outra forma com o **TypeScript**. Seu sistema de tipos e tipagem estática são recursos muito poderosos que nos ajudam a expressar melhor a nossa intenção no código. Ele também garante, já em tempo de desenvolvimento, que não teremos erros como uma propriedade não poder ser acessada em um tipo não definido ou invocar um elemento que, na verdade, não é invocável por não ser uma função — quantas vezes já se deparou com esse erro no **JavaScript**?

O **TypeScript** também nos proporciona novas estruturas de dados que não existem no **JavaScript** que, muitas vezes, podem nos ajudar a resolver de uma forma melhor e mais coesa alguns problemas que encontramos no dia a dia do desenvolvimento de software, ou aumentar a nossa caixa de ferramentas e o nosso poder de escolha na hora de resolvê-los.

-------------------------------------------------------------------------------------------------------------------------------------

# Tipos de coleção

Chegou a hora de conhecer mais sobre os dois tipos de coleção mais importantes do **Typescript**: (**Arrays**) (que você provavelmente já trabalhou bastante ao longo do curso) e (**Tuplas**).

Bora lá! 🚀

## Arrays

**(Arrays)** são conjuntos de valores de mesmo tipo. Para declará-los, você pode adicionar o tipo esperado do array com a sintaxe **(let arrayName: type[] = [...];)**

```javascript
let names: string[] = ["Mary Joe", "Alan Joe"];

```

## Tuplas

**(Tuplas)** permitem declarar um conjunto de valores cuja ordem e tipo dos valores são fixas. Em JavaScript, elas são representadas como arrays (por isso a semelhança!), mas são estruturas diferentes. Por exemplo, você pode querer representar um valor como um par de uma **(string)** e um **(número)**.

Para declarar uma **(tupla)**, use a sintaxe **(let variableName: [type, type, ...]:)**

```javascript
let fullName: [string, string] = ["Jane", "Doe"];
let person: [string, number] = ["Jane Doe", 35];
let car: [string, string, number] = ["Ford", "F400", 10];

```

# `Type Aliases e Type Unions`

## `Type Aliases`

*Type Aliases* (apelidos de tipos) são utilizados para declarar a forma de um objeto nomeando o tipo, o que nos permite usar o mesmo tipo mais de uma vez e nos referir a ele através de um único nome. Um `type alias` é exatamente isso: um nome para qualquer tipo.

Para criar um `type alias` utilizamos a seguinte sintaxe:

```javascript
type Point = {
  x: number;
  y: number;
};

function printCoord(pt: Point) {
  console.log("O valor da coordenada x é: " + pt.x);
  console.log("O valor da coordenada y é: " + pt.y);
}

printCoord({ x: 100, y: 100 });
//saída:
//O valor da coordenada x é: 100
//O valor da coordenada y é: 100

```

Podemos dar um nome a qualquer tipo não apenas a um tipo de objeto.

### `Exercício Type Aliases`


1. Crie um `type` para um objeto que represente um pássaro.

2. Crie um `type` que represente uma função que recebe dois valores numéricos e retorne a soma deles.

3. Crie um `type` para um objeto que represente um endereço.


## `Type Unions`

*Type Unions* (união de tipos) é uma forma de declarar que um objeto é um tipo formado a partir de dois ou mais outros tipos, representando valores que podem ser qualquer um desses tipos. Para isso, é preciso declarar os tipos esperados separados por barra vertical `(|)` conhecido em inglês como pipe.

```javascript
// A função abaixo pode receber tanto um número
// quanto uma string.
function imprimirCPF(cpf: number | string){
  console.log("Seu CPF é: " + cpf);
}

imprimirCPF(11111111111);
// Saída:
// Seu CPF é: 11111111111
imprimirCPF('111.111.111-11');
// Saída:
// Seu CPF é: 111.111.111-11

```

## `Exercício Type Unions`

1. Crie um `type union` que represente os estados físicos da matéria: líquido, sólido ou gasoso.

2. Crie um `type union` que represente o documento identificador de uma pessoa que pode receber valores numéricos ou texto - Ex: “123.567.890-12” ou 123456789012.

3. Crie um `type union` que represente sistemas operacionais: linux, mac os ou windows.

4. Crie um `type union` que represente as vogais do alfabeto.

