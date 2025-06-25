# Cartões de Resumo: Java 8 Streams 🌊🔄

  Streams oferecem uma forma **declarativa** e **encadeada** de processar sequências de dados em Java, com suporte a paralelismo, avaliação preguiçosa e sem efeitos colaterais.


## 1. O que é Stream? 🤔

  - **Definição:**  

    Sequência de elementos de uma fonte de dados que suporta operações agregadas (pipeline).  


  - **Fontes de Dados:**  


    - Coleções (`Collection.stream()` / `parallelStream()`)  


    - Arrays (`Arrays.stream()`)  


    - `Stream.of(...)`, `Stream.ofNullable(...)`, `Stream.iterate(...)`  


    - I/O e outras APIs de geração de elementos  


## 2. Características Principais ✨

  - **Declarativa:** Iteração interna oculta (você diz “o quê”, não “como”).  


  - **Parallel-friendly:** Opera sobre dados imutáveis e seguros para threads.  


  - **Sem Efeitos Colaterais:** Ideal para código puro e previsível.  


  - **Lazy Evaluation:** Executa só quando uma operação terminal é invocada.  


  - **Acesso Sequencial:** Sem índices — navegamos de forma linear.  


  - **Single-use:** Uma vez consumida, não pode ser reutilizada.  



## 3. Pipeline de Operações 🔗

  Um pipeline de stream é composto por:


  1. **Operações Intermediárias** (retornam novas streams; são “lazy”)  


  2. **Operação Terminal** (produz resultado final e dispara o processamento)



## 4. Operações Intermediárias 🛠️

  - **filter(Predicate):** filtra elementos  


  - **map(Function):** transforma cada elemento  


  - **flatMap(Function):** “achata” fluxos de streams  


  - **peek(Consumer):** inspeção em meio ao pipeline  


  - **distinct():** remove duplicatas  


  - **sorted():** ordena elementos  


  - **skip(n):** ignora os primeiros n  


  - **limit(n):** pega até n elementos (short-circuit)  



## 5. Operações Terminais 🎯

  - **forEach(Consumer):** aplica ação em cada elemento  


  - **toArray():** gera array  


  - **reduce(...):** acumula valores  


  - **collect(...):** reúne em coleção ou outro container  


  - **min()/max():** busca extremo  


  - **count():** conta elementos  


  - **anyMatch/allMatch/noneMatch(Predicate):** verifica condição (short-circuit)  


  - **findFirst()/findAny():** obtém elemento opcional (short-circuit)  



## 6. Criando Streams 🏗️


  ```java
    List<Integer> list = Arrays.asList(3,4,5,10,7);
    Stream<Integer> st1 = list.stream();
    Stream<String> st2 = Stream.of("Maria","Alex","Bob");
    Stream<Integer> st3 = Stream.iterate(0, x -> x + 2);
    Stream<Long> st4 = Stream.iterate(new long[]{0L,1L},
        p -> new long[]{p[1], p[0]+p[1]})
      .map(p -> p[0]);
  ```


  - **Conversões:**

    - List → Stream: .stream()


    - Stream → List: .collect(Collectors.toList())

### Exemplo Lúdico 🎲

  Imagine um canal de tratamento de água:


    - A água cru (dados da fonte) entra no pipeline.


    - Cada filtro (filter), clarificador (distinct) e bombeamento (map) são operações intermediárias.


    - No final, a torneira (operação terminal collect ou forEach) libera a água tratada (resultado) para uso.



### Exemplo Prático 💻


  ```java
    List<Product> products = List.of(
      new Product("TV", 900.0),
      new Product("Mouse", 50.0),
      new Product("Tablet", 350.5),
      new Product("HD Case", 80.9)
    );

    // 1. Filtrar preços >= 100
    // 2. Extrair preços
    // 3. Somar valores
    double total = products.stream()
      .filter(p -> p.getPrice() >= 100.0)
      .map(Product::getPrice)
      .reduce(0.0, Double::sum);

    System.out.println("Total ≥100: " + total);

    // 4. Listar nomes em caixa alta
    List<String> names = products.stream()
      .map(p -> p.getName().toUpperCase())
      .collect(Collectors.toList());

    names.forEach(System.out::println);
  ```


## 7. Conclusão 🏁


  - Streams transformam loops em pipelines declarativos, tornando o código mais legível e modular.


  - Aproveite a lazy evaluation, o paralelismo fácil e a segurança de operações imutáveis.


  - Combine intermediárias e terminais para processar dados de forma poderosa e expressiva! 😊🚀