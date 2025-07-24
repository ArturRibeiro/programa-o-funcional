
# ❓ Conceito: Option (Maybe Monad) em C#

## ✅ O que é Option?

`Option<T>` (ou `Maybe<T>`) é um tipo que representa a **presença (`Some`) ou ausência (`None`) de um valor**.  
Evita o uso de `null` e melhora a segurança do código contra exceções de referência nula.

---

## 🎯 Propósito

- Evitar `null` e `NullReferenceException`;
- Controlar o fluxo com base em presença de valores;
- Facilitar composição de validações e transformações seguras;
- Tornar explícita a possibilidade de "nada" ser retornado.

---

## 🧱 Estrutura básica

```csharp
public abstract class Option<T>
{
    public static Option<T> Some(T value) => new Some<T>(value);
    public static Option<T> None() => new None<T>();

    public abstract Option<TResult> Map<TResult>(Func<T, TResult> func);
    public abstract Option<TResult> Bind<TResult>(Func<T, Option<TResult>> func);
}

public class Some<T> : Option<T>
{
    private readonly T _value;
    public Some(T value) => _value = value;

    public override Option<TResult> Map<TResult>(Func<T, TResult> func)
        => Option<TResult>.Some(func(_value));

    public override Option<TResult> Bind<TResult>(Func<T, Option<TResult>> func)
        => func(_value);
}

public class None<T> : Option<T>
{
    public override Option<TResult> Map<TResult>(Func<T, TResult> func)
        => Option<TResult>.None();

    public override Option<TResult> Bind<TResult>(Func<T, Option<TResult>> func)
        => Option<TResult>.None();
}
```

---

## 💡 Exemplo prático: Validação e transformação

```csharp
public static Option<string> ValidarCpf(string cpf)
    => cpf.Length == 11 ? Option<string>.Some(cpf) : Option<string>.None();

public static string NormalizarCpf(string cpf)
    => cpf.Replace(".", "").Replace("-", "").Trim();

public static Option<string> BuscarCliente(string cpf)
    => cpf == "12345678901" ? Option<string>.Some("João da Silva") : Option<string>.None();
```

### 🧾 Uso:

```csharp
ValidarCpf("12345678901")
    .Map(NormalizarCpf)
    .Bind(BuscarCliente)
    .Match(
        cliente => Console.WriteLine($"Cliente: {cliente}"),
        () => Console.WriteLine("CPF inválido ou cliente não encontrado")
    );
```

---

## 📦 Extensão para `Match`

```csharp
public static class OptionExtensions
{
    public static void Match<T>(
        this Option<T> option,
        Action<T> onSome,
        Action onNone)
    {
        if (option is Some<T> some)
            onSome(GetValue(some));
        else
            onNone();
    }

    private static T GetValue<T>(Some<T> some)
        => (T)typeof(Some<T>)
            .GetField("_value", System.Reflection.BindingFlags.NonPublic | System.Reflection.BindingFlags.Instance)
            ?.GetValue(some);
}
```

---

## 🛠️ Dicas Práticas

- Substitua retornos `null` por `Option<T>`;
- Combine com `Map` e `Bind` para evitar checagens `if/else`;
- Facilita testes e clareza do fluxo de dados;
- Ideal para pipelines funcionais e composições seguras.

---

## 📚 Alternativas prontas

- [LanguageExt](https://github.com/louthy/language-ext)
- [Optional](https://github.com/nlkl/Optional)
- Crie seu próprio `Option<T>` para aprendizado e domínio conceitual.

---
