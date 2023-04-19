# Introdução - TypeScript

## O que vamos aprender?

Aqui você vai aprender sobre a linguagem de programação TypeScript, sua importância e os contextos em que ela pode ser aplicada.

Você também vai entender a relação que o TypeScript tem com JavaScript e quais são os “superpoderes” que ele adiciona à linguagem com a qual estamos trabalhando desde o início da nossa jornada.

# Introdução

## O que vamos aprender?

Hoje vamos conhecer o **TypeScript**, que é um superset para o **JavaScript**, por que esse superset foi criado, onde é utilizado e por que tem se tornado cada vez mais relevante no mundo da programação.

## Você será capaz de:

Definir o que é o superset **TypeScript**;
Compreender a relação entre o **TypeScript** e o **JavaScript**;
Compreender o que é Tipagem (Dicas de tipo);
Compreender a diferença entre Compilador e Transpilador;
Compilar o seu código **TypeScript** em código **JavaScript**;
Compreender o sistema de tipos do **TypeScript**; e
Declarar variáveis de tipos primitivos do **TypeScript**.

## Por que isso é importante?

Você pode estar se perguntando: “Poxa! Mais uma linguagem de programação?” 🤔

Realmente, aprender uma nova linguagem de programação é sempre um desafio. No entanto, aumenta nosso poder de escolha como pessoas desenvolvedoras e ajuda a tomar decisões mais assertivas na hora de desenvolver nossos programas.

Talvez você já tenha ouvido no mundo da programação a seguinte expressão: **“Não existe bala de prata.”** — que nesse contexto quer dizer que não existe uma tecnologia, linguagem ou ferramenta que resolva, principalmente de forma ótima, todos os problemas na computação. É por isso que existem tantas linguagens, ferramentas e bibliotecas nesse mundo enorme e em constante expansão que é o da tecnologia.

Ao aprender **TypeScript** você expandirá sua árvore de habilidades como pessoa desenvolvedora😉.

Além de ela estar presente em inúmeras ferramentas e frameworks do mercado como: *Jest, Redux, Deno, Vercel, Yarn, GitHub Desktop*, etc, também tem sido adotada por muitas empresas, incluindo grandes players como: Slack, Airbnb e Google. O TypeScript foi desenvolvido por ninguém mais ninguém menos que a **Microsoft**😱.

Ela pode ser usada tanto no Front-End quanto no Back-End e no ano de 2022 foi uma das tecnologias mais populares de acordo com o Stack Overflow de acordo com uma pesquisa feita pelo site.

Aposto que você ficou se perguntando, mas o que tem de diferente entre o **JavaScript** e o **TypeScript**?

A diferença mais evidente à primeira vista, é que agora fazemos a tipagem estática de variáveis. Um bom exemplo seria uma função que faz alguma operação matemática e deve receber duas variáveis do tipo *number*. No **JavaScript** puro se você passar uma dessas variáveis como *string*, só descobrirá o erro quando executar o código, já com o **TypeScript** o erro de tipagem é detectado no momento da transpilação.

Pense como é maravilhoso para você, pessoa desenvolvedora, perceber que algo não vai funcionar antes de executar, isso evita erros simples que podem nos tomar muito tempo. 😉

O **TypeScript** tem muito mais recursos além da tipagem estática como *interfaces, types*, e modificadores de acesso (veremos mais sobre isso nas seções à frente). Agora que já sabemos algumas das vantagens do **TypeScript**, vamos aprender mais sobre ele no conteúdo de hoje.

# Introdução (O que é TypeScript?)

**TypeScript** é uma linguagem de programação de código aberto desenvolvida pela *Microsoft*. Ela é um *superconjunto (superset) do JavaScript*, isso significa que você poderá continuar utilizando todo o conhecimento adquirido até agora em *JavaScript* para desenvolver em **TypeScript**. Isso é sensacional, não é? 🤓

Especificamente, o **TypeScript** é um superconjunto do *ECMAScript 2015*, mais comumente denominado *ECMAScript 6* ou *ES6*. Sendo assim, todo o código *JavaScript* também é código **TypeScript**, e um programa desenvolvido em **TypeScript** pode consumir o *JavaScript* de forma direta. É de explodir a mente! 🤯

## Por que a linguagem TypeScript foi criada?

*JavaScript* é, hoje, a linguagem oficial da Web, sendo utilizada para criar aplicações multiplataforma que rodam tanto no navegador quanto em servidores, e até mesmo em dispositivos mobile e IoT *(Internet of Things* - internet das coisas). No entanto, ela tem uma limitação: não foi concebida para a criação de aplicativos envolvendo milhares ou até mesmo milhões de linhas de código, pois ela não possui alguns dos recursos presentes em outras linguagens.

A linguagem **TypeScript** foi desenvolvida justamente para resolver as limitações do *JavaScript*, sem prejudicar sua capacidade de executar código em todas as plataformas.

# Tipagem (dicas de tipo)

O grande recurso do **TypeScript** é o sistema de tipos. Em **TypeScript** podemos identificar o tipo de dado em variáveis, parâmetros ou retornos de funções utilizando a tipagem.

Tipagem, também conhecida como dicas de tipos, é a forma que utilizamos para descrever de qual tipo será o valor de um componente do nosso código - por exemplo: variáveis, expressões, funções ou módulos. Isso proporciona uma melhor documentação do código e permite que o **TypeScript** valide se ele está funcionando da maneira correta.

Antes de avançarmos para como o **TypeScript** faz isso, vamos falar um pouco mais sobre tipagem em linguagens de programação.

Podemos categorizar a tipagem em uma linguagem de programação como:

## Tipagem Estática:

Não permite que a pessoa desenvolvedora altere o tipo após ele ser declarado e, geralmente, a verificação de tipo é feita em tempo de compilação.

✅ A tipagem utilizada na linguagem **TypeScript** tem essa característica e vamos aprender sobre o seu compilador mais à frente.

## Tipagem Dinâmica:

Está ligada à habilidade da linguagem de programação em “escolher o tipo de dado” de acordo com o valor atribuído à variável em tempo de execução - ou seja, de forma dinâmica.

❌ Não há essa característica na tipagem do **TypeScript**.

## Tipagem Forte:

Linguagens fortemente tipadas não realizam conversões automaticamente. Melhor dizendo, não é possível realizar operações entre valores de diferentes tipos, sendo necessário que a pessoa desenvolvedora faça a conversão para um dos tipos, caso seja possível.

✅ A tipagem utilizada na linguagem **TypeScript** também possui essa característica.

## Tipagem Fraca:

A tipagem fraca tem a característica da linguagem de realizar conversões automáticas entre tipos diferentes de dados - ou melhor, operações entre valores de tipos diferentes podem ocorrer sem a necessidade de uma conversão explícita de tipo. Porém, o resultado pode não ser o esperado e erros podem ocorrer durante a execução.

❌ Não há essa característica na tipagem do **TypeScript**.

![typescript](https://content-assets.betrybe.com/prod/Imagem%20que%20demonstra%20a%20tipagem%20do%20TypeScript.png)

Tipagem	 | Significado
---------|------------
Estática | Não permite que a pessoa desenvolvedora altere o tipo após ele ser declarado.
Dinâmica | A linguagem de programação “escolhe” o tipo de dado a partir do valor atribuído à variável em tempo de execução.
Fraca    | Tipagem fraca tem a característica da linguagem realizar conversões automáticas entre tipos diferentes de dados.
Forte    | Linguagens fortemente tipadas não realizam conversões automaticamente.

## Inferência de tipo:

Algumas linguagens com tipagem estática podem fazer a inferência de tipo na declaração de variáveis, mas sem permitir que o tipo seja alterado após a declaração.

O **TypeScript** é uma dessas linguagens. Podemos usar a inferência de tipo, mas o compilador apresenta um erro quando tentamos atribuir um valor de tipo diferente à variável. Isso porque ele apenas realiza a inferência do tipo inicial da variável. Depois disso, como a linguagem possui tipagem estática, não é possível alterar o tipo.

Então, **TypeScript** é uma linguagem fortemente tipada e estaticamente tipada que possui inferência de tipo. Veremos exemplos disso quando começarmos a escrever nossas primeiras linhas de código nas seções a seguir.

Antes disso, vamos falar sobre **Transpiladores** e **Compiladores**, e sobre o **TSC**, que é o compilador do **TypeScript**.

# Diferença entre Compilador e Transpilador

Um **Compilador** é um programa que traduz o código desenvolvido usando uma **linguagem de mais alto nível** (mais próxima dos seres humanos) em um código de um programa equivalente de uma linguagem de mais baixo nível (mais próxima do processador). Como exemplo temos o GCC da Linguagem **C** e o Javac da linguagem **Java**.

Um **Transpilador** é um programa de sistema que traduz o código desenvolvido utilizando uma **linguagem de mais alto nível** em um código de um programa equivalente de uma outra **linguagem de mais alto nível** ou em uma **versão diferente da mesma linguagem**. Como exemplo, temos o J2CL que transpila código na linguagem Java para a linguagem **JavaScript** ou o Babel que transpila código **EcmaScript 6** para **EcmaScript 5**.

Um **Transpilador** também é considerado por algumas pessoas como um tipo de **Compilador** que atua em um nível mais alto de abstração. Por isso, muitas vezes você verá pessoas dizendo que o **TypeScript** é uma linguagem transpilada por traduzir código **TypeScript** em código **JavaScript**, ambas linguagens de mais alto nível.

No entanto, o **Typescript** possui um Compilador denominado **TSC (TypeScript Compiler)**, que é responsável por fazer essa tradução. Além disso, a própria documentação da linguagem trata esse processo de tradução do código feito pelo **TSC** como compilação. Vamos estudar mais sobre ele na próxima seção.

![transpilador](https://content-assets.betrybe.com/prod/Imagem%20que%20demonstra%20a%20diferen%C3%A7a%20entre%20compilador%20e%20transpilador.png)

# TSC - TypeScript Compiler

O **TSC** é o responsável por realizar a tradução do nosso código **TypeScript** para código **JavaScript**.

Lembra que nas seções anteriores nós estudamos a tipagem em linguagens de programação e descobrimos que o **TypeScript** é uma linguagem estaticamente tipada e fortemente tipada? O TSC também é o responsável por realizar a verificação de tipo no nosso código TypeScript. Veremos como isso funciona.

Para isso, podemos instalar o **TSC** e o suporte ao **TypeScript** em nossa máquina. Há duas maneiras de instalar o **TSC**: localmente e globalmente. Esta última não é recomendável, pois fixa a versão do TypeScript em todos os projetos em que for utilizado.

Obs: para instalar o TSC globalmente basta executar o comando *npm install -g -E typescript@4.4.4.*

A melhor prática de utilização do **Typescript** em um projeto é instalá-lo como uma *devDependency* e utilizá-lo por meio do comando *npx*. Isso garante que toda vez que o projeto for compilado, será utilizada a mesma versão do TypeScript definida no *package.json*, e não a versão global instalada, que pode variar conforme o ambiente.

Para instalar o compilador TypeScript no seu projeto execute:

```
## Comando para instalar a dependência do typescript na node_modules do seu projeto
npm i -D -E typescript@4.4.4
```

Podemos gerar o código JavaScript de um arquivo TypeScript da seguinte forma:

```
npx tsc nomeDoArquivo.ts
```

OU caso tenha instalado globalmente:

```
tsc nomeDoArquivo.ts
```
**Obs**: A extensão **.ts** é a extensão padrão para os arquivos **TypeScript**.

Ao rodarmos esse comando, será verificado o conteúdo do arquivo *nomeDoArquivo.ts* e, caso nenhum problema seja encontrado, um novo arquivo será criado com o nome *nomeDoArquivo.js* e contendo o código compilado para **JavaScript**. A seguir, podemos rodar o arquivo **.js** gerado utilizando o *Node*. Caso haja erro, o compilador apontará uma mensagem de erro no terminal e o arquivo **.js** não será gerado.

Para rodar o arquivo gerado utilizando o *Node*:

```
node nomeDoArquivo.js
```
# Introdução ao TSConfig

O que define que um projeto é **TypeScript** é a presença de um arquivo de configuração **TSConfig**. O arquivo *tsconfig.json* possui as variáveis de configuração que definirão como o nosso código será compilado.

É possível criar manualmente o arquivo *tsconfig.json* ou, como boas pessoas desenvolvedoras que somos, podemos utilizar as ferramentas que a linguagem nos fornece para gerá-lo automaticamente, já com as principais configurações. Depois, podemos escolher quais queremos utilizar.

**OBS** Lembre-se que, independente da forma que criar o *tsconfig.json*, ele deve estar na raiz do seu projeto.

Para gerar o *tsconfig.json* vamos utilizar o *tsc*. Sim, a ferramenta de compilação da linguagem TypeScript também traz essa incrível funcionalidade.

Entre em um diretório vazio de sua escolha e execute um dos seguintes comandos no terminal.

Caso tenha instalado o compilador globalmente em sua máquina:

```
tsc --init
```

OU caso queira utilizar o *tsc* como um executável npx:

```
npx tsc --init
```

Um arquivo tsconfig.json será gerado no diretório com o seguinte conteúdo:

```
{
  "compilerOptions": {
    /* Visit https://aka.ms/tsconfig.json to read more about this file */

    /* Projects */
    [...]
    /* Language and Environment */
    "target": "es2016",                                  /* Set the JavaScript language version for emitted JavaScript and include
    [...]

    /* Modules */
    "module": "commonjs",                                /* Specify what module code is generated. */
    "rootDir": "./",                                     /* Specify the root folder within your source files. */
    [...]

    /* JavaScript Support */
    [...]

    /* Emit */
    "outDir": "./",                                      /* Specify an output folder for all emitted files. */
    [...]

    /* Interop Constraints */
    "esModuleInterop": true,                             /* Emit additional JavaScript to ease support for importing CommonJS modules.
    [...]

    /* Type Checking */
    "strict": true,                                      /* Enable all strict type-checking options. */
    [...]
  }
}
```

Veja que fantástico: o arquivo gerado traz as principais configurações e um comentário à frente de cada linha dizendo o que aquela configuração em específico faz e quais são os valores aceitos. Além disso, para fechar com chave de ouro, também traz uma URL explicando mais sobre o arquivo *tsconfig.json*.

Agora, vamos conhecer um pouco mais do que já vem configurado no arquivo *tsconfig.json* e o que precisamos configurar para criar nosso primeiro projeto em **Typescript**!

- **module**: especifica o sistema de módulo a ser utilizado no código JavaScript que será gerado pelo compilador como sendo o CommonJS;
- **target**: define a versão do JavaScript do código compilado como ES6;
- **rootDir**: define a localização raiz dos arquivos do projeto;
- **outDir**: define a pasta onde ficará nosso código compilado;
esModuleInterop: habilitamos essa opção para ser possível compilar módulos ES6 para módulos CommonJS;
- **strict**: habilitamos essa opção para ativar a verificação estrita de tipo;
- **include**: essa chave vai depois do objeto CompilerOptions e com ela conseguimos incluir na compilação os arquivos ou diretórios mencionados; e
- **exclude**: essa chave também vai depois do objeto CompilerOptions e com ela conseguimos excluir da compilação os arquivos mencionados.

Não vamos explicar cada uma das outras configurações. À medida que utilizarmos novas configurações, vamos falar sobre aquelas que escolhemos. Caso queira saber mais, é uma ótima oportunidade para exercitar a aprendizagem ativa acessando o link do arquivo😉.

Também podemos utilizar uma configuração base para o ambiente **JavaScript** (versão do *Node*) que estamos utilizando provida pela própria equipe de desenvolvimento do **TypeScript** por meio de um repositório no *GitHub*. Não existe uma versão base para todos os ambientes **JavaScript**, apenas para os mais recentes. Com *node*, é possível utilizar a partir da versão 12.

Por exemplo, se estivermos desenvolvendo um projeto que usará a versão 16 do *Node*, podemos utilizar o módulo base *@typescript/node16*.

```
npm i -D -E @tsconfig/node16@1.0.3
```

Então o *tsconfig.json* ficaria parecido com isso:

```
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
  },
  "include": ["src/**/*"], /* aqui estamos incluindo todos os arquivos dentro da pasta src */
  "exclude": ["node_modules", "**/*.spec.ts"] /* aqui estamos excluindo a pasta node_modules e os arquivos de teste */
}
```

Isso permite que nosso *tsconfig.json* concentre as configurações únicas para o nosso projeto, e não todas as configurações para o nosso ambiente de execução **JavaScript**.

# TypeScript Playground

Segundo o time desenvolvedor da ferramenta, o **TypeScript** **Playground** é um site feito para você escrever, compartilhar e aprender **TypeScript**.

Esse site possui vários recursos interessantes: nele, você pode ver exemplos de programas criados com **TypeScript**; testar os recursos mais novos do compilador; criar seus próprios programas e compartilhar a URL deles com outras pessoas. O melhor de tudo é que o *Playground* é um ambiente seguro de aprendizagem, sem o risco do seu código afetar alguma aplicação.

Você pode acessá-lo neste link.

![ts_playground](https://content-assets.betrybe.com/prod/Imagem%20que%20demonstra%20o%20site%20TypeScript%20Playground.png)

## Como utilizar o Playground

Na imagem acima podemos verificar que este ambiente apresenta, basicamente, os seguintes recursos, do lado esquerdo:

- O botão *v.4.4.2* para seleção da versão do TypeScript;
- O botão *Run* que irá transpilar, compilar e executar o código;
- Um painel para digitar o código em TypeScript.

E do lado direito temos:

- A guia *.JS* que apresenta o código transpilado para JavaScript;
- A guia *Erros* que exibe erros de sintaxe identificados pelo TypeScript;
- A guia *Logs* que mostra o resultado da execução do código, realizado pelo botão **Run**.

## Tipos e Subtipos

Vamos falar um pouco mais sobre o grande recurso do **TypeScript** em relação ao **JavaScript**: os tipos.

Em **TypeScript**, todos os tipos são subtipos de um tipo principal chamado [any], e este é um tipo que pode representar qualquer valor em **JavaScript**. Os demais tipos são os tipos primitivos, tipos de objeto ou parâmetros de tipo.

![any_types](https://content-assets.betrybe.com/prod/Imagem%20que%20demonstra%20a%20divis%C3%A3o%20de%20tipos%20na%20linguagem%20TypeScript.png)

## Tipos primitivos:

Hoje nós vamos focar em alguns dos tipos primitivos, que são os tipos (boolean), (number), (string), (void), (null) e (undefined).

**boolean**: recebe verdadeiro (true) ou falso (false)

```
let yes: boolean = true; // cria uma variável de nome "yes" e diz que o tipo é booleano e o valor é true
let no: boolean = false; // cria uma variável de nome "no" e diz que o tipo é booleano e o valor é false

```

**number**: recebe valores numéricos e, assim como no JavaScript, todos são valores de ponto flutuante.

```
// cria uma variável de nome "x" e diz que o tipo é number mas não seta o valor
// isso não funciona com const
let x: number;

let y: number = 0;
let z: number = 123.456;

```

**string**: recebe uma sequência de caracteres armazenados como unidades de código UTF-16 Unicode.

```
let s: string;
let empty: string = "";
let abc: string = 'abc';

```

**void**: existe apenas para indicar a ausência de um valor, como em uma função sem valor retornado.

```
function sayHelloWorld(): void {
  console.log("Hello World!");
}

```

**null** e **undefined**: são subtipos de todos os outros tipos.

```
let nullValue = null;
let undefinedValue = undefined;

```

## Exemplo de declaração de variáveis utilizando inferência de tipo

Como visto anteriormente, podemos utilizar a inferência de tipo no **TypeScript**. É possível declarar uma variável sem especificarmos explicitamente o tipo e o compilador fará a inferência do tipo por meio do valor definido para a variável. Vamos verificar isso no site do *Playground TypeScript*. Após digitar o código abaixo, clique no botão (Run) e, ao término da execução, será exibido o resultado na guia (Logs).

```
let flag = true; // o compilador irá inferir o tipo boolean
console.log('O tipo de "flag" é:', typeof flag);

const numberPI = 3.1416; // o compilador irá inferir o tipo number
console.log('O tipo de "numberPI" é:', typeof numberPI);

let message = "Hello World!"; // o compilador irá inferir o tipo string
console.log('O tipo de "message" é:', typeof message);

```

A imagem abaixo apresenta o resultado esperado.

![log_playground](https://content-assets.betrybe.com/prod/c7ac3605-f5ee-4669-a00b-6d1051e9d607-Verifica%C3%A7%C3%A3o%20de%20tipos%20no%20site%20TypeScript%20Playground.png)

