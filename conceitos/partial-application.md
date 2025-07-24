
# 🧩 Conceito: Partial Application em C#

## ✅ O que é Partial Application?

**Partial application** (aplicação parcial) é uma técnica que consiste em **fornecer apenas parte dos argumentos** de uma função, gerando uma nova função com os parâmetros restantes.

---

## 🎯 Propósito

- **Especializar funções genéricas**;
- **Melhorar reutilização** e **clareza do código**;
- Permitir criação de funções específicas com menos parâmetros;
- Excelente para pipelines e programação declarativa.

---

## 💡 Exemplo: Função com dois argumentos

```csharp
public static int Potencia(int baseNum, int expoente)
    => (int)Math.Pow(baseNum, expoente);
```

---

## 💡 Partial Application manual

```csharp
public static Func<int, int> AplicarBase(int baseNum)
{
    return expoente => Potencia(baseNum, expoente);
}
```

### 🧾 Uso:

```csharp
var aoQuadrado = AplicarBase(2);     // cria função x => 2^x
Console.WriteLine(aoQuadrado(3));    // 8
```

---

## 💡 Função genérica de partial application

```csharp
public static Func<T2, TResult> Partial<T1, T2, TResult>(Func<T1, T2, TResult> func, T1 valorFixado)
{
    return x => func(valorFixado, x);
}
```

### 🧾 Uso:

```csharp
Func<int, int, int> multiplicar = (a, b) => a * b;

var multiplicarPor5 = Partial(multiplicar, 5);
Console.WriteLine(multiplicarPor5(3)); // 15
```

---

## 🛠️ Dicas Práticas

- Útil para **injeção funcional de dependência** (parâmetros de contexto fixados);
- Facilita composição em **pipelines**;
- Em C#, simula-se via lambdas, pois não há suporte nativo;
- Pode ser combinada com `Currying` para aplicação progressiva de argumentos.

---

## ⚠️ Atenção

- Partial application é **diferente de currying**:  
  - Currying transforma a função;  
  - Partial application **usa** a função como está e **aplica valores parcialmente**;
- Em contextos complexos, pode dificultar o entendimento se mal utilizada.

---
