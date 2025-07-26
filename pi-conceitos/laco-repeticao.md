
# 🧮 Conceito: Laço de Repetição em C#

## O que é um Laço de Repetição?

Um **laço de repetição** (ou loop) é uma estrutura de controle que permite executar um bloco de código **várias vezes**, enquanto uma condição for verdadeira ou até que uma sequência se esgote. É essencial no paradigma imperativo para automatizar tarefas repetitivas.

---

## 🎯 Propósito

- Repetir instruções até que uma condição de parada seja atingida.
- Iterar sobre coleções de dados.
- Automatizar contagens, somas, buscas e verificações.

---

## 💡 Exemplo de Laço de Repetição

```csharp
for (int i = 0; i < 5; i++)
{
    Console.WriteLine($"Valor de i: {i}");
}
```

---

## 🧾 Uso

- `for`: usado quando se conhece o número de iterações.
- `while`: executa enquanto a condição for verdadeira.
- `do while`: executa pelo menos uma vez.
- `foreach`: percorre coleções como arrays ou listas.

```csharp
string[] nomes = { "Ana", "Bruno", "Carlos" };

foreach (var nome in nomes)
{
    Console.WriteLine(nome);
}
```

---

## ❌ Exemplo de Laço de Repetição (Evite em Laço de Repetição)

```csharp
while (true)
{
    // Loop infinito sem condição de saída
}
```

⚠️ Evite laços sem condição de saída clara. Eles podem travar o sistema.

---

## ⚠️ Problemas

- Loops infinitos por erro lógico.
- Acesso fora dos limites da coleção.
- Performance degradada com coleções grandes sem controle.

---

## 🛠️ Dica de Uso no Dia a Dia

✅ Use `foreach` para iterar coleções sem modificar índices.  
✅ Use `break` para sair de loops quando necessário, mas com moderação.  
✅ Evite lógica complexa no corpo do laço — delegue para métodos separados.

```csharp
foreach (var produto in produtos)
{
    if (!ProdutoValido(produto))
        continue;

    Processar(produto);
}
```

---
