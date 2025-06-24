# Cartões de Resumo: Herdar vs. Cumprir Contrato em Java ⚖️📜

  Ao desenvolver aplicações orientadas a objetos em Java, você pode estruturar seu código usando **herança** ou **interfaces**. Cada abordagem tem vantagens específicas, e entender a diferença entre "herdar" e "cumprir contrato" é fundamental para criar sistemas flexíveis e bem organizados.


## 1. Aspectos em Comum entre Herança e Interfaces

  - **Relação é-um:**  
    Tanto a herança quanto a implementação de interfaces estabelecem uma relação "é-um". Por exemplo, um *Circle* é um *Shape*.


  - **Generalização/Especialização:**  
    Ambos os mecanismos permitem criar hierarquias. Uma classe mais genérica define comportamentos que podem ser especializados em subclasses ou em classes que implementam alguma interface.


  - **Polimorfismo:**  
    Permitem que você trate objetos de diferentes classes de forma uniforme. Por exemplo, métodos que recebem um argumento do tipo `Shape` podem trabalhar com qualquer objeto cuja classe seja derivada ou implemente `Shape`.


## 2. Diferença Fundamental

  - **Herança (Herdar):**  


    - **Reuso de Código:**  
      Permite que uma classe herde a implementação e os atributos de uma superclasse, facilitando o reuso e a centralização de comportamentos comuns.


    - **Exemplo Conceitual:**  
      Se todas as formas geométricas compartilham propriedades e métodos comuns (como a cor ou métodos para desenhar), uma classe abstrata base pode fornecer essa implementação comum aos seus filhos.



  - **Interface (Cumprir Contrato):**  


    - **Contrato a ser Cumprido:**  
      Uma interface define um conjunto de métodos sem fornecer implementação, obrigando as classes que a implementam a fornecer o comportamento específico.


    - **Exemplo Conceitual:**  
      A interface `Shape` pode definir os métodos `area()` e `perimeter()`, e qualquer classe que implemente `Shape` deve fornecer a lógica para esses métodos.


## 3. Quando Utilizar Cada Abordagem?


  - **Uso de Herança:**  

    - Quando há um forte reuso de código e uma estrutura comum reutilizável (por exemplo, métodos e atributos compartilhados entre todas as formas).
    

  - **Uso de Interface:**  

    - Quando você deseja definir um contrato claro que diversas classes devem seguir, garantindo que todas implementem determinados métodos, mas podendo ter implementações distintas.


  - **Combinação de Abordagens:**  

    - **Desafio Diagnóstico:**  
      "E se eu precisar implementar `Shape` como interface, porém também quiser definir uma estrutura comum reutilizável para todas as figuras?"  


    - **Solução:**  
      Combine ambos os conceitos: defina uma **interface** `Shape` que estabelece o contrato e crie uma **classe abstrata** (por exemplo, `AbstractShape`) que implementa alguns comportamentos comuns. As classes concretas então estendem a classe abstrata e cumprem o contrato da interface.


### Exemplo Lúdico 🎲

  Imagine um contrato de aluguel:

  - **Interface:** O contrato estipula que o inquilino deve pagar aluguel, cuidar da propriedade e seguir regras básicas – esse é o *contrato* que todos devem cumprir.

  - **Herança:** Ao mesmo tempo, a imobiliária pode oferecer um modelo padrão de apartamento, com uma estrutura comum (ambientes, decoração básica, etc.) que é herdada por diferentes tipos de apartamentos. Assim, cada apartamento "é um" modelo padrão, mas também cumpre o contrato de aluguel.


### Exemplo Prático 💻

### 1. Definindo a Interface e a Classe Abstrata

  ```java
    // Interface definindo o contrato de uma forma geométrica
    public interface Shape {
        double area();
        double perimeter();
    }

    // Classe abstrata com implementação comum para todas as formas
    public abstract class AbstractShape implements Shape {
        protected String color;

        public AbstractShape(String color) {
            this.color = color;
        }

        // Método comum a todas as formas
        public void display() {
            System.out.println("Color: " + color);
        }
    }

    // Classe concreta que herda da classe abstrata e cumpre o contrato da interface
    public class Circle extends AbstractShape {
        private double radius;

        public Circle(String color, double radius) {
            super(color);
            this.radius = radius;
        }

        @Override
        public double area() {
            return Math.PI * radius * radius;
        }

        @Override
        public double perimeter() {
            return 2 * Math.PI * radius;
        }
    }
  ```

### 2. Utilizando a Implementação

  ```java
    public class Program {
        public static void main(String[] args) {
            // Graças ao contrato (interface), podemos tratar Circle como um Shape
            Shape shape = new Circle("Red", 5.0);
            
            // Demonstração de polimorfismo: todos os métodos definidos na interface podem ser chamados
            System.out.println("Area: " + shape.area());
            System.out.println("Perimeter: " + shape.perimeter());
            
            // Como Circle também herda de AbstractShape, pode usar métodos comuns
            if (shape instanceof AbstractShape) {
                ((AbstractShape) shape).display();
            }
        }
    }
  ```

  - **Explicação:**
  

    - **Interface Shape:** Define os métodos `area()` e `perimeter()`, que qualquer forma geométrica deve implementar.
  
  
    - **Classe Abstrata AbstractShape:** Fornece uma implementação comum (como a propriedade `color` e o método `display()`).
  
  
    - **Classe Circle:** Implementa a interface `Shape` e estende a classe abstrata `AbstractShape`, fornecendo implementações específicas para os métodos do contrato.
  
  
    - **Polimorfismo:** Permite tratar objetos `Circle` como `Shape`, tornando o código mais flexível e desacoplado.


    - **Interface Shape:** Define os métodos area() e perimeter().


    - **Classe Abstrata AbstractShape:** Fornece uma estrutura comum (por exemplo, uma propriedade color e o método display()).


    - **Classe Circle:**  Estende AbstractShape e implementa os métodos do contrato definido por Shape.


    - **Polimorfismo:** Permite tratar objetos `Circle` como `Shape`, gerando código mais flexível e desacoplado.


### Conclusão 🏁

  **Herança vs. Cumprir Contrato:**


  - **Herança:** Foca no reuso de código; fornece uma estrutura comum reutilizável através de uma classe base.


    - **Interface:** Define um contrato que as classes devem cumprir; foca na padronização do comportamento.


    - **Combinação Ideal:**  Utilizar interfaces para definir contratos e classes abstratas para compartilhar implementações comuns resulta em sistemas modulares, flexíveis e de fácil manutenção.


Domine esses conceitos para criar arquiteturas de software robustas e desacopladas, facilitando a evolução do seu código ao longo do tempo! 😊🚀