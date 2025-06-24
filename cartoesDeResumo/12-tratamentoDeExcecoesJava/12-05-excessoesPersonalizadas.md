# Cartões de Resumo: Criando Exceções Personalizadas em Java ⚠️🐞

  As exceções personalizadas permitem que você trate erros específicos do domínio da sua aplicação de forma clara e organizada. Em vez de espalhar validações em todo o código ou retornar mensagens de erro via strings, você delega a lógica de validação para suas classes de modelo e utiliza o mecanismo de exceções para interromper a execução quando uma regra de negócio é violada.


## 1. Contexto e Motivação

  - **Problema Exemplo – Hotel Reservation:**  
    Imagine um sistema para gerenciar reservas de hotel. O sistema recebe dados como número do quarto, data de entrada e data de saída, e deve exibir a reserva com a duração em dias.  
    
    
    **Regras de validação:**  
    - As atualizações só podem ocorrer para datas futuras.  
    - A data de saída deve ser maior que a data de entrada.  
    - Dados inválidos devem interromper o processo e exibir uma mensagem de erro.


  - **Por Que Utilizar Exceções Personalizadas?**  

    Em vez de:
      
      - **Solução 1 (muito ruim):** Incluir toda a lógica de validação no programa principal, dificultando a manutenção e entendimento.  
      

      - **Solução 2 (ruim):** Retornar uma string de erro, comprometendo a semântica da operação e tornando o fluxo de controle confuso.


      - **Solução 3 (boa):** Utilizar exceções personalizadas para delegar a lógica de erro para a própria classe de reserva, melhorando o reuso, a legibilidade e permitindo o auxílio do compilador.


## 2. Conceitos-Chave

  - **Cláusula `throw`:**  
    Lança explicitamente uma exceção e interrompe a execução do método. Por exemplo, se uma data inválida for encontrada, o método "corta" a execução e lança a exceção.


  - **Cláusula `throws`:**  
    Propaga a exceção para ser tratada em um nível superior, em vez de tratá-la no mesmo método.


  - **Exception vs. RuntimeException:**  
    
    - **Exception:** Exige tratamento ou propagação (ex.: suas exceções personalizadas podem estender `Exception` para forçar o tratamento).  
    
    - **RuntimeException:** Não obriga o tratamento pelo compilador.


  - **Vantagens do Modelo de Exceções:**  
    
    - **Lógica Delegada:** A validação fica encapsulada na classe que conhece as regras do domínio (ex.: Reserva).  
    
    - **Código Mais Simples:** Reduz estruturas condicionais aninhadas, interrompendo o fluxo assim que um problema é detectado.  
    
    - **Auxílio do Compilador:** Ao usar exceções verificadas, o compilador força o tratamento dos erros.
    
    - **Consistência:** Facilita o tratamento de erros de diferentes tipos de forma higiênica e centralizada.



- **Exemplo Lúdico**
  Imagine que você é um concierge responsável por organizar reservas em um hotel 🏨. Quando um hóspede tenta fazer uma reserva com datas inválidas (como reservar para o passado ou com data de saída anterior à data de entrada), um alarme personalizado é disparado. Esse "alarme" age como uma exceção personalizada — ele imediatamente interrompe o processo e informa o hóspede com uma mensagem clara sobre o que há de errado, garantindo que apenas reservas corretas sejam processadas.


  - **Exemplo Prático em Código**

  ### Criação de uma Exceção Personalizada

  ```java
    // Exceção personalizada para reservas inválidas
    public class ReservationException extends Exception {
        public ReservationException(String message) {
            super(message);
        }
    }
  ```

  
### Classe de Reserva com Validação

  ```java
    import java.text.ParseException;
    import java.text.SimpleDateFormat;
    import java.util.Date;

    public class Reservation {
        private int roomNumber;
        private Date checkIn;
        private Date checkOut;
        
        private static SimpleDateFormat sdf = new SimpleDateFormat("dd/MM/yyyy");
        
        public Reservation(int roomNumber, Date checkIn, Date checkOut) throws ReservationException {
            if (!checkOut.after(checkIn)) {
                throw new ReservationException("Check-out date must be after check-in date");
            }
            this.roomNumber = roomNumber;
            this.checkIn = checkIn;
            this.checkOut = checkOut;
        }
        
        public int duration() {
            long diff = checkOut.getTime() - checkIn.getTime();
            return (int)(diff / (1000 * 60 * 60 * 24));
        }
        
        public void updateDates(Date newCheckIn, Date newCheckOut) throws ReservationException {
            Date now = new Date();
            if (newCheckIn.before(now) || newCheckOut.before(now)) {
                throw new ReservationException("Reservation dates for update must be future dates");
            }
            if (!newCheckOut.after(newCheckIn)) {
                throw new ReservationException("Check-out date must be after check-in date");
            }
            this.checkIn = newCheckIn;
            this.checkOut = newCheckOut;
        }
        
        @Override
        public String toString() {
            return "Room " + roomNumber + ", check-in: " +
                    sdf.format(checkIn) + ", check-out: " + sdf.format(checkOut) +
                    ", " + duration() + " nights";
        }
    }
  ```

### Uso e Tratamento da Exceção

  ```java
    import java.text.ParseException;
    import java.util.Date;

    public class Main {
        public static void main(String[] args) {
            SimpleDateFormat sdf = new SimpleDateFormat("dd/MM/yyyy");
            try {
                int roomNumber = 8021;
                Date checkIn = sdf.parse("23/09/2019");
                Date checkOut = sdf.parse("26/09/2019");
                
                Reservation reservation = new Reservation(roomNumber, checkIn, checkOut);
                System.out.println("Reservation: " + reservation);
                
                // Tentar atualizar a reserva com novas datas
                Date newCheckIn = sdf.parse("24/09/2019");
                Date newCheckOut = sdf.parse("29/09/2019");
                reservation.updateDates(newCheckIn, newCheckOut);
                System.out.println("Updated Reservation: " + reservation);
                
                // Exemplo de dados inválidos: data de saída antes da data de entrada
                newCheckOut = sdf.parse("21/09/2019");
                reservation.updateDates(newCheckIn, newCheckOut);
            } catch (ParseException e) {
                System.out.println("Invalid date format");
            } catch (ReservationException e) {
                System.out.println("Error in reservation: " + e.getMessage());
            }
        }
    }
  ```

- **Explicação:**
  
  - A classe Reservation encapsula as regras de negócio para reservas de hotel.  
  
  - Se as regras são violadas (por exemplo, data de saída não depois da data de entrada ou datas passadas para atualização), uma ReservationException é lançada, interrompendo a operação.
  
  - No método main, os blocos try-catch capturam esses erros, exibindo mensagens claras ao usuário.

**Conclusão**
  
  - **Usar exceções personalizadas:**

    - **Delegar Lógica de Validação:**
    A lógica do erro fica dentro da classe que "conhece" as regras da reserva, não dispersa pelo programa.

    - **Simplificar o Código:** 
    Elimina aninhamentos de condicionais, interrompendo a execução imediatamente quando um problema é detectado.

    - **Apoio do Compilador:**
    Ao usar exceções do tipo Exception, o compilador garante que o programador trate ou propague os erros.

Domine o uso de exceções personalizadas para criar sistemas mais robustos, claros e de fácil manutenção! 😊🚀