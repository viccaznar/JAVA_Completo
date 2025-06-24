# Cartões de Resumo: Sobreposição, Palavra `super` e Anotação `@Override` em Java 🎭🔧

  Neste cartão, exploramos conceitos fundamentais para customizar comportamentos em hierarquias de classes: sobreposição (ou sobrescrita), o uso da palavra `super` e a anotação `@Override`. Estes mecanismos são essenciais para implementar polimorfismo e promover um código mais legível, reutilizável e consistente.


## 1. Sobreposição (Sobrescrita) 🌟
  - **Conceito:**  
    A sobreposição é a implementação, na subclasse, de um método que já existe na superclasse. Em outras palavras, a subclasse redefine o comportamento herdado para adequá-lo às suas necessidades.  
    - Relação "é-um": A subclasse é um tipo especializado da superclasse.
    - Facilita o polimorfismo, pois permite que o mesmo método execute ações diferentes, dependendo do objeto.

  - **Exemplo Lúdico:**  
  Imagine um ator que segue um roteiro. A superclasse representa o roteiro original, e a subclasse é como se o ator decidisse dar sua própria interpretação ou emoção a uma cena. Essa "sobrescrita" da interpretação permite que o personagem se adapte melhor ao contexto do espetáculo.

  - **Exemplo Prático:**  
  Considere uma classe `Account` com o método `withdraw` que sempre cobra uma taxa de R$5,00. Em uma subclasse `SavingsAccount`, essa taxa não se aplica:
 
  ```java
    // Superclasse: Conta comum com taxa de saque
    public class Account {
        protected double balance;
        
        public void withdraw(double amount) {
            balance -= amount + 5.0;
        }
    }
    
    // Subclasse: Conta poupança sem taxa de saque
    public class SavingsAccount extends Account {
        @Override
        public void withdraw(double amount) {
            balance -= amount;
        }
    }
  ```


## 2. Anotação `@Override` ✔️

  - **Conceito:**  
    A anotação `@Override` indica ao compilador e ao leitor do código que o método está sobrescrevendo uma implementação definida na superclasse.

    - **Vantagens:**
      - **Segurança:** O compilador verifica se realmente existe um método na superclasse com a mesma assinatura, evitando erros de digitação.
  
      - **Legibilidade:** Facilita a identificação das áreas onde o comportamento foi customizado.

  - **Exemplo Lúdico:**  
  Pense em `@Override` como uma etiqueta adesiva que o ator coloca em sua performance para lembrar a todos que sua interpretação foi cuidadosamente adaptada, e não é apenas o roteiro lido de forma automática.

  - **Exemplo Prático:**  
  Na classe `SavingsAccount` acima, o uso de `@Override` garante que o método `withdraw` está corretamente sobrescrito:
  ```java
    @Override
    public void withdraw(double amount) {
        balance -= amount;
    }
  ```

## 3. Palavra `super` 🚀

  - **Conceito:**  
    `super` é uma palavra-chave que permite chamar a implementação original do método na superclasse a partir da subclasse.
    - Útil quando se deseja executar parcialmente o comportamento herdado, adicionando algo extra.
    - Pode ser usada tanto em métodos quanto em construtores para acessar membros da superclasse.

  - **Exemplo Lúdico:**  
  Imagine um chef de cozinha que segue uma receita base (a superclasse) mas adiciona um toque especial. Ele primeiro prepara a receita conforme o padrão (usando `super` para chamar o procedimento original) e depois acrescenta um ingrediente secreto para personalizar o prato.

  - **Exemplo Prático:**  
  Na classe `BusinessAccount`, ao realizar um saque, a regra é executar o saque normal da superclasse e, em seguida, deduzir uma taxa adicional de R$2,00:
 
  ```java
  public class BusinessAccount extends Account {
      private double loanLimit;
      
      public BusinessAccount(Integer number, String holder, Double balance, double loanLimit) {
          super(number, holder, balance); // Chamando construtor da superclasse
          this.loanLimit = loanLimit;
      }
  
      @Override
      public void withdraw(double amount) {
          super.withdraw(amount); // Executa a lógica de saque da superclasse (que, por exemplo, cobra R$5,00)
          balance -= 2.0;         // Aplica uma taxa adicional específica da conta empresarial
      }
  }
  ```


## 4. Recapitulando com Construtores ⛑️

  - **Uso de `super` em Construtores:**  
    Ao criar uma subclasse, você pode chamar o construtor da superclasse com `super(...)` para inicializar os atributos herdados corretamente.
  
  - **Exemplo Prático:**
  ```java
    public class Account {
        private Integer number;
        private String holder;
        private Double balance;
        
        public Account(Integer number, String holder, Double balance) {
            this.number = number;
            this.holder = holder;
            this.balance = balance;
        }
    }
    
    public class BusinessAccount extends Account {
        private double loanLimit;
        
        public BusinessAccount(Integer number, String holder, Double balance, double loanLimit) {
            super(number, holder, balance);  // Inicializa os atributos da superclasse
            this.loanLimit = loanLimit;
        }
    }
  ```


## Conclusão 🏁

  - **Sobreposição:** Permite adaptar e especializar comportamentos herdados.

  - **Anotação `@Override`:** Facilita a manutenção e garante a correção na sobrescrita.

  - **Palavra `super`:** Oferece acesso à implementação original, possibilitando a expansão de funcionalidades sem duplicação de código.

Utilize estas técnicas para desenvolver sistemas mais flexíveis e robustos, garantindo que seu código seja claro, reutilizável e alinhado com os princípios da orientação a objetos! 😊🚀
