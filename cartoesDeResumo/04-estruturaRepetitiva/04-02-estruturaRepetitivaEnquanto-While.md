# Estrutura Repetitiva "enquanto" (while) em Java 🔄

## 1. Conceito 🤓
- **Definição:**  
  A estrutura repetitiva "enquanto" (while) permite repetir um bloco de comandos enquanto uma condição definida seja verdadeira.  
- **Objetivo:**  
  Usada em situações onde o número de repetições não é conhecido previamente, executando o bloco de código até que a condição se torne falsa.



## 2. Quando Utilizar 🚀
- **Uso Ideal:**  
  Utilize o `while` quando você precisa continuar executando uma ação sem saber quantas iterações serão necessárias, como ler dados do usuário até encontrar um valor de parada.



## 3. Sintaxe e Regras de Funcionamento 🛠️
- **Sintaxe Básica:**
  ```java
  while (condição) {
      // comando 1
      // comando 2
  }
  ```

  - **Regras:**
    - Condição Verdadeira **(V)**: Executa o bloco de comandos e reavalia a condição novamente.
    - Condição Falsa **(F)**: Interrompe o loop e continua a execução do programa a partir da próxima instrução após o laço.

  - **Exemplo Lúdico**🎲
    Imagine um jogo de tabuleiro onde você continua avançando enquanto joga uma peça que mostra "siga" (Verdadeiro). Assim que a peça mostra "pare" (Falso), você para e o turno termina. Essa mecânica é similar ao funcionamento do while, onde o jogo (ou o laço) continua enquanto a condição for atendida. 🎯

  - **Exemplo Prático** 💻
    Faça um programa que leia números inteiros até que seja lido o número 0 e, ao final, mostre a soma dos números lidos.
  ```java
  import java.util.Scanner;

  public class SomaNumeros {
      public static void main(String[] args) {
          Scanner sc = new Scanner(System.in);
          int numero;
          int soma = 0;

          // Continua lendo números enquanto o número digitado for diferente de 0
          while ((numero = sc.nextInt()) != 0) {
              soma += numero; // acumula a soma dos números
          }

          System.out.println("Soma dos números: " + soma);
          sc.close();
      }
  }
  ```

  - **Explicação:**
  Neste exemplo, o loop while continua a executar enquanto o usuário não digita 0. Cada número lido é somado à variável soma. Quando o número 0 é inserido, a condição se torna falsa e o programa exibe o resultado final.

Esta estrutura é essencial para controlar fluxos indeterminados em programas, proporcionando flexibilidade ao repetir ações até que determinada condição seja satisfeita. 🚀🔄


