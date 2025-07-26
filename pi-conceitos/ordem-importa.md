
# 🧮 Conceito: Ordem Importa em C#

## O que significa "Ordem Importa"?

No paradigma imperativo, a **ordem das instruções é fundamental**, pois o estado do programa pode mudar a cada comando. A execução ocorre de forma sequencial, e alterar a ordem dos comandos pode gerar resultados completamente diferentes.

---

## 🎯 Propósito

- Definir precisamente **o fluxo de execução** do programa.
- Controlar como e quando o estado será alterado.
- Garantir que efeitos colaterais ocorram na ordem correta.

---

## 💡 Exemplo de Ordem Importa

```csharp
int x = 5;
Console.WriteLine(x);
x++;
```

Saída: `5`

Se invertermos a ordem:

```csharp
int x = 5;
x++;
Console.WriteLine(x);
```

Saída: `6`

---

## 🧾 Uso

- Importante em cálculos sequenciais, atribuições, operações condicionais e loops.
- Também afeta chamadas de métodos com efeitos colaterais.

```csharp
SalvarNoBanco(dados); 
EnviarNotificacao(); 
```

A inversão dessas chamadas pode gerar falhas lógicas.

---

## ❌ Exemplo de Ordem Importa (Evite em Ordem Importa)

```csharp
AtualizarSaldo();
RegistrarLog(); // Executa log antes da operação crítica?
```

⚠️ Evite operações dependentes em sequência **sem clareza explícita**. Isso dificulta a manutenção e pode gerar efeitos colaterais incorretos.

---

## ⚠️ Problemas

- Bugs silenciosos causados por ordem incorreta de execução.
- Testes que falham apenas em determinados cenários.
- Difícil rastreamento em sistemas com muitos efeitos colaterais.

---

## 🛠️ Dica de Uso no Dia a Dia

✅ Agrupe comandos relacionados em **métodos com nomes claros** para deixar a ordem explícita.  
✅ Sempre que possível, **evite dependências ocultas** entre comandos.  
✅ Use logs ou comentários para deixar clara a importância da sequência.

```csharp
ValidarPedido();
SalvarPedido();
EnviarEmailConfirmacao();
```

---
