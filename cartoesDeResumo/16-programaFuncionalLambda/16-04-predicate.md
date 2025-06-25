# Cartões de Resumo: Predicate e removeIf em Java 🎯🔍

  Este cartão apresenta o conceito de **Predicate**, uma interface funcional fundamental para programar de forma concisa e declarativa, especialmente para filtrar ou remover elementos de coleções com o método `removeIf`.


## 1. Conceito de Predicate

- **Definição:**  
  
  Uma *Predicate* é uma interface funcional (localizada em `java.util.function.Predicate`) que possui apenas um método abstrato:
  

  ```java
  public interface Predicate<T> {
      boolean test(T t);
  }
  ```


  - **Função:**
    
    -  Recebe um objeto do tipo T e retorna um boolean (true ou false) dependendo da condição testada.


    - **Uso:** Muito utilizada para filtrar dados, validar condições e, em conjunto com métodos como    removeIf, alterar coleções com base em critérios específicos.


## 2. Uso do Predicate com o método removeIf
  
  - **removeIf:** É um método da interface Collection em Java que recebe um Predicate e remove todos os elementos que satisfazem a condição (ou seja, para os quais o método test retorna true).

  
  - **Problema Exemplo:** Remover da lista de produtos todos os itens cujo preço seja inferior a R$100,00.


  ```java
    List<Product> list = new ArrayList<>();
    list.add(new Product("Tv", 900.00));
    list.add(new Product("Mouse", 50.00));
    list.add(new Product("Tablet", 350.50));
    list.add(new Product("HD Case", 80.90));
    // Após aplicar removeIf: "Mouse" e "HD Case" serão removidos.
  ```


## 3. Diferentes Abordagens para Fornecer o Predicate

  Você pode passar o Predicate de várias formas:


  - **Implementação da Interface:** Criar uma classe que implementa Predicate<Product> e define o método test(Product p).


  - **Reference Method com Método Estático:** Criar um método estático que aceite um Product e retorne um boolean, referenciando-o com Classe::método.


  - **Reference Method com Método Não Estático:** Usar um método de instância como referência para testar a condição.


  - **Expressão Lambda Declarada:** Atribuir a expressão lambda a uma variável do tipo Predicate<Product> e depois passá-la para o método.


  - **Expressão Lambda Inline:** Fornecer a lambda diretamente no argumento do método removeIf.


## 4. Exemplo Lúdico 🎲

  Imagine uma loja onde há um segurança inteligente. Esse segurança avalia cada produto ao entrar na loja e remove imediatamente os itens que não atingem um preço mínimo (por exemplo, R$100,00).


  - **Predicate:** É como o critério de avaliação do segurança, que "testa" cada produto e decide se ele deve ser deixado na loja ou removido.


  - **removeIf:** É a ação do segurança que retira os produtos indesejados, garantindo que apenas os itens de "bom valor" permaneçam disponíveis.


## 5. Exemplo Prático 💻

  - Código Completo usando Expressão Lambda Inline:


  ```java
    package application;

    import java.util.ArrayList;
    import java.util.List;
    import entities.Product; // Suponha que Product possua getPrice() e o construtor Product(String, Double)

    public class Program {
        public static void main(String[] args) {
            List<Product> list = new ArrayList<>();
            list.add(new Product("Tv", 900.00));
            list.add(new Product("Mouse", 50.00));
            list.add(new Product("Tablet", 350.50));
            list.add(new Product("HD Case", 80.90));

            // Remover elementos com preço inferior a 100 usando uma expressão lambda inline
            list.removeIf(product -> product.getPrice() < 100.00);

            // Imprimir os produtos restantes
            list.forEach(System.out::println);
        }
    }
    ```


  - **Explicação:**

   - A expressão lambda (product -> product.getPrice() < 100.00) implementa o método test da interface Predicate<Product>.

   - O método removeIf aplica esse predicate a cada elemento, removendo os que satisfazem a condição (preço menor que 100).



### Conclusão 🏁

  - Predicate é uma interface funcional com um único método test(T t) que determina se um objeto cumpre ou não uma determinada condição.


  - Em conjunto com removeIf, permite filtrar coleções de forma eficiente e concisa.


  - Diversas formas de fornecer o predicate (interface dedicada, referência de método, ou expressões lambda) aumentam a flexibilidade e a expressividade do código.


Domine o uso de Predicate e removeIf para escrever código Java mais limpo, modular e poderoso! 😊🚀