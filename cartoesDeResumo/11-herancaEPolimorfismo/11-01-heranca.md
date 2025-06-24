# Cartões de Resumo: Herança em Java 🏛️🔗

  Herança é um princípio fundamental da orientação a objetos que permite que uma classe (subclasse) herde atributos e métodos de outra (superclasse), promovendo reuso, organização e polimorfismo no código.


## 1. Conceito de Herança 🤝

  - **Definição:**  
    Herança é uma associação entre classes, onde uma subclasse herda os dados e comportamentos (métodos) da superclasse. Essa relação é conhecida como "é-um", ou seja, a subclasse é um tipo especializado da superclasse.

  - **Generalização/Especialização:**  
    A superclasse define características gerais, enquanto as subclasses adicionam ou especializam essas características.

 - **Exemplo Lúdico:**  
  Pense na herança como as características familiares: assim como um filho herda os traços dos pais (cor dos olhos, cabelos, etc.) 👨‍👩‍👧, uma subclasse herda os atributos e métodos da sua superclasse.


## 2. Vantagens da Herança 🌟

  - **Reuso:**  
    Permite reutilizar código já existente, evitando duplicação e facilitando a manutenção. ♻️

  - **Polimorfismo:**  
    Possibilita que objetos de subclasses sejam tratados como objetos da superclasse, aumentando a flexibilidade do sistema. 🔄


## 3. Sintaxe e Conceitos-Chave 📝

  - **Sintaxe Básica:**  
    ```java
      class Subclasse extends Superclasse {
          // Implementação ou sobrescrita de métodos, novos atributos, etc.
      }
    ```

  - **Modificador protected:**
   Permite que atributos e métodos sejam acessados pelas subclasses, mantendo um nível de encapsulamento menor que o private.

  - **Relação:**
  
    - **"É-um":** A subclasse é um tipo especializado da superclasse.

    - **Herança/Extensão:** Permite a especialização da superclasse.


  - **Exemplo Prático:** Sistema Bancário 💼
  Imagine um sistema de banco que possui uma conta comum e uma conta para empresas. A conta para empresas herda os membros da conta comum e adiciona funcionalidades específicas, como um limite de empréstimo e o método para realizar empréstimos.

  - **Código Exemplo:**
  ```java
    // Superclasse: Representa uma conta bancária comum
    public class Account {
        protected double balance;
        
        public Account(double balance) {
            this.balance = balance;
        }
        
        public void deposit(double amount) {
            balance += amount;
        }
        
        public double getBalance() {
            return balance;
        }
    }

    // Subclasse: Conta Empresarial que herda de Account e adiciona um limite de empréstimo
    public class BusinessAccount extends Account {
        private double loanLimit;
        
        public BusinessAccount(double balance, double loanLimit) {
            super(balance); // Chama o construtor da superclasse
            this.loanLimit = loanLimit;
        }
        
        // Método para realizar empréstimo com uma taxa de 10.0
        public void loan(double amount) {
            if (amount <= loanLimit) {
                // Adiciona o valor ao saldo descontando a taxa de 10.0
                balance += (amount - 10.0);
            }
        }
    }
    Demonstração de Uso:
    java
    public class Main {
        public static void main(String[] args) {
            BusinessAccount ba = new BusinessAccount(100.0, 500.0);
            System.out.println("Saldo Inicial: " + ba.getBalance());
            ba.loan(100.0); // Realiza um empréstimo; taxa de 10.0 será descontada
            System.out.println("Saldo após Empréstimo: " + ba.getBalance());
        }
    }
  ```

- **Resumo Lúdico:**
  Assim como em uma família onde os filhos herdaram habilidades e características dos pais, em herança, a classe BusinessAccount herda as funcionalidades da classe Account e ainda adiciona novas funcionalidades (como o empréstimo), tornando o sistema mais organizado e reutilizável.

## 4. Conclusão 🏁

  - Herança permite o reuso de atributos e métodos, promovendo um design mais coerente e modular.

  - Ela estabelece uma relação "é-um" entre classes, facilitando a especialização e o polimorfismo.

  - O uso do modificador protected garante que as subclasses possam acessar os membros essenciais da superclasse sem expô-los publicamente.

  - **Exemplo prático:**
   No sistema bancário, uma conta empresarial expande a funcionalidade de uma conta comum, demonstrando claramente os benefícios da herança.

Domine o conceito de herança para construir sistemas mais robustos, flexíveis e fáceis de manter em Java! 🚀😊