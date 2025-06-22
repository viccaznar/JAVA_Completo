# Cartões de Resumo: Classes, Métodos e Packages em Java 🏫📦

## 1. Pacotes (Packages) 🔖
  - **Fundamento:**  
  Pacotes organizam classes relacionadas em um mesmo agrupamento, facilitando a manutenção e hierarquização do código.

  - **Exemplo Lúdico:**  
  Imagine uma caixa de brinquedos chamada "entities" na qual você guarda todos os brinquedos similares. Assim, fica fácil encontrar o que precisa.
  
  - **Exemplo Prático:**  
  ```java
    package entities;
  ```

## 2. Classes 🔷
  - **Fundamento:**
  Uma classe é o molde ou projeto que define um tipo de objeto, especificando seus atributos (dados) e métodos (comportamentos).

  - **Detalhes:**
    
    - **Nome da Classe:** Define o tipo (ex.: Triangle).
  
    - **Atributos:** Variáveis que armazenam os dados do objeto (ex.: a, b, c).
    
    - **Modificador public:** Permite que atributos e métodos sejam acessados de outros arquivos.

  - **Exemplo Lúdico:**
  Pense em uma classe como um molde para criar bonecos. Cada boneco (objeto) produzido a partir do molde terá as características definidas na classe.

  - **Exemplo Prático:**
  ```java
    package entities;

    public class Triangle {
        public double a;
        public double b;
        public double c;
    }
  ```


## 3. Métodos 🔧
  - **Fundamento:**
  Métodos são funções definidas dentro de uma classe que realizam operações com os dados. Eles são compostos por:

    - **Tipo de Retorno:** O tipo de dado que o método retorna (exemplo: double). Se não houver retorno, usa-se void.
    
    - **Nome do Método:** Identifica a função (exemplo: area).
    
    - **Parâmetros:** A lista de dados que o método utiliza.

    - **Corpo do Método:** O bloco de código que implementa a funcionalidade.

  - **Exemplo Lúdico:**
    Imagine um super-herói (o objeto) que possui habilidades especiais. O método area() é como uma superhabilidade que permite ao objeto calcular sua área.

  - **Exemplo Prático:**
  ```java
      public double area() {
        double p = (a + b + c) / 2.0;
        return Math.sqrt(p * (p - a) * (p - b) * (p - c));
    }
  ```


## 4. Projeto da Classe (Diagrama UML) 📊
  - **Fundamento:**
  Um diagrama UML de classe é uma representação visual que mostra:

    - **Nome da Classe**
  
    - **Atributos:** As variáveis que compõem a classe.

    - **Métodos:** As funções que definem o comportamento da classe.

  - **Exemplo Lúdico:**
  Imagine um mapa do tesouro que revela todos os segredos (atributos e métodos) de um objeto. Esse mapa ajuda a entender como o objeto funciona.

  - **Exemplo Prático:**
  Para a classe Triangle:

    - **Nome:** Triangle
  
    - **Atributos:** a, b, c
  
    - **Método:** area()

Este resumo abrange os conceitos essenciais de packages, classes, métodos e a representação UML para projetar classes em Java. Com esses fundamentos, você tem as bases para organizar seu código de forma clara e modular, facilitando tanto o desenvolvimento quanto a manutenção futura! 😊📘


