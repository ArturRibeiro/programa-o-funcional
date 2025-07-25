
# 📦 Conceito: Monads em C#

## ✅ O que é uma Monad?

**Monad** é um *design pattern* funcional que representa **operações encadeáveis com contexto**.

Uma Monad precisa suportar:

1. **Retornar (unit)** → encapsular um valor simples em uma estrutura;
2. **Bind (flatMap / SelectMany)** → aplicar uma função que também retorna a estrutura.

---

## 🎯 Propósito

- Encapsular lógica de controle como:
  - Possibilidade de ausência (`Option`);
  - Erros (`Either`);
  - Efeitos (`Task`);
- Compor operações sequenciais seguras;
- Reduzir complexidade de código imperativo com controle de fluxo explícito.

---

## 🧱 Estrutura genérica

```csharp
public interface IMonad<T>
{
    IMonad<TResult> Bind<TResult>(Func<T, IMonad<TResult>> func);
}
```

---

## 💡 Exemplos de Monads comuns em C#

| Monad     | Contexto                     | Exemplo                          |
|-----------|------------------------------|----------------------------------|
| `Option<T>` | Falta de valor (null safety) | `Option.Some("A").Bind(...)`     |
| `Either<L, R>` | Erro/sucesso funcional     | `Parse().Bind(...).Bind(...)`     |
| `Task<T>`   | Execução assíncrona         | `await func().ContinueWith(...)`  |
| `IEnumerable<T>` | Sequências (stream)        | `SelectMany(...).Where(...).Select(...)` |

---

## 💡 Encadeamento via LINQ (`SelectMany`)

```csharp
var resultado =
    from nome in Option<string>.Some("Ana")
    from email in BuscarEmail(nome)
    select $"{nome} <{email}>";
```

---

## 🔁 Leis das Monads (Monad Laws)

1. **Left Identity**:  
   `unit(x).Bind(f) == f(x)`

2. **Right Identity**:  
   `m.Bind(unit) == m`

3. **Associativity**:  
   `m.Bind(f).Bind(g) == m.Bind(x => f(x).Bind(g))`

Essas leis garantem previsibilidade ao compor operações com Monads.

---

## 🛠️ Dicas Práticas

- Use monads para **encapsular efeitos, controle de erro, nulidade, sequências, etc**;
- **Bind** deve ser usado quando a função retorna uma monad;
- Use `Map` quando a função retorna um valor simples;
- Preferível em pipelines de validação, transformação ou execução com falha controlada.

---

## ⚠️ Cuidado

- Monads não são "mágicas" — são um padrão para composição com contexto;
- O uso excessivo pode aumentar complexidade se mal compreendido;
- Prefira `Option`, `Either`, `Task`, `IEnumerable` ao invés de criar novas monads, a menos que necessário.

---

## 📚 Recomendado

- [Category Theory for Programmers - Bartosz Milewski](https://github.com/hmemcpy/milewski-ctfp-pdf)
- [Functional Programming in C#](https://github.com/la-yumba/functional-csharp-code)
