# Cartões de Resumo: Pipeline de Streams em Java 🌊🔗

  Em Java 8+, **Streams** permitem criar **pipelines** de operações que processam sequências de dados de forma declarativa. A seguir, resumimos os conceitos do demo de pipeline e apresentamos um exercício prático.


## 1. O Que é um Pipeline? 🏭


  - **Definição:**  
    Cadeia (fluxo) de operações em uma `Stream` onde cada etapa recebe, transforma e entrega dados para a próxima.  


  - **Vantagens:**  


    - **Declarativo:** você descreve **o quê** fazer, não **como** iterar.  
    
    
    - **Lazy Evaluation:** etapas intermediárias só executam quando há uma operação terminal, economizando processamento.  
    
    
    - **Encadeamento:** fácil composição de filtros, mapeamentos e agregações.  



## 2. Operações Intermediárias e Terminais 🛠️🎯


  - **Intermediárias:** retornam outra `Stream` e podem ser encadeadas. Ex.:  


    - `map` – transforma cada elemento.  


    - `filter` – retém somente os que satisfazem um `Predicate`.  


    - `sorted` – ordena segundo `Comparable` ou `Comparator`.  


    - *(+ outras: `flatMap`, `peek`, `distinct`, `skip`, `limit`)*  



  - **Terminais:** encerram o pipeline, retornando valor ou coleção. Ex.:  


    - `toArray()`, `collect(...)` – converte para array ou coleção.  


    - `reduce(...)` – agrega em um único valor.  


    - `forEach(...)` – aplica ação a cada elemento.  


    - `min`, `max`, `count`, `anyMatch`, `allMatch`, `findFirst`, etc.



## 3. Demo Básico: map e reduce 🔢➕  


  ```java
    List<Integer> list = Arrays.asList(3, 4, 5, 10, 7);

    // Multiplica por 10 (map) e imprime
    Stream<Integer> st1 = list.stream().map(x -> x * 10);
    System.out.println(Arrays.toString(st1.toArray())); 
    // -> [30, 40, 50, 100, 70]

    // Soma todos os valores (reduce)
    int sum = list.stream().reduce(0, (x, y) -> x + y);
    System.out.println("Sum = " + sum); // Sum = 29
  ```



## 4. Demo Avançado: filter → map → collect 🎯🔄


  ```java
    List<Integer> newList = list.stream()
        .filter(x -> x % 2 == 0)    // somente pares
        .map(x -> x * 10)           // multiplica por 10
        .collect(Collectors.toList()); // coleta em List

    System.out.println(Arrays.toString(newList.toArray())); 
    // -> [40, 100]
  ```



## 5. Exercício Prático: CSV → média → nomes abaixo da média 📊📜


  - **Requisitos:**


    - Ler produtos de um arquivo CSV (name,price).


    - Calcular preço médio.


    - Listar nomes dos produtos com preço inferior à média, em ordem decrescente.



  ```java
     List<Product> products = Files.lines(Paths.get(path))
         .map(line -> line.split(","))         // String[] {name, price}
         .map(fields -> new Product(
             fields[0], Double.parseDouble(fields[1])
         ))
         .collect(Collectors.toList());

     // 1) Calcular média
     double avg = products.stream()
         .mapToDouble(Product::getPrice)
         .average()
         .orElse(0.0);
     System.out.printf("Average price: %.2f%n", avg);

     // 2) Filtrar, ordenar decrescente e imprimir nomes
     products.stream()
         .filter(p -> p.getPrice() < avg)
         .map(Product::getName)
         .sorted(Comparator.reverseOrder())
         .forEach(System.out::println);
  ```



### Exemplo Lúdico 🎲


  Pense num carrossel de filtros e transformações:


  - Cada cavalo (elemento) passa por uma ferramenta (filter) que escolhe quem continua,


  - Em seguida, cada um ganha uma injeção de cor (map),


  - Até chegar no final onde são coletados para o desfile (collect) ou contados (count).



## 6. Conclusão 🏁


  - Pipelines de Stream facilitam o processamento de coleções de forma modular, preguiçosa e legível.


  - Combine filter, map, sorted e reduce (ou collect) para criar fluxos poderosos de dados.


Utilize a fluidez do encadeamento para resolver problemas complexos com poucas linhas de código. 🚀😊