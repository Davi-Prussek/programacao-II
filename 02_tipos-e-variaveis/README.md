# Tipos e Variáveis em TypeScript

Este guia apresenta os principais tipos de dados e como declarar variáveis em TypeScript.  
Ele serve como base para você escrever código seguro e organizado, evitando erros comuns de JavaScript.

---

## 1. Variáveis

Em TypeScript (assim como em JavaScript moderno), usamos **`let`**, **`const`** e **`var`** (não recomendado).  

- `let` → variável que pode ser reatribuída  
- `const` → variável que não pode ser reatribuída  
- `var` → não recomendado (escopo confuso)  

Exemplo:

```ts
let idade: number = 17;  // pode mudar
idade = 18;

const nome: string = "Joao"; // não pode mudar
// nome = "Ana";             // Erro de compilação
```

---

## 2. Tipos Primitivos

No TypeScript você consegue declarar o tipo de uma variável, e os tipos existentes são:

- **string** → texto/escrita

- **number** → números (inteiros ou decimais)

- **boolean** → true ou false

- **any** → aceita qualquer valor (não recomendado, pois ignora a verificação de tipos)

- **unknown** → aceita qualquer valor, mas precisa de verificação antes de usar

```ts
let nome: string = "Joao"; // A variável nome foi tipada para ser uma string
//nome = 123;              // Erro de compilação


let idade: number = 17; // A variável idade foi tipada para ser um number
//idade = "17";         // Erro de compilação


let ativo: boolean = true; // A variável ativo foi tipada para ser um boolean
//ativo = "ligado"         // Erro de compilação


let qualquerCoisa: any = "teste"; // A variável qualquerCoisa foi tipada como any
qualquerCoisa = "123";
qualquerCoisa = 123;
qualquerCoisa = true;
// Todas essas opções são aceitáveis, pois o tipo any aceita todos tipos de dados
```

---

## 3. Tipos compostos (básicos)

Tipos compostos são estruturas que já existiam no JavaScript e aqui no TypeScript receberam tipagem, como arrays, objetos e funções.

### **arrays:**

Os arrays no TypeScript funcionam de forma parecida com o JavaScript, porém com uma diferença importante: **é necessário definir o tipo dos valores que o array pode armazenar**.

### number[ ]

Um array que aceita apenas valores do tipo number.

```ts
let listaCoisas1: number[] = [1,2,3,4,5]; 
```

> O TypeScript entende que esse array só pode conter valores do tipo number e dá erro caso tente adicionar valores de outros tipos, por exemplo:

```ts 
// listaCoisas1.push(6)   // Permitido
// listaCoisas1.push("6") // Erro de compilação
```

### string[ ]

Um array que aceita apenas valores do tipo string.

```ts
let listaCoisas2: string[] = ["carro","moto","aviao"]; 
```

> O TypeScript entende que esse array só pode conter valores do tipo string e dá erro caso tente adicionar valores de outros tipos, por exemplo:

```ts 
// listaCoisas2.push("submarino") // Permitido
// listaCoisas2.push(678)         // Erro de compilação
```

### boolean[ ]

Um array que aceita apenas valores do tipo boolean.

```ts
let listaCoisas3: boolean[] = [true, false, false]; 
```

> O TypeScript entende que esse array só pode conter valores do tipo boolean e dá erro caso tente adicionar valores de outros tipos, por exemplo:

```ts 
// listaCoisas3.push(false) // Permitido
// listaCoisas3.push(12)    // Erro de compilação
```

#

### Observação importante

> O TypeScript não permite misturar tipos diferentes dentro do mesmo array, a menos que isso seja declarado explicitamente (veremos isso mais adiante).

#

## objetos: 

Os objetos no TypeScript funcionam de forma parecida com o JavaScript, porém com uma diferença importante: **é necessário definir o tipo de cada propriedade do objeto.**

```ts
const objetoQualquer: {nome: string; idade: number} = {
nome: "Joao",
idade: 17,
};
```

---

## 4. Inferência de Tipos

A inferência de tipos é quando o TypeScript descobre sozinho qual é o tipo de uma variável, sem você precisar escrever : number, : string, etc.

### Exemplos:

# 

Com tipagem clara:

```ts
let idade: number = 17;
```

Com inferência:

```ts
let idade = 17;
```

No segundo jeito não foi especificado o tipo da variável mas o TypeScript entende que é **number** por meio da infêrencia.

### COMO O TS PENSA?

#

Ele olha o valor da variável: 

```ts
let qualquerCoisa1 = 17;
```

> Aí ele vai pensar: "hmm, o valor da variável é um number então o tipo da variável também só pode ser number" e vai compreender assim:

```ts
let qualquerCoisa1: number = 17;
```

Depois disso a variável fica travada com a tipagem **number** e não pode receber valores de outros tipo, por exemplo:

```ts
qualquerCoisa1 = 21; // Permitido
// qualquerCoisa1 = "sanduiche"; // Erro de compilação 
```

Com outros tipos de valores por exemplo:

## **string:**

```ts
let qualquerCoisa2 = "Hello world";
```

> Foi travada como string e o TypeScript vai inferir ela como:

```ts
let qualquerCoisa2: string = "Hello world";
```

### Mas se tentar mudar o tipo do valor da variável dá erro também igual aos outros exemplos:

```ts
qualquerCoisa2 = "Goodbye world" // Permitido;
// qualquerCoisa2 = 158 // Erro de compilação;
```

## boolean

```ts
let qualquerCoisa3 = true;
```

> Foi travada como boolean e o TypeScript vai inferir ela como:

```ts
let qualquerCoisa3: boolean = true;
```

### Mas se tentar mudar o tipo do valor da variável dá erro também igual aos outros exemplos:

```ts
qualquerCoisa3 = false // Permitido;
// qualquerCoisa3 = "computador" // Erro de compilação;
```

## arrays (number[ ], string[ ] e boolean[ ]):

### number[ ]:
```ts
let listaCoisas1 = [1,2,3];
```

> Foi travada como number[] e o TypeScript vai inferir ela como:

```ts
let listaCoisas1: number[] = [1,2,3,4,5];
```

### Mas se tentar adicionar valores de tipos diferentes, dá erro:

```ts
listaCoisas1.push(6) // Permitido;
// listaCoisas1.push("hello country") // Erro de compilação;
```

### string[ ]:

```ts
let listaCoisas2 = ["carro","moto","aviao"];
```

> Foi travada como string[] e o TypeScript vai inferir ela como:

```ts
let listaCoisas2: string[] = ["carro","moto","aviao"];
```

### Mas se tentar adicionar valores de tipos diferentes, dá erro:

```ts
listaCoisas2.push("submarino") // Permitido;
// listaCoisas2.push(7) // Erro de compilação;
```

### boolean[ ]:

```ts
let listaCoisas3 = [true,false,false];
```

> Foi travada como string[] e o TypeScript vai inferir ela como:

```ts
let listaCoisas3: boolean[] = [true,false,false];
```

### Mas se tentar adicionar valores de tipos diferentes, dá erro:

```ts
listaCoisas3.push(true) // Permitido;
// listaCoisas3.push("hello country") // Erro de compilação;
```

## objetos

```ts
let objetoCoisa = {
nome: "Joao",
idade: 17,
};
```

> A propriedade **nome** foi travada como string e a propriedade **idade** foi travada como number e o TypeScript vai inferir elas como:

```ts
let objetoCoisa: {nome: string; idade: number} = {
nome: "Joao",
idade: 17,
};
```

### Mas se tentar adicionar valores de tipos diferentes nas propriedades, dá erro:

```ts
objetoCoisa.nome = "Jorge"; // Permitido
objetoCoisa.idade = 19; // Permitido

// objetoCoisa.nome = 65 // Erro de compilação
// objetoCoisa.idade = "25" // Erro de compilação
```

## function

```ts
function soma(a: number, b: number) {
  return a + b;
}
```

> O return da função foi travado como number e o TypeScript vai inferir ela como:

```ts
function soma(a: number, b: number): number {
  return a + b;
}
```

### Mas se tentar usar valores de tipos diferentes nos parâmetros, dá erro:

```ts
soma(1, 2) // Permitido
soma(12, 35) // Permitido

soma("1", 2)    // Erro de compilação
soma(1, "2")    // Erro de compilação
soma("1", "2")  // Erro de compilação
```

---

### ATENÇÃO: 

A inferência de tipos não é algo ruim e pode até agilizar a escrita do código. Porém, é preciso ter alguns cuidados ao utilizá-la:

> Só usar a infêrencia de dados quando a variável for criada com um valor predefinido com tipo explícito.

> Evitar criar variáveis vazias pois o TypeScript entende a variável como sendo do tipo any e permite a entrada de qualquer valor, assim quebrando a segurança do TS. 

### SIGA ESTÁ REGRA PARA FACILITAR O APRENDIZADO:

se a variável nasce com valor = inferência é segura e recomendada para deixar o código mais simples e limpo.

Se a variável nasce sem valor = declare o tipo explicitamente antes para deixar ocódigo seguro de erros.

### EXEMPLO PRÁTICO: 

```ts
let qualquerCoisa4;
```

> A variável foi tipada como any e vai aceitar qualquer valor e deixar seu código Suscetível a valores errados nas variáveis erradas, tipe antes.

```ts
// let qualquerCoisa4: string;
// let qualquerCoisa4: number;
// let qualquerCoisa4: boolean;
// let qualquerCoisa4: string[ ];
// let qualquerCoisa4: number[ ];
// let qualquerCoisa4: boolean[ ];
// let qualquerCoisa4: {nome: string; idade: number};
```

> Qualquer uma, só lembre dessa regrinha do TS.

---

### Quando usar inferência:

 - Quando o valor inicial deixa o tipo óbvio
 - Em variáveis simples
 - Para código mais limpo
 
### Quando NÃO usar:
 
 - Variáveis vazias
 - APIs
 - Dados que mudam de forma
 - Código público / compartilhado
