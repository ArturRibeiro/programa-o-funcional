
# 💤 Conceito: Lazy Evaluation em C#

## ✅ O que é Lazy Evaluation?

**Lazy Evaluation** (Avaliação Preguiçosa) é uma estratégia onde a **execução de uma expressão é adiada até que seu valor seja realmente necessário**.

Em C#, isso pode ser implementado com:

- `IEnumerable<T>` (LINQ);
- `yield return`;
- `Lazy<T>`.

---

## 🎯 Propósito

- **Evitar computações desnecessárias**;
- Melhorar performance em coleções grandes;
- Trabalhar com **pipelines infinitos ou parciais**;
- Adiar inicialização de objetos pesados.

---

## 💡 Exemplo com `IEnumerable<T>` (LINQ é lazy)

```csharp
var numeros = Enumerable.Range(1, 1000);

var filtrados = numeros
    .Where(x => x % 2 == 0)
    .Select(x => x * 2); // ainda não executado

var lista = filtrados.Take(3).ToList(); // execução acontece aqui
```

---

## 💡 Exemplo com `yield return`

```csharp
public static IEnumerable<int> Pares(int ate)
{
    for (int i = 0; i <= ate; i++)
        if (i % 2 == 0)
            yield return i;
}
```

### 🧾 Uso:

```csharp
foreach (var x in Pares(10))
    Console.WriteLine(x); // imprime sob demanda
```

---

## 💡 Exemplo com `Lazy<T>`

```csharp
Lazy<string> conexaoLenta = new(() =>
{
    Console.WriteLine("Inicializando conexão...");
    return "Conexão OK";
});

Console.WriteLine("Antes do acesso...");
Console.WriteLine(conexaoLenta.Value); // inicializa aqui
```

---

## 🛠️ Dicas Práticas

- Use `yield return` para criar coleções sob demanda;
- Use `Lazy<T>` quando a criação do valor for cara ou opcional;
- Em pipelines de dados, evite `ToList()` prematuro para manter o comportamento lazy;
- Combine com `Take`, `Any`, `First` para aproveitar a avaliação mínima.

---

## ⚠️ Atenção

- A avaliação preguiçosa só ocorre até que você **materialize** a sequência (`ToList`, `ToArray`, etc);
- Evite múltiplas enumerações de `IEnumerable` lazy se a fonte for dinâmica ou não-repetível;
- Nem tudo é lazy: estruturas como `List<T>` e `Array` são **eager**.

---
