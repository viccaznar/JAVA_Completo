# Cartões de Resumo: Generics em Java 🎯🔒⚡

  Generics são um recurso essencial do Java que permite a criação de classes, interfaces e métodos parametrizados por tipo. Isso promove reuso, segurança de tipo (type safety) e performance, além de ser amplamente utilizado em coleções.


## 1. Conceito e Benefícios

  - **Definição:**  
    Generics possibilitam que você defina classes, métodos e interfaces com parâmetros de tipo. Assim, o código pode ser reutilizado com diferentes tipos, sem a necessidade de conversões (casts) e com verificação de tipos em tempo de compilação.


  - **Principais Benefícios:**  


    - **Reuso:** Crie uma única implementação que funcione para diferentes tipos de dados.  


    - **Type Safety:** Erros de conversão são detectados em tempo de compilação, evitando falhas em tempo de execução.  


    - **Performance:** Menos castings e operações de verificação de tipo em tempo de execução, melhorando a eficiência.
    

    - **Uso Comum:** É muito utilizado em coleções, por exemplo:
      ```java
        List<String> list = new ArrayList<>();
        list.add("Maria");
        String name = list.get(0);
      ```


## 2. Problemas Motivadores

  - **Motivador 1:** Reuso
  

    - **Problema:** Faça um programa que leia uma quantidade N e, em seguida, N números inteiros. Ao final, imprima esses números organizadamente e informe qual foi o primeiro valor inserido.


  - **Exemplo de Saída:**

  ```console
    How many values? 3
    10
    8
    23
    [10, 8, 23]
    First: 10
  ```


  - **Objetivo:** Criar um serviço de impressão que permita o reuso do código em diferentes contextos.


  - **Motivador 2:** Type Safety & Performance


    - **Problema:** Faça um programa similar para ler N nomes de pessoas, imprimindo-os de forma organizada e informando o primeiro nome informado.


    - **Objetivo:** Usar Generics para garantir que o serviço de impressão seja seguro em termos de tipo e eficiente, sem a necessidade de conversões desnecessárias.


## 3. Exemplos Lúdicos e Práticos

### Exemplo Lúdico 🎲

  - Imagine que você tem um cesto mágico que pode armazenar objetos.


    - Sem Generics, cada vez que você adiciona algo, tem que verificar manualmente se é do tipo certo, como se você tivesse que etiquetar cada item ao acaso.

    - Com Generics, você escolhe um cesto exclusivo para frutas, outro para livros e assim por diante, garantindo que só o tipo esperado seja armazenado. Assim, seu cesto de frutas nunca se encherá de livros!


### Exemplo Prático 💻

  - A seguir, um serviço de impressão genérico que pode ser usado para imprimir listas de números, nomes ou qualquer outro tipo:

  ```java
    package application;

    import java.util.ArrayList;
    import java.util.List;

    public class PrintService<T> {
        private List<T> list = new ArrayList<>();

        // Adiciona um valor à lista
        public void addValue(T value) {
            list.add(value);
        }

        // Retorna o primeiro valor da lista
        public T first() {
            if (list.isEmpty()) {
                throw new IllegalStateException("List is empty");
            }
            return list.get(0);
        }

        // Imprime a lista organizada
        public void print() {
            System.out.println(list);
        }
    }
  ```
  - O código acima define uma classe `PrintService<T>` que utiliza Generics para armazenar e processar elementos de qualquer tipo. O método `first()` garante que o primeiro elemento seja obtido sem necessidade de conversão, promovendo segurança de tipo. O uso de Generics evita duplicação de código e permite que o serviço seja reutilizado tanto para números inteiros quanto para nomes ou outros tipos, com desempenho otimizado.
  
  
  ```java
    package application;
    import java.util.ArrayList;
    import java.util.List;

    public class PrintService<T> {
        private List<T> list = new ArrayList<>();

        // Adiciona um valor à lista
        public void addValue(T value) {
            list.add(value);
        }

        // Retorna o primeiro valor da lista
        public T first() {
            if (list.isEmpty()) {
                throw new IllegalStateException("List is empty");
            }
            return list.get(0);
        }

        // Imprime a lista organizada
        public void print() {
            System.out.println(list);
        }
    }
  ```

  ```java
  package application;
  import java.util.ArrayList;
  import java.util.List;
  import java.util.Scanner;

  // Serviço genérico de impressão
  public class PrintService<T> {
      private List<T> list = new ArrayList<>();

      // Adiciona um valor à lista
      public void addValue(T value) {
          list.add(value);
      }

      // Retorna o primeiro valor da lista
      public T first() {
          if (list.isEmpty()) {
              throw new IllegalStateException("List is empty");
          }
          return list.get(0);
      }

      // Imprime a lista organizada
      public void print() {
          System.out.println(list);
      }
  }
  ```

  ```java
    package application;
    import java.util.Scanner;
    public class Program {
        public static void main(String[] args) {
            Scanner sc = new Scanner(System.in);
            System.out.print("How many values? ");
            int n = sc.nextInt();

            // Serviço de impressão para números inteiros (reuso)
            PrintService<Integer> psIntegers = new PrintService<>();
            for (int i = 0; i < n; i++) {
                int value = sc.nextInt();
                psIntegers.addValue(value);
            }
            psIntegers.print();
            System.out.println("First: " + psIntegers.first());

            // Serviço de impressão para, por exemplo, nomes (type safety & performance)
            // PrintService<String psStrings = new PrintService<();
            // for (int i = 0; i < n; i++) {
            //     sc.nextLine();
            //     String name = sc.nextLine();
            //     psStrings.addValue(name);
            // }
            // psStrings.print();
            // System.out.println("First: " + psStrings.first());
            
            sc.close();
        }
    }
  ```
    - **Saída esperada:**
    ```console
      How many values? 3
      10
      8
      23
      [10, 8, 23]
      First: 10
    ```


  - **Explicação:** 
  

    - A classe PrintService<T> utiliza Generics para armazenar e processar elementos de qualquer tipo.


    - O método first() garante que o primeiro elemento seja obtido sem necessidade de conversão, promovendo segurança de tipo. 


    - O uso de Generics evita duplicação de código e permite que o serviço seja reutilizado tanto para números inteiros quanto para nomes ou outros tipos, com desempenho otimizado.


### Conclusão 🏁

  - **Generics:** Permitem parametrizar classes, interfaces e métodos por tipo, levando a código mais reutilizável, seguro e eficiente.


  - **Benefícios:**


    - **Reuso:** Crie componentes genéricos que funcionam com qualquer tipo de dado.


    - **Type Safety:** Erros de tipo são detectados em tempo de compilação.


    - **Performance:** Elimina a sobrecarga dos castings.


    - **Aplicações Comuns:** Muito utilizados em coleções (por exemplo, List<String), onde a segurança e a eficiência são essenciais.


Domine os Generics para escrever código Java mais robusto, flexível e reutilizável! 😊🚀