# Cartões de Resumo: Método toString e Herança de Object em Java 😊🔍

## 1. Herança da Classe Object 🌳
  - **Fundamento:**  
  Toda classe em Java herda da classe `Object`, o que significa que automaticamente ela ganha métodos úteis para manipulação e comparação de objetos.

  - **Métodos Herdados Importantes:**
  
    - **getClass()**: Retorna a classe (tipo) do objeto.
    
    - **equals(Object obj)**: Compara se dois objetos são iguais.
    
    - **hashCode()**: Gera um código hash que representa o objeto, útil em estruturas de dados.
    
    - **toString()**: Converte o objeto para uma representação em forma de string.
    
  - **Exemplo Lúdico:**  
    Imagine que cada objeto é como uma pessoa que, ao nascer, recebe um "passaporte básico" (os métodos da classe `Object`) que o identifica e permite interagir com outros.

  - **Exemplo Prático:**  
    ```java
      Product p = new Product();
      System.out.println(p.getClass()); // Exibe: class entities.Product
    ```

## 2. Sobrescrita (Override) do Método toString() ✍️
  - **Fundamento:**
  Ao sobrescrever o método toString(), você pode definir uma maneira personalizada de representar um objeto como uma string. Isso é especialmente útil para depuração e exibição dos dados do objeto.

  - **Exemplo Lúdico:**
  Pense em um livro autobiográfico onde o próprio personagem (o objeto) conta sua história de maneira única — a sobrescrita do toString() permite que o objeto se apresente de forma especial.

  - **Exemplo Prático:**
  ```java
    public String toString() {
        return name + ", $ " 
              + String.format("%.2f", price) 
              + ", " + quantity 
              + " units, Total: $ " 
              + String.format("%.2f", totalValueInStock());
    }
  ```

## 3. A Classe Product e Seus Componentes 💼🔢
  - **Fundamento:**
  A classe Product é um exemplo prático que utiliza atributos e métodos para representar um produto.
  
  - **Atributos:**
    - name – Nome do produto.
    - price – Preço do produto.
    - quantity – Quantidade disponível em estoque.

  - **Métodos:**
    - totalValueInStock(): Calcula o valor total em estoque (preço multiplicado pela quantidade).
    - addProducts(int quantity): Incrementa a quantidade de produtos.
    - removeProducts(int quantity): Decrementa a quantidade de produtos.
    - toString(): Retorna uma string formatada com os detalhes do produto.

  - **Exemplo Lúdico:**
  Imagine uma vitrine de loja onde cada produto tem uma "cartela de descrição" especialmente preparada para destacar suas características. O método toString() é essa cartela, que resume as informações de maneira clara e atrativa.

  - **Exemplo Prático:**
  ```java
    Product prod = new Product();
    prod.name = "Smartphone";
    prod.price = 1200.00;
    prod.quantity = 10;
    System.out.println(prod.toString());
    // Saída: Smartphone, $ 1200.00, 10 units, Total: $ 12000.00
  ```

Este resumo explica como a herança da classe Object em Java oferece métodos básicos para qualquer objeto e destaca a importância de sobrescrever o método toString() para criar representações personalizadas e legíveis de objetos. Adquirir esses conceitos melhora significativamente a forma como os objetos são exibidos e depurados em seus programas! 😎📚


