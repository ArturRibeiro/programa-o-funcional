
# 🔗 Conceito: Composição de Funções em C#

## ✅ O que é Composição de Funções?

**Composição de funções** é o ato de combinar duas ou mais funções, de forma que a saída de uma função seja a entrada da próxima.

Matematicamente:
```
f(g(x)) = (f ∘ g)(x)
```

Em C#, é feita com `Func<T>` e expressões lambda.

---

## 🎯 Propósito

- Modularizar transformações de dados;
- Reduzir duplicação de lógica;
- Tornar o fluxo de dados mais claro e declarativo;
- Facilita testes e reutilização de funções pequenas.

---

## 💡 Exemplo simples: Compor duas funções

```csharp
Func<int, int> dobrar = x => x * 2;
Func<int, int> incrementar = x => x + 1;

Func<int, int> dobrarDepoisIncrementar = x => incrementar(dobrar(x));

Console.WriteLine(dobrarDepoisIncrementar(3)); // (3 * 2) + 1 = 7
```

---

## 💡 Composição genérica com método auxiliar

```csharp
public static Func<T, TResult> Compor<T, TIntermediario, TResult>(
    Func<TIntermediario, TResult> f,
    Func<T, TIntermediario> g)
{
    return x => f(g(x));
}
```

### 🧾 Uso:

```csharp
var composicao = Compor(incrementar, dobrar); // f(g(x))
Console.WriteLine(composicao(4)); // (4 * 2) + 1 = 9
```

---

## 💡 Exemplo prático: Pipeline de validação

```csharp
Func<string, string> removerEspacos = s => s.Trim();
Func<string, string> paraMinusculo = s => s.ToLower();
Func<string, string> removerAcentos = s => Regex.Replace(s, "[áàâã]", "a");

Func<string, string> normalizarTexto = s => removerAcentos(paraMinusculo(removerEspacos(s)));

var entrada = "  Árvore  ";
Console.WriteLine(normalizarTexto(entrada)); // "arvore"
```

---

## 🛠️ Dicas Práticas

- Componha funções pequenas com responsabilidades únicas;
- Use em validações, transformações e pipelines de dados;
- Funciona bem com `LINQ`, `Option`, `Either` e outras estruturas funcionais.

---

## ⚠️ Atenção

- Evite composições excessivamente profundas que dificultem a legibilidade;
- Nomeie funções intermediárias para melhor clareza;
- Composição funciona melhor com **funções puras** e **imutáveis**.

---
