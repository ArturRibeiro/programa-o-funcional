
# 🔁 Conceito: Recursão (Tail Recursion) em C#

## ✅ O que é Recursão?

**Recursão** é uma técnica onde uma função **chama a si mesma** para resolver um problema em partes menores.

### Tail Recursion

**Tail recursion** ocorre quando a **última operação** de uma função é a chamada recursiva.  
Idealmente, pode ser otimizada pelo compilador para evitar uso excessivo da pilha (TCO - Tail Call Optimization).

**C# não implementa otimização de tail call nativamente**, mas a técnica pode ser simulada.

---

## 🎯 Propósito

- Resolver problemas iterativos de forma declarativa;
- Evitar loops imperativos;
- Implementar algoritmos naturalmente recursivos (ex: fatorial, Fibonacci, árvores, etc).

---

## 💡 Exemplo clássico: Fatorial recursivo (não tail-recursive)

```csharp
public static int Fatorial(int n)
{
    if (n == 0) return 1;
    return n * Fatorial(n - 1);
}
```

---

## 💡 Tail Recursive (simulado com parâmetro acumulador)

```csharp
public static int FatorialTail(int n, int acumulador = 1)
{
    if (n == 0) return acumulador;
    return FatorialTail(n - 1, acumulador * n);
}
```

### 🧾 Uso:

```csharp
Console.WriteLine(FatorialTail(5)); // 120
```

---

## 💡 Simulação com `while` (evitar stack overflow)

```csharp
public static int FatorialIterativo(int n)
{
    int acumulador = 1;
    while (n > 0)
    {
        acumulador *= n;
        n--;
    }
    return acumulador;
}
```

---

## 💡 Recursão em listas (soma)

```csharp
public static int SomarLista(List<int> lista)
{
    if (lista.Count == 0) return 0;
    return lista[0] + SomarLista(lista.Skip(1).ToList());
}
```

---

## 🛠️ Dicas Práticas

- Evite profundidade de recursão muito grande → risco de `StackOverflowException`;
- Use acumuladores para simular tail recursion;
- Em problemas com muitos passos, prefira versão iterativa ou TCO manual;
- Recursão é ótima para estruturas como árvores, grafos, processamento de arquivos em hierarquia.

---

## ⚠️ Cuidado

- C# **não possui TCO** (Tail Call Optimization) como linguagens funcionais puras (ex: F#, Haskell);
- Recursão ingênua pode quebrar para N > 10000 (dependendo da profundidade da pilha);
- Prefira `Span<T>` ou `Stack<T>` para chamadas profundas ou otimizações manuais.

---
