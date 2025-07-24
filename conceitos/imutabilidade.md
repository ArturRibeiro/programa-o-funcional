
# 🧱 Conceito: Imutabilidade em C#

## ✅ O que é Imutabilidade?

**Imutabilidade** significa que **um objeto, uma vez criado, nunca muda**.  
Se for necessário alterar seu estado, um novo objeto é criado com os novos valores.

---

## 🎯 Propósito

- Evita efeitos colaterais inesperados;
- Facilita concorrência e paralelismo;
- Melhora a previsibilidade e segurança do código;
- Torna debugging e testes mais simples e confiáveis.

---

## 💡 Exemplo de Objeto Imutável

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
```

---

## 🧾 Uso

```csharp
var pessoa1 = new Pessoa("Ana", 30);
var pessoa2 = pessoa1.ComNovaIdade(31);

Console.WriteLine(pessoa1.Idade); // 30
Console.WriteLine(pessoa2.Idade); // 31
```

---

## ❌ Exemplo de Objeto Mutável (Evite para FP)

```csharp
public class Pessoa
{
    public string Nome { get; set; }
    public int Idade { get; set; }
}
```

---

## ⚠️ Problema

Modificações são feitas diretamente, o que quebra o princípio da imutabilidade.  
Isso dificulta o rastreamento de alterações e introduz efeitos colaterais em contextos concorrentes.

---

## 📦 Dica com `record` (C# 9+)

```csharp
public record Pessoa(string Nome, int Idade);
```

---

## 🔁 Atualização com `with`

```csharp
var pessoa1 = new Pessoa("João", 25);
var pessoa2 = pessoa1 with { Idade = 26 };

Console.WriteLine(pessoa1.Idade); // 25
Console.WriteLine(pessoa2.Idade); // 26
```

---

## 🛠️ Dicas Práticas

- Prefira `readonly` para campos e propriedades calculadas;
- Use `init` em propriedades para permitir definição somente na inicialização (C# 9+);
- Prefira `record` para modelar objetos de valor imutáveis;
- Retorne novas instâncias em vez de modificar objetos existentes;
- Em pipelines funcionais, mantenha os dados imutáveis entre etapas de transformação.

---
