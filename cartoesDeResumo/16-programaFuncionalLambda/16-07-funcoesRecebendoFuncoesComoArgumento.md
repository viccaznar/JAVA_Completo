# Cartões de Resumo: Funções que Recebem Funções como Argumento 🧩✨

  Neste módulo, aprendemos a criar **funções de alta ordem** em Java—ou seja, métodos que recebem outras funções como parâmetros—usando as interfaces funcionais `Predicate`, `Function`, `Consumer` e operações de **Stream** para compor lógica de forma declarativa.


## 1. Recordando Funções Padrão em Coleções

  - **removeIf(Predicate<T> pred):**  
    Remove todos os elementos que satisfazem a condição `pred.test(t)`.


  - **forEach(Consumer<T> action):**  
    Aplica `action.accept(t)` a cada elemento da coleção.


  - **map(Function<T,R> mapper):**  
    Transforma cada elemento `T` em um `R`, produzindo uma nova `Stream<R>`.


## 2. Funções de Alta Ordem (Higher-Order Functions)

  - **Definição:**  

    Métodos que **recebem** outras funções (lambdas ou method references) como argumentos, permitindo filtrar, transformar e agregar coleções sem escrever laços explícitos.


  - **Vantagens:**  

    - **Reuso de lógica**: regras de filtro e transformação são passadas como parâmetros.  


    - **Código conciso**: reduz boilerplate de loops.  


    - **Expressividade:** foca no **“o quê”** (declaração) em vez do **“como”** (imperativo).


## 3. Problema Exemplo 🎯

  - **Objetivo:**  


  - A partir de uma `List<Product>`, **calcular a soma dos preços** apenas dos produtos cujo **nome começa com “T”**.


  ```java
    List<Product> list = new ArrayList<>();
    list.add(new Product("Tv", 900.00));
    list.add(new Product("Mouse", 50.00));
    list.add(new Product("Tablet", 350.50));
    list.add(new Product("HD Case", 80.90));
  ```


## 4. Exemplo Prático 💻

  ### 4.1. Usando Streams e Expressões Lambda


    ```java
      double sum = list.stream()
          // Filtra produtos que começam com "T"
          .filter(p -> p.getName().startsWith("T"))
          // Extrai apenas o preço de cada produto
          .map(Product::getPrice)
          // Soma todos os preços (0.0 é valor inicial)
          .reduce(0.0, Double::sum);

      System.out.printf("Sum of prices for 'T' products: %.2f%n", sum);
    ```


  - **filter:** recebe um Predicate<Product>


  - **map:** recebe um Function<Product, Double>


  - **reduce:** recebe um BinaryOperator<Double> (a soma)


 ### 4.2. Método Genérico de Soma

    - Podemos generalizar em um método:


    ```java
      public static <T> double sumIf(List<T> list,
                                    Predicate<T> filter,
                                    Function<T, Double> mapper) {
          return list.stream()
                    .filter(filter)
                    .map(mapper)
                    .reduce(0.0, Double::sum);
      }

      // Uso:
      double totalT = sumIf(list,
          p -> p.getName().startsWith("T"),
          Product::getPrice);
    ```


## 5. Exemplo Lúdico 🎲

  Imagine uma peneira mágica que seleciona apenas maçãs vermelhas de uma cesta de frutas e soma seus pontos de sabor.


  - A peneira é o filter (Predicate).


  - A balança que lê o peso de cada maçã é o map (Function).


  - O contador final que soma os pesos é o reduce (BinaryOperator). Tudo isso em um único fluxo, sem explicitar loops.



## 6. Conclusão 🏁

  - Funções de Alta Ordem aceleram a criação de pipelines de processamento: filtrar, transformar e agregar dados.


  - Streams + Lambdas proporcionam código mais legível e declarativo.


  - Você pode criar métodos genéricos que recebem Predicate, Function e outros, aumentando a modularidade e o reuso.


Experimente compor suas próprias funções de alta ordem para dominar a programação funcional em Java! 😊🚀