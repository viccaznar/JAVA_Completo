# Cartões de Resumo: Criando um Método para Reaproveitamento e Delegação em Java 🎯🔄

## 1. Instanciação e Alocação Dinâmica de Memória 🏗️💾
  - **Conceito:**  
  Instanciação é o processo de criar um objeto a partir de uma classe usando o operador `new`. Isso aloca dinamicamente a memória no heap, onde cada objeto criado reside.

  - **Exemplo Lúdico:**  
  Imagine que você tem um molde (a classe `Triangle`) e cada vez que precisa de um novo triângulo, você "imprime" uma cópia desse molde. Cada cópia tem seu espaço reservado na "fábrica de objetos" (heap).

  - **Exemplo Prático:**  
    ```java
    Triangle x, y;
    x = new Triangle();  // Instanciação do objeto x na memória heap
    y = new Triangle();  // Instanciação do objeto y na memória heap
    ```

## 2. Reaproveitamento e Delegação via Métodos ♻️🔧
  - **Conceito:**
  
  - **Reaproveitamento:** Ao encapsular o cálculo da área em um método (area()) dentro da classe Triangle, evitamos a repetição de código. Cada objeto Triangle pode calcular sua própria área usando essa mesma lógica.

  - **Delegação:** Delegar essa tarefa ao objeto (por meio do método) torna o código mais modular e organizado, separando claramente a responsabilidade de cada componente.

  - **Exemplo Lúdico:**
  Imagine um super-herói (a classe Triangle) que possui uma habilidade especial (o método area()). Cada vez que precisa demonstrar sua força (sua área), ele simplesmente utiliza essa habilidade, sem precisar ser reensinado toda vez.

  - **Exemplo Prático:**
  ```java
    // Instanciando objetos Triangle e delegando o cálculo da área ao método area()
    Triangle x, y;
    x = new Triangle();
    y = new Triangle();

    // Valores dos lados são atribuídos a cada triângulo
    x.a = sc.nextDouble();
    x.b = sc.nextDouble();
    x.c = sc.nextDouble();

    y.a = sc.nextDouble();
    y.b = sc.nextDouble();
    y.c = sc.nextDouble();

    // Os objetos calculam sua área por meio do método area()
    double areaX = x.area();
    double areaY = y.area();
  ```


## 3. Definindo Métodos na Classe: O Exemplo do Método area() 📐🔢
  - **Conceito:**
  Um método em uma classe é uma função que executa uma tarefa específica. No exemplo, o método area() calcula a área do triângulo usando a Fórmula de Heron:

  - Primeiro, calcula o semiperímetro: p = (a + b + c) / 2.0
  - Em seguida, calcula a área: área = √[p * (p - a) * (p - b) * (p - c)]

  - **Exemplo Lúdico:**
  Pense em um triângulo que é "autoconsciente" e sabe se medir sozinho. Ele usa seu método area() assim como um atleta que confia em seu treinamento para marcar seus próprios recordes.

  - **Exemplo Prático:**
  ```java
    package entities;

    public class Triangle {
        public double a;
        public double b;
        public double c;

        public double area() {
            double p = (a + b + c) / 2.0;
            return Math.sqrt(p * (p - a) * (p - b) * (p - c));
        }
    }
  ```

Este resumo ilustra como criar métodos em classes permite aproveitar e delegar funcionalidades, tornando o código mais modular, reutilizável e organizado. Esses conceitos são fundamentais para desenvolver programas eficientes e fáceis de manter em Java! 🚀😊


