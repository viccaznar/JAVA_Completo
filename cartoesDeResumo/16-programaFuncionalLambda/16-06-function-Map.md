# Cartões de Resumo: Function e map em Java 🌀🔄

  A interface **Function** e o método **map** das **Streams** permitem transformar coleções de forma declarativa, aplicando uma função a cada elemento e gerando uma nova coleção com os resultados.


## 1. Interface Function<T, R>


  - **Definição:**  


    ```java
    public interface Function<T, R> {
        R apply(T t);
    }
    ```


  - **T:** tipo de entrada


  - **R:** tipo de saída



  - O método apply recebe um objeto T e retorna um objeto R.


    - **Uso:** Permite encapsular uma lógica de transformação (por exemplo, converter um Product em seu nome, ou uma String em maiúsculas).


## 2. Streams e o Método map

  - **Streams:**

    - Uma Stream é uma sequência de elementos que pode ser processada de forma funcional e declarativa.


    - Permite operações como filtragem, mapeamento e redução de forma eficiente e concisa.


  - Cria-se uma Stream a partir de uma coleção com .stream().


  - Depois de transformar os elementos, converte-se de volta para List com .collect(Collectors.toList()).


  - **map:**
  
    - É um método da Stream que recebe uma Function<T, R> e aplica essa função a cada elemento da Stream.


  - É um método intermediário que aplica uma Function<T,R> a cada elemento de uma stream, produzindo uma Stream<R>.


  - **Exemplo de Uso:**

    - Para transformar uma Stream de Product em uma Stream de String (nomes dos produtos), usa-se:


    ```java
    stream.map(function)
    ```


## 3. Problema Exemplo

  - **Objetivo:** A partir de uma lista de Product, gerar uma nova lista contendo apenas os nomes em caixa alta.


  ```java
    List<Product> list = new ArrayList<>();
    list.add(new Product("Tv", 900.00));
    list.add(new Product("Mouse", 50.00));
    list.add(new Product("Tablet", 350.50));
    list.add(new Product("HD Case", 80.90));
  ```


## 4. Exemplo Lúdico 🎲

  Imagine um tradutor mágico que pega uma coleção de palavras em diferentes idiomas e as transforma todas para inglês.


  - Cada palavra (elemento) entra no tradutor (Function) e sai traduzida.


  - Depois dessa “tradução em massa” (map), você obtém uma nova lista de palavras em inglês.


### Exemplo Prático 💻

  ```java
    package application;

    import java.util.ArrayList;
    import java.util.List;
    import java.util.stream.Collectors;
    import entities.Product;

    public class Program {
        public static void main(String[] args) {
            List<Product> list = new ArrayList<>();
            list.add(new Product("Tv", 900.00));
            list.add(new Product("Mouse", 50.00));
            list.add(new Product("Tablet", 350.50));
            list.add(new Product("HD Case", 80.90));

            // Função que extrai e converte o nome para maiúsculas
            Function<Product, String> toUpperName = p -> p.getName().toUpperCase();

            // Cria nova lista de nomes em caixa alta
            List<String> names = list.stream()
                                    .map(toUpperName)
                                    .collect(Collectors.toList());

            // Imprime o resultado
            names.forEach(System.out::println);
        }
    }
  ```


  - **Conversions:**


    ```java
      List<Product> → Stream<Product>: list.stream()
    ```


    ```java
    Stream<String> → List<String>: .collect(Collectors.toList())
    ```



## 5. Conclusão 🏁

  - **Function<T,R>:** Define uma transformação de T para R via apply.


  - **map:** Aplica essa transformação a cada elemento de uma stream.


  - **Streams + map:** Poderoso para criar pipelines de processamento de coleções de forma declarativa e concisa.


Domine Function e map para escrever código Java mais expressivo, modular e enxuto! 😊🚀