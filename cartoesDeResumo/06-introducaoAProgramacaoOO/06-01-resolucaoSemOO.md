# Cartões de Resumo: Resolvendo um Problema sem Orientação a Objetos 😃📐

## 1. Objetivo do Problema
  - **Fundamento:** O programa lê as medidas dos lados de dois triângulos (X e Y), calcula suas áreas usando a fórmula de Heron e determina qual triângulo possui a maior área.
  
  - **Exemplo Lúdico:** Imagine dois campos de futebol e precisamos descobrir qual deles é maior para escolher a melhor área de jogo!
  
  - **Exemplo Prático:** Ao digitar as medidas dos triângulos, o programa exibe:
    ```java
    Triangle X area: 6.0000 Triangle Y area: 7.5638 Larger area: Y
    ```

## 2. Entrada de Dados (Input) 📥
  - **Fundamento:** Utiliza a classe `Scanner` para capturar os valores dos lados dos triângulos a partir do console. O uso de `Locale.setDefault(Locale.US)` garante a interpretação adequada dos números (com ponto como separador decimal).

  - **Exemplo Lúdico:** Pense em um cozinheiro que seleciona cuidadosamente os ingredientes de cada receita; aqui, cada número lido é um “ingrediente” para o cálculo.

  - **Exemplo Prático:**
  ```java
  Locale.setDefault(Locale.US);
  Scanner sc = new Scanner(System.in);

  System.out.println("Enter the measures of triangle X: ");
  double xA = sc.nextDouble();
  double xB = sc.nextDouble();
  double xC = sc.nextDouble();

  System.out.println("Enter the measures of triangle Y: ");
  double yA = sc.nextDouble();
  double yB = sc.nextDouble();
  double yC = sc.nextDouble();
  ```


## 3. Processamento: Cálculo da Área com a Fórmula de Heron ➗
  - **Fundamento:** A Fórmula de Heron calcula a área de um triângulo a partir dos seus lados. Primeiro, calcula-se o semiperímetro (p = (a + b + c) / 2), e depois a área com a fórmula:
  
  `area = √[p * (p - a) * (p - b) * (p - c)]`

  - **Exemplo Lúdico:** Imagine um detetive que, com pistas (as medidas dos lados), usa uma fórmula mágica para descobrir o “mistério” da área do triângulo.

  - **Exemplo Prático:**
    ```java
  // Cálculo da área do triângulo X utilizando a fórmula de Heron
  double p = (xA + xB + xC) / 2.0;
  double areaX = Math.sqrt(p * (p - xA) * (p - xB) * (p - xC));

  // Cálculo da área do triângulo Y
  p = (yA + yB + yC) / 2.0;
  double areaY = Math.sqrt(p * (p - yA) * (p - yB) * (p - yC));
  ```


## 4. Saída de Dados e Controle de Fluxo 📤
  - **Fundamento:** Após calcular as áreas, o programa utiliza System.out.printf para exibir valores com formatação (4 casas decimais) e uma estrutura condicional if-else para identificar qual triângulo possui a área maior.

  - **Exemplo Lúdico:** Imagine dois competidores que correm para ver quem é maior; ao fim da corrida, o programa anuncia o vencedor com clareza.
  - **Exemplo Prático:**
  ```java
    System.out.printf("Triangle X area: %.4f%n", areaX);
    System.out.printf("Triangle Y area: %.4f%n", areaY);

    if (areaX > areaY) {
        System.out.println("Larger area: X");
    } else {
        System.out.println("Larger area: Y");
    }
   ```


## 5. Estrutura Geral do Programa e Fechamento de Recursos ⚙️
  - **Fundamento:** O problema é resolvido dentro do método main de uma classe, sem a utilização explícita de orientação a objetos para modelagem dos triângulos. O pacote é definido (package application;) e o Scanner é fechado com sc.close() para liberar recursos.

- **Exemplo Lúdico:** Pense em um roteiro bem planejado, onde cada ato (entrada, processamento, saída) é executado em ordem e, ao final, todas as "portas" são fechadas para manter a organização.

- **Exemplo Prático Completo:**
  ```java
    package application;
    import java.util.Locale;
    import java.util.Scanner;

    public class Program {
        public static void main(String[] args) {
            Locale.setDefault(Locale.US);
            Scanner sc = new Scanner(System.in);

            System.out.println("Enter the measures of triangle X: ");
            double xA = sc.nextDouble();
            double xB = sc.nextDouble();
            double xC = sc.nextDouble();

            System.out.println("Enter the measures of triangle Y: ");
            double yA = sc.nextDouble();
            double yB = sc.nextDouble();
            double yC = sc.nextDouble();

            double p = (xA + xB + xC) / 2.0;
            double areaX = Math.sqrt(p * (p - xA) * (p - xB) * (p - xC));

            p = (yA + yB + yC) / 2.0;
            double areaY = Math.sqrt(p * (p - yA) * (p - yB) * (p - yC));

            System.out.printf("Triangle X area: %.4f%n", areaX);
            System.out.printf("Triangle Y area: %.4f%n", areaY);

            if (areaX > areaY) {
                System.out.println("Larger area: X");
            } else {
                System.out.println("Larger area: Y");
            }

            sc.close();
        }
    }
  ```


Este resumo demonstra como resolver um problema prático utilizando entrada e saída de dados, processamento com a fórmula de Heron e controle de fluxo em Java de forma procedural (sem orientação a objetos)! 🚀😊



