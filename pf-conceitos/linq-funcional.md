
# 🧬 Conceito: LINQ Funcional em C#

## ✅ O que é LINQ Funcional?

`LINQ Funcional` refere-se ao uso das **operações de extensão sobre `IEnumerable<T>`** baseadas em conceitos funcionais como:

- `Where` → filtro (semelhante a `filter`);
- `Select` → projeção (semelhante a `map`);
- `Aggregate`, `Any`, `All`, `FirstOrDefault`, etc.

São funções puras, imutáveis e encadeáveis, inspiradas em programação funcional.

---

## 🎯 Propósito

- Expressar **operações sobre coleções** de forma declarativa;
- Eliminar o uso de `foreach`, `for` e mutabilidade;
- Compor transformações e filtros com clareza;
- Promover legibilidade, testabilidade e modularização.

---

## 💡 Exemplo básico

```csharp
var numeros = new[] { 1, 2, 3, 4, 5 };

var paresDobrados = numeros
    .Where(x => x % 2 == 0)
    .Select(x => x * 2)
    .ToList(); // [4, 8]
```

---

## 💡 Exemplo com `Aggregate`

```csharp
var palavras = new[] { "C#", "é", "funcional" };

var frase = palavras.Aggregate((acc, next) => $"{acc} {next}");

// Resultado: "C# é funcional"
```

---

## 💡 Exemplo com `GroupBy`, `OrderBy`, `Take`

```csharp
var produtos = new[]
{
    new { Nome = "Teclado", Categoria = "Periférico" },
    new { Nome = "Mouse", Categoria = "Periférico" },
    new { Nome = "Placa de Vídeo", Categoria = "Hardware" }
};

var agrupados = produtos
    .GroupBy(p => p.Categoria)
    .Select(g => new { Categoria = g.Key, Itens = g.ToList() });
```

---

## 🧠 Comparação imperativo vs funcional

### Imperativo:

```csharp
var resultado = new List<int>();
foreach (var x in numeros)
{
    if (x % 2 == 0)
        resultado.Add(x * 2);
}
```

### Funcional (LINQ):

```csharp
var resultado = numeros
    .Where(x => x % 2 == 0)
    .Select(x => x * 2)
    .ToList();
```

---

## 🛠️ Dicas Práticas

- Prefira `IEnumerable<T>` a `List<T>` para compor pipelines imutáveis;
- `Where`, `Select`, `SelectMany`, `Aggregate`, `Distinct`, `GroupBy` são essenciais;
- Utilize `ToList()` ou `ToArray()` apenas quando precisar materializar os dados;
- Evite `ToList()` prematuro no meio do pipeline.

---

## ⚠️ Atenção

- LINQ é **preguiçoso (lazy)**: só executa ao iterar ou materializar;
- Pode afetar performance em coleções muito grandes se mal utilizado;
- Para uso em banco de dados (ex: EF Core), **use `IQueryable<T>`** com cautela.

---
