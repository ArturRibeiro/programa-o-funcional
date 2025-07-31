
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

## 📊 Métodos e seus Propósitos

| Método       | Propósito                                                                 |
|--------------|---------------------------------------------------------------------------|
| `Match`      | Avalia `Left` ou `Right` e retorna um valor em ambos os casos             |
| `Map`        | Aplica uma função apenas se for `Right`, preservando `Left`               |
| `Bind`       | Aplica uma função que também retorna um `Either` (evita `nested Either`)  |

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


# 📦 Comparativo: Venda Online com Programação Funcional vs Imperativa

Este material demonstra a diferença entre os estilos de programação **funcional** e **imperativo** no contexto de uma aplicação de venda online com:

- Busca de produto
- Verificação de estoque
- Validação da forma de pagamento
- Geração de pedido

---

## ✅ Estilo Funcional (`ApplicationProgramacaoFuncional.cs`)

**Características:**

- Utiliza `Either<string, T>` para representar erros ou sucesso
- Encadeamento de operações com `Bind`
- Sem uso de exceções
- Alta testabilidade
- Separação clara de responsabilidades com funções puras

### Fluxo:

```csharp
BuscarProduto
  → VerificarEstoque
    → ValidarPagamento
      → GerarPedido
```

### Exemplo:

```csharp
return BuscarProduto(produtoId)
    .Bind(produto => VerificarEstoque(produto, quantidade)
        .Bind(_ => ValidarPagamento(pagamentoTexto)
            .Bind(fp => GerarPedido(produto, quantidade, fp))));
```

---

## 🛠 Estilo Imperativo (`ApplicationProgramacaoImperativa.cs`)

**Características:**

- Usa `try/catch` para tratamento de erro
- Estrutura sequencial clássica
- Lançamento de exceções para controle de fluxo
- Mais próximo de código típico em aplicações comerciais

### Fluxo:

```csharp
Produto → if null → throw
Estoque → if < quantidade → throw
Pagamento → if invalid → throw
→ Calcula total e retorna Pedido
```

### Exemplo:

```csharp
if (!Enum.TryParse<FormaPagamento>(pagamentoTexto, out var formaPagamento))
    throw new Exception("Forma de pagamento inválida.");
```

---

## 📊 Tabela Comparativa

| Aspecto              | Funcional (`Either`)                     | Imperativo (`try/catch`)               |
|----------------------|------------------------------------------|----------------------------------------|
| Tratamento de Erro   | `Either.Left` e `Right` (explícito)     | Exceções (`throw`)                     |
| Fluxo de Controle    | Encadeado (`Bind`, `Map`)               | Linear com `if` e `throw`              |
| Clareza              | Mais declarativo                       | Mais direto, mas com duplicações       |
| Testabilidade        | Alta (sem exceções)                    | Boa, exige mocks e validações extras   |
| Composição           | Natural com funções                    | Verbosa com `if`/`else`                |
| Tipagem de Erro      | Estruturado por tipos                  | Apenas `string` ou exceção             |

---

## 🧾 Arquivos de Referência

#### 🧱 Programação Funcional

```csharp
public static Either<string, PedidoPF> ProcessarVenda(string produtoId
    , int quantidade
    , string formaPagamentoTexto)
{
    var pedidoRepository = new PedidoRepositoryPF();

    return pedidoRepository.Obter(produtoId)
        .Bind(produto => VerificarEstoque(produto, quantidade)
            .Bind(_ => ValidarPagamento(formaPagamentoTexto)
                .Bind(formaValida => GerarPedido(produto, quantidade, formaValida))
            )
        );
}

private static readonly Func<ProdutoPF, int, Either<string, ProdutoPF>> VerificarEstoque =
    (produto, quantidade)
        => produto.Estoque >= quantidade
            ? new Right<string, ProdutoPF>(produto)
            : new Left<string, ProdutoPF>("Estoque insuficiente.");

private static Either<string, FormaPagamentoPF> ValidarPagamento
    (string input)
    => Enum.TryParse<FormaPagamentoPF>(input, ignoreCase: true, out var formaValida)
        ? new Right<string, FormaPagamentoPF>(formaValida)
        : new Left<string, FormaPagamentoPF>("Forma de pagamento inválida.");

private static readonly Func<ProdutoPF, int, FormaPagamentoPF, Either<string, PedidoPF>> GerarPedido =
    (produto, quantidade, pagamento) 
        => new Right<string, PedidoPF>(new PedidoPF(produto.Id, quantidade, produto.Preco * quantidade, pagamento));
```

#### 🧱 Programação Imperativa

```csharp
    public static string ProcessarVenda(string produtoId, int quantidade, string formaPagamentoTexto)
    {
        try
        {
            // Buscar produto
            var pedidoRepository = new PedidoRepositoryPI();
            var produto = pedidoRepository.Obter(produtoId);
            if (produto == null) throw new Exception("Produto não encontrado.");

            // Verificar estoque
            if (produto.Estoque < quantidade) throw new Exception("Estoque insuficiente.");
            
            // Validar forma de pagamento
            if (!Enum.TryParse<FormaPagamentoPI>(formaPagamentoTexto, ignoreCase: true, out var formaPagamento))
                throw new Exception("Forma de pagamento inválida.");
            
            // Calcular pedido
            var pedido = new PedidoPI
            {
                ProdutoId = produto.Id,
                Quantidade = quantidade,
                Total = produto.Preco * quantidade,
                PagamentoPi = formaPagamento
            };
            return $"✅ Pedido: {pedido.ProdutoId}, Quant: {pedido.Quantidade}, Total: R${pedido.Total}, Pagamento: {pedido.PagamentoPi}";
        }
        catch (Exception ex)
        {
            return $"❌ Erro: {ex.Message}";
        }
    }
```

---

## 🎯 Conclusão

- Use o estilo **funcional** quando quiser controle rigoroso de fluxo e **sem exceções**, ideal para pipelines e validações.
- Use o estilo **imperativo** quando precisar de código mais direto e legível para times acostumados ao padrão tradicional.

---

> Ambos os estilos são válidos. Escolha com base na clareza, manutenção e coesão da sua aplicação.



## 🛠️ Dicas Práticas

- Use `Right` para valores válidos e `Left` para falhas controladas;
- Substitui o uso de `try/catch` em pipelines funcionais;
- Ideal para modelar validações, acessos externos, parsing e I/O.

---

## 📚 Alternativas prontas

- [LanguageExt.Either](https://github.com/louthy/language-ext)
- [CSharpFunctionalExtensions.Either](https://github.com/vkhorikov/CSharpFunctionalExtensions)

---
