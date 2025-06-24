# Cartões de Resumo: Introdução ao Polimorfismo em Java 🎭💡

  O polimorfismo é um dos pilares fundamentais da Programação Orientada a Objetos, ao lado de encapsulamento e herança. Ele permite que variáveis de um tipo genérico, geralmente uma superclasse, possam referenciar objetos de tipos mais específicos (subclasses) e executem comportamentos distintos conforme o tipo real do objeto em tempo de execução.


## 1. Conceito de Polimorfismo

  - **Definição:**  
    Em Java, polimorfismo é o mecanismo pelo qual o mesmo método (ou operação) pode ter comportamentos diferentes quando invocado em objetos de classes distintas, mesmo que esses objetos sejam referenciados pela mesma variável de tipo genérico.
  
  - **Como Funciona:**  
    
    - **Upcasting:** A regra estática que permite atribuir referências de subclasses a variáveis do tipo da superclasse.  
    
    - **Dynamic Method Dispatch:** Em tempo de execução, a JVM determina qual implementação do método deve ser chamada com base no tipo real do objeto.  
    
    - **Exemplo:** Uma variável do tipo `Account` pode apontar tanto para um objeto da classe `Account` quanto para um objeto de uma subclasse como `SavingsAccount` ou `BusinessAccount`.

  - **Exemplo Lúdico:**  
  Imagine um controle remoto universal 🎮 que, ao apertar um botão "play", pode iniciar diferentes ações dependendo do dispositivo que está controlando (TV, DVD, ou sistema de som). Embora o botão seja o mesmo, o comportamento varia conforme o equipamento. Esse é o polimorfismo em ação: o mesmo comando se adapta ao contexto específico do dispositivo.


## 2. Exemplo Prático em Código

  Suponha que temos uma classe `Account` representando uma conta bancária e uma subclasse `SavingsAccount`, que sobrescreve o método de saque para não aplicar uma taxa.
  ```java
    // Superclasse: Conta comum com taxa de saque
    public class Account {
        protected double balance;

        public Account(int number, String holder, double balance) {
            this.balance = balance;
        }
        
        public void withdraw(double amount) {
            // Cobrança de taxa padrão de R$5,00
            balance -= amount + 5.0;
        }

        public double getBalance() {
            return balance;
        }
    }

    // Subclasse: Conta poupança sem cobrança de taxa de saque
    public class SavingsAccount extends Account {

        public SavingsAccount(int number, String holder, double balance, double interestRate) {
            super(number, holder, balance);
        }
        
        @Override
        public void withdraw(double amount) {
            // Sobrescrita: não cobra a taxa padrão
            balance -= amount;
        }
    }

    // Demonstração do polimorfismo
    public class Main {
        public static void main(String[] args) {
            Account x = new Account(1020, "Alex", 1000.0);
            Account y = new SavingsAccount(1023, "Maria", 1000.0, 0.01);
            
            // Ambos os objetos são do tipo Account, mas comportam-se de maneira diferente:
            x.withdraw(50.0); // Executa o método da classe Account: taxa de R$5,00 é cobrada.
            y.withdraw(50.0); // Executa o método sobrescrito em SavingsAccount: sem cobrança de taxa.
            
            System.out.println("Saldo da conta do Alex: " + x.getBalance());
            System.out.println("Saldo da conta da Maria: " + y.getBalance());
        }
    }
 ```

  - **Explicação:**
    No exemplo, mesmo ambos os objetos x e y sendo do tipo Account, a chamada de withdraw(50.0) resulta em comportamentos diferentes. O objeto x utiliza a implementação da superclasse, enquanto y, que é uma instância de SavingsAccount, usa a implementação sobrescrita que não inclui a taxa. Isso demonstra o polimorfismo: a decisão sobre qual método executar é feita em tempo de execução.


## 3. Importância do Polimorfismo

  Flexibilidade e Reuso: Permite escrever código mais genérico e reutilizável, facilitando a manutenção e extensão do sistema.

  - **Organização:** Separa comportamentos específicos nas subclasses enquanto mantém uma interface comum (o método withdraw em Account), facilitando a compreensão e o gerenciamento do código.

  - **Polimorfismo e Upcasting:** A associação do tipo específico com o tipo genérico é feita automaticamente (upcasting), ou seja, o compilador só sabe que a variável é do tipo Account mesmo quando ela armazena uma instância de SavingsAccount. A resolução do método adequado é feita em tempo de execução.

Domine o conceito de polimorfismo para desenvolver sistemas orientados a objetos robustos e flexíveis, onde o comportamento adequado é aplicado automaticamente conforme o tipo real do objeto! 😊🚀