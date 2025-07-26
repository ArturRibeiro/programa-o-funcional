
# 🧮 Conceito: Break/Continue em C#

## O que é Break e Continue?

As instruções `break` e `continue` são comandos de **controle de fluxo** usados dentro de laços (`for`, `while`, `foreach`) no paradigma imperativo. Elas alteram o comportamento padrão do loop: o `break` **interrompe completamente o laço**, enquanto o `continue` **pula para a próxima iteração**.

---

## 🎯 Propósito

- `break`: Encerrar a execução de um loop antecipadamente.
- `continue`: Pular o restante da iteração atual e continuar com a próxima.
- Controlar melhor a lógica de repetição em loops com condições específicas.

---

## 💡 Exemplo de Break e Continue

```csharp
for (int i = 0; i < 10; i++)
{
    if (i == 5)
        break;

    if (i % 2 == 0)
        continue;

    Console.WriteLine(i);
}
```

Saída:
```
1
3
```

- O `continue` pula os números pares.
- O `break` encerra o loop quando `i == 5`.

---

## 🧾 Uso

- Em loops para parar ao encontrar uma condição (ex: valor desejado).
- Evitar código desnecessário em iterações específicas.
- Pode ser usado para melhorar performance e legibilidade em certos casos.

---

## ❌ Exemplo de Break/Continue (Evite em Break/Continue)

```csharp
while (true)
{
    // lógica sem break — loop infinito não controlado
}
```

⚠️ Não use `break` ou `continue` para contornar lógica mal estruturada. Eles devem ser **usados com intenção clara**, não como atalhos para evitar refatoração.

---

## ⚠️ Problemas

- Uso excessivo pode dificultar o entendimento do fluxo.
- Pode indicar que o código do loop está fazendo **mais de uma coisa**.
- Torna mais difícil extrair o loop para um método separado.

---

## 🛠️ Dica de Uso no Dia a Dia

✅ Use `break` para **interromper loops com segurança** ao encontrar a condição necessária.  
✅ Use `continue` para **filtrar casos** no início da iteração, evitando aninhamentos profundos.

```csharp
foreach (var produto in produtos)
{
    if (!produto.EstaDisponivel)
        continue;

    Exibir(produto);
}
```

---
