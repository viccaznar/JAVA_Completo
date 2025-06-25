# Cartões de Resumo: Consumer e forEach em Java 🍏➡️📋

  O **Consumer** é uma interface funcional que representa uma operação com efeitos colaterais sobre um objeto. Muito usada com o método `forEach` para aplicar uma ação a cada elemento de uma coleção.


## 1. Conceito de Consumer

  - **Definição:**  


    ```java
    public interface Consumer<T> {
        void accept(T t);
    }
    ```


  - Recebe um objeto do tipo T e não retorna valor.

  - Ideal para operações que modificam o estado (efeitos colaterais).


  - **Uso com forEach:**


    ```java
    list.forEach(consumer);
    ```


  - Aplica o Consumer a cada elemento da lista.


## 2. Problema Exemplo 💰

  A partir de uma lista de produtos, queremos aumentar o preço de cada item em 10%:


    ```java
      List<Product> list = new ArrayList<>();
      list.add(new Product("Tv", 900.00));
      list.add(new Product("Mouse", 50.00));
      list.add(new Product("Tablet", 350.50));
      list.add(new Product("HD Case", 80.90));
      list.forEach(consumer);
    ```


  - Aplica o Consumer a cada elemento da lista.



## 3. Problema Exemplo 💰

  A partir de uma lista de produtos, queremos aumentar o preço de cada item em 10%:


  ```java
    List<Product> list = new ArrayList<>();
    list.add(new Product("Tv", 900.00));
    list.add(new Product("Mouse", 50.00));
    list.add(new Product("Tablet", 350.50));
    list.add(new Product("HD Case", 80.90));
  ```



### Exemplo Lúdico 🎲

  Imagine que você é um 🎨 artista aplicando uma tinta especial em cada obra de arte da galeria.


  - **Consumer:** É o pincel carregado com tinta.


  - **forEach:** É o movimento de passar o pincel em cada tela, deixando todas as obras com uma camada nova.


### Exemplo Prático 💻

  ```java
    package application;

    import java.util.ArrayList;
    import java.util.List;
    import entities.Product;

    public class Program {
        public static void main(String[] args) {
            List<Product> list = new ArrayList<>();
            list.add(new Product("Tv", 900.00));
            list.add(new Product("Mouse", 50.00));
            list.add(new Product("Tablet", 350.50));
            list.add(new Product("HD Case", 80.90));

            // Aumenta 10% do preço de cada produto usando Consumer via lambda
            list.forEach(product -> product.setPrice(product.getPrice() * 1.10));

            // Imprime resultados
            list.forEach(System.out::println);
        }
    }
  ```


  - **Lambda:** product -> product.setPrice(...) implementa accept.


  - **Method Reference:** System.out::println simplifica a impressão.


## 4. Conclusão 🏁

  - **Consumer:** Operações com efeito sobre cada elemento.


  - **forEach + Consumer:** Forma concisa e declarativa de iterar e modificar coleções.


  - **Expressividade:** Código mais limpo e fácil de ler! 😊🚀