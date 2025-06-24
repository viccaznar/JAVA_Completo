# Cartões de Resumo: Classes Abstratas em Java 🎓🔒

  As classes abstratas são um componente essencial da Programação Orientada a Objetos, permitindo que se defina um "molde" para um conjunto de classes sem que esse molde seja instanciado diretamente.


## 1. Conceito de Classes Abstratas

  - **Definição:**  
    Uma classe abstrata é uma classe que não pode ser instanciada. Ela existe para definir atributos e comportamentos comuns que devem ser compartilhados por todas as suas subclasses.  

  - **Objetivo:**  
    - Fornecer um ponto comum de herança para suas subclasses.  
    - Garantir herança total: somente subclasses “concretas” podem ser instanciadas, nunca a própria classe abstrata.

  - **Exemplo Lúdico:**  
  Imagine uma fábrica de brinquedos 🎠 que tem um molde básico para "brinquedos". Esse molde, chamado "Brinquedo", é abstrato e nunca é vendido por si só; você só vende brinquedos específicos como "Carrinho" ou "Boneca". Assim, o molde garante que todos os brinquedos compartilhem características comuns enquanto cada tipo tem suas particularidades.


## 2. Por Que Usar Classes Abstratas? 🛠️

  - **Reuso de Código:**  
    Ao definir os atributos e métodos comuns em uma classe abstrata, você evita duplicação e melhora a organização do código.
  
  - **Polimorfismo:**  
    Uma variável do tipo da classe abstrata pode referenciar objetos de qualquer uma das subclasses. Isso facilita o tratamento uniforme de diferentes tipos de objetos (ex.: tratar tanto uma `SavingsAccount` quanto uma `BusinessAccount` como uma `Account`).

  - **Exemplo no Contexto Bancário:**  
    Em um sistema bancário, você pode querer que apenas contas poupança e contas para empresas sejam instanciadas. Em vez de permitir a criação de uma "Conta" genérica, declara-se a classe `Account` como abstrata.


## 3. Exemplo Prático em Código 💻

### Definição da Classe Abstrata e Subclasses

  ```java
    // Classe abstrata que define um modelo comum para todas as contas
    public abstract class Account {
        protected int number;
        protected String holder;
        protected double balance;
        
        public Account(int number, String holder, double balance) {
            this.number = number;
            this.holder = holder;
            this.balance = balance;
        }
        
        // Método de saque comum, pode ser sobrescrito pelas subclasses
        public void withdraw(double amount) {
            balance -= amount + 5.0;
        }
        
        public double getBalance() {
            return balance;
        }
    }

    // Subclasse que representa Conta Poupança - não permite instanciar Account diretamente
    public class SavingsAccount extends Account {
        private double interestRate;
        
        public SavingsAccount(int number, String holder, double balance, double interestRate) {
            super(number, holder, balance);
            this.interestRate = interestRate;
        }
        
        // Sobrescrevendo o método withdraw para não cobrar taxa
        @Override
        public void withdraw(double amount) {
            balance -= amount;
        }
    }

    // Subclasse que representa Conta Empresarial
    public class BusinessAccount extends Account {
        private double loanLimit;
        
        public BusinessAccount(int number, String holder, double balance, double loanLimit) {
            super(number, holder, balance);
            this.loanLimit = loanLimit;
        }
        
        // Pode ter métodos específicos, como loan(double amount)
        public void loan(double amount) {
            if (amount <= loanLimit) {
                balance += amount - 10.0;
            }
        }
    }
  ```

### Uso do Polimorfismo
  ```java
    public class Main {
        public static void main(String[] args) {
            // Variáveis do tipo da classe abstrata, mas instanciando subclasses
            Account account1 = new SavingsAccount(1023, "Maria", 1000.0, 0.01);
            Account account2 = new BusinessAccount(1024, "Alex", 1000.0, 500.0);
            
            // Aqui, a variável do tipo Account chama withdraw,
            // mas o comportamento é definido pela implementação de cada subclasse.
            account1.withdraw(50.0); // Executa o método sobrescrito em SavingsAccount (sem taxa)
            account2.withdraw(50.0); // Executa o método em Account (com taxa de R$5,00)
            
            System.out.println("Saldo de Maria (Conta Poupança): " + account1.getBalance());
            System.out.println("Saldo de Alex (Conta Empresarial): " + account2.getBalance());
        }
    }
```

## 4. Notação UML e Observações 📊

  - **Notação UML:** Em diagramas UML, uma classe abstrata é normalmente representada usando o itálico para seu nome e métodos.

  - **Por Que Não Instanciar a Superclasse?**

    **Reuso:** Centraliza e reutiliza o código comum.

    **Polimorfismo:** Permite tratar todas as contas de forma uniforme, facilitando operações como iterar sobre uma coleção de diferentes tipos de contas para totalizar saldos ou aplicar operações em massa.


**Conclusão** 🏁
  - Utilize classes abstratas para:

  - Garantir que apenas subclasses concretas possam ser instanciadas.

  - Promover reuso e manter o código organizado.

  - Facilitar o uso do polimorfismo, permitindo que variáveis de um tipo genérico (a superclasse abstrata) tratem uniformemente objetos de diferentes subclasses.

Domine esse conceito para criar sistemas mais robustos e flexíveis em Java! 😊🚀