# Introdução ao Java

## Setup
- Java é uma linguagem compiladas, mas é necessário um ambiente próprio para execução.
- Algumas aplicações que são instalada no computador, obriga você a instalar o Java na sua máquina, como Minecraft, ou outros jogos, isso é chamado de JRE - Java Runtime Enviroment. Isso é apenas para a execução de uma aplicação.
- Para desenvolver aplicações Java, é necessário um kit de desenvolvimento conhecido como JDK - Java Development Kit.

### Instalação
- Acessar: [Link de downloads](https://www.oracle.com/java/technologies/downloads/)
- Instalação no linux
    - Através do terminal acessar a pasta onde foi instalado o .deb
    - Digitar o comando: `sudo dpkg -i <nome_arquivo>`
    - Verificar se o java foi instalado corretamente através do comando: `java --version`

### Primeiro comando java
- No terminal digitar o comando `jshell`
- `System.out.println("Hello world!");`
- Para sair do terminal `/exit`

## IDE - Integrated Development Environment
- A melhor ferramenta para desenvolvimento em Java atualmente, é o IntelliJ
- Acessar: [Link de download](https://www.jetbrains.com/idea/download/download-thanks.html?platform=linux)
- Instalação no Linux
    - Através do terminal acessar a pasta onde foi instalado o .tar.gz
    - Clicar duas vezes no executável, ele irá gerar uma pastinha descompactada
    - Clicar duas vezes na pasta, e duas vezes na próxima pasta, onde fica as pastas bin e o arquivo de instrução de instalação Install-Linux-tar.txt
    - Acessar essa pasta através do terminal e digitar o comando `cd bin`
    - Em seguida `./idea`
    - Irá aparecer uma interface gráfica de instalação como no windows, basta aceitar as condições e dar next.

## Primeiro projeto
- Ao finalizar a instalação clicar em New Project
- Não é necessário adicionar nenhuma configuração adicional, apenas nomear o projeto como `hello-word`
- Criar o mesmo programa que foi feito no jshell

  ```java
  void main() {
     IO.println(String.format("Hello world!"));
  }
```

- Depois disso, basta executar dar CTRL + F5 na aplicação, e irá aparecer a string "Hello world" no terminal

## Tutorial Java
- [Tutorial de Java](https://docs.oracle.com/javase/tutorial/index.html)
- [Índice](https://docs.oracle.com/javase/tutorial/reallybigindex.html)

## Variáveis
### Tipos primitivos
- O Java tem 8 tipos de dados primitivos: `byte, short, int, long, float, double, boolean e char`.
- `byte, short, int, long, float, e double` são tipos numéricos.
    - `byte, short, int e long` são tipos numéricos para números inteiros
    - A diferença entre eles é a capacidade de armazenamento.
        - `byte` é utilizado para variáveis com valor entre -128 e 127.
        - `short` é utilizado para variáveis com valor entre -32,768 e 32,767.
        - `int` é utilizado para variáveis com valor entre -2^31 e 2^31-1
        - `long` é utilizado para variáveis com valor entre -2^63 e 2^63-1
    - Ou seja se quiser declarar um número > 127 é necessário declarar short, e assim sucessivamente.
- Java é fortemente tipada, ou seja, todas as variáveis devem ser tipadas com algum dos tipos existentes.
- Na maioria das vezes utilizamos int, ele tem um intervalo de valor que abrange a maioria das situações.
- Para utilizar números decimais é necessário declarar como `float` ou `double`.
- `boolean` é utilizado para representar valores verdadeiros ou falsos.
- `char` é utilizado para representar um único caractere, seja número, letra ou qualquer outro tipo de caractere.

Exemplo de declaração e atribuição de variável:
```java
void main() {
    String name; // declaração de variável
    name = "Vitória"; // atribuição de variável
    name = "Brasil"; // reatribuição de variável (o valor anterior é descartado)
    IO.println(String.format("Hello " + name));

    // OUTPUT Hello Brasil
}
```

### Operadores aritméticos
`+` representa soma
`-` representa subtração
`*` representa multiplicação
`/` representa divisão

Exemplo de utilização de variáveis numéricas e operadores aritméticos
```java
void main() {
    int a;
    int b = 2; // é possível declarar e atribuir uma variável em uma única linha

    a = 3;

    int soma = a + b;
    int subtract = a - b;
    int multiplication = a * b;
    int divisor = a / b;

    IO.println(soma);
    IO.println(subtract);
    IO.println(multiplication);
    IO.println(divisor);

    // OUTPUT 5
    // OUTPUT 1
    // OUTPUT 6
    // OUTPUT 1
}
```

- Podemos notar que a divisão não retornou o valor correto, pois declaramos a variável `divisor` como `int`.
- `int` não retorna valores decimais, por esse motivo o programa arredonda automáticamente.
- Para receber o valor exato, devemos trocar o tipo para `float` ou `double`.
- Devemos levar em conta o comportamento do Java, não basta trocar apenas a variável `divisor` para `float`, é necessário trocar o tipo de todas as variáveis, inclusive as que estão realizando uma operação `soma/subtract/multiplication`.
    - Realizar essa mudança em uma aplicação de 20 linhas é simples, mas em uma aplicação maior seria inviável, para isso existe uma solução chamada `CAST`.
    - Então basta atribuir a variável `divisor` da seguinte forma `float divisor = (float) a / b;`

```java
void main() {
    int a;
    int b = 2; // é possível declarar e atribuir uma variável em uma única linha

    a = 3;

    int soma = a + b;
    int subtract = a - b;
    int multiplication = a * b;
    float divisor = (float) a / b; // mudança

    IO.println(soma);
    IO.println(subtract);
    IO.println(multiplication);
    IO.println(divisor);

    // OUTPUT 5 / 1 / 6 / 1.5
}
```  

## Operadores lógicos
- O tipo de dado `boolean` armazena valores lógicos ou seja `true` ou `false`.

### Tabela verdade
- Operador `&&` (AND) <br/>
  `true && true = true`<br/>
  `true && false = false`<br/>
  `false && true = false`<br/>
  `false && false = false`

- Operador `||` (OR) <br/>
  `true && true = true`<br/>
  `true && false = true`<br/>
  `false && true = true`<br/>
  `false && false = false`

## Estruturas condicionais

### `IF/ELSE`

A estrutura `if-else` permite tomar decisões baseadas em condições booleanas (true/false). O `if` executa um bloco de código se a condição for verdadeira, enquanto o `else` define um bloco alternativo para quando a condição for falsa. Para múltiplas condições, utiliza-se `else if`.

Exemplo de uso
```java
void main() {
    int nota = 70;

    if(nota >= 70) IO.println("Aluno aprovado");
    else IO.println("Não aprovado");

    // OUTPUT Aluno aprovado
}
```
### `SWITCH`
A estrutura `switch case` é uma alternativa eficiente aos múltiplos `if-else` para seleções baseadas no valor exato de uma variável (inteiros, strings, enums). Ela compara um valor com vários casos `case`, executando o código correspondente e usando `break` para finalizar, com `default` para valores não correspondidos.

Exemplo de uso

```java
void main() {
    String graduacao = "C";

    switch (graduacao){
        case "A":
        case "B":
            IO.println("Aluno aprovado!");
        case "C":
        case "D":
            IO.println("Aluno reprovado!");
        default:
            IO.println("Graduação inválida!");
    }

    // OUTPUT Aluno reprovado!
    // OUTPUT Graduação inválida!
}
```
Para parar assim que uma condição for verdadeira devemos utilizar o `break;`, caso contrário, o switch continua executando os próximos cases.

```java
void main() {
    String graduacao = "C";

    switch (graduacao){
        case "A":
        case "B":
            IO.println("Aluno aprovado!");
            break;
        case "C":
        case "D":
            IO.println("Aluno reprovado!");
            break;
        default:
            IO.println("Graduação inválida!");
    }

    // OUTPUT Aluno reprovado!
}
```

## Operador ternário

- Estrutura `condicao ? expressao1 : expressao2`.
- Ele funciona como um simplificador de if/else

Exemplo de uso
```java
void main() {
    boolean fimDeSemana = true;

    String mensagem = fimDeSemana ? "É fim de semana" : "Não é fim de semana"; // Se fim de semana for true irá aparecer "É fim de semana" caso contrário irá aparecer "Não é fim de semana"

    IO.println(mensagem);

    // OUTPUT É fim de semana
}
```

## Manipulação de String e Datas

```java
void main() {
  String nome = "Vitória";
  String outroNome = "Itália";

  IO.println(nome.toUpperCase()); // Deixa a variável nome em maiúsculo
  IO.println(nome.toLowerCase()); // Deixa a variável nome em minúsculo
  IO.println(nome.length()); // Conta a quantidade de caracteres

  IO.println(nome.equals(outroNome)); // Verifica se a variável nome é igual a variável outro nome considerando o case
  IO.println(nome.equalsIgnoreCase(outroNome)); // Verifica se a variável nome é igual a variável outro nome desconsiderando o case
}
```

Construindo a string `Olá, {nome}. Hoje é {dia-da-semana}, BOM DIA.`

```java
void main() {
  String saudacao;
  String nome = "Vitória";

  LocalDate hoje = LocalDate.now();
  Locale brasil = new Locale("pt", "BR");
  String diaSemana = hoje.getDayOfWeek().getDisplayName(TextStyle.Full, brasil);

  LocalDateTime agora = LocalDateTime.now();
  int horaAtual = agora.getHour();

  if (horaAtual >= 0 && horaAtual < 12)
    saudacao = "bom dia";
  else if (horaAtual >= 12 && horaAtual < 18)
    saudacao = "boa tarde";
  else if (horaAtual >= 18 && horaAtual < 24)
    saudacao = "boa noite";
  else
    saudacao = "horário inválido!";

  // concatenação de string
  System.out.printf("Olá, %s. Hoje é %s, %s.%n", nome, diaSemana, saudacao.toLowerCase());
}
```

## Laços numéricos

Laços numéricos (for, while, do-while) são estruturas fundamentais para repetir blocos de código com base em contadores numéricos ou condições booleanas. O for é ideal para um número definido de repetições, enquanto while e do-while são usados quando a condição de término é dinâmica ou incerta.

```java
void main() {
  for (int i = 0; i <= 10; i++){
    System.out.printf(i);
  }

  // OUTPUT 1 / 2 / 3 / 4 / 5 / 6 / 7 / 8 / 9 / 10
}  
```

## Vetores

Um vetor (ou array unidimensional) é uma estrutura de dados que armazena uma coleção sequencial de elementos do mesmo tipo (homogêneos), ocupando posições contíguas na memória. Ele permite acessar cada valor individualmente por meio de um índice numérico, começando em 0.
- No Java não é permitido misturar tipos em um mesmo array.
- Os arrays tem tamanho imutável, portanto ao definir um tamanho, não é possível redefinir, como também não é permitido adicionar mais elementos do que foi predefinido inicialmente.

```java
void main() {
    int [] numeros = new int[5];

    numeros[0] = 1;
    numeros[1] = 2;
    numeros[2] = 3;
    numeros[3] = 4;
    numeros[4] = 5;

    System.out.println(numeros);

    // OUTPUT [I@54bedef2

    // Interpretação
    // [ - É um array
    // I - É um array de inteiros
    // @54bedef2 - É a posição de memória onde está armazenado o array
}
```

### Manipulação de Arrays

```java
void main() {
    int [] numeros = new int[5];

    numeros[0] = 1;
    numeros[1] = 2;
    numeros[2] = 3;
    numeros[3] = 4;
    numeros[4] = 5;

    for (int i = 0; i < numeros.length; i++){
        System.out.println(numeros[i]);
    }

    // OUTPUT 1 / 2 / 3 / 4 / 5
}
```
- Não é necessário passar por um laço, o Java possui uma propriedade para realizar essa manipulação.
```java
void main() {
    int [] numeros = new int[5];

    numeros[0] = 1;
    numeros[1] = 2;
    numeros[2] = 3;
    numeros[3] = 4;
    numeros[4] = 5;

    System.out.println(Arrays.toString(numeros));

    // OUTPUT [1 / 2 / 3 / 4 / 5]
}
```
#### Descobrindo o maior, menor e a média de valores de um Array
```java
void main() {
    int [] numeros = { 9, 10, 12, 25, 2};

    int maior = numeros[0];
    int menor = numeros[0];
    int media = 0;

    for (int i = 0; i < numeros.length; i++){
        if(numeros[i] > maior)
            maior = numeros[i];

        if(numeros[i] < menor)
            menor = numeros[i];

        media += numeros[i];
    }

    System.out.println("Maior: " + maior );
    System.out.println("Menor: " + menor );
    System.out.println("Média: " + media/numeros.length );

// OUTPUT 25 / 2 / 11
}
```
## Funções
Uma função em programação é um bloco de código reutilizável, projetado para realizar uma tarefa específica, permitindo organizar, modularizar e evitar repetições no desenvolvimento de software. Ela pode receber dados de entrada (parâmetros), processá-los e retornar um resultado. Funções facilitam a manutenção e a legibilidade, dividindo sistemas complexos em partes menores.

```java
void main() {
    String nome = "Vitória";
    saudacao(nome);
}

public static void saudacao(String nome){
    System.out.println("Hello " + nome + "!");
}

// OUTPUT Hello Vitória!
```

- Nesse exemplo, não retornamos nada, por esse motivo o retorno é tipado como `void`

#### Exemplo de função que retorna um valor inteiro
```java
void main() {
    int result = soma(2,3);

    System.out.println(result);
}

public static int soma(int n1 , int n2){
    return n1 + n2;
}

// OUTPUT = 5
```


## Convenções Java
- Para nome de variáveis deve ser utilizado o padrão `camelCase`

## Atalhos IntelliJ
- `CTRL + F5` executa uma aplicação
- `sout` é um autocomplete para `System.out.println();`

