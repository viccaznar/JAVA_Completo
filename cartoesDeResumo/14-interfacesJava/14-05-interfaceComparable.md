# Cartões de Resumo: Interface Comparable em Java 📏🔍

  A interface **Comparable** define o "contrato" que permite que objetos sejam comparados e ordenados de forma natural. Ela é fundamental para a ordenação de coleções usando métodos como `Collections.sort()`.


## 1. Conceito e Definição

  - **Interface Comparable:**  

    - Define um método único:

      ```java
        public interface Comparable<T> {
            int compareTo(T o);
        }
      ```


 - **Contrato do método `compareTo()`:**


    - Retorna um valor negativo se o objeto atual é menor que o objeto o.

    - Retorna zero se ambos são iguais.

    - Retorna um valor positivo se o objeto atual é maior que o.

    - **Aplicação:** Permite ordenar objetos "por natureza" sem a necessidade de um comparador externo.


## 2. Objetivos e Vantagens


  - **Ordenação Natural:** Ao implementar Comparable, uma classe define sua própria ordem natural.


  - **Utilização em Coleções:** Objetos que implementam Comparable podem ser facilmente ordenados com Collections.sort().


  - **Polimorfismo:** Permite que diferentes tipos de objetos sejam comparados de forma consistente usando o mesmo contrato.


## 3. Exemplos de Problemas e Aplicações


  - **Exemplo 1:** Ordenação de Nomes
  

    **Problema:** Ler um arquivo contendo nomes (um por linha), armazená-los numa lista, ordenar e exibir os nomes em ordem alfabética.


    **Solução:** A classe String já implementa Comparable, permitindo que Collections.sort(list) ordene a lista de nomes automaticamente.



  - **Exemplo 2:** Ordenação de Funcionários


    **Problema:** Ler um arquivo CSV contendo funcionários (formato: nome e salário), armazená-los numa lista, ordenar por nome e exibir os dados.


    **Solução:** Crie uma classe Employee que implementa Comparable<Employee>, definindo a ordem natural baseada no nome.


### Exemplo:

  ```java
    package entities;

    public class Employee implements Comparable<Employee {
        private String name;
        private Double salary;

        public Employee(String name, Double salary) {
            this.name = name;
            this.salary = salary;
        }

        public String getName() {
            return name;
        }

        public Double getSalary() {
            return salary;
        }

        @Override
        public int compareTo(Employee other) {
            return this.name.compareTo(other.getName());
        }
    }
  ```

  - **Exemplo Lúdico** 🎲
  Imagine que você está organizando um campeonato de corrida 🏁:
  

    - Cada corredor tem uma velocidade e desempenho diferentes.

    - A interface Comparable é como um regulamento que decide, com base em um critério (por exemplo, tempo de corrida), qual corredor fica em qual posição.

    - Assim, toda vez que você for definir o ranking, o método compareTo ajuda a "classificar" os corredores do mais rápido ao mais lento.


  - **Exemplo Prático de Código 💻**
  A seguir, um exemplo que lê um arquivo CSV contendo dados de funcionários, cria objetos do tipo Employee, ordena esses objetos usando Collections.sort(), e imprime o nome e salário ordenados.

  ```java
    package application;

    import java.io.BufferedReader;
    import java.io.FileReader;
    import java.io.IOException;
    import java.util.ArrayList;
    import java.util.Collections;
    import java.util.List;
    import entities.Employee;

    public class Program {
        public static void main(String[] args) {
            List<Employee list = new ArrayList<();
            String path = "C:\\temp\\in.txt";
            
            try (BufferedReader br = new BufferedReader(new FileReader(path))) {
                String employeeCsv = br.readLine();
                while (employeeCsv != null) {
                    String[] fields = employeeCsv.split(",");
                    list.add(new Employee(fields[0], Double.parseDouble(fields[1])));
                    employeeCsv = br.readLine();
                }
                // Ordena a lista utilizando a ordem natural definida no compareTo de Employee
                Collections.sort(list);
                for (Employee emp : list) {
                    System.out.println(emp.getName() + ", " + emp.getSalary());
                }
            } catch (IOException e) {
                System.out.println("Error: " + e.getMessage());
            }
      }
    }
  ```

  - **Explicação:**
  
    - O arquivo CSV é lido linha a linha, e para cada linha um objeto Employee é criado e adicionado à lista.

    -  Collections.sort(list) utiliza o método compareTo da classe Employee para ordenar a lista por nome.  

    - Os dados ordenados são exibidos na tela.


### Conclusão 🏁


  - **Interface Comparable:** Fornece um contrato para definir a ordem natural dos objetos, essencial para a ordenação e para promover flexibilidade e modularidade em coleções.


  - **Vantagens:** Simplifica a ordenação sem a necessidade de comparadores externos e melhora a legibilidade e manutenibilidade do código.


  - **Aplicação:** Útil em muitos contextos, desde a ordenação de listas de nomes simples até a ordenação de objetos complexos, como registros de funcionários.


Domine o uso de Comparable para criar aplicativos mais organizados e eficientes! 😊🚀