
# 🌳 Conceito: Expression Trees em C#

## ✅ O que são Expression Trees?

**Expression Trees** representam **código como uma estrutura de dados** em tempo de execução.  
Permitem analisar, modificar e compilar expressões lambda dinamicamente.

Usadas amplamente em:

- LINQ to SQL / Entity Framework;
- Compiladores e metaprogramação;
- Construção de DSLs (Domain-Specific Languages);
- Serialização de lógica de consulta.

---

## 🎯 Propósito

- **Analisar expressões** como árvores sintáticas;
- Traduzir expressões para outro formato (ex: SQL, MongoDB, etc.);
- Gerar código dinâmico com segurança;
- Evitar reflexões verbosas.

---

## 💡 Exemplo básico: Analisando expressão

```csharp
Expression<Func<int, bool>> expr = x => x > 10;

Console.WriteLine(expr); // x => (x > 10)
Console.WriteLine(expr.Body); // (x > 10)
```

---

## 💡 Exemplo: Decompilar árvore de expressão

```csharp
var parametro = Expression.Parameter(typeof(int), "x");
var constante = Expression.Constant(10);
var maiorQue = Expression.GreaterThan(parametro, constante);

var lambda = Expression.Lambda<Func<int, bool>>(maiorQue, parametro);

var compilado = lambda.Compile();

Console.WriteLine(lambda);     // x => (x > 10)
Console.WriteLine(compilado(15)); // True
```

---

## 📦 Cenário prático: LINQ dinâmico

```csharp
Expression<Func<Produto, bool>> filtro = p => p.Preco > 100;

var query = dbContext.Produtos.Where(filtro);
```

Aqui o Entity Framework converte a árvore de expressão para SQL.

---

## 🧱 Construindo dinamicamente

```csharp
var param = Expression.Parameter(typeof(string), "s");
var lengthProp = Expression.Property(param, "Length");
var constExpr = Expression.Constant(5);
var greater = Expression.GreaterThan(lengthProp, constExpr);

var lambda = Expression.Lambda<Func<string, bool>>(greater, param);
```

---

## 🛠️ Dicas Práticas

- Use `Expression<T>` quando quiser manipular lógica como dados;
- Combine com reflexão ou `Emit` para geradores de código avançados;
- Útil para filtros dinâmicos em repositórios genéricos e mapeamento de regras.

---

## ⚠️ Cuidado

- Expressões complexas podem gerar árvores difíceis de manter;
- Difere de `Func<T>` — este já está compilado e não pode ser inspecionado;
- Performance pode ser afetada se a compilação for feita repetidamente.

---

## 📚 Recomendado

- [Documentação oficial .NET - Expressions](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/expression-trees/)
- Livro: *C# in Depth* - Jon Skeet (Cap. sobre Expressions)

---
