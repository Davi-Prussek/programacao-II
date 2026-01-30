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