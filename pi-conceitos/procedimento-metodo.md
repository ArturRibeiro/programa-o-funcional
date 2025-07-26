
# 🧮 Conceito: Procedimento (Método) em C#

## O que é um Procedimento (Método)?

Um **procedimento** (ou método, em linguagens orientadas a objetos) é um bloco de código **nomeado e reutilizável**, que executa uma tarefa específica. Ele pode ou não retornar um valor. No paradigma imperativo, procedimentos são fundamentais para modularizar e organizar o código.

---

## 🎯 Propósito

- Encapsular lógica reutilizável.
- Melhorar legibilidade e manutenção.
- Reduzir repetição de código (DRY — Don’t Repeat Yourself).
- Facilitar testes unitários.

---

## 💡 Exemplo de Procedimento (Método)

```csharp
void MostrarMensagem(string nome)
{
    Console.WriteLine($"Olá, {nome}!");
}
```

Chamando o método:

```csharp
MostrarMensagem("João");
```

---

## 🧾 Uso

- Métodos com `void` não retornam valores.
- Métodos com `return` devolvem valores ao chamador.
- Os parâmetros permitem entrada de dados externos.

```csharp
int Somar(int a, int b)
{
    return a + b;
}
```

---

## ❌ Exemplo de Procedimento (Evite em Procedimento)

```csharp
void Processar()
{
    Console.WriteLine("Iniciando...");
    Console.WriteLine("Processando...");
    Console.WriteLine("Finalizando...");
}
```

⚠️ Este método tem múltiplas responsabilidades e não pode ser reutilizado. Divida-o em partes menores.

---

## ⚠️ Problemas

- Procedimentos muito longos dificultam entendimento.
- Alta complexidade ciclomática pode indicar necessidade de refatoração.
- A falta de coesão torna o código difícil de manter.

---

## 🛠️ Dica de Uso no Dia a Dia

✅ Dê nomes **claros e descritivos** que indiquem a ação:

```csharp
bool UsuarioAutenticado(string login, string senha)
```

✅ Siga o princípio de responsabilidade única:  
Cada método deve fazer **uma única coisa bem feita**.

✅ Métodos curtos são mais fáceis de entender e testar.

---
