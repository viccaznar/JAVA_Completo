# Cartões de Resumo: Pilha de Chamadas de Métodos em Java ⬆️📚

  A pilha de chamadas (call stack) é uma estrutura de dados do tipo LIFO que armazena a sequência de métodos invocados durante a execução de um programa, sendo fundamental para entender o fluxo de execução e o tratamento de exceções.


## 1. Conceito de Pilha de Chamadas

  - **O que é:**  
    Cada vez que um método é chamado, um novo "quadro" (frame) é empilhado na call stack, contendo informações como parâmetros, variáveis locais e o endereço de retorno. Quando o método termina, seu quadro é removido (desempilhado) e o controle retorna ao método chamador.

  - **Por que é importante:**  

    - **Fluxo de Execução:** Permite rastrear a ordem em que os métodos são chamados.  

    - **Tratamento de Exceções:** Se uma exceção ocorre, ela se propaga pela pilha de chamadas até ser capturada, e métodos como `printStackTrace()` exibem essa sequência para facilitar a depuração.


  - **Exemplo Lúdico** 🎲

    Imagine a call stack como uma pilha de pratos em um restaurante 🍽️:  

    - Cada pedido de um prato é empilhado;  
    - Quando um prato é servido, ele é removido do topo;  
    - Se um problema acontecer (como um prato quebrado), o gerente examina a pilha para ver a ordem dos pedidos e identificar onde ocorreu o erro.


 - **Exemplo Prático em Código** 💻

  No exemplo a seguir, o método `main()` chama `method1()`, que por sua vez chama `method2()`. Se ocorrer uma exceção em `method2()`, o método `printStackTrace()` imprime a pilha de chamadas para ajudar a identificar o problema.

  ```java
    package application;
    import java.util.InputMismatchException;
    import java.util.Scanner;

    public class Program {
        public static void main(String[] args) {
            method1();
            System.out.println("End of program");
        }
        
        public static void method1() {
            System.out.println("***METHOD1 START***");
            method2();
            System.out.println("***METHOD1 END***");
        }
        
        public static void method2() {
            System.out.println("***METHOD2 START***");
            Scanner sc = new Scanner(System.in);
            try {
                // Lê uma linha e divide em um vetor
                String[] vect = sc.nextLine().split(" ");
                // Lê um número que representa a posição no vetor
                int position = sc.nextInt();
                System.out.println(vect[position]);
            } catch(ArrayIndexOutOfBoundsException e) {
                System.out.println("Invalid position!");
                e.printStackTrace(); // Imprime a pilha de chamadas
                sc.next();
            } catch(InputMismatchException e) {
                System.out.println("Input error");
            }
            sc.close();
            System.out.println("***METHOD2 END***");
        }
    }
  ```

## 2. Fluxo de Execução:

  - main() chama method1().

    - method1() imprime "METHOD1 START" e invoca method2().

      - method2() imprime "METHOD2 START", executa seu código e, se ocorrer uma exceção, o bloco catch a captura, imprime uma mensagem e exibe a pilha de chamadas com printStackTrace().

        - Após o tratamento, os métodos finalizam e o controle retorna para main(), onde "End of program" é impresso.


- **Conclusão**
  - A compreensão da pilha de chamadas é essencial para:

  - Rastrear o fluxo de execução: Entender como os métodos interagem.


  - **Depuração:**
  Identificar a origem dos erros com ferramentas como printStackTrace().

  - **Manutenção do Código:**
  Garantir que o programa lide corretamente com exceções e encerre as operações de recursos.


Dominar a call stack ajuda a construir programas Java mais robustos, facilitando tanto a gestão de excepcionais quanto a depuração eficaz! 😊🚀