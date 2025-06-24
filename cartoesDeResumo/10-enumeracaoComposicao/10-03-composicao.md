# Cartões de Resumo: Composição em Java 🔗🏗️

  A composição é um dos pilares da programação orientada a objetos e define uma forma de associação entre classes, onde um objeto "tem" outro ou "tem vários". Essa técnica promove um design mais limpo e modular.


## 1. Conceito de Composição 🤝

  - **Definição:**  
    Composição é uma associação em que um objeto contém outro(s) para modelar relações "tem-um" ou "tem-vários".  
  
  - **O que significa:**  
    Um objeto composto é responsável por gerenciar a vida dos objetos que ele contém, criando uma forte ligação entre o "todo" e suas "partes".

  - **Exemplo Lúdico:**  
  Imagine um carro 🚗. Ele "tem um" motor, "tem" rodas, "tem" porta-malas, etc. Cada parte é essencial para o funcionamento do carro e faz parte da sua composição.


## 2. Vantagens da Composição 🌟

  - **Organização:**  
    Facilita a divisão de responsabilidades, permitindo que cada objeto cuide de um aspecto específico do sistema.
  
  - **Coesão:**  
    Grupos de funcionalidades estão reunidos em objetos internos, tornando o código mais modular e de fácil compreensão.
  
  - **Flexibilidade:**  
    Permite alterar ou estender funcionalidades sem afetar outros componentes do sistema.
  
  - **Reuso:**  
    Componentes bem definidos podem ser reutilizados em diferentes contextos e sistemas.

  - **Exemplo Lúdico:**  
  Pense em um time esportivo ⚽, onde cada jogador tem funções específicas, mas todos trabalham juntos para o sucesso do time. Assim como jogadores especializados, as partes de uma composição são reutilizáveis e podem ser ajustadas conforme a necessidade.


  - **Exemplo Prático em Java:** 💻
  Imagine duas classes: `Order` (pedido) e `OrderItem` (item do pedido). Um pedido possui vários itens, caracterizando uma relação de composição.
  ```java
```    public class OrderItem {
        private String product;
        private int quantity;
        private double price;

        public OrderItem(String product, int quantity, double price) {
            this.product = product;
            this.quantity = quantity;
            this.price = price;
        }

        // Getters e setters
        public String getProduct() {
            return product;
        }

        public int getQuantity() {
            return quantity;
        }

        public double getPrice() {
            return price;
        }
    }
  ```

  ```java
    import java.util.ArrayList;
    import java.util.List;

    public class Order {
        private int id;
        private List<OrderItem items; // A composição: Order "tem vários" OrderItems

        public Order(int id) {
            this.id = id;
            this.items = new ArrayList<();
        }

        public void addItem(OrderItem item) {
            items.add(item);
        }

        public List<OrderItem getItems() {
            return items;
        }

        public double total() {
            return items.stream().mapToDouble(i - i.getPrice() * i.getQuantity()).sum();
        }
        
        // Outros métodos como removeItem, etc.
    }
  ```

  ```java
    public class Main {
        public static void main(String[] args) {
            Order order = new Order(1);
            order.addItem(new OrderItem("Laptop", 1, 1500.00));
            order.addItem(new OrderItem("Mouse", 2, 25.50));
            
            System.out.println("Total do Pedido: " + order.total());
        }
    }
  ```

  - **Explicação:**
  Neste exemplo, a classe Order é composta por vários objetos da classe OrderItem. Cada item é parte integrante do pedido. Quando o pedido é finalizado, todos os seus itens fazem parte desse contexto, demonstrando a relação "tem-vários".

## 3. Nota sobre UML e Notação 🎨

  - Na UML, a composição é representada pelo diamante preto na extremidade que representa o "todo".

  - Aqui, chamamos de composição qualquer associação "tem-um" ou "tem-vários", mesmo que nem sempre seja representada explicitamente pelo símbolo UML.

Utilize a composição para organizar melhor seu código, promover o reuso e garantir maior coesão entre os objetos do seu sistema. Esse conceito é fundamental para aplicar boas práticas de design em Java! 😊🚀