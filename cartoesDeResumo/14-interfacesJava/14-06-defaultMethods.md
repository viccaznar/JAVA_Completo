# Cartões de Resumo: Default Methods em Java 🔧💡

  Desde o Java 8, as interfaces evoluíram e passaram a suportar **default methods** (ou métodos "defender"), permitindo que forneçam implementações padrão para seus métodos. Essa funcionalidade traz diversas vantagens e impacta o design orientado a objetos.


## 1. Conceitos Básicos

  - **Default Methods em Interfaces:**

    - A partir do Java 8, uma interface pode conter métodos com implementação concreta usando a palavra-chave `default`.

      - **Exemplo de definição:**
  

        ```java
        public interface InterestService {
            // Método a ser implementado pelas classes concretas para definir a taxa de juros
            double getInterestRate();
            
            // Método default que calcula o pagamento usando juros compostos
            default double payment(double amount, int months) {
                double payment = amount;
                for (int i = 0; i < months; i++) {
                    payment *= (1 + getInterestRate() / 100);
                }
                return payment;
            }
        }
        ```


  - **Propósito e Benefícios:**


    - **Evitar Repetição:** Possibilita reutilizar uma implementação padrão em todas as classes que implementam a interface, sem precisar replicar código.


    - **Elimina a Necessidade de Classes Abstratas:** Pode-se fornecer reuso sem criar uma hierarquia de classes abstratas somente para compartilhar métodos comuns.


    - **Retrocompatibilidade:** Permite que interfaces evoluam sem quebrar implementações existentes.


    - **Herança Múltipla de Comportamento:** Oferece uma forma de "herança múltipla" de métodos (não de atributos ou construtores), permitindo que uma classe implemente diversas interfaces com métodos default sem conflitos – desde que não haja assinaturas duplicadas.


## 2. Vantagens Práticas


  - **Reuso de Implementação:**  
    Classes que implementam a interface herdam automaticamente o comportamento padrão, economizando tempo e reduzindo erros.


  - **Facilita Implementação de "Interfaces Funcionais":**  
    Serviços que deveriam ter apenas um método abstrato podem ainda oferecer operações padrão reutilizáveis.


  - **Flexibilidade e Evolução:**  
    Novos métodos podem ser adicionados às interfaces sem forçar a alteração de todas as classes que já as implementam.


### Exemplo Lúdico 🎲


  Imagine uma fábrica de juros:


  - **Sem Default Methods:** Cada gerente de empréstimos (classe concreta) teria que desenvolver a mesma regra de cálculo de juros, como se cada um estivesse reinventando a roda.


  - **Com Default Methods:** A fábrica cria uma "receita padrão" (método default) para o cálculo de juros. Assim, todos os gerentes (classes que implementam a interface) simplesmente "seguiam a receita", garantindo uniformidade e poupando tempo. Se um gerente precisar de uma regra diferente, ele pode sobrescrever o método.



### Exemplo Prático 💻

  #### Cenário: Cálculo de Juros Compostos para Empréstimos


  - **Problema:**  
    Ler uma quantia e a duração (em meses) de um empréstimo e calcular o valor a ser pago após o prazo, aplicando juros compostos. No Brasil, a regra é de 2% ao mês.


  - **Exemplo 1 (Brasil):**
    - Quantia: 200.00
    - Meses: 3
    - Cálculo: `200 * 1.02 * 1.02 * 1.02 ≈ 212.24`


  - **Exemplo 2 (Outro País, taxa 1%):**
    - Quantia: 200.00
    - Meses: 3
    - Cálculo: `200 * 1.01 * 1.01 * 1.01 ≈ 206.06`


  #### Implementação:

  ```java
    // Interface definindo o contrato para serviços de juros
    public interface InterestService {
        double getInterestRate();
        
        // Método default para calcular o pagamento com juros compostos
        default double payment(double amount, int months) {
            double payment = amount;
            for (int i = 0; i < months; i++) {
                payment *= (1 + getInterestRate() / 100);
            }
            return payment;
        }
    }

    // Implementação para o serviço de juros do Brasil (2% ao mês)
    public class BrazilInterestService implements InterestService {
        @Override
        public double getInterestRate() {
            return 2.0;
        }
    }

    // Implementação para um serviço de juros de outro país (1% ao mês)
    public class USInterestService implements InterestService {
        @Override
        public double getInterestRate() {
            return 1.0;
        }
    }

    // Classe principal para execução do cálculo
    public class Program {
        public static void main(String[] args) {
            double amount = 200.00;
            int months = 3;
            
            InterestService brazilService = new BrazilInterestService();
            InterestService usService = new USInterestService();
            
            double brazilPayment = brazilService.payment(amount, months);
            double usPayment = usService.payment(amount, months);
            
            System.out.println("Payment after " + months + " months (Brazil): " + brazilPayment);
            System.out.println("Payment after " + months + " months (US): " + usPayment);
        }
    }
  ```

- **Explicação:**


  - **Interface InterestService:** Define o método getInterestRate() que cada implementação deve fornecer e um método default payment().  


 - **Classes Concretas:** BrazilInterestService e USInterestService implementam a interface e fornecem taxas diferentes.


 - **Resultado:** O método payment() usa a implementação default para calcular o valor do empréstimo com juros compostos, evitando a duplicação de código.


## 3. Considerações Importantes


  - **Herança Múltipla de Métodos:** Uma interface pode ter diversos default methods. Se houver métodos com a mesma assinatura herdados de diferentes interfaces, o compilador exigirá que o programador sobrescreva esse método para resolver o conflito.


 - **Limitações das Interfaces:** Diferentemente de classes abstratas, interfaces não podem ter atributos de instância nem construtores.


 - **Flexibilidade e Retrocompatibilidade:** Permitem evoluir interfaces sem quebrar implementações existentes, compatibilizando com sistemas legados.



### Conclusão 🏁 


  - **Default Methods:**
   Proporcionam reuso de código e permitem que interfaces não sejam apenas contratos, mas também forneçam implementações padrão.


  - **Benefícios:**


   - Menor repetição de código.

   - Não há necessidade de criar classes abstratas apenas para compartilhar implementação.

   - Suporte à herança múltipla de comportamento sem os problemas típicos da herança múltipla de classes.


Domine os Default Methods para escrever interfaces mais robustas, flexíveis e com maior reutilização de código! 😊🚀