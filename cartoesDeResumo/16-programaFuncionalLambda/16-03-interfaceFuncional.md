# Cartões de Resumo: Interfaces Funcionais em Java 🎯💡

  As interfaces funcionais são a espinha dorsal da programação funcional no Java 8+ e posteriores. Elas possibilitam que você trate funções como valores e as utilize em expressões lambda, promovendo um código mais conciso e declarativo.


## 1. Conceito de Interface Funcional

  - **Definição:**  


    Uma **interface funcional** é uma interface que possui **um único método abstrato**. Esse único método é conhecido como o "método funcional" e é o contrato que a interface representa.


  - **Utilização com Expressões Lambda:**  
    Como há somente um método abstract, suas implementações podem ser fornecidas de forma concisa utilizando **expressões lambda** ao invés de classes anônimas ou implementações explícitas.


  - **Exemplo Clássico – Comparator:**  
    Em vez de modificar a classe `Product` para implementar `Comparable`, podemos criar um comparador separado:


    ```java
      public class MyComparator implements Comparator<Product> {
          @Override
          public int compare(Product p1, Product p2) {
              return p1.getName().toUpperCase()
                      .compareTo(p2.getName().toUpperCase());
          }
      }
      
      public static void main(String[] args) {
          List<Product> list = ...;
          list.sort(new MyComparator());
      }
    ```


   - **Observação:** Esse código pode ser simplificado utilizando uma expressão lambda ou method reference.


## 2. Outras Interfaces Funcionais Comuns

  - **Predicate<T>:** Representa uma função que recebe um argumento e retorna um boolean. Útil para filtros e condições.

  Documentação: Predicate


  - **Function<T, R>:** Representa uma função que recebe um argumento do tipo T e retorna um resultado do tipo R. É usada para transformações.

  Documentação: Function


  - **Consumer<T>:** Representa uma operação que recebe um argumento do tipo T e não retorna resultado, podendo gerar efeitos colaterais (por exemplo, imprimir ou modificar algum estado fora da função).

  Documentação: Consumer


  - **Nota:** Diferente das outras interfaces funcionais (que geralmente não alteram o estado externo), o Consumer é projetado para permitir efeitos colaterais.


### Exemplo Lúdico 🎲

  Imagine que você seja um maestro regendo uma orquestra.


    - As interfaces funcionais são como partituras que têm apenas uma melodia essencial (um único tema principal).


    - Usar expressões lambda é como fornecer uma pequena nota musical que todos os músicos entendem, sem a necessidade de escrever a partitura completa.


    - Se você quiser transformar a melodia de acordo com o humor do público (por exemplo, filtrar ou alterar o som), você pode usar Predicate ou Function para adaptar a música sem reescrever a peça inteira.


### Exemplo Prático 💻

  Ordenação de Produtos com Expressões Lambda e Method Reference
  Imagine que você tenha uma lista de produtos e deseja ordená-los pelo nome sem alterar a classe Product:

  ```java
    package application;

    import java.util.ArrayList;
    import java.util.List;
    import entities.Product; // Assume que Product possui os atributos name e price

    public class Program {
        public static void main(String[] args) {
            List<Product> list = new ArrayList<>();
            list.add(new Product("TV", 900.00));
            list.add(new Product("Notebook", 1200.00));
            list.add(new Product("Tablet", 450.00));
            
            // Ordenando com expressão lambda (simples e concisa)
            list.sort((p1, p2) -> p1.getName().compareToIgnoreCase(p2.getName()));
            // Ou utilizando method reference:
            // list.sort(Comparator.comparing(Product::getName, String.CASE_INSENSITIVE_ORDER));
            
            // Imprime a lista ordenada
            list.forEach(System.out::println);
        }
    }
  ```

  - **Destaques:**


    - A expressão lambda (p1, p2) -> p1.getName().compareToIgnoreCase(p2.getName()) é uma implementação concisa de um Comparator<Product>.


    - O uso do forEach(System.out::println) é uma method reference que facilita a impressão dos elementos.


### Conclusão 🏁

  Interface Funcional: Uma interface com um único método abstrato que suporta expressões lambda.


  Vantagens:


   - Código mais conciso, expressivo e flexível.


   - Permite a criação e uso imediato de comportamentos customizados sem boilerplate.


   - Interfaces Comuns: Predicate, Function, Consumer – cada uma adequada a diferentes cenários na programação funcional.


Adote o paradigma funcional e as expressões lambda para transformar seu código em algo mais limpo, modular e poderoso! 😊🚀