# Cartões de Resumo: Funções (Sintaxe) em Java 🎯🤓

## 1. Conceito de Função
- **Definição:** Uma função é um bloco de código que realiza um processamento específico e possui um significado.  
- **Exemplo Lúdico:** Imagine uma receita secreta: você junta os ingredientes certos e, ao seguir os passos, obtém um prato delicioso!  
- **Exemplo Prático:**  
  ```java
  // A função Math.sqrt(double) calcula a raiz quadrada de um número.
  double resultado = Math.sqrt(16); // resultado é 4.0
  System.out.println("Raiz quadrada de 16 = " + resultado);
  ```

## 2. Principais Vantagens das Funções
- **Modularização:** Organiza o código em blocos independentes, facilitando a leitura e manutenção.
- **Delegação:** Cada função tem uma responsabilidade bem definida, permitindo que tarefas sejam delegadas de forma clara.
- **Reaproveitamento:** Uma vez escrita, a função pode ser chamada de várias partes do programa, evitando repetição.
  
- **Exemplo Lúdico:** Pense em um conjunto de blocos de montar: cada bloco (função) pode ser reutilizado para construir diferentes estruturas.

- **Exemplo Prático:**
  ```java
    // Função que identifica o maior número entre três valores.
    public static int max(int a, int b, int c) {
        int aux;
        if (a > b && a > c) {
            aux = a;
        } else if (b > c) {
            aux = b;
        } else {
            aux = c;
        }
        return aux;
    }
    ```


## 3. Entrada e Saída de Dados nas Funções
- **Parâmetros (Entrada):** Permitem que dados sejam passados para a função, personalizando sua execução.
- **Retorno (Saída):** A função pode retornar um valor como resultado ou executar uma tarefa sem devolver dados (void).
  
- **Exemplo Lúdico:** Imagine uma máquina de sucos onde você coloca diferentes frutas (parâmetros) e, dependendo da combinação, recebe um sabor específico (retorno).

- **Exemplo Prático:**
  ```java
    // Uma função que exibe o resultado:
    public static void showResult(int value) {
        System.out.println("Higher = " + value);
    }
  ```


## 4. Funções em Orientação a Objetos: Métodos
- **Definição:** Em Java, funções declaradas dentro de classes são chamadas de métodos.

- **Exemplo Lúdico:** Imagine um robô que possui diferentes habilidades (métodos) que o ajudam a executar diversas tarefas, como andar, falar e pegar objetos.

- **Exemplo Prático:**
  ```java
  package course;

  import java.util.Scanner;

  public class Program {
      public static void main(String[] args) {
          Scanner sc = new Scanner(System.in);
          System.out.println("Enter three numbers:");
          int a = sc.nextInt();
          int b = sc.nextInt();
          int c = sc.nextInt();
          int higher = max(a, b, c);  // Chamada ao método que determina o maior número
          showResult(higher);         // Chamada ao método que exibe o resultado
          sc.close();
      }

      public static int max(int x, int y, int z) {
          int aux;
          if (x > y && x > z) {
              aux = x;
          } else if (y > z) {
              aux = y;
          } else {
              aux = z;
          }
          return aux;
      }

      public static void showResult(int value) {
          System.out.println("Higher = " + value);
      }
  }
  ```

Este exemplo integra o uso de funções para modularizar, delegar tarefas e reaproveitar código, evidenciando a importância dos métodos na programação orientada a objetos. 😎💻


