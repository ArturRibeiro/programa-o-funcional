# 🧱 Conceito: Imutabilidade em C#

## ✅ O que é Imutabilidade?

**Imutabilidade** significa que **um objeto, uma vez criado, nunca muda**. 
Se for necessário alterar seu estado, um novo objeto é criado com os novos valores.

---

## 🎯 Propósito

- **Evita efeitos colaterais**;
- **Facilita concorrência e paralelismo**;
- **Melhora a previsibilidade e segurança do código**;
- **Torna debugging e testes mais simples**.

---

## 🔐 Exemplo de Objeto Imutável

```csharp
public class Pessoa
{
    public string Nome { get; }
    public int Idade { get; }

    public Pessoa(string nome, int idade)
    {
        Nome = nome;
        Idade = idade;
    }

    public Pessoa ComNovaIdade(int novaIdade)
        => new Pessoa(this.Nome, novaIdade);
}
