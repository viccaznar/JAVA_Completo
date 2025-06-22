# ⚙️ Processamento de Dados e Casting em Java

- 🔄 **Atribuição**  
  O comando `<variável> = <expressão>;` calcula a expressão e guarda o resultado na variável.  
  🧚‍♂️ Lúdico: o gnomo mistura 2 gemas + 3 gemas e guarda as 5 gemas no saquinho mágico.  
  💻 Prático:
  ```java
  int x;
  x = 5;            // x recebe 5
  int y = 2 * x;    // y recebe 10
  System.out.println(y); // imprime 10
  ```

- 🧮 **Avaliação de Expressões**
    O Java segue ordem de operações (parênteses, divisão, multiplicação, soma, subtração).
        🧙‍♂️ **Lúdico:** o alquimista primeiro mistura ingredientes (parênteses), depois aquece (dividir), depois congela (multiplicar).
        💻 **Prático:**
    ```java
    double area = (6.0 + 8.0) / 2.0 * 5.0;
    System.out.println(area); // imprime 35.0
    ```

- 🔢 **Tipos e Literais Numéricos**
    int → inteiro; double → ponto flutuante (use .0); float → ponto flutuante simples (use f).
        🏺 **Lúdico:** cada tipo é um baú diferente – baú de inteiros, cofre de doubles, caixa de floats.
        💻 **Prático:**
    ```java
    float b = 6f;     // literal float
    double B = 8.0;   // literal double
    ```

- ➗ **Divisão Inteira vs. Ponto Flutuante**
    Inteiros divididos por inteiros descartam fração; use ponto flutuante ou casting para obter decimais.
        🍰 **Lúdico:** cortar um bolo em 5 pedaços com facas cegas só gera 2 pedaços inteiros.
        💻 **Prático:**
    ```java
    int a = 5, b = 2;
    double r1 = a / b;         // 2.0 (resto descartado)
    double r2 = (double)a / b; // 2.5 (com casting)
    ```


- 🔀 **Casting (Conversão Explícita)**
    (tipo) valor força a conversão quando o compilador não infere automaticamente.
        🔮 **Lúdico:** o mago transforma uma pedra (double) em pó (int) para caber no frasco minúsculo.
        💻  **Prático:**
    ```java
    double a = 5.0;
    int b = (int)a;         // força conversão de double para int
    System.out.println(b);  // imprime 5
    ```




