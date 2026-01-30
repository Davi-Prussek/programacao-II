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
let idade: number = 17;  //pode mudar
idade = 18;

const nome: string = "Joao"; //não pode mudar
// nome = "Ana";             //Erro de compilação
```

## 2. Tipos Primitivos

No TypeScript você consegue declarar o tipo de uma variável, e os tipos existentes são:

- string → texto/escrita

- number → números (inteiros ou decimais)

- boolean → true ou false

- any → aceita qualquer valor (não recomendado, pois ignora a verificação de tipos)

- unknown → aceita qualquer valor, mas precisa de verificação antes de usar

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

## 3. Inferência de Tipos
