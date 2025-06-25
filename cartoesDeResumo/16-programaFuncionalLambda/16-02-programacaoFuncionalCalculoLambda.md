# Cartões de Resumo: Programação Funcional e Cálculo Lambda em Java 💻⚡

  Este cartão apresenta os conceitos fundamentais da programação funcional, mostrando como as expressões lambda e outras técnicas modernas (como method references e inferência de tipos) transformaram a forma de escrever código Java. Esses conceitos, baseados no Cálculo Lambda de Church (1930), contrastam com os paradigmas imperativos e orientados a objetos.


## 1. Paradigmas de Programação 🌐

  - **Imperativo:**  


    - Exemplos: C, Pascal, Fortran, Cobol  

    - Aborda "Como" algo deve ser computado por meio de comandos sequenciais.


  - **Orientado a Objetos:**  


    - Exemplos: C++, ObjectPascal, Java (< 8), C# (< 3)  

    - Trabalha com objetos mutáveis e encapsulados.


  - **Funcional:**  


    - Exemplos: Haskell, Clojure, Clean, Erlang  

    - Baseado no formalismo matemático do **Cálculo Lambda** (Church, 1930)  

    - Foca em **expressões declarativas** ("o que" deve ser feito) em vez de comandos.


  - **Lógico:**  


    - Exemplo: Prolog


  - **Multiparadigma:**  


    - Exemplos: JavaScript, Java (8+), C# (3+), Ruby, Python, Go  

    - Combina características de diversos paradigmas.


## 2. Características da Programação Funcional 🌟

  - **Transparência Referencial:**  


    - Uma função é referencialmente transparente se, para os mesmos dados de entrada, ela sempre retorna o mesmo resultado, sem efeitos colaterais.  

    - *Benefícios:* Simplicidade, previsibilidade e facilidade de raciocínio.



  - **Funções de Primeira Classe:**  


    - Funções podem ser tratadas como valores: passadas como parâmetro, retornadas de métodos, armazenadas em variáveis.



  - **Imutabilidade:**  


    - Objetos imutáveis são comuns na programação funcional, facilitando o raciocínio e evitando efeitos colaterais.


  - **Expressividade e Código Conciso:**  


    - Permite escrever soluções mais curtas e expressivas (exemplo: usar streams e reduce() em vez de laços de repetição).


  - **Tipagem Dinâmica / Inferência de Tipos:**  


    - Menor necessidade de declarar os tipos explicitamente, melhorando a legibilidade do código.


## 3. Expressões Lambda e Cálculo Lambda ⏩

  - **Cálculo Lambda:**  


    - Formalismo matemático que fundamenta a programação funcional.



  - **Expressão Lambda:**  


    - Função anônima de primeira classe.


    - **Sintaxe:**  


      Pode ser escrita com ou sem chaves, sendo frequentemente usada para implementar interfaces funcionais (interfaces com um único método abstrato).  


    - *Exemplo:*  

      ```java
        (p1, p2) -> p1.getPrice().compareTo(p2.getPrice())
      ```


  - **Method References:**  


    - Forma concisa de referenciar métodos já existentes.


    - **Sintaxe:**  


      ```java
      Classe::método
      ```


    - Exemplo de uso com `List.sort`:


      ```java
      list.sort(Program::compareProducts);
      ```


## 4. Exemplos Lúdico e Prático 🎲 & 💻

  ### Exemplo Lúdico: A Receita de um Chef 👨‍🍳
  
  - **Cenário:**  
    Imagine um chef que cozinha seguindo uma *receita* (função) que sempre produz o mesmo prato com os mesmos ingredientes (entrada).  
  
  
    - **Transparência Referencial:**  
      Se o chef seguir a receita, o resultado será sempre o mesmo, sem surpresas.  
  
  
    - **Funções de Primeira Classe:**  
      A receita pode ser passada para outros cozinheiros ou combinada com outras receitas para criar novos pratos.
  
  
    - **Lambda (Receita Expressa):**  
      Em vez de escrever toda a receita passo a passo (métodos completos), o chef pode dar uma “gambiarra” rápida, dizendo somente “misture tudo” com ingredientes já definidos – uma forma concisa de alcançar o resultado desejado.


  ### Exemplo Prático em Java:


   ```java
      package application;

      import java.util.ArrayList;
      import java.util.List;

      import entities.Product;

      public class Program {
          // Método estatístico para comparar produtos por preço
          public static int compareProducts(Product p1, Product p2) {
              return p1.getPrice().compareTo(p2.getPrice());
          }

          public static void main(String[] args) {
              List<Product> list = new ArrayList<>();
              list.add(new Product("TV", 900.00));
              list.add(new Product("Notebook", 1200.00));
              list.add(new Product("Tablet", 450.00));
              
              // Ordena utilizando method reference (mais conciso)
              list.sort(Program::compareProducts);
              
              // Ou utilizando uma expressão lambda sem chaves
              // list.sort((p1, p2) -> p1.getPrice().compareTo(p2.getPrice()));
              
              // Imprime os produtos ordenados
              list.forEach(System.out::println);
              
              // Exemplo de redução utilizando streams, demonstrando expressividade
              int sum = list.stream().mapToInt(p -> p.getPrice().intValue()).reduce(0, Integer::sum);
              System.out.println("Total Sum: " + sum);
          }
      }
  ```

  - **Classe Product (exemplo simplificado):**

  ```java
    package entities;

    public class Product {
        private String name;
        private Double price;
        
        public Product(String name, Double price) {
            this.name = name;
            this.price = price;
        }
        
        public String getName() {
            return name;
        }
        
        public Double getPrice() {
            return price;
        }
        
        @Override
        public String toString() {
            return "Product [name=" + name + ", price=" + price + "]";
        }
    }
  ```


### Conclusão 🏁

  - **Paradigma Funcional:** Baseado no Cálculo Lambda, enfatizando transparência referencial e imutabilidade.


  - **Expressões Lambda e Method References:** Permitem escrever funções anônimas concisas e reutilizáveis, melhorando a expressividade do código.


  - **Benefícios:**


    - Código mais conciso e declarativo (“o que” em vez de “como”).

    - Funções de primeira classe possibilitam maior reuso e flexibilidade.

    - Inferência de tipos e tipagem dinâmica tornam o código mais claro e limpo.



Adote a programação funcional e utilize lambda expressions para criar código moderno, conciso e de alta expressividade em Java! 😊🚀