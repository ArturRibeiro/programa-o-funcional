
# 🔁 Conceito: Funções de Ordem Superior em C#

## ✅ O que são Funções de Ordem Superior?

Funções de ordem superior são funções que:

- Recebem outras funções como parâmetro, ou
- Retornam outras funções como resultado.

Em C#, são representadas por delegates como `Func`, `Action`, `Predicate` e expressões lambda.

---

## 🎯 Propósito

- Promover **abstração e reutilização** de lógica;
- Tornar o código mais **modular e declarativo**;
- Permitir **composição de comportamentos** de forma flexível.

---

## 💡 Exemplo: Receber função como parâmetro

```csharp
public class Operacoes
{
    public static int Calcular(int a, int b, Func<int, int, int> operacao)
        => operacao(a, b);
}
```

### 🧾 Uso:

```csharp
var soma = Operacoes.Calcular(3, 4, (x, y) => x + y); // 7
var mult = Operacoes.Calcular(3, 4, (x, y) => x * y); // 12
```

---

## 💡 Exemplo: Retornar uma função

```csharp
public static Func<int, int> Multiplicador(int fator)
{
    return x => x * fator;
}
```

### 🧾 Uso:

```csharp
var dobro = Multiplicador(2);
var triplo = Multiplicador(3);

Console.WriteLine(dobro(5));   // 10
Console.WriteLine(triplo(5));  // 15
```

---

## 📦 Composição com LINQ

```csharp
var numeros = Enumerable.Range(1, 10);

var paresDobrados = numeros
    .Where(x => x % 2 == 0)             // Predicate<int>
    .Select(x => x * 2)                 // Func<int, int>
    .ToList();
```

---

## 🛠️ Dicas Práticas

- Use `Func<T, TResult>` para funções com retorno;
- Use `Action<T>` para funções sem retorno;
- Use `Predicate<T>` para expressões booleanas (ex: filtros);
- Componha pequenas funções para construir pipelines maiores;
- Evite capturar variáveis mutáveis externas em lambdas.

---
