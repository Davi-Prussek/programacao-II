# Diferenças entre JavaScript e TypeScript

Este guia mostra as principais diferenças entre **JavaScript (JS)** e **TypeScript (TS)**, 
para você entender por que usamos TS em Programação II.

---

## 1. JavaScript (JS)

- Linguagem **interpretada**, roda diretamente no navegador ou Node.js.
- **Tipagem dinâmica**: você não precisa declarar tipos de variáveis.
- Funciona imediatamente, sem compilação.
- Mais flexível, mas erros de tipo aparecem **só na execução**.

Exemplo:

```js
let nome = "Davi";  // string
nome = 123;         // JS permite, sem erro
console.log(nome);  // 123
```

## 2. TypeScript (TS)

- Superconjunto do JavaScript → todo JS escrito em um arquivo TS é válido, mas TS adiciona recursos.

- Tipagem estática: você declara o tipo das variáveis, parâmetros e retornos.

- Precisa compilar para JS antes de rodar (tsc arquivo.ts).

- Detecta erros antes de executar, ajudando a reduzir bugs.

- Recursos extras: interfaces, enums, generics, decoradores, etc.

```ts
let nome: string = "Davi";    //string
//nome = 123;                 //Erro de compilação
console.log(nome);            //"Davi"

```
