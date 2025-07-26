
# 🧮 Conceito: Declaração de Variável em C#

## O que é uma Declaração de Variável?

A **declaração de variável** é o ato de informar ao compilador que você irá utilizar um identificador (nome) para armazenar um valor de determinado **tipo de dado**. Em linguagens imperativas como C#, isso também define o espaço de memória a ser alocado para esse dado.

---

## 🎯 Propósito

- Armazenar valores temporários durante a execução de um programa.
- Manipular o estado do sistema.
- Tornar o código mais legível ao nomear dados.

---

## 💡 Exemplo de Declaração de Variável

```csharp
int idade = 30;
string nome = "Maria";
bool ativo = true;
double saldo = 1540.75;
```

---

## 🧾 Uso

- `int idade = 30;` — Armazena um número inteiro.
- `string nome = "Maria";` — Texto com o nome da pessoa.
- `bool ativo = true;` — Valor lógico que representa um estado.
- `double saldo = 1540.75;` — Valor decimal para cálculos financeiros.

---

## ❌ Exemplo de Declaração de Variável (Evite em Declaração de Variável)

```csharp
var x = 10;
var y = 15.5;
var z = true;
```

⚠️ **Evite** nomes genéricos como `x`, `y`, `z` fora de contextos matemáticos. Eles dificultam a leitura e manutenção do código.

---

## ⚠️ Problemas

- Nomes pouco descritivos geram ambiguidade.
- Alterar o tipo de dado exige atenção para não quebrar o código.
- Variáveis globais podem levar a efeitos colaterais difíceis de rastrear.

---

## 🛠️ Dica de Uso no Dia a Dia

✅ Use nomes que reflitam **intenção clara**:

```csharp
int quantidadeDeProdutos = 10;
bool usuarioAutenticado = false;
decimal precoTotal = 199.99m;
```

✅ Use `var` apenas quando o tipo for **óbvio e legível** no contexto.

---

