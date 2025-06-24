# Cartões de Resumo: Interfaces em Java e Aplicação no Sistema de Aluguel de Carros 🚗📜

  Este cartão aborda o conceito de **interfaces** na Programação Orientada a Objetos em Java, explicando sua definição clássica, suas vantagens, e como são utilizadas para criar sistemas de baixo acoplamento e alta flexibilidade – ilustrado com um problema real de aluguel de carros e geração de fatura. Também tocamos brevemente no conceito de *default methods* introduzido no Java 8.


## 1. Conceito de Interfaces

  - **Definição:**
    
    Uma **interface** define um conjunto de operações (métodos) que uma classe deve implementar, atuando como um contrato a ser seguido.  
    ```java
      interface Shape {
          double area();
          double perimeter();
      }
    ```

- **Objetivo:**


    **Baixo Acoplamento:** Permite que as classes se comuniquem por meio de contratos, sem saber detalhes da implementação.

    **Flexibilidade e Reusabilidade:** Facilita a criação de sistemas modulares e facilmente substituíveis.

    **Nota Importante:** A partir do Java 8, interfaces podem ter default methods (métodos com implementação padrão), mas inicialmente trabalhamos com a definição clássica.


  - **Exemplo Lúdico:**
      Pense em uma interface como um contrato de aluguel onde ambas as partes – locador e locatário – assinam um acordo com regras claras. Assim, qualquer tipo de veículo (ou forma) que "assina" esse contrato promete oferecer as funcionalidades contratadas, sem revelar como internamente isso será realizado.


## 2. Aplicação: Sistema de Aluguel de Carros 🚗💰


  **Problema Exemplo:**
  
    - Uma locadora brasileira de carros possui regras específicas para cobrança:

    - Para locações de até 12 horas: Cobrança por hora.

    - Para locações acima de 12 horas: Cobrança com base diária.
    
    - Além disso, há imposto:

      - 20% para valores até R$100.00

      - 15% para valores acima de R$100.00



  **Dados de Entrada:**

    - Modelo do carro, data e hora da retirada, data e hora do retorno;

    - Preço por hora e preço por dia.



  **Saída:** Gerar uma fatura contendo:

  - Pagamento básico (calculado a partir da duração da locação e o preço, seja por hora ou por dia),

  - Valor do imposto,

  - Pagamento total (soma dos dois).


## 3. Resolução do Problema com Interfaces


  Para organizar o sistema, utiliza-se um design em camadas:

  - **Entities:** Representam os dados do domínio, como a classe CarRental que contém informações da locação.

  - **Services:** A camada de serviço, como RentalService, define operações (por meio de uma interface, por exemplo) para processar o aluguel e gerar a fatura.


## 4. Exemplo de uso na camada de serviço:

  ```java
    CarRental cr = new CarRental(...);          // Dados da locação
    RentalService service = new RentalServiceImpl(); // Implementação do serviço
    service.processInvoice(cr);
  ```

    - Isso permite que o contrato (interface) para o serviço seja mantido, garantindo que qualquer implementação futura respeite a mesma assinatura e comportamento, promovendo flexibilidade e baixo acoplamento.


  - **Exemplo Lúdico:**
    Imagine que a locadora tem um "manual de instruções" (interface) que detalha como calcular a fatura. Qualquer departamento (ou sistema) que siga esse manual entrega o mesmo resultado esperado – seja usando cálculo por hora ou por dia, com a taxa de imposto adequada.


  - **Exemplo Prático:**
    A seguir, veja como podemos definir uma interface para o serviço de fatura e sua utilização no contexto do problema:

  ```java
    // Interface definindo o contrato do serviço de fatura
    public interface RentalService {
        void processInvoice(CarRental carRental) throws Exception;
    }

    // Implementação do serviço de fatura
    public class RentalServiceImpl implements RentalService {
        private double pricePerHour;
        private double pricePerDay;
        
        public RentalServiceImpl(double pricePerHour, double pricePerDay) {
            this.pricePerHour = pricePerHour;
            this.pricePerDay = pricePerDay;
        }
        
        @Override
        public void processInvoice(CarRental carRental) throws Exception {
            // Exemplo simplificado:
            // Calcular duração da locação e determinar taxa: se durar até 12h, usa preço por hora, caso contrário, preço por dia.
            long durationInMinutes = /* cálculo a partir de carRental.getStart() e carRental.getFinish() */;
            double basicPayment;
            if(durationInMinutes <= 12 * 60) {
                basicPayment = Math.ceil(durationInMinutes / 60.0) * pricePerHour;
            } else {
                basicPayment = Math.ceil(durationInMinutes / (24 * 60.0)) * pricePerDay;
            }
            double tax;
            if(basicPayment <= 100.00)
                tax = basicPayment * 0.20;
            else
                tax = basicPayment * 0.15;
            
            Invoice invoice = new Invoice(basicPayment, tax);
            carRental.setInvoice(invoice);
        }
    }
    ```
  - **Explicação:**
  

   - **Interface RentalService:** Define que qualquer serviço de aluguel deve implementar o método processInvoice.

   - **Implementação RentalServiceImpl:** Realiza o processamento baseado na duração da locação e nos preços informados, atribuindo o imposto conforme as regras.
   
   - **CarRental e Invoice:** São as entidades (do domínio) que armazenam os dados da locação e da fatura, respectivamente.



**Conclusão**

  - **Uso de Interfaces:** As interfaces servem como contratos para definir operações que as classes devem implementar, garantindo baixa dependência entre componentes e alta flexibilidade no design do sistema.

   - **Benefícios:**

   
      - **Modularidade e Reuso:** Componentes podem ser facilmente substituídos, desde que implementem a mesma interface.

      - **Facilidade de Manutenção:** As mudanças podem ocorrer isoladamente nas implementações sem afetar o contrato.


   - **Default Methods:** Embora neste primeiro momento trabalhamos com a definição clássica de interfaces, a partir do Java 8, as interfaces podem incluir métodos com implementação padrão, ampliando ainda mais sua flexibilidade para evoluir sem quebrar contratos existentes.


Domine o uso de interfaces para construir sistemas orientados a objetos robustos e flexíveis, onde cada componente cumpre um contrato bem definido e facilita a manutenção e evolução do código! 😊🚀