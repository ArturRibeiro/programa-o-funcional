
# 🧮 Conceito: Mutação de Estado em C#

## O que é uma Mutação de Estado?

Mutação de estado ocorre quando o **valor armazenado em uma variável é alterado** após sua declaração. No paradigma imperativo, isso é comum e essencial para representar a evolução do sistema ao longo do tempo.

---

## 🎯 Propósito

- Permitir que variáveis reflitam mudanças no comportamento do programa.
- Controlar fluxos de decisão baseados em atualizações de valores.
- Simular sistemas dinâmicos e interativos.

---

## 💡 Exemplo de Mutação de Estado

```csharp
int contador = 0;
contador = contador + 1;
contador += 5;
```

---

## 🧾 Uso

- `contador = contador + 1;` — Incremento tradicional.
- `contador += 5;` — Operação abreviada de mutação.
- Mutação é usada com frequência em laços (`for`, `while`) e operações condicionais.

---

## ❌ Exemplo de Mutação de Estado (Evite em Mutação de Estado)

```csharp
int total = 0;
for (int i = 0; i < 100; i++)
{
    total = total + i;
    Console.WriteLine(total); // Efeito colateral dentro do loop
}
```

⚠️ Evite acoplamento entre mutação e saída (I/O) no mesmo bloco. Isso dificulta testes e manutenção.

---

## ⚠️ Problemas

- Introduz **efeitos colaterais**.
- Dificulta **testes unitários**, especialmente em código acoplado.
- Pode gerar **condições de corrida** em ambientes concorrentes.

---

## 🛠️ Dica de Uso no Dia a Dia

✅ Use mutações **localizadas e previsíveis**.  
✅ Considere o uso de `readonly` e `record` quando imutabilidade for desejável.  
✅ Em métodos, minimize alterações de estado global.

```csharp
int Soma(int a, int b)
    => a + b; // Função pura, sem mutação

void Incrementar(ref int valor)
    => valor++; // Mutação explícita, clara e localizada
```

---
