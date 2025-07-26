
# 🧮 Conceito: Operações Sequenciais em C#

## O que são Operações Sequenciais?

No paradigma imperativo, **operações sequenciais** são instruções executadas **em ordem**, uma após a outra. Essa ordem é fundamental para definir o fluxo e o resultado do programa. Cada instrução pode depender do efeito da anterior.

---

## 🎯 Propósito

- Definir um fluxo lógico claro e previsível.
- Executar tarefas em etapas controladas.
- Refletir a lógica de negócios na ordem correta.

---

## 💡 Exemplo de Operações Sequenciais

```csharp
int numero = 5;
int resultado = numero * 2;
Console.WriteLine(resultado);
```

As instruções são executadas:
1. Declaração de variável `numero`
2. Cálculo e atribuição em `resultado`
3. Impressão no console

---

## 🧾 Uso

- Comandos em sequência representam a linha do tempo de execução.
- Muito comum em inicializações, transformações, etapas de processamento.

```csharp
ObterDados();
ValidarDados();
ProcessarDados();
SalvarDados();
```

---

## ❌ Exemplo de Operações Sequenciais (Evite em Operações Sequenciais)

```csharp
Processar();
Validar(); // Inversão da ordem lógica
```

⚠️ A ordem incorreta de execução pode causar efeitos colaterais indesejados e comportamentos inesperados.

---

## ⚠️ Problemas

- Mudança de ordem pode causar falhas difíceis de identificar.
- Reuso de variáveis entre etapas pode gerar acoplamento excessivo.
- Torna difícil o isolamento de etapas para testes se misturadas.

---

## 🛠️ Dica de Uso no Dia a Dia

✅ Mantenha as operações sequenciais com **ordem lógica explícita**.  
✅ Separe etapas em **métodos bem nomeados** para manter clareza.  
✅ Documente (com comentários ou nomes de métodos) o fluxo de execução se for crítico.

```csharp
CarregarUsuario();
VerificarPermissoes();
ExibirDashboard();
```

---
