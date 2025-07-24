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

## 🧪 Exemplo de Função Pura

```csharp
public class FuncoesMatematicas
{
    public static int Somar(int a, int b)
        => a + b;

    public static int Dobrar(int x)
        => x * 2;
}
