
# 🔄 Conceito: Bind (FlatMap / SelectMany) em C#

## ✅ O que é `Bind`?

`Bind`, também conhecido como `FlatMap` ou `SelectMany`, é uma operação usada para **encadear funções que retornam tipos elevados** como `Option`, `Either`, `Task`, etc.

---

## 🎯 Propósito

- Evitar aninhamento de containers (`Option<Option<T>>`, etc);
- Encadear operações que podem falhar ou serem opcionais;
- Construir pipelines funcionais com controle de fluxo robusto;
- Tornar o código mais legível e linear.

---

## 💡 Exemplo com `Option<T>`

```csharp
Option<string> BuscarUsuario(string id) =>
    id == "1" ? Option<string>.Some("João") : Option<string>.None();

Option<string> BuscarEmail(string nome) =>
    nome == "João" ? Option<string>.Some("joao@email.com") : Option<string>.None();

var email = BuscarUsuario("1")
    .Bind(BuscarEmail);
```

### Resultado: `Some("joao@email.com")` ou `None()`

---

## 💡 Exemplo com `Either<L, R>`

```csharp
Either<string, int> Parsear(string entrada)
    => int.TryParse(entrada, out var valor)
        ? new Right<string, int>(valor)
        : new Left<string, int>("Não é um número");

Either<string, double> RaizQuadrada(int numero)
    => numero >= 0
        ? new Right<string, double>(Math.Sqrt(numero))
        : new Left<string, double>("Negativo");

var resultado = Parsear("9").Bind(RaizQuadrada);
```

---

## 🧱 Implementação para `Bind` em `Option<T>`

```csharp
public abstract class Option<T>
{
    public abstract Option<TResult> Bind<TResult>(Func<T, Option<TResult>> func);
}

public class Some<T> : Option<T>
{
    private readonly T _value;

    public Some(T value) => _value = value;

    public override Option<TResult> Bind<TResult>(Func<T, Option<TResult>> func)
        => func(_value);
}

public class None<T> : Option<T>
{
    public override Option<TResult> Bind<TResult>(Func<T, Option<TResult>> func)
        => Option<TResult>.None();
}
```

---

## 💡 LINQ com `SelectMany` (sintaxe query)

```csharp
var resultado = 
    from usuario in BuscarUsuario("1")
    from email in BuscarEmail(usuario)
    select email;
```

---

## 🛠️ Dicas Práticas

- Use `Bind` para encadear funções que retornam monads (`Option`, `Either`, `Task`, etc);
- Evita `if` aninhados e facilita leitura de fluxo condicional;
- Combine com `Map` para transformação simples após validação com `Bind`.

---

## ⚠️ Diferença entre `Map` e `Bind`

| Operação | Quando usar                                     | Tipo de retorno        |
|----------|--------------------------------------------------|------------------------|
| `Map`    | Quando a função interna retorna **valor simples** | `Option<T>`            |
| `Bind`   | Quando a função interna retorna **Option/Either** | `Option<Option<T>> → Option<T>` |

---
