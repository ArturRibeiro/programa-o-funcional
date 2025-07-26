
# 🗺️ Conceito: Map em C#

## ✅ O que é `Map`?

`Map` é uma operação funcional usada para **transformar o valor interno** de um contêiner (ex: `Option`, `Either`, `List`, `IEnumerable`, etc.) **sem modificar sua estrutura externa**.

---

## 🎯 Propósito

- Aplicar transformações de forma segura;
- Evitar condicionais explícitas (`if`, `null`, `try/catch`);
- Compor funções puras em contextos funcionais;
- Promover legibilidade e consistência.

---

## 💡 Exemplo com `Option<T>`

```csharp
var nomeOption = Option<string>.Some("ana");

var nomeCapitalizado = nomeOption.Map(nome => 
    char.ToUpper(nome[0]) + nome.Substring(1)
);

// Resultado: Some("Ana")
```

---

## 💡 Exemplo com `Either<L, R>`

```csharp
var resultado = new Right<string, int>(10);

var dobrado = resultado.Map(x => x * 2);

// Resultado: Right(20)
```

---

## 💡 Exemplo com `List<T>` (via LINQ)

```csharp
var numeros = new List<int> { 1, 2, 3 };

var quadrados = numeros.Select(x => x * x).ToList();

// Resultado: [1, 4, 9]
```

---

## 🧱 Implementação genérica (Exemplo `Option<T>`)

```csharp
public abstract class Option<T>
{
    public abstract Option<TResult> Map<TResult>(Func<T, TResult> func);
}

public class Some<T> : Option<T>
{
    private readonly T _value;

    public Some(T value) => _value = value;

    public override Option<TResult> Map<TResult>(Func<T, TResult> func)
        => Option<TResult>.Some(func(_value));
}

public class None<T> : Option<T>
{
    public override Option<TResult> Map<TResult>(Func<T, TResult> func)
        => Option<TResult>.None();
}
```

---

## 🛠️ Dicas Práticas

- Use `Map` para transformação simples e segura de dados;
- Mantenha funções puras dentro do `Map`;
- Combine com `Bind` para transformações que também retornam containers;
- Ideal para pipelines onde os dados podem estar ausentes (`Option`) ou falhos (`Either`).

---

## ⚠️ Evite

- Lógica com efeitos colaterais dentro de `Map`;
- `Map` sobre valores mutáveis;
- Substituir `Bind` por `Map` quando a função interna retorna um `Option`/`Either`.

---
