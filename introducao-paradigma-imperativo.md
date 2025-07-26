
# 📘 Introdução ao Paradigma Imperativo

O **paradigma imperativo** é um estilo de programação onde as instruções são dadas ao computador de forma sequencial, descrevendo **como** realizar uma tarefa, por meio de **comandos que modificam o estado interno do programa**.

Este paradigma é direto e próximo do funcionamento da máquina, o que o torna eficiente, porém com maior responsabilidade do programador sobre o controle de estado e fluxo.

---

## 🧬 Origem e História

O paradigma imperativo remonta às origens da programação computacional, sendo o estilo mais próximo do código de máquina e Assembly. Surgiu com a necessidade de controlar **explicitamente o fluxo de execução**, memória e operações aritméticas.

---

## 🗓️ Linha do Tempo

| Ano | Evento/Linguagem             | Relevância                          |
|-----|------------------------------|--------------------------------------|
| 1940s | Máquina de Turing / Assembly | Base do pensamento sequencial        |
| 1957 | **Fortran**                 | Primeira linguagem imperativa de alto nível |
| 1970 | **Pascal**                  | Organização e estruturação de programas |
| 1972 | **C**                       | Sintaxe próxima do hardware, base para Unix |
| 1983 | **C++**                     | Paradigma imperativo + OOP           |
| 1995 | **Java**                    | Imperativo com orientação a objetos  |
| 2000 | **C#**                      | Combina imperativo, OOP e funcional  |

---

## 🎯 Propósito da Programação Imperativa

O objetivo principal é:
- Oferecer **controle total sobre o estado e fluxo de execução**
- Permitir a **otimização de desempenho**
- Ser direto e próximo da máquina

É ideal para aplicações que exigem controle detalhado de recursos, como jogos, sistemas embarcados e drivers.

---

## 🧩 Características Fundamentais

| Característica              | Descrição                                                                 |
|----------------------------|---------------------------------------------------------------------------|
| 🔁 **Sequência de Instruções**   | Código executado passo a passo, na ordem escrita                        |
| 🧮 **Mutabilidade de Estado**    | Variáveis podem mudar ao longo da execução                              |
| 🔂 **Controle Explícito de Fluxo** | Uso de `if`, `while`, `for`, `switch`, etc.                            |
| 📦 **Efeitos Colaterais**        | Funções e métodos alteram variáveis externas ou globais                 |
| 🛠️ **Ordem de Execução Importa** | Diferente de programação declarativa, a ordem muda o resultado          |
| 📚 **Uso intensivo de variáveis**| O estado é salvo e alterado por meio de variáveis                       |

---

## 💬 Linguagens que adotam o Paradigma Imperativo

- **Assembly** (baixo nível)
- **Fortran**, **Pascal**
- **C**, **C++**
- **Java**, **C#**, **Python**
- **JavaScript** (com suporte a múltiplos paradigmas)

> ⚠️ Linguagens modernas como C# e JavaScript suportam múltiplos paradigmas (imperativo, orientado a objetos, funcional, etc.).

---

## 📚 Leitura Recomendada

1. **"Clean Code" – Robert C. Martin**
2. **"The Pragmatic Programmer" – Andrew Hunt, David Thomas**
3. **"Programming C# 8.0" – Ian Griffiths**
4. **"C# in Depth" – Jon Skeet**
5. **"Structure and Interpretation of Computer Programs" – Abelson, Sussman**

---

## 📊 Tabela: Conceitos de Paradigma Imperativo em C#

| Conceito                                                             | Exemplo em C#                                                        | Explicação                                         |
|----------------------------------------------------------------------|----------------------------------------------------------------------|---------------------------------------------------|
| [**Declaração de variável**](pi-conceitos/declaracao-de-variavel.md) | `int x = 10;`                                                       | Criação e atribuição inicial                      |
| [**Mutação de estado**](pi-conceitos/mutacao-de-estado.md)           | `x = x + 1;`                                                        | Estado da variável é alterado                     |
| [**Condicional**](pi-conceitos/condicional.md)                       | `if (x > 5) { ... }`                                                | Executa blocos com base em condições              |
| [**Laço de repetição**](pi-conceitos/laco-repeticao.md)              | `for (int i = 0; i < 10; i++)`                                     | Repetição de comandos                             |
| [**Procedimento (método)**](pi-conceitos/procedimento-metodo.md)     | `void MostrarMensagem() { Console.WriteLine("Olá"); }`             | Sub-rotina que executa comandos                   |
| [**Efeito colateral**](pi-conceitos/efeito-colateral.md)             | Método que altera uma variável global ou escreve no console         | Afeta elementos fora de seu escopo                |
| [**Ordem importa**](pi-conceitos/ordem-importa.md)                   | `Console.WriteLine(x); x++;` ≠ `x++; Console.WriteLine(x);`        | Ordem afeta o resultado                           |
| [**Break/Continue**](pi-conceitos/break-continue.md)                 | `for (...) { if (cond) break; }`                                   | Manipula controle de loops                        |
| [**Operações sequenciais**](pi-conceitos/operacoes-sequenciais.md)   | `A(); B(); C();`                                                   | Cada comando é executado em sequência             |
