
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

1. Crie uma `interface` cujo objeto represente um Automóvel.
2. Crie uma `interface` cujo objeto represente um Felino.
3. Crie uma `interface` cujo objeto represente uma Aeronave.


# Type Assertion e Generics

## Type Assertion (as Type)

Há momentos em que precisamos utilizar recursos nativos do JavaScript, ou até mesmo bibliotecas externas, que podem não oferecer opções para realizarmos uma tipagem eficiente para obtermos o tipo correto para uma variável ou objeto. Quando nos deparamos com cenários assim, a melhor alternativa é buscar entender a estrutura que a variável ou objeto terá em momento de execução (runtime) para então forçar um tipo específico utilizando o `Type Assertions` do TypeScript.

Por exemplo, a seguir temos uma função que converte `string` para `json`. Por ser muito genérica, a tipagem que a função retorna é desconhecida `(unknown)`, mas observando o código dá para notar na `string` a ser convertida qual estrutura será retornada depois que a função for executada. Sendo assim, podemos forçar um tipo específico para aquele objeto e continuar aproveitando os recursos do TypeScript:

```javascript
type Address = {
  street: string,
  number: number | null,
}

type User = {
  name: string,
  email: string,
  password: string,
}

// função que converte de string para json
function stringToJson(str: string): unknown {
  const result = JSON.parse(str);
  return result;
}

// utilizando o "as" para converter de unknown para User
const user = stringToJson('{"name":"André Soares","email":"andre@trybe.com","password":"senha_secreta"}') as User

// Outra forma de usar o Assertion. A sintaxe é diferente mas tem o mesmo objetivo
const address = <Address> stringToJson('{"street":"Rua Tamarindo","number":1}')

user.name;
address.street;
```

## Mais exemplos curtos usando Type Assertions

```javascript
const str: unknown = 'texto'; // simulando um valor supostamente desconhecido

str.split(''); // Dispara um erro por aplicar um split em um tipo desconhecido
(str as string).split('') // Corrigindo o erro acima usando o 'as'

const num: string = '2';

num as number // dispara um erro, pois não é possível usar Type Assertions com tipos incompatíveis
(num as unknown) as number // Corrigindo o erro acima convertendo primeiramente para unknown

```

**Type Assertion** é uma forma de você falar para o compilador “confia em mim, eu sei o que estou fazendo”. Portanto, é um recurso que você só deve utilizar se realmente souber a estrutura de tipo esperada para uma variável ou objeto. O ideal, na verdade, é que `Type Assertion` seja a sua segunda alternativa para conseguir atribuir tipos específicos em valores incertos ou desconhecidos. A primeira alternativa para tentar tipar comportamentos genéricos que você pode optar é utilizar os Generics que o próprio TypeScript oferece.

## Generics

Generics é uma forma de passarmos, por meio de parâmetros, tipos para funções que se comportam de forma genérica.

Para entendermos melhor podemos refatorar o código anterior, que fizemos utilizando `Type Assertions`, para começar a utilizar Generics:

```javascript
/ [...]
function stringToJson<T>(str: string): T {
  const result = JSON.parse(str);
  return result;
}

const user = stringToJson<User>('{"name":"André Soares","email":"andre@trybe.com","password":"senha_secreta"}');

const address = stringToJson<Address>('{"street":"Rua Tamarindo","number":1}')

user.name;
address.street;
```

Note que agora estamos recebendo um parâmetro genérico `T` na função destino e esperamos que seja retornado esse mesmo tipo. Na hora de utilizar a função basta somente informar o tipo que gostaríamos de obter.

Perceba que o código ainda se comporta da mesma forma que quando usamos `Type Assertions`, porém estamos tipando com uma estratégia diferente.

Optar pelo uso de `Generics` para casos como o do exemplo de código acima, acaba sendo mais vantajoso, pois se nosso código precisar passar por alterações o `Generics` consegue oferecer possibilidades mais organizadas para escalar a tipagem. Por exemplo, vamos imaginar que agora nossa função `stringToJson` precisará adicionar um identificador único no resultado do nosso objeto. Nós vamos informar esse identificador como segundo parâmetro da função, e além disso atribuir um outro tipo genérico:

```javascript
// [...]
function stringToJson<T, U>(str: string, id: U ): T & { id: U } {
  // const result = JSON.parse(str);
  result.id = id;
  // return result;
}

const user = stringToJson<User, number>('{"name":"André Soares","email":"andre@trybe.com","password":"senha_secreta"}', Date.now());

const address = stringToJson<Address, string>('{"street":"Rua Tamarindo","number":1}', '#01')

user.id;
address.id;
```

Veja os pontos que alteramos acima:

 - O envio de múltiplos tipos por parâmetro (`T` e o `U`);
 - A possibilidade de usar o parâmetro genérico de maneira distribuída na função destino (tanto no parâmetro `id: U` como no retorno `T & { id: U })`;
 - A manipulação dos genéricos para modificar o tipo de retorno esperado (na interseção `T & { id: U }`)

Note que as propriedades `id` de `user` e `address` têm exatamente o mesmo tipo que informamos no segundo parâmetro do Generics (assim como o segundo parâmetro da função). Você pode provocar um erro proposital trocando o tipo `string` por `boolean`, por exemplo. Se fizer isso vai perceber que o TypeScript irá reclamar. 😁

Declaramos uma variável de nome `numberArray` chamando a função `getArray` e passando a ela um `array` de `numbers`, enquanto uma variável `stringArray` é declarada com um `array` de `strings`. Como o tipo `any` foi usado, não há nada que impeça o código de enviar um `string` para o `numberArray` ou um `number` para o `stringArray`.

## Mais exemplos curtos usando Generics

```javascript
function identity<T, U> (value: T, message: U) : T {
    console.log(message);
    return value
}

const returnNumber = identity<number, string>(100, "Olá");
const returnString = identity<string, string>("100", "Mundo");
const returnBoolean = identity<boolean, string>(true, "Olá, Mundo!");
```

```javascript
function getArray<T>(items : T[]) : T[] {
  return new Array<T>().concat(items); // construindo um Array que só pode conter elementos do tipo T
}

const numberArray = getArray<number>([5, 10, 15, 20]);
numberArray.push(25);
numberArray.push("This is not a number"); // Isto vai gerar um erro de compilação

const stringArray = getArray<string>(["Cats", "Dogs", "Birds"]);
stringArray.push("Rabbits");
stringArray.push(30); // Isto vai gerar um erro de compilação
```

# Model com MySQL

Vamos agora colocar os aprendizados em prática e ver como podemos usar *Type Assertions, Generics, Classes e Interfaces ao estilo real life*.

## Criação do banco de dados

Para esse projeto, vamos usar um banco de dados MySQL para gerenciar uma lista de livros. Crie o banco usando o SQL abaixo (caso precise lembrar como criar um banco de dados a partir de uma *query* SQL acesse esse [conteúdo] (https://app.betrybe.com/learn/course/5e938f69-6e32-43b3-9685-c936530fd326/module/94d0e996-1827-4fbc-bc24-c99fb592925b/section/2ed87e4f-9049-4314-8091-8f71b1925cf6/day/6b700197-22c6-4a2d-b791-b66d5247d3f0/lesson/d55e780a-a5a4-44a4-8d83-d73a2c99c691)):

```javascript
CREATE DATABASE IF NOT EXISTS books_api;

USE books_api;

CREATE TABLE IF NOT EXISTS books
(
  id INT NOT NULL AUTO_INCREMENT,
  title VARCHAR(30) NOT NULL,
  price DECIMAL(10, 2),
  author VARCHAR(100) NOT NULL,
  isbn VARCHAR(100),
  PRIMARY KEY(id)
);

INSERT INTO books (title, price, author, isbn)
VALUES ('Código Limpo', 125.9, 'Robert C Martin', '8576082675'),
  ('Refatoração', 129.9, 'Martin Fowler', '8575227246'),
  ('Padrões de Projetos', 141.98, 'Erich Gamma', '8573076100');

```

## Configuração inicial do projeto

Execute os comandos abaixo para criar a base para um novo projeto em TypeScript:

```zsh
mkdir ts-with-mysql && cd ts-with-mysql 
npm init -y
npm install -D -E typescript@4.4.4 @tsconfig/node16@1.0.3 @types/node@16.18.23
touch tsconfig.json
```

Preencha o arquivo `tsconfig.json` com algumas configurações iniciais:

```javascript
// ./tsconfig.json
{
  "extends": "@tsconfig/node16/tsconfig.json",
  "compilerOptions": {
    "target": "es2016",                                 
    "module": "commonjs",
    "rootDir": "./",
    "outDir": "./dist",
    "preserveConstEnums": true,
    "esModuleInterop": true,
    "forceConsistentCasingInFileNames": true,
    "strict": true,
    "skipLibCheck": true
  }
}
```

Iniciaremos vendo como a lib `mysql2` utiliza o recurso de Generics em seus métodos. Para isso, vamos começar implementando nosso arquivo `connection.ts.`

> **Observação**: Lembre-se de criar o arquivo `.env` com os valores das variáveis de ambiente utilizadas no arquivo `models/connection.ts` e de instalar a biblioteca `mysql2` com `npm install mysql2@2.3`. Use esse ![conteúdo](https://app.betrybe.com/learn/course/5e938f69-6e32-43b3-9685-c936530fd326/module/94d0e996-1827-4fbc-bc24-c99fb592925b/section/2ed87e4f-9049-4314-8091-8f71b1925cf6/day/6b700197-22c6-4a2d-b791-b66d5247d3f0/lesson/aa97630a-167e-456b-b18f-bdc3019202b5) para lembrar como atribuir os valores correspondentes às variáveis de ambiente utilizadas pelo arquivo exemplificado abaixo.

```javascript
// ./models/connection.ts

import mysql from 'mysql2/promise';

export default mysql.createPool({
  host: process.env.DB_HOSTNAME,
  user: process.env.DB_USER,
  password: process.env.DB_PASSWORD,
  database: process.env.DB_DATABASE,
});
```

Agora, vamos ver como a função `connection.execute` que usamos para executar queries usa o recurso de Generics. Ao olhar para a sua definição podemos encontrar a seguinte assinatura:

```javascript
execute<
    T extends RowDataPacket[][] | RowDataPacket[] | OkPacket | OkPacket[] | ResultSetHeader
  >(
    sql: string,
    values: any | any[] | { [param: string]: any }
  ): Promise<[T, FieldPacket[]]>;
```

Vamos nos concentrar no generic utilizado na definição da função. O método `execute` pode receber qualquer tipo que estenda uma das seguintes interfaces:

 - RowDataPacket[][]
 - RowDataPacket[]
 - OkPacket
 - OkPacket[]
 - ResultSetHeader

Perceba que se quisermos atribuir um tipo genérico `T` a algum resultado de consulta, esse `T` precisará ser (ou herdar) algum dos 3 tipos esperados na assinatura do execute: `RowDataPacket`, `OkPacket` ou `ResultSetHeader`.

A título de exemplo, vamos fazer o seguinte trecho de código:

```javascript

// ./main.ts

import connection from './models/connection';

const main = async () => {
  const result = await connection.execute('SELECT * FROM books');
  const [rows] = result;
  console.log(rows);
};

main();

```

Note que mesmo sem especificar nenhuma tipagem, o TypeScript não reclama do código. Isso acontece, pois para todos os tipos possíveis de retorno para `connection.execute`, por padrão, pode-se extrair um elemento do array.

Agora, vamos ver o que aconteceria se você tentasse fazer uma query do tipo `INSERT` e extrair o `insertId`:

Observação: Para executar o exemplo a seguir instale a biblioteca `readline-sync`.

```zsh
npm i readline-sync@1.4 @types/readline-sync@1.4

```

```javascript
// ./execute.insert.ts

import readline from 'readline-sync';
import connection from './models/connection';

const main = async () => {
  const title = readline.question('Digite o nome do livro: ');
  const price = readline.questionFloat('Digite o preço do livro: ');
  const author = readline.question('Digite o autor do livro: ');
  const isbn = readline.question('Digite o isbn do livro: ');

  const [{ insertId }] = await connection.execute(
    'INSERT INTO books (title, price, author, isbn) VALUES (?, ?, ?, ?)',
    [title, price, author, isbn]
  );
  console.log(insertId);
};

main();
```

Você vai perceber que seu código não pode ser compilado, pois o TypeScript não consegue identificar a origem do atributo `insertId`. O erro encontrado será:

> Property ‘insertId’ does not exist on type ‘RowDataPacket[] | RowDataPacket[][] | OkPacket | OkPacket[] | ResultSetHeader’.

Porém na própria lib `mysql2` temos uma interface que possui esse atributo, que é `ResultSetHeader`. Ao passar essa interface como generic para `connection.execute`, você vai perceber que a linha que extrai o atributo `insertId` passa a ser compilável.

```javascript
// ./execute.insert.ts

// import readline from  'readline-sync';
import { ResultSetHeader } from 'mysql2';
// import connection  from './models/connection';

// const main = async () => {
//   const title = readline.question('Digite o nome do livro: ');
//   const price = readline.questionFloat('Digite o preço do livro: ');
//   const author = readline.question('Digite o autor do livro: ');
//   const isbn = readline.question('Digite o isbn do livro: ');

const [{ insertId }] = await connection.execute<ResultSetHeader>(
  'INSERT INTO books (title, price, author, isbn) VALUES (?, ?, ?, ?)',
  [title, price, author, isbn]
); // essa linha não acusa mais erro de compilação.
//  console.log(insertId);
// }
//
// main();
```

Este é um primeiro exemplo do uso de Generics no dia a dia que já podemos encontrar. Com base nisso, vamos implementar nosso modelo.

## Implementando um model como uma classe

Para este exemplo, criaremos nosso modelo como uma classe que vai possuir o atributo `connection`. Esta classe também terá o método `getAll` que irá retornar o resultados da query.

```javascript
// ./models/Book.ts

import { Pool } from 'mysql2/promise';
import connection from './connection';

export default class BookModel {
  connection: Pool;

  constructor() {
    this.connection = connection;
  }

  async getAll() {
    const result = await this.connection.execute('SELECT * FROM books');
    const [rows] = result;
    return rows;
  }
}
```

Dessa forma, podemos usar esse modelo para ser nossa fonte de acesso aos dados. Vamos instanciar um objeto dessa classe e chamá-lo no nosso arquivo `main.ts`.

```javascript
// ./main.ts

import BookModel from './models/Book';

const main = async () => {
  const bookModel = new BookModel();

  const books = await bookModel.getAll();
  console.log(books);
};

main();
```

Apesar do código acima retornar resultados, não temos uma previsibilidade sobre o tipo desses dados. Para resolver isso podemos tentar aplicar duas formas de tipagens que já aprendemos: *Type Assertions e Generics*. Ambas as formas devem atender nosso objetivo que é mapear as propriedades do resultado que a query trará. Mas antes, vamos começar definindo uma interface que represente a entidade `Book` e que poderá ser utilizado em ambas alternativas de tipagem.

```javascript
// ./models/Book.ts

// import { Pool } from 'mysql2/promise';
// import connection from './connection';

export interface Book {
  id?: number;
  title: string;
  price: number;
  author: string;
  isbn: string;
}

// export default class BookModel {
//   connection: Pool;

//   constructor(){
//     this.connection = connection;
//   }

//   async getAll() {
//     const result = await this.connection.execute('SELECT * FROM books');
//     const [rows] = result;
//     return rows;
//   }
// }
```

Agora que já temos a interface, vamos precisar dizer ao Typescript que a nossa variável `rows` conterá um array de `Books` e para isso vamos usar *Type Assertions*. Podemos fazer da seguinte forma:

```javascript
// ./models/Book.ts

// import { Pool } from 'mysql2/promise';
// import connection from './connection';

// export interface Book {
//   id?: number,
//   title: string,
//   price: number,
//   author: string,
//   isbn: string,
// }

export default class BookModel {
//   connection: Pool;

//   constructor(){
//     this.connection = connection;
//   }

  async getAll(): Promise<Book[]> {
    const result = await this.connection.execute('SELECT * FROM books');
    const [rows] = result;
    return rows as Book[];
  }
}
```

Note que com essa estratégia conseguimos informar a qualquer função que utilizar o `getAll` que o resultado que será obtido no retorno será um array com a estrutura da interface `Books`.

Agora, como uma alternativa a *Type Assertions*, vamos tentar tipar utilizando o recurso *Generics*, e como foi comentado acima na parte da assinatura do método `execute`, para conseguir informar o tipo de retorno pelo parâmetro genérico é necessário enviar um tipo que herde pelo menos uma das três interfaces esperadas.

Trazendo para nosso cenário, se quisermos mapear o resultado da `query` para que tenha as propriedades da interface `Book`, então devemos enviar como parâmetro a interface `Book`, herdando o tipo `RowDataPacket` que é a interface genérica que devemos utilizar quando realizamos queries de `SELECT`. A tipagem ficará assim:

```javascript
// ./models/Book.ts

import { Pool, RowDataPacket } from 'mysql2/promise';
// import connection from './connection';

// export interface Book {
//   id?: number,
//   title: string,
//   price: number,
//   author: string,
//   isbn: string,
// }

export default class BookModel {
  // connection: Pool;

  // constructor(){
  //   this.connection = connection;
  // }

  async getAll(): Promise<Book[]> {
    const [rows] = await this.connection.execute<(Book & RowDataPacket)[]>(
      'SELECT * FROM books');

    return rows;
  }
}
```

Note que utilizando `Generics` nós conseguimos realizar a tipagem de maneira antecipada. Na mesma linha onde chamamos o execute já é possível saber todas as propriedades da variável `rows`. Já no *Type Assertion*, tivemos que desestruturar o array para conseguir atribuir o tipo. Mas vale reforçar que, para esse caso, ambas as alternativas são válidas pois atendem nosso objetivo.

## Método create

Vamos implementar agora o método `create` com base no que vimos anteriormente.

```javascript
// ./models/Book.ts

import { Pool, RowDataPacket, ResultSetHeader } from 'mysql2/promise';
// import connection from './connection';

// export interface Book {
//   id?: number,
//   title: string,
//   price: number,
//   author: string,
//   isbn: string,
// }

// export default class BookModel {

// connection: Pool;

// constructor(){
//   this.connection = connection;
// }

//   async getAll(): Promise<Book[]> {
//     const [rows] = await this.connection.execute<(Book & RowDataPacket)[]>('SELECT * FROM books');

//     return rows;
//   }

  async create(book: Book): Promise<Book> {
    const { title, price, author, isbn } = book;

    const [{ insertId }] = await this.connection.execute<ResultSetHeader>(
        'INSERT INTO books (title, price, author, isbn) VALUES (?, ?, ?, ?)',
        [title, price, author, isbn],
    );

    return { id: insertId, ...book };
  }

// }

```

Perceba que recebemos um objeto do tipo `Book` como parâmetro e usamos essa informação para salvar os valores no banco.

Podemos usar o código abaixo para ler valores e cadastrar um livro através do método `create` do nosso modelo.

```javascript
// ./main.ts

import readline from 'readline-sync';

import BookModel, { Book } from './models/Book';

const main = async () => {
  const bookModel = new BookModel();

  const title = readline.question('Digite o título do livro: ');
  const price = readline.questionFloat('Digite o preço do livro: ');
  const author = readline.question('Digite o autor do livro: ');
  const isbn = readline.question('Digite o isbn do livro: ');

  const newBook: Book = { title, price, author, isbn };

  const createdBook = await bookModel.create(newBook);
  console.log(createdBook);
};

main();
```

Com isso temos um primeiro modelo criado.