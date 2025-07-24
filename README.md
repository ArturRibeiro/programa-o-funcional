## 📊 Tabela: Conceitos de Programação Funcional em C#

| Conceito                         | Descrição Técnica                                                                 | Propósito Prático                                                                                  |
|----------------------------------|------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------|
| **[Função Pura](http://x "Função Pura")**                  | Função que não depende de ou modifica estado externo.                             | Facilita testes unitários e concorrência segura.                                                    |
| **Imutabilidade**                | Dados não são modificados após sua criação.                                       | Evita efeitos colaterais e simplifica o raciocínio sobre o estado do sistema.                      |
| **Funções de Ordem Superior**    | Funções que recebem ou retornam outras funções (`Func`, `Action`, `Predicate`).   | Permite reutilização e composição de lógica.                                                        |
| **Currying**                     | Transformação de uma função de múltiplos argumentos em uma cadeia de funções unárias. | Torna funções mais reutilizáveis e compatíveis com `Partial Application`.                         |
| **Partial Application**          | Fixar um ou mais parâmetros de uma função, criando uma nova função com menos argumentos. | Especializa funções de forma incremental.                                                          |
| **Composição de Funções**       | Combinar duas ou mais funções em uma única, aplicando uma após a outra.           | Modulariza pipelines de dados e lógica.                                                            |
| **Option (Maybe Monad)**         | Representa presença ou ausência de valor sem usar `null`.                         | Elimina o uso de `null` e facilita controle de fluxo.                                               |
| **Either (Erro Funcional)**      | Representa valor de sucesso (`Right`) ou erro (`Left`).                           | Modela erros como valores previsíveis ao invés de lançar exceções.                                 |
| **Map**                          | Aplica uma função sobre o valor interno de um `Option`, `Either`, `List`, etc.     | Transforma valores encapsulados de forma segura.                                                   |
| **Bind (FlatMap / SelectMany)**  | Encadeia funções que retornam tipos elevados (`Option`, `Either`, etc.).           | Permite criar pipelines funcionais com controle de fluxo robusto.                                  |
| **LINQ Funcional**               | Uso de `Where`, `Select`, `Aggregate`, etc. sobre `IEnumerable` como funções puras. | Facilita o processamento funcional sobre coleções.                                                  |
| **Recursão (tail recursion)**    | Repetição baseada em chamada de função a si mesma.                                | Evita uso de loops imperativos (com suporte limitado em C# sem TCO).                              |
| **Lazy Evaluation**              | Avaliação de expressões apenas quando necessário (`Lazy<T>`, `yield return`).     | Aumenta performance em coleções ou cálculos pesados e potencialmente infinitos.                    |
| **Monads**                       | Padrão para encadear operações em tipos elevados (`Option`, `Either`, `Task`, etc.). | Uniformiza encadeamentos seguros e previsíveis em contextos com efeitos colaterais.               |
| **Expression Trees**             | Representam funções como dados (`Expression<Func<T>>`).                           | Permite compor, serializar ou executar expressões de forma dinâmica (ex: EF Core, LINQ).           |


### 🧮 Conceito: Função Pura em C#

#### ✅ O que é uma Função Pura?

Uma **função pura** é uma função que:

1. **Sempre retorna o mesmo resultado** para os mesmos argumentos;
2. **Não possui efeitos colaterais** (não altera estado externo, não grava em disco, não envia e-mails, etc).

---

#### 🎯 Propósito

- **Previsibilidade**: comportamento determinístico.
- **Testabilidade**: fácil de testar com dados de entrada e verificar o resultado.
- **Paralelismo seguro**: pode ser executada em múltiplas threads sem conflitos de estado.

---

#### 🧪 Exemplo de Função Pura

```csharp
public class FuncoesMatematicas
{
    public static int Somar(int a, int b)
        => a + b;

    public static int Dobrar(int x)
        => x * 2;
}


