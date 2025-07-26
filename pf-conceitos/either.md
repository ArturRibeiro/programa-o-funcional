
# ⚖️ Conceito: Either (Erro Funcional) em C#

## ✅ O que é Either?

`Either<L, R>` representa um valor que pode ser de **dois tipos possíveis**:

- `Left` → geralmente representa um **erro ou falha**;
- `Right` → representa um **valor válido ou sucesso**.

É uma alternativa segura e expressiva ao uso de exceções.

---

## 🎯 Propósito

- Modelar **erros como valores**, evitando `try/catch`;
- Tornar o **fluxo de erro explícito**;
- Facilitar encadeamento de operações com controle de falha;
- Promover legibilidade e testabilidade de código funcional.

---

## 🧱 Estrutura base

```csharp
public abstract class Either<L, R>
{
    public abstract TResult Match<TResult>(Func<L, TResult> leftFunc, Func<R, TResult> rightFunc);
    public abstract Either<L, R2> Bind<R2>(Func<R, Either<L, R2>> func);
    public abstract Either<L, R2> Map<R2>(Func<R, R2> func);
}

public class Left<L, R> : Either<L, R>
{
    private readonly L _value;
    public Left(L value) => _value = value;

    public override TResult Match<TResult>(Func<L, TResult> leftFunc, Func<R, TResult> rightFunc)
        => leftFunc(_value);

    public override Either<L, R2> Bind<R2>(Func<R, Either<L, R2>> func)
        => new Left<L, R2>(_value);

    public override Either<L, R2> Map<R2>(Func<R, R2> func)
        => new Left<L, R2>(_value);
}

public class Right<L, R> : Either<L, R>
{
    private readonly R _value;
    public Right(R value) => _value = value;

    public override TResult Match<TResult>(Func<L, TResult> leftFunc, Func<R, TResult> rightFunc)
        => rightFunc(_value);

    public override Either<L, R2> Bind<R2>(Func<R, Either<L, R2>> func)
        => func(_value);

    public override Either<L, R2> Map<R2>(Func<R, R2> func)
        => new Right<L, R2>(func(_value));
}
```

---

## 💡 Exemplo prático: Validação com erro funcional

```csharp
public static Either<string, string> ValidarEmail(string email)
{
    return email.Contains("@")
        ? new Right<string, string>(email)
        : new Left<string, string>("Email inválido");
}

public static Either<string, string> ExtrairDominio(string email)
{
    try
    {
        var dominio = email.Split('@')[1];
        return new Right<string, string>(dominio);
    }
    catch
    {
        return new Left<string, string>("Erro ao extrair domínio");
    }
}
```

---

## 🧾 Uso:

```csharp
ValidarEmail("teste@exemplo.com")
    .Bind(ExtrairDominio)
    .Match(
        erro => Console.WriteLine($"Erro: {erro}"),
        dominio => Console.WriteLine($"Domínio: {dominio}")
    );
```

---

## 🛠️ Dicas Práticas

- Use `Right` para valores válidos e `Left` para falhas controladas;
- Substitui o uso de `try/catch` em pipelines funcionais;
- Ideal para modelar validações, acessos externos, parsing e I/O.

---

## 📚 Alternativas prontas

- [LanguageExt.Either](https://github.com/louthy/language-ext)
- [CSharpFunctionalExtensions.Either](https://github.com/vkhorikov/CSharpFunctionalExtensions)

---
