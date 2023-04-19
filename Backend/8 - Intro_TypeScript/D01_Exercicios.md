# Exercícios - agora, a prática

Antes de começar, crie uma pasta e, dentro dela, crie um pacote Node.js com o (npm init) chamado (my-ts-scripts). Realize os exercícios dentro desse pacote.

## Configuração Inicial

```
mkdir my-ts-scripts && cd my-ts-scripts

```

```
npm init -y

```

```
npm install -D -E @tsconfig/node16@1.0.3 @types/node@16.18.23 typescript@4.4.4

```

```
touch tsconfig.json

```

```javascript
// ./tsconfig.json
{
  "extends": "@tsconfig/node16/tsconfig.json", // estendemos a configuração base para o Node 16
  "compilerOptions": {
    "outDir": "./dist" // pasta onde nossos arquivos compilados serão salvos
  }
}

```

## Exercício 1

Temos uma API que começou a ter diversos erros e apresentar bugs frequentes. Como solução, o CTO do time, avaliou que utilizar o Typescript em suas funções, diminuiria um pouco desses problemas.

Para isso você foi direcionado a modificar as funções abaixo, escritas em Javascript, para que fossem tipadas e executassem sem erros no compilador de Typescript:

Observação: Não é necessário alterar o valor dos parâmetros passados.

Dica: utilize o Typescript playground para testar o comportamento de cada função.

### Função 1

```javascript
const numberInput = 7;

const isItAPrime = (param) => {
  for (let i = 2; i < param; i++)
    if (param % i === 0) {
      return false;
    }
  return param > 1;
};

isItAPrime(numberInput)
  ? console.log(`${numberInput} é primo`)
  : console.log(`${numberInput} não é primo`);

```

### Função 2

```javascript
// Essa função é responsável por validar se o formato do e-mail está correto.

const emailInput = 'email@email.com';

const validateEmailFormat = (param) => {
  var re = /\S+@\S+\.\S+/;
  return re.test(param);
};

console.log(validateEmailFormat(emailInput))

```

### Função 3

```javascript
// Essa função recebe uma lista e ordena seu conteúdo de forma crescente.

const numberList = [10, 5, 18, 2, 8, 23];

const sortInput = (param) => {
  return param.sort(function(a, b){return a-b});
};

console.log(sortInput(numberList));

```


### Função 4

Dica: leia a [documentação](https://www.typescriptlang.org/docs/handbook/2/objects.html)

```javascript
// Essa função é responsável por receber um objeto e formar uma frase utilizando as chaves do mesmo.
const peopleInput = {
  name: 'Rui',
  age: 23,
};

const createSimpleSentence = (param) => {
  return `Olá, meu nome é ${param.name} e tenho ${param.age} anos.`;
}

console.log(createSimpleSentence(peopleInput));

```

### Função 5
**Dica**: essa função poderá receber um parâmetro com dois tipos diferentes.

```javascript
// Essa é uma função que verifica se a idade passada é maior ou menor de 18 anos.
const ageInput = 15;

const isOfLegalAge = (param) => {
  return !!param
}

ageInput >= 18
  ? console.log(isOfLegalAge('true'))
  : console.log(isOfLegalAge(false));

```
## Exercício 2

Crie um script para converter unidades de medida de comprimento:

1 - Esse script deverá se chamar length.ts;
2 - Ele deverá possuir uma função chamada convert que recebe como parâmetro:
 - valor - number
 - unidade base - string
 - unidade para a conversão - string

**Tabela de conversão:**

**Nome** |	**Símbolo** |	**Valor**
---------|--------------|-----------
Quilômetro |	km |	1000m
Hectômetro |  hm |	100m
Decâmetro |	dam |	10m
Metro |	m |	1m
Decímetro |	dm |	0,1m
Centímetro |	cm |	0,01m
Milímetro | mm |	0,001m

