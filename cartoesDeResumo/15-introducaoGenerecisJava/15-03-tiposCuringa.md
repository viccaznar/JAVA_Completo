# Cartões de Resumo: Tipos Curinga (Wildcard Types) em Java 🎯🔀

  Generics permitem que classes, interfaces e métodos sejam parametrizados por tipo, proporcionando reuso e segurança de tipo. Contudo, os generics em Java são **invariantes**, o que significa que, por exemplo, uma `List<Integer>` **não** é considerada um subtipo de `List<Object>`. Para contornar essa limitação, utilizamos os **wildcard types** (tipos curinga).


## 1. Invariância dos Generics

  - **Conceito:**  
    Uma lista parametrizada com um tipo específico (ex.: `List<Integer>`) não pode ser atribuída a uma variável do tipo `List<Object>`, pois os generics são invariantes.


  - **Exemplo:**


    ```java
      List<Object> myObjs = new ArrayList<Object>();
      List<Integer> myNumbers = new ArrayList<Integer>();
      // myObjs = myNumbers; // ERRO de compilação!
    ```


## 2. Uso de Tipos Curinga – List<?>

  - **Definição:** O supertipo de qualquer lista parametrizada é List<?>, onde o ? é um curinga que representa "qualquer tipo".


  - **Benefícios:**
 
    - Permite referenciar listas de qualquer tipo, facilitando a criação de métodos genéricos que operam em listas sem depender de um tipo específico.


    - Proporciona flexibilidade ao trabalhar com coleções, permitindo que você escreva código mais genérico e reutilizável.


    - Permite referenciar listas de qualquer tipo.


    - Facilita a criação de métodos genéricos que operam em listas sem depender de um tipo específico.


  - **Exemplo de Atribuição:**


  ```java
    List<?> myObjs = new ArrayList<Object>();
    List<?> myObjs = new ArrayList<Object>();
    List<?> myObjs = new ArrayList<Object>();
    List<Integer> myNumbers = new ArrayList<Integer>();
    myObjs = myNumbers; // OK: List<?> aceita qualquer List<T>
  ```


## 3. Métodos que Usam Wildcard Types

  - **Exemplo de Método Genérico:** Você pode criar métodos que aceitam qualquer lista, independentemente do tipo de seus elementos.


  ```java
    public static void printList(List<?> list) {
        for (Object obj : list) {
            System.out.println(obj);
        }
    }

    // Uso:
    List<Integer> myInts = Arrays.asList(5, 2, 10);
    printList(myInts);
  ```


  - **Importante:** Esses métodos podem ler os elementos da lista, mas não permitem a adição de novos elementos, pois o compilador não sabe qual é o tipo específico da lista.


## 4. Limitações: Não é Possível Adicionar Elementos

  - **Exemplo Prático com Erro:**
  ```java
    List<?> list = new ArrayList<Integer>();
    list.add(3); // ERRO de compilação!
  ```


    - **Motivo:** O compilador não sabe qual o tipo exato da lista, e permitir adição poderia violar a segurança de tipo.


- **Exemplo Lúdico 🎲**
  Imagine uma caixa misteriosa que pode conter itens de qualquer tipo, sem que você saiba exatamente o que há dentro.


    - **Leitura:** Você pode abrir a caixa e ver os itens existentes, mas você não pode adicionar novos itens a ela, pois não tem certeza se os itens que você está tentando colocar correspondem ao que a caixa pode realmente armazenar.


    - **Wildcard:** Funciona da mesma forma—List<?> permite que você "observe" os elementos armazenados, mas não permite inserir novos elementos, garantindo a segurança de tipo.

## 5. Princípio Get/Put

  - **Get:** Você pode "obter" elementos de uma coleção com wildcard, pois o tipo é desconhecido, mas seguro.


  - **Put:** Você não pode "colocar" elementos em uma coleção com wildcard, pois o compilador não sabe qual o tipo exato.

## 6. Conclusão

  - **Generics Invariantes:** Uma List<Integer> não pode ser atribuída a List<Object>.

  - **Tipos Curinga (List<?>):** Permitem referenciar listas de qualquer tipo e criar métodos genéricos que operam em coleções com segurança.

  - **Limitação:** Com wildcards, é possível ler, mas não adicionar elementos à coleção, pois o tipo exato é desconhecido.

Domine os wildcards para escrever métodos genéricos flexíveis e seguros, melhorando o reuso e a robustez do seu código Java! 😊🚀