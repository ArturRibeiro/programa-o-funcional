
# 🧪 Conceito: Currying em C#

## ✅ O que é Currying?

**Currying** é a técnica de transformar uma função que recebe múltiplos argumentos  
em uma cadeia de funções que recebem **um único argumento por vez**.

É comum em linguagens funcionais puras, mas pode ser simulado em C# usando lambdas.

---

## 🎯 Propósito

- Permitir **aplicação parcial** de argumentos;
- Aumentar a **reutilização de lógica**;
- Facilitar a **composição de funções**;
- Tornar o código mais **modular e declarativo**.

---

## 💡 Exemplo: Função comum

```csharp
public static int Somar(int a, int b)
    => a + b;
```

---

## 💡 Currying manual em C#

```csharp
public static Func<int, Func<int, int>> SomarCurried()
{
    return a => b => a + b;
}
```

---

## 🧾 Uso:

```csharp
var somar = SomarCurried();

var somar10 = somar(10);       // retorna Func<int, int>
var resultado = somar10(5);    // 15

Console.WriteLine(resultado);  // 15
```

---

## 💡 Currying com tipos genéricos

```csharp
public static Func<T1, Func<T2, TResult>> Curry<T1, T2, TResult>(Func<T1, T2, TResult> func)
{
    return a => b => func(a, b);
}
```

### 🧾 Uso:

```csharp
Func<int, int, int> soma = (x, y) => x + y;
var curried = Curry(soma);

var somar5 = curried(5);
Console.WriteLine(somar5(3)); // 8
```

---

## 🛠️ Dicas Práticas

- Currying é útil quando se deseja criar **funções especializadas** a partir de funções genéricas.
- Trabalha bem com **injeção de dependências** funcional.
- Ideal para uso com **funções de ordem superior** e **partial application**.

---

## ⚠️ Limitações em C#

- Currying **não é nativo** em C#, mas pode ser implementado com lambdas;
- Usar currying em excesso pode deixar o código difícil de ler;
- Prefira usar onde **há ganho real de composição ou reutilização**.

---
