
# 🧮 Conceito: Função Pura em C#

## ✅ O que é uma Função Pura?

Uma **função pura** é uma função que:

1. **Sempre retorna o mesmo resultado** para os mesmos argumentos;
2. **Não possui efeitos colaterais** (não altera estado externo, não grava em disco, não envia e-mails, etc).

---

## 🎯 Propósito

- **Previsibilidade**: comportamento determinístico.
- **Testabilidade**: fácil de testar com dados de entrada e verificar o resultado.
- **Paralelismo seguro**: pode ser executada em múltiplas threads sem conflitos de estado.

---

## 💡 Exemplo de Função Pura

```csharp
public class FuncoesMatematicas
{
    public static int Somar(int a, int b)
        => a + b;

    public static int Dobrar(int x)
        => x * 2;
}
```

---

## 🧾 Uso

```csharp
public class Program
{
    public static void Main()
    {
        var resultado1 = FuncoesMatematicas.Somar(3, 5); // 8
        var resultado2 = FuncoesMatematicas.Somar(3, 5); // 8 sempre, sem exceção

        Console.WriteLine(FuncoesMatematicas.Dobrar(10)); // 20
    }
}
```

---

## ❌ Exemplo de Função Impura (Evite em programação funcional)

```csharp
public static int SomarComLog(int a, int b)
{
    var resultado = a + b;
    Console.WriteLine($"Somando {a} + {b} = {resultado}");
    return resultado;
}
```

---

## ⚠️ Problemas

- Tem **efeito colateral**: escreve no console.
- Quebra o princípio de isolamento e previsibilidade.

---

## 🛠️ Dica de Uso no Dia a Dia

Utilize funções puras para:

- Regras de negócio (ex: cálculo de impostos);
- Transformações de dados;
- Validações puras (`string.IsNullOrWhiteSpace`, regex, etc).

Evite dependências externas como `DateTime.Now`, `Guid.NewGuid()`, `Console.WriteLine()` dentro de funções puras.  
Caso precise, use **injeção de dependência funcional**.

---
