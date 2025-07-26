
# 📖 Introdução à Programação Funcional

## 🧬 Origem e História

A **programação funcional (FP)** tem suas raízes na matemática, mais precisamente no **cálculo lambda**, formalizado em **1930** por **Alonzo Church**, professor de matemática da Universidade de Princeton.  
O cálculo lambda é um sistema formal que descreve computações puramente como aplicação de funções.

### 🗓️ Linha do tempo:

| Ano  | Marco                                                                 |
|------|------------------------------------------------------------------------|
| 1930 | Alonzo Church cria o **λ-calculus**                                   |
| 1958 | Surge **LISP** — primeira linguagem funcional prática (John McCarthy) |
| 1970s | Desenvolvimento de linguagens como ML e Scheme                       |
| 1990s | Criação do **Haskell**, linguagem funcional pura moderna             |
| 2000s+ | Popularização de conceitos funcionais em linguagens imperativas      |

---

## 🎯 Propósito da Programação Funcional

O objetivo da programação funcional é **modelar computações como avaliação de funções matemáticas puras**, evitando efeitos colaterais e estados mutáveis.

### Benefícios:

- ✅ Imutabilidade como princípio central;
- ✅ Funções puras, previsíveis e testáveis;
- ✅ Estímulo à composição de funções e reutilização;
- ✅ Facilita paralelismo e concorrência;
- ✅ Reduz bugs relacionados a estado e mutabilidade.

---

## 🧠 Características Fundamentais

| Conceito               | Descrição                                                                 |
|------------------------|---------------------------------------------------------------------------|
| Funções puras          | Resultado depende apenas dos argumentos de entrada                        |
| Imutabilidade          | Dados não podem ser alterados após criação                                |
| Funções de ordem superior | Funções que recebem ou retornam outras funções                     |
| Recursão               | Preferida no lugar de loops imperativos                                   |
| Avaliação preguiçosa   | Cálculo adiado até que o valor seja necessário                            |
| Composição             | Encadeamento de funções para formar pipelines de transformação de dados   |

---

## 💬 Linguagens que adotam Programação Funcional

### Funcionais puras:

- Haskell
- Elm
- F#

### Multi-paradigma (com suporte funcional):

- C#
- Scala
- JavaScript
- Kotlin
- Python
- Rust

---

## 🔄 Paradigma Declarativo

A programação funcional é um subtipo do paradigma **declarativo**, ou seja, descreve *o que* deve ser feito, em contraste com o paradigma imperativo que descreve *como* fazer.

---

## 📚 Leitura Recomendada

- [Cálculo Lambda - Wikipedia](https://pt.wikipedia.org/wiki/C%C3%A1lculo_lambda)
- Livro: *Structure and Interpretation of Computer Programs (SICP)*
- Livro: *Functional Programming in C#* (Enrico Buonanno)

---


## 📊 Tabela: Conceitos de Programação Funcional em C#

| Conceito                         | Descrição Técnica                                                                 | Propósito Prático                                                                                  |
|----------------------------------|------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------|
| [**Função Pura**](conceitos/funcao-pura.md)                  | Função que não depende de ou modifica estado externo.                             | Facilita testes unitários e concorrência segura.                                                    |
| [**Imutabilidade**](conceitos/imutabilidade.md)                | Dados não são modificados após sua criação.                                       | Evita efeitos colaterais e simplifica o raciocínio sobre o estado do sistema.                      |
| [**Funções de Ordem Superior**](conceitos/funcoes-ordem-superior.md)    | Funções que recebem ou retornam outras funções (`Func`, `Action`, `Predicate`).   | Permite reutilização e composição de lógica.                                                        |
| [**Currying**](conceitos/currying.md)                     | Transformação de uma função de múltiplos argumentos em uma cadeia de funções unárias. | Torna funções mais reutilizáveis e compatíveis com `Partial Application`.                         |
| [**Partial Application**](conceitos/partial-application.md)          | Fixar um ou mais parâmetros de uma função, criando uma nova função com menos argumentos. | Especializa funções de forma incremental.                                                          |
| [**Composição de Funções**](conceitos/composicao-funcoes.md)       | Combinar duas ou mais funções em uma única, aplicando uma após a outra.           | Modulariza pipelines de dados e lógica.                                                            |
| [**Option (Maybe Monad)**](conceitos/option.md)         | Representa presença ou ausência de valor sem usar `null`.                         | Elimina o uso de `null` e facilita controle de fluxo.                                               |
| [**Either (Erro Funcional)**](conceitos/either.md)      | Representa valor de sucesso (`Right`) ou erro (`Left`).                           | Modela erros como valores previsíveis ao invés de lançar exceções.                                 |
| [**Map**](conceitos/map.md)                          | Aplica uma função sobre o valor interno de um `Option`, `Either`, `List`, etc.     | Transforma valores encapsulados de forma segura.                                                   |
| [**Bind (FlatMap / SelectMany)**](conceitos/bind.md)  | Encadeia funções que retornam tipos elevados (`Option`, `Either`, etc.).           | Permite criar pipelines funcionais com controle de fluxo robusto.                                  |
| [**LINQ Funcional**](conceitos/linq-funcional.md)               | Uso de `Where`, `Select`, `Aggregate`, etc. sobre `IEnumerable` como funções puras. | Facilita o processamento funcional sobre coleções.                                                  |
| [**Recursão (tail recursion)**](conceitos/recursao.md)    | Repetição baseada em chamada de função a si mesma.                                | Evita uso de loops imperativos (com suporte limitado em C# sem TCO).                              |
| [**Lazy Evaluation**](conceitos/lazy-evaluation.md)              | Avaliação de expressões apenas quando necessário (`Lazy<T>`, `yield return`).     | Aumenta performance em coleções ou cálculos pesados e potencialmente infinitos.                    |
| [**Monads**](conceitos/monads.md)                       | Padrão para encadear operações em tipos elevados (`Option`, `Either`, `Task`, etc.). | Uniformiza encadeamentos seguros e previsíveis em contextos com efeitos colaterais.               |
| [**Expression Trees**](conceitos/expression-trees.md)             | Representam funções como dados (`Expression<Func<T>>`).                           | Permite compor, serializar ou executar expressões de forma dinâmica (ex: EF Core, LINQ).           |
