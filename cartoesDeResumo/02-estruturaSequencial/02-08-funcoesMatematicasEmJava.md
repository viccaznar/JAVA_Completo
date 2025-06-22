# 🎲 Funções Matemáticas em Java

- 📐 **Math.sqrt(x)**  
  • Conceito: calcula a raiz quadrada de um número.  
  • Lúdico: o elfo mede o lado de um quadrado mágico e descobre seu “coração” (lado do quadrado).  
  • Prático:
    ```java
    double x = 16.0;
    double raiz = Math.sqrt(x);
    System.out.println("√" + x + " = " + raiz); // √16.0 = 4.0
    ```

- 🚀 **Math.pow(x, y)**  
  • Conceito: eleva x à potência y (x^y).  
  • Lúdico: o mago multiplica sua energia (base) várias vezes (expoente) para lançar um feitiço supremo.  
  • Prático:
    ```java
    double base = 2.0, expoente = 8.0;
    double pot = Math.pow(base, expoente);
    System.out.println(base + "^" + expoente + " = " + pot); // 2.0^8.0 = 256.0
    ```

- 🎯 **Math.abs(x)**  
  • Conceito: retorna o valor absoluto de x (sem sinal).  
  • Lúdico: a fênix ignora o aspecto “negativo” das cinzas e renasce pura e positiva.  
  • Prático:
    ```java
    double negativo = -5.5;
    double positivo = Math.abs(negativo);
    System.out.println("|" + negativo + "| = " + positivo); // |-5.5| = 5.5
    ```

> Mais informações: consulte a classe `java.lang.Math` na documentação oficial da Oracle.  