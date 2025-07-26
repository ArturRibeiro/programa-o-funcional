
# 🧮 Conceito: Efeito Colateral em C#

## O que é um Efeito Colateral?

Um **efeito colateral** ocorre quando a execução de um método ou expressão **altera o estado do sistema fora de seu escopo local**, como modificar variáveis globais, escrever em arquivos ou exibir algo na tela. No paradigma imperativo, isso é comum, mas precisa ser gerenciado com cuidado.

---

## 🎯 Propósito

- Permitir que ações produzam impacto visível no mundo externo (I/O).
- Atualizar o estado compartilhado entre componentes.
- Implementar funcionalidades que interagem com o usuário, banco de dados ou sistema de arquivos.

---

## 💡 Exemplo de Efeito Colateral

```csharp
int contador = 0;

void Incrementar()
{
    contador++;
}
```

Neste caso, o método `Incrementar` altera o valor de uma variável fora de seu escopo direto.

Outro exemplo clássico:

```csharp
void Log(string mensagem)
{
    Console.WriteLine($"LOG: {mensagem}");
}
```

---

## 🧾 Uso

- Métodos que escrevem em arquivos, bancos de dados, logs ou tela.
- Atualizações de variáveis de instância, estáticas ou globais.
- Comunicação com APIs, serviços externos e dispositivos.

---

## ❌ Exemplo de Efeito Colateral (Evite em Efeito Colateral)

```csharp
int total = 0;

int Somar(int a, int b)
{
    total += a + b; // Modifica estado externo
    return total;
}
```

⚠️ Métodos que modificam variáveis externas **sem necessidade** violam o princípio da previsibilidade e dificultam testes.

---

## ⚠️ Problemas

- Reduz testabilidade e previsibilidade.
- Pode introduzir bugs difíceis de rastrear em ambientes concorrentes.
- Aumenta o acoplamento entre componentes.

---

## 🛠️ Dica de Uso no Dia a Dia

✅ Mantenha métodos **puros** sempre que possível (sem efeitos colaterais).  
✅ Quando necessário, **isole** efeitos colaterais em camadas específicas (ex: repositórios, adaptadores).  
✅ Use **injeção de dependência** para facilitar o controle e testes.

```csharp
public interface INotificador
{
    void Notificar(string mensagem);
}

public class EmailNotificador : INotificador
{
    public void Notificar(string mensagem)
        => Console.WriteLine($"Enviando email: {mensagem}");
}
```

---
