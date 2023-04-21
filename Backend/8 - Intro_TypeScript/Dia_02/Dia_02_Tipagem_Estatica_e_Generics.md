
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

2. Crie um `type union` que represente o documento identificador de uma pessoa que pode receber valores numéricos ou texto.
  Ex: “123.567.890-12” ou 123456789012.

3. Crie um `type union` que represente sistemas operacionais: linux, mac os ou windows.

4. Crie um `type union` que represente as vogais do alfabeto.


# Classes

No **TypeScript**, as classes são uma maneira de definir a forma de um objeto. Podemos considerar uma classe como um projeto para a criação de objetos. Uma classe `Person` descreve os atributos de uma pessoa, por exemplo: nome, data de nascimento e idade. Ela também descreve ações que uma pessoa pode executar, como falar, comer ou andar.

Mas a classe `Person` é apenas um plano para a criação de uma pessoa. Você deve criar uma instância de pessoa da classe `Person` antes que ela se torne um objeto ao qual você possa atribuir valores de propriedade (como definir a idade como 27) ou chamar suas ações (como falar).

```javascript

// usamos a palavra reservada class para definir uma classe
class Person {
    name: string;
    birthDate: Date; // o tipo Date está presente no TypeScript assim como no JavaScript
    age: number;
    // aprenderemos mais sobre o construtor na próxima seção
    // considere-o como uma função utilizada para construir um objeto a partir da classe,
    // nele recebemos todos os dados necessários para construir um objeto de pessoa
    constructor(name: string, birthDate: Date, age: number;) {
        // usamos o this para acessar as propriedades da instância da classe,
        // ele representa a própria instância que estamos criando
        // atribuímos o valor do parâmetro recebido a propriedade da instância da classe
        this.name  = name;
        this.birthDate  = birthDate;
        this.age  = age;
    }

    speak(): void {
        console.log(`${this.name} está falando.`);
    }

    eat(): void {
        console.log(`${this.name} está comendo.`)
    }

    walk(): void {
        console.log(`${this.name} está andando.`)
    }
}
```

A classe `Person` pode ser reutilizada para criar qualquer quantidade de novos objetos `Person`, cada um com suas próprias características.

```javascript
// usamos a palavra reservada new para criar uma instância de Person
// e passamos os parâmetros necessários para o construtor
const person1 = new Person("Jane Doe", new Date("1986-01-01"), 27);
const person2 = new Person("Jon Doe", new Date("1980-08-05"), 42);

console.log(person1);
person1.speak()

// saída:
// Person: {
//   "name": "Jane Doe",
//   "birthDate": "1986-01-01T00:00:00.000Z",
//   "age": 27
// }
// "Jane Doe está falando."

console.log(person2);
person2.walk();

// saída:
// Person: {
//   "name": "Jon Doe",
//   "birthDate": "1980-08-05T00:00:00.000Z",
//   "age": 42
// }
// "Jon Doe está andando."
```

Também é possível dizer que uma das propriedades da nossa classe `Person` não é obrigatória para criarmos um objeto pessoa. Podemos usar o caractere `?` para marcar uma propriedade como opcional, o que faz com seu tipo seja um union type entre o tipo original e `undefined`. Se quiséssemos dizer que a idade não é obrigatória nossa classe ficaria assim:

```javascript
class Person {
    name: string;
    birthDate: Date;
    age?: number;

    constructor(name: string, birthDate: Date, age?: number) {
        this.name  = name;
        this.birthDate  = birthDate;
        this.age  = age;
    }

    speak(): void {
        console.log(`${this.name} está falando.`);
    }

    eat(): void {
        console.log(`${this.name} está comendo.`)
    }

    walk(): void {
        console.log(`${this.name} está andando.`)
    }
}
```

A criação das nossas instâncias de `Person` poderiam ou não serem criadas com a idade.

```javascript
const person1 = new Person("Jane Doe", new Date("1986-01-01"));
const person2 = new Person("Jon Doe", new Date("1980-08-05"), 31);

console.log(person1);
person1.speak()

// saída:
// Person: {
//   "name": "Jane Doe",
//   "birthDate": "1986-01-01T00:00:00.000Z"
// }
// "Jane Doe está falando."

console.log(person2);
person2.walk();

// saída:
// Person: {
//   "name": "Jon Doe",
//   "birthDate": "1980-08-05T00:00:00.000Z",
//   "age": 31
// }
// "Jon Doe está andando."
```

E poderíamos adicionar essa informação depois da criação:

```javascript
const person1 = new Person("Jane Doe", new Date("1986-01-01"));

console.log(person1);
person1.speak()

// saída:
// Person: {
//   "name": "Jane Doe",
//   "birthDate": "1986-01-01T00:00:00.000Z"
// }
// "Jane Doe está falando."

person1.age = 23;
console.log(person1);

// saída:
// Person: {
//   "name": "Jane Doe",
//   "birthDate": "1986-01-01T00:00:00.000Z",
//   "age": 23
// }
```

Agora vamos entender como implementar classes na prática! Assista ao vídeo abaixo:

`Video no Course`

## Exercícios

1. Crie uma `classe` cujo objeto represente um Cachorro.
2. Crie uma `classe` cujo objeto represente uma Casa.
3. Crie uma `classe` cujo objeto represente um Voo.


# Interfaces

Esta é mais uma estrutura que não existe no **JavaScript**. A **Interface** é utilizada para declarar a forma de um objeto, nomear e parametrizar os tipos do objeto e compor tipos de objetos nomeados existentes em novos. São uma forma eficiente de definir um “contrato de código”, ou seja, aquilo que você espera que seja implementado dentro do seu código.

Por exemplo, se quiséssemos criar uma `interface` que define as propriedades e métodos de uma pessoa funcionária, seria assim:

```javascript
interface Employee {
    firstName: string;
    lastName: string;
    fullName(): string;
}
```

Uma `interface` não inicializa nem implementa as propriedades declaradas dentro dela, porque **o único trabalho de uma** `interface` **é descrever o objeto**. Ela define o que o contrato de código exige, enquanto quem implementa a `interface` deve atender ao contrato fornecendo os detalhes de implementação necessários.

```javascript
let employee: Employee = {
    firstName : "John",
    lastName: "Doe",
    fullName(): string {
        return this.firstName + " " + this.lastName; // usamos o "this" para acessar as propriedades da interface
    }
}

employee.firstName = 10;  // Error: Type "number" is not assignable to type "string"
```

Uma `interface` também pode estender de uma outra, o que permite que copiemos as propriedades de uma `interface` em outra, proporcionando mais flexibilidade na maneira de separará-las em componentes reutilizáveis. Podemos estender uma `interface`, usando a palavra reservada `extends`:

```javascript
interface Teacher extends Employee {
    subject: string;
    sayHello(): string;
}
```

E para criar um objeto do tipo `Teacher` seria assim:

```javascript
let teacher: Teacher = {
    firstName: "John",
    lastName: "Doe",
    subject: "Matemática",
    fullName(): string {
        return this.firstName + " " + this.lastName;
    },
    sayHello(): string {
        return `Olá, eu sou ${this.fullName()} e leciono ${this.subject}`;
    }
}
```

Observe que um objeto que atende à interface Teacher precisa definir valores para todas as propriedades exigidas por essa interface, incluindo as propriedades da interface base Employee.

Por exemplo, o objeto `teacher` possui as propriedades `firstName`, `lastName` e o método `fullName` da `interface` Employee, mas também possui as próprias propriedade `subject` e o método `sayHello` que são específicas da `interface` Teacher.

`Classes` também podem implementar `interfaces`, o que faz com que a `classe` possua todas as propriedades e métodos daquela `interface`.

### Exercícios

1. Crie uma interface cujo objeto represente um Automóvel.
2. Crie uma interface cujo objeto represente um Felino.
3. Crie uma interface cujo objeto represente uma Aeronave.

