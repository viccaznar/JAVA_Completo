# Cartões de Resumo: Programação Funcional, Expressões Lambda e Comparator em Java 🚀🔧

  Neste cartão, exploramos como a programação funcional e as expressões lambda, introduzidas no Java 8, permitem trabalhar de forma mais flexível com a ordenação de objetos usando o **Comparator**. Veremos como isso ajuda a desacoplar a lógica de comparação da própria classe de domínio.


## 1. Contexto e Problema

  - **Cenário:**  
    Imagine uma classe `Product` com os atributos `name` e `price`. Uma abordagem tradicional seria fazer com que `Product` implemente `Comparable<Product>` para definir sua ordem natural.


    - **Problema:**  
      Se o critério de comparação mudar (por exemplo, ordenar por preço em vez de nome), você teria que alterar a classe `Product`, o que viola o princípio de "fechado para alteração".


    - **Solução:**  
      Utilizar a interface **Comparator** para criar objetos que definam diferentes critérios de ordenação sem modificar a classe `Product`. Dessa forma, você pode passar um Comparator como argumento para o método default `sort` da interface `List`:


      ```java
        default void sort(Comparator<? super E> c)
      ```


## 2. Fundamentos do Comparator

  - **Comparator:**


    - É uma interface funcional (apenas um método abstrato: compare(T o1, T o2)) usada para definir a forma de ordenar objetos.


    - Permite criar diferentes estratégias de ordenação sem alterar as classes dos objetos a serem comparados.



  - **Formas de Criar um Comparator:**


    - **Objeto de Classe Separada:** Criar uma classe que implementa Comparator<Product>.


    - **Classe Anônima:** Instanciar um Comparator diretamente usando uma classe anônima.



    - **Expressões Lambda:**


      - **Com chaves:** Fornecendo um bloco de código com { ... }.


      - **Sem chaves:** Expressões concisas de única linha.


    - **Comparator Direto no Argumento:** Definir o Comparator inline na chamada do método sort.



### Exemplo Lúdico 🎲

  Imagine que você tem uma coleção de livros.


  - **Sem Comparator:** Cada livro "conhece" apenas sua ordenação natural, mas se você precisar ordenar os livros por um critério diferente (por exemplo, por data de publicação em vez de título), terá que modificar a classe Livro.


  - **Com Comparator:** Você cria "filtros" ou "regras" de ordenação que podem ser aplicadas dependendo da necessidade. É como ter diferentes lentes para olhar a coleção: uma lente pode ordenar por título, outra por ano de publicação - e você escolhe a que melhor atende à situação sem alterar os livros.



### Exemplo Prático 💻

  - **Definindo a Classe Product:**


  ```java
    package entities;

    public class Product {
        private String name;
        private Double price;
        
        public Product(String name, Double price) {
            this.name = name;
            this.price = price;
        }
        
        // Getters e setters omitidos para brevidade

        @Override
        public String toString() {
            return "Product [name=" + name + ", price=" + price + "]";
        }
    }
  ```


  - **Usando Comparator para Ordenar Produtos:**


    - **Comparator como Classe Anônima**


    ```java
      import java.util.ArrayList;
      import java.util.Collections;
      import java.util.List;
      import entities.Product;

      public class Program {
          public static void main(String[] args) {
              List<Product> products = new ArrayList<>();
              products.add(new Product("TV", 900.0));
              products.add(new Product("Notebook", 1200.0));
              products.add(new Product("Tablet", 400.0));
              
              // Ordena produtos por nome (sem alterar a classe Product) usando Comparator (classe anônima)
              Collections.sort(products, new Comparator<Product>() {
                  @Override
                  public int compare(Product p1, Product p2) {
                      return p1.toString().compareTo(p2.toString()); // exemplo simples
                  }
              });
              
              // Impressão dos produtos ordenados
              for (Product p : products) {
                  System.out.println(p);
              }
          }
      }
    ```


  - **Comparator com Expressões Lambda (Sem chaves)**


  ```java
    import java.util.ArrayList;
    import java.util.List;
    import entities.Product;

    public class ProgramLambda {
        public static void main(String[] args) {
            List<Product> products = new ArrayList<>();
            products.add(new Product("TV", 900.0));
            products.add(new Product("Notebook", 1200.0));
            products.add(new Product("Tablet", 400.0));
            
            // Ordena por nome utilizando lambda direto no argumento do método sort
            products.sort((p1, p2) -> p1.toString().compareTo(p2.toString()));
            
            // Impressão dos produtos ordenados
            products.forEach(System.out::println);
        }
    }
  ```


  - **Obs.:** No exemplo, usamos toString() apenas para ilustrar; normalmente, você usaria critérios reais, como p1.getName().compareToIgnoreCase(p2.getName()) ou comparando preços.


### Conclusão 🏁

  Programação Funcional e Expressões Lambda: Permitem escrever código mais conciso e flexível.


  - **Comparator:** É uma alternativa poderosa ao uso de Comparable que desacopla o critério de ordenação da classe de domínio.


  - **Várias formas de implementação:** classe separada, anônima ou expressão lambda.


  - **Uso do Método sort da Interface List:** Permite ordenar coleções sem modificar os objetos armazenados.


Adote o uso de Comparator com expressões lambda para criar soluções flexíveis e adaptáveis, sem comprometer a integridade das classes originais! 😊🚀