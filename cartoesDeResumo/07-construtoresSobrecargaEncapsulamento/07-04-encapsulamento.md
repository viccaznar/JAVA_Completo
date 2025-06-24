# Cartões de Resumo: Encapsulamento em Java 🔒✨

  O **encapsulamento** é um pilar fundamental da programação orientada a objetos em Java. Ele consiste em esconder os detalhes internos de implementação de uma classe, expondo apenas operações seguras que garantam que os objetos permaneçam sempre em um estado consistente.



## 1. Conceito e Importância 🧐💡

  - **Definição:**  
  O encapsulamento é o princípio que permite isolar os atributos internos de uma classe, protegendo-os de acessos diretos e indesejados. Isso assegura que somente métodos autorizados possam ler ou modificar estes valores, mantendo a integridade do objeto.

  - **Regra de Ouro:**  
  O objeto deve sempre estar em um estado consistente, e a própria classe é responsável por garantir essa consistência.



## 2. Regras Gerais para Encapsulamento 📜✅

  - **Atributos Privados:**  
    - Um objeto **não deve expor** seus atributos diretamente.  
    - Utilize o modificador de acesso `private` para torná-los inacessíveis diretamente de fora da classe.

  - **Acesso por Getters e Setters:**  
    - Os atributos devem ser acessados e modificados através de métodos públicos conhecidos como **getters** e **setters**.
    
    - Este padrão segue as diretrizes do JavaBeans, permitindo uma interface segura para interagir com os dados internos.

*Exemplo da implementação do padrão JavaBeans:*
  ```java
    private String name;
    private double price;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public double getPrice() {
        return price;
    }

    public void setPrice(double price) {
        this.price = price;
    }
  ```

## 3. Exemplo Prático: Classe Product 🛍️🖥️
  Veja um exemplo de implementação de encapsulamento na classe Product, onde os atributos são privados e acessados somente via getters e setters:
  ```java
    package entities;

    public class Product {
        private String name;
        private double price;
        private int quantity;
        
        // Construtor padrão
        public Product() {
        }
        
        // Construtor que inicializa todos os atributos
        public Product(String name, double price, int quantity) {
            this.name = name;
            this.price = price;
            this.quantity = quantity;
        }
        
        // Construtor opcional que inicializa apenas name e price
        // A quantidade é definida com valor padrão (zero)
        public Product(String name, double price) {
            this.name = name;
            this.price = price;
            this.quantity = 0;
        }
        
        // Getters e Setters
        public String getName() {
            return name;
        }
        
        public void setName(String name) {
            this.name = name;
        }
        
        public double getPrice() {
            return price;
        }
        
        public void setPrice(double price) {
            this.price = price;
        }
        
        public int getQuantity() {
            return quantity;
        }
        
        // Poderia ter também um setQuantity se necessário
    }
  ```
  
  Neste exemplo, a classe Product protege seus atributos com modificadores private e garante acesso controlado por meio de métodos, mantendo a consistência dos dados.

## 4. Exemplo Lúdico: A Caixa de Segredos 🎁🔐
  Imagine que você possui uma caixa de segredos com informações muito valiosas:

  **Atributos Privados:** São os segredos dentro da caixa que ninguém deve ver diretamente.

  **Getters e Setters:** Funcionam como a única chave que pode abrir a caixa e permitir que você veja ou altere os segredos de forma segura.

  **Consistência:** Assim como você deseja que a caixa nunca seja deixada aberta e seus segredos expostos, a classe deve garantir que os dados do objeto permaneçam em um estado consistente, evitando alterações diretas que possam causar erros.

  Essa metáfora ilustra como o encapsulamento protege as informações e mantém a integridade dos dados, apenas permitindo o acesso por meio de métodos controlados.

Adote essa prática em seus projetos para garantir que seus objetos estejam sempre bem protegidos e organizados. A disciplina do encapsulamento é crucial para criar sistemas robustos, seguros e de fácil manutenção! 🚀💻