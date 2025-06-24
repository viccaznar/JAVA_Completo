# Cartões de Resumo: Inversão de Controle e Injeção de Dependência em Java 🔄🛠️

  Este cartão aborda dois conceitos fundamentais para a criação de sistemas desacoplados e flexíveis: **Inversão de Controle (IoC)** e **Injeção de Dependência (DI)**. Aprenda como reduzir o acoplamento entre classes e facilitar a manutenção e evolução do código!


## 1. Acoplamento Forte vs. Acoplamento Fraco

  - **Acoplamento Forte:**
 

    - **Definição:** A classe dependente conhece e instancia diretamente a dependência concreta.
 
    - **Exemplo:** Em uma classe `RentalService`, se o objeto `taxService` for instanciado internamente (por exemplo, `new BrazilTaxService()`), a classe fica diretamente dependente dessa implementação. Se a dependência mudar, `RentalService` precisa ser alterado.


  - **Acoplamento Fraco:**
 

    - **Definição:** A classe dependente não conhece a implementação concreta da dependência, mas sim a abstração (interface).
 
    - **Vantagens:**  
      - Facilita a substituição ou alteração da dependência sem afetar a classe que a utiliza.
      - Torna o sistema mais flexível e de fácil manutenção.


  - **Exemplo Lúdico:**  
    Pense em um restaurante: se o chef precisar sempre buscar os ingredientes sozinho, qualquer mudança no fornecedor exigirá alterações no método de preparo. Mas se os ingredientes são entregues por um fornecedor externo (contrato bem definido), o chef só se preocupa com o preparo – independente de quem os forneceu.


## 2. Inversão de Controle (IoC)

  - **Definição:**  
    É um padrão de desenvolvimento que inverte a responsabilidade de criar objetos. Ao invés de uma classe instanciar suas dependências diretamente, essa responsabilidade é delegada a um componente externo.
    
  - **Benefícios:**
    - Promove um desenvolvimento com baixo acoplamento.
    - Melhora a testabilidade e a modularidade do código.

  - **Exemplo Lúdico:**  
    Imagine que em vez de um pintor ir comprar suas tintas, um assistente as providencia. Assim, o pintor pode se concentrar apenas em pintar, sem se preocupar com a aquisição dos materiais.


## 3. Injeção de Dependência (DI)

  - **Definição:**  
    É uma forma concreta de implementar a inversão de controle, na qual um componente externo cria as dependências e as "injeta" na classe que precisa delas.


  - **Formas de Implementação:**

    - **Por Construtor:** A dependência é passada como parâmetro no construtor.

    - **Por Setter:** A dependência é injetada via métodos setter.

    - **Por Framework/Container:** Um container (por exemplo, Spring) gerencia as instâncias.


  - **Exemplo Prático – Injeção por Construtor:**
  ```java
  // Interface que define o contrato para o serviço de imposto
  public interface TaxService {
      double calculateTax(double amount);
  }

  // Implementação concreta para o Brasil
  public class BrazilTaxService implements TaxService {
      @Override
      public double calculateTax(double amount) {
          // Exemplo simples: 20% de imposto para valores até 100 e 15% para valores maiores
          if(amount <= 100.0)
              return amount * 0.20;
          else
              return amount * 0.15;
      }
  }

  // Classe RentalService que depende de um TaxService para processar a fatura
  public class RentalService {
      private double pricePerHour;
      private double pricePerDay;
      private TaxService taxService;
      
      // Injeção de dependência via construtor
      public RentalService(double pricePerHour, double pricePerDay, TaxService taxService) {
          this.pricePerHour = pricePerHour;
          this.pricePerDay = pricePerDay;
          this.taxService = taxService;
      }
      
      public void processInvoice(CarRental carRental) {
          // Lógica para calcular o pagamento básico (exemplo simplificado)
          double basicPayment = /* cálculo baseado na duração da locação */;
          double tax = taxService.calculateTax(basicPayment);
          Invoice invoice = new Invoice(basicPayment, tax);
          carRental.setInvoice(invoice);
      }
  }

  // Em uma classe principal, a dependência é injetada no objeto RentalService
  public class Program {
      public static void main(String[] args) {
          double pricePerHour = 10.0;
          double pricePerDay = 130.0;
          
          // Ao invés de RentalService criar a dependência, ela é passada por fora
          RentalService rentalService = new RentalService(pricePerHour, pricePerDay, new BrazilTaxService());
          
          // Seguindo com o processamento do aluguel
          CarRental carRental = new CarRental(/* parâmetros da reserva */);
          rentalService.processInvoice(carRental);
          
          // Aqui, RentalService trabalha de forma desacoplada em relação a TaxService
          System.out.println("Invoice Processed!");
      }
  }
  ```

  - **Explicação:**  

     - A classe RentalService não cria internamente o objeto BrazilTaxService, mas recebe um objeto que implementa a interface TaxService por meio do construtor.  
  
    - Isso permite que se substitua a implementação do serviço de imposto sem modificar RentalService, alcançando baixo acoplamento.



**Conclusão**

  - **Inversão de Controle:** Remove a responsabilidade de instanciar dependências da classe "pai", tornando o código mais modular.

  - **Injeção de Dependência:** Uma prática que implementa IoC, onde as dependências são injetadas externamente (via construtor, setter ou container), promovendo baixo acoplamento e melhor manutenção.

Adote essas práticas para criar sistemas flexíveis e facilmente testáveis, onde componentes podem ser modificados ou substituídos sem grandes impactos no restante do código! 😊🚀