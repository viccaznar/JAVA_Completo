# Cartões de Resumo: Generics e Cálculo do Maior Elemento em Java 🎯📈

  Este cartão aborda como usar **Generics** para construir um serviço de cálculo que encontra o maior elemento (por exemplo, o produto mais caro) a partir de uma lista, resolvendo problemas de reuso, segurança de tipo (*type safety*) e performance.


## 1. Problema Motivador

  **Cenário:** Uma empresa de consultoria precisa avaliar a performance de diversos itens, como produtos e funcionários. Um cálculo importante é identificar o maior valor dentre um conjunto de elementos.  


  **Exemplo de Dados (arquivo):**

    - Computer,890.50 IPhone X,910.00 Tablet,550.00


  **Saída Esperada:**

  Most expensive: IPhone X, 910.00


  *Objetivo:* Ler um conjunto de produtos de um arquivo, armazená-los numa lista e encontrar o mais caro.


## 2. Conceitos Fundamentais

### Generics em Java

  - **Definição:** Permite parametrizar classes, interfaces e métodos por tipo.  


  - **Benefícios:**  

    - **Reuso:** Uma implementação única funciona para diferentes tipos.  


    - **Type Safety:** Erros de tipo são detectados em tempo de compilação.  


    - **Performance:** Evita a necessidade de castings desnecessários.


  *Exemplo comum:*


    ```java
      List<String> list = new ArrayList<>();
      list.add("Maria");
      String name = list.get(0);  // Nenhum cast necessário
    ```


  - **Interface Comparable**


    - **Objetivo:** Define a ordem natural dos objetos por meio do método compareTo(T o).


      - **Contrato do compareTo:**


        - Retorna um negativo se o objeto atual for menor que o.


        - Retorna zero se forem iguais.


        - Retorna um positivo se o objeto atual for maior que o.


## 3. Serviço de Cálculo do Maior Elemento

  Para encontrar o maior elemento em uma lista, cria-se um método genérico que utiliza o contrato da interface Comparable.

  - **Implementação Básica**

  ```java
        T max = list.get(0);
        for (T item : list) {
            if (item.compareTo(max) > 0) {
                max = item;
            }
        }
        return max;
  ```


- **Versão Alternativa (mais completa)**


```java
      public static <T extends Comparable<? super T>> T max(List<T> list) {
          if (list.isEmpty()) {
              throw new IllegalStateException("List can't be empty");
          }
          T max = list.get(0);
          for (T item : list) {
              if (item.compareTo(max) > 0) {
                  max = item;
              }
          }
          return max;
      }
```


  - *Observação:* A versão com `<? super T>` amplia a compatibilidade com hierarquias de tipos, garantindo que o método funcione corretamente para qualquer tipo que implemente Comparable.


  - **Versão Alternativa (mais completa)**

    ```java
      public static <T extends Comparable<? super T>> T max(List<T> list) {
          if (list.isEmpty()) {
              throw new IllegalStateException("List can't be empty");
          }
          T max = list.get(0);
          for (T item : list) {
              if (item.compareTo(max) > 0) {
                  max = item;
              }
          }
          return max;
      }
    ```

 - **Observação:** A versão com <? super T> amplia a compatibilidade com hierarquias de tipos, garantindo que o método funcione corretamente para qualquer tipo que implemente Comparable.


### Exemplo Lúdico 🎲

  Imagine que cada produto é um corredor em uma corrida. 
  Cada corredor tem um "tempo" medido pelo seu preço – quanto maior, melhor sua performance. O método max é como um juiz que, comparando os tempos (preços), determina qual corredor (produto) cruzou a linha de chegada como o vencedor, ou seja, o mais caro. 
  Essa abordagem evita que o juiz tenha que "reavaliar" cada corredor de forma independente, utilizando regras claras para a comparação.


### Exemplo Prático 💻

  - **Classe Produto (Product)**

  ```java
    package entities;

    public class Product implements Comparable<Product> {
        private String name;
        private Double price;
        
        public Product(String name, Double price) {
            this.name = name;
            this.price = price;
        }
        
        public String getName() {
            return name;
        }
        
        public Double getPrice() {
            return price;
        }
        
        // Ordem natural baseada no preço
        @Override
        public int compareTo(Product other) {
            return this.price.compareTo(other.getPrice());
        }
        
        @Override
        public String toString() {
            return name + ", " + price;
        }
    }
  ```


  - **Programa Principal**


    ```java
    package application;

    import java.util.ArrayList;
    import java.util.List;
    import entities.Product;
    import services.CalculationService;

    public class Program {
        public static void main(String[] args) {
            // Cria uma lista de produtos
            List<Product> products = new ArrayList<>();
            products.add(new Product("Computer", 890.50));
            products.add(new Product("IPhone X", 910.00));
            products.add(new Product("Tablet", 550.00));
            
            // Usa o serviço de cálculo para encontrar o produto mais caro
            Product mostExpensive = CalculationService.max(products);
            System.out.println("Most expensive:");
            System.out.println(mostExpensive);
        }
    }
    ```


  - **Resultado Esperado:**


    ```console
      Most expensive:
      IPhone X, 910.0
    ```


### Conclusão

  - **Generics:** Permitem criar métodos e classes reutilizáveis, garantindo segurança e performance ao trabalhar com múltiplos tipos.


  - **Interface Comparable:** Define como os objetos são comparados, essencial para ordenar e encontrar o máximo em coleções.


  - **CalculationService:** Um exemplo prático que demonstra como encontrar o maior elemento de uma lista de produtos (ou qualquer outro tipo que implemente Comparable), promovendo reuso e flexibilidade no código.


Domine o uso de Generics e da interface Comparable para desenvolver aplicações Java robustas e flexíveis! 😊🚀