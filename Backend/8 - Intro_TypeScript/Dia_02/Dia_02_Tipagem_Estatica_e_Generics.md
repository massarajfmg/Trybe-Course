
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

```zsh
npm i express@4.17.1 mysql2@2.3.3 --save-exact
```

A novidade aqui está no módulo (ou drive) **mysql2**, responsável por permitir que uma aplicação **Node.js** consiga comunicar-se com o MySQL. Comumente chamamos esse tipo de biblioteca (que permite nossa aplicação conversar com banco de dados) de **client**, o qual possui todo o código necessário para enviarmos comandos SQL para o nosso banco de dados, no caso o MySQL, e recebermos as respostas dos comandos enviados.

Precisaremos criar em nossa aplicação o arquivo `src/db/connection.js`, que será responsável por realizar a conexão com o servidor MySQL utilizando a biblioteca `mysql2`:

```javascript
// src/db/connection.js

const mysql = require('mysql2/promise');

const connection = mysql.createPool({
  host: 'localhost',
  port: 33060,
  user: 'root',
  password: 'root',
  database: 'trybecashdb',
  waitForConnections: true,
  connectionLimit: 10,
  queueLimit: 0,
});

module.exports = connection;
```

No trecho de código acima estamos importando a biblioteca **mysql2** com o recurso de `promises`. Isso permitirá utilizar o MySQL de forma assíncrona com **async/await**. Em seguida, criamos uma constante `connection` que recebe um `pool de conexões` criado com a função **createPool**.

Um `pool de conexões` é um repositório que contém um conjunto de conexões estabelecidas previamente com o banco de dados. Essas conexões serão reutilizadas durante a execução da aplicação conforme a necessidade. Em outras palavras, quando uma operação no banco de dados for necessária nossa aplicação irá:

 1. Requisitar uma conexão no pool de conexões;
 2. Utilizar essa conexão para enviar uma operação SQL ao servidor MySQL;
 3. Devolver a conexão para o pool de conexões ao final da operação com o MySQL;
 4. Tornar a conexão disponível para ser utilizada em requisições futuras.

O diagrama abaixo mostra de forma visual a interação entre uma aplicação Node.js, o pool de conexões e o servidor MySQL.

![Diagrama de interação entre Node.js, o pool de conexões e o servidor MySQL](https://content-assets.betrybe.com/prod/Diagrama%20de%20intera%C3%A7%C3%A3o%20entre%20Nodejs%20o%20pool%20de%20conex%C3%B5es%20e%20o%20servidor%20MySQL.png)

O uso do `pool` de conexões é encorajado, pois sem ele, para cada operação com o *MySQL* uma conexão seria aberta e, após seu uso, seria fechada. Assim, seria necessário abrir novamente uma nova conexão com o *MySQL* para executar uma nova operação. E abrir uma nova conexão com o *MySQL* demanda tempo, adicionando um atraso para cada requisição da *API* como consequência.

Logo, o uso de um `pool` de conexões acelera o processo de execução de consultas no *MySQL*, pois reutiliza as conexões em operações futuras, não precisando criar uma nova conexão a cada operação.

A função **createPool** recebe um objeto com os seguintes parâmetros:

**Parâmetro** | **Descrição** | **Observações**
--------------|---------------|-----------------
**host** | O endereço IP do MySQL |	Como temos um container `docker` sendo executado em nossa máquina local, o valor será **localhost** ou **127.0.0.1** (ambos são equivalentes)
**user** | O nome de usuário que nossa aplicação utilizará para acessar o *MySQL* |	Estamos utilizando o usuário **root** do *MySQL*
**port** | O número da porta que nossa aplicação utilizará para acessar o *MySQL* |	Estamos utilizando a porta 33060 (a porta do computador local que vinculamos com o container no `docker compose`)
**password** | A senha do usuário que nossa aplicação utilizará para acessar o *MySQL* | Estamos utilizando a senha **root** que foi definida na variável de ambiente **MYSQL_ROOT_PASSWORD** no `docker compose` criado anteriormente
**database** | O nome do banco de dados *MySQL*, o qual queremos que nossa aplicação realize uma conexão | Estamos utilizando o nome do banco que foi definido na variável de ambiente **MYSQL_DATABASE** no `docker compose`
**waitForConnections** | Determina qual será a ação da `pool` de conexões quando nenhuma conexão estiver disponível na `pool` e quando o limite de criação de novas conexões tiver sido alcançado | Se o valor for `true`, será criada uma fila de espera por conexões, caso contrário a `pool` retornará uma *callback* com um erro. Caso este parâmetro seja omitido, o valor padrão será **true**
**connectionLimit** | O número máximo de requisições de conexão que a `pool` criará de uma vez | Caso este parâmetro seja omitido, o valor padrão será **10**
**queueLimit** | O número máximo de requisições de conexão que a `pool` irá enfileirar antes de retornar um erro |  Se o valor deste parâmetro for igual a **0** significa que não existe limite. Caso este parâmetro seja omitido, o valor padrão será **0**

Agora que o conceito de `pool` de conexões foi explicado e o arquivo `connection.js` foi criado, está na hora de configurarmos o `express` no projeto e testarmos se ele consegue se comunicar com o MySQL. Para isso, vamos criar o arquivo `src/app.js` com o seguinte conteúdo:

```javascript
// src/app.js

const express = require('express');

const app = express();

app.use(express.json());

module.exports = app;
```

No código acima estamos criando as definições do `express`. Vale ressaltar que a função `app.listen()` não está sendo executada no arquivo `src/app.js`. Contudo, estamos realizando um `module.exports` na constante `app` que inicializa o express e registra os `middlewares` que serão utilizados inicialmente.

A razão disso é que quando formos escrever nossos testes de integração, a definição de inicialização, rotas e `middlewares` do express, devem estar separadas da inicialização dele. Isso nos permitirá criar um `mock` das nossas rotas facilitando o processo de testar nossa API.

🤔 Você deve estar se perguntando: *“onde realizaremos a chamada da função `app.listen()` necessária para inicializar o express?”* Nesse ponto entra o nosso arquivo `src/server.js`, no qual adicionaremos o seguinte conteúdo:

```javascript
// src/server.js
const app = require('./app');
const connection = require('./db/connection');

const PORT = 3001;

app.listen(PORT, async () => {
  console.log(`API TrybeCash está sendo executada na porta ${PORT}`);

  // O código abaixo é para testarmos a comunicação com o MySQL
  const [result] = await connection.execute('SELECT 1');
  if (result) {
    console.log('MySQL connection OK');
  }
});
```

Acima, criamos uma constante `app` que importa o que foi definido no arquivo `src/app.js` e, a partir dessa constante, iniciamos o nosso express executando a função `app.listen().`

Dentro da função `app.listen()` foi adicionado um trecho de código que executa a função `connection.execute()`, que recebe como parâmetro uma consulta SQL `SELECT 1`. Essa função realiza uma conexão com o MySQL, executa o SQL passado como parâmetro e recebe uma resposta que é armazenada na constante `result` (note que o processo de desestruturação de variáveis está sendo utilizado! 😎).

Depois é verificado com um if se o objeto `result` contém alguma coisa e, em caso de positivo, é impresso no console a mensagem `MySQL connection OK`. Se você for no console e executar o comando `npm start`, o `express` será iniciado e apresentará a seguinte saída:

![Saída esperada ao inicializar o projeto.](https://content-assets.betrybe.com/prod/Sa%C3%ADda%20esperada%20ao%20inicializar%20o%20projeto.png)

Se você obteve na saída do terminal a mensagem `MySQL connection OK`, saiba que acabou de realizar a sua primeira conexão com o MySQL por meio do **Express**! Parabéns! 🎉 🥳 🎉

Pode parecer pouca coisa, mas não é! Você realizou toda a configuração necessária para que isso fosse possível e, a partir desse ponto, podemos criar funcionalidades mais complexas utilizando comandos SQL mais robustos!

Antes de avançarmos, vamos `refatorar` nosso arquivo `src/server.js` para retirar o código que utilizamos para testar se a comunicação com o MySQL estava ocorrendo, pois esse código não será mais útil para nós de agora em diante. O arquivo deverá estar assim:

```javascript
// src/server.js

const app = require('./app');

const PORT = 3001;

app.listen(PORT, () => {
  console.log(`API TrybeCash está sendo executada na porta ${PORT}`);
});
```

E nesse ponto teremos a seguinte estrutura de arquivos e diretórios no projeto:

```
.
└── trybecash-api/
    ├── src/
    │   ├── db/
    │   │   └── connection.js
    │   ├── app.js
    │   └── server.js
    ├── tests/
    │   └── -
    ├── docker-compose.yaml
    ├── Dockerfile
    ├── package.json
    └── trybecash_script.sql

```

E agora, a incrível produção cinematográfica Trybe Missions está de volta, dessa vez migrando os dados das missões para o MySQL utilizando Docker! 🚀

`Video do Course`

Caso queira, você pode ver o código SQL utilizado no `Trybe Missions` logo abaixo! 😉

```javascript
DROP DATABASE IF EXISTS trybestrelar;

CREATE DATABASE trybestrelar;

USE trybestrelar;

CREATE TABLE
    missions (
        id INT NOT NULL AUTO_INCREMENT,
        name VARCHAR(90) NOT NULL,
        year VARCHAR(45) NOT NULL,
        country VARCHAR(90) NOT NULL,
        destination VARCHAR(90) NOT NULL,
        PRIMARY KEY(id)
    );

INSERT INTO missions 
    (`id`,`name`,`year`,`country`,`destination`) 
VALUES 
    (1,'Mariner 2','1962','Estados Unidos','Vênus'),
    (2,'Venera 4','1967','URSS','Vênus'),
    (3,'Mariner 5','1967','Estados Unidos','Vênus'),
    (4,'Apollo 11','1969','Estados Unidos','Lua'),
    (5,'Mariner 10','1973','Estados Unidos','Mercúrio e Vênus'),
    (6,'Voyager 1','1977','Estados Unidos','Espaço interestelar'),
    (7,'Venera 16','1983','URSS','Vênus'),
    (8,'Phobos 1','1988','URSS','Marte'),
    (9,'Phobos 2','1988','URSS','Marte'),
    (10,'Galileo','1989','Estados Unidos','Júpiter'),
    (11,'Mars Pathfinder','1996','Estados Unidos','Marte'),
    (12,'Cassini-Huygens','1997','Estados Unidos e Europa','Saturno'),
    (13,'Nozomi (Planeta B)','1998','Japão','Marte'),
    (14,'Estação Internacional Espacial','1998','Estados Unidos e Rússia','Órbita terrestre'),
    (15,'Mars Polar Lander','1999','Estados Unidos','Marte'),
    (16,'2001 Mars Odyssey','2001','Estados Unidos','Marte'),
    (17,'Genesis','2001','Estados Unidos','Terra'),
    (18,'MESSENGER','2004','Estados Unidos','Mercúrio'),
    (19,'Telescópio Espacial Kepler','2009','Estados Unidos','Espaço interestelar'),
    (20,'Telescópio Espacial James Webb','2021','Estados Unidos, União Europeia e Canadá','Espaço interestelar');

```


