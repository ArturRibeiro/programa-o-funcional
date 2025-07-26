
# 🧮 Conceito: Condicional em C#

## O que é uma Condicional?

Uma **condicional** é uma construção de controle de fluxo que executa blocos de código diferentes dependendo do resultado de uma **expressão booleana** (`true` ou `false`). É um dos pilares do paradigma imperativo, permitindo decisões e ramificações lógicas durante a execução.

---

## 🎯 Propósito

- Tomar decisões com base em condições.
- Controlar o fluxo do programa conforme o estado atual.
- Executar caminhos diferentes em tempo de execução.

---

## 💡 Exemplo de Condicional

```csharp
int idade = 18;

if (idade >= 18)
{
    Console.WriteLine("Maior de idade");
}
else
{
    Console.WriteLine("Menor de idade");
}
```

---

## 🧾 Uso

- `if`, `else if`, `else` são estruturas básicas para avaliação condicional.
- Também é possível utilizar `switch` para múltiplas opções.
- Operadores lógicos (`&&`, `||`, `!`) ajudam a compor condições.

---

## ❌ Exemplo de Condicional (Evite em Condicional)

```csharp
if (x = 5) // Erro: atribuição ao invés de comparação
{
    // Código nunca funciona corretamente
}
```

⚠️ Evite confundir `=` (atribuição) com `==` (comparação).  
⚠️ Não abuse de condicionais aninhadas sem abstração.

---

## ⚠️ Problemas

- Condicionais excessivas dificultam legibilidade.
- Podem indicar **baixa coesão** e violação do princípio do método único responsável.
- Se não forem bem controladas, resultam em código espaguete.

---

## 🛠️ Dica de Uso no Dia a Dia

✅ Prefira usar métodos com nomes descritivos para encapsular condições complexas.

```csharp
if (UsuarioPodeEfetuarLogin(usuario))
{
    Autenticar(usuario);
}
```

✅ Considere usar **pattern matching** com `switch` no C# moderno:

```csharp
switch (usuario)
{
    case { Idade: >= 18 }: Console.WriteLine("Adulto"); break;
    default: Console.WriteLine("Menor de idade"); break;
}
```

---
