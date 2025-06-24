# Cartões de Resumo: Conceitos de Sobrecarga e Construtores em Java 🧩🚀

## 1. Sobrecarga de Métodos 🔄

  **Fundamento:**  
  Sobrecarga é um recurso que permite a uma classe ter mais de um método com o mesmo nome, mas com diferentes listas de parâmetros. Isso possibilita realizar operações similares de maneiras variadas, conforme a assinatura do método.

  **Exemplo Lúdico:**  
  Imagine uma caixa de giz de cera 🎨; todos os lápis têm o mesmo nome “giz”, mas com cores diferentes. Assim como a sobrecarga, o nome é igual, mas cada “cor” (parâmetro) traz um resultado distinto para o desenho.

  **Exemplo Prático:**
  ```java
    public class Calculadora {
        // Método para somar dois números inteiros
        public int soma(int a, int b) {
            return a + b;
        }

        // Método para somar três números inteiros
        public int soma(int a, int b, int c) {
            return a + b + c;
        }
    }
  ```

## 2. Construtores em Java: Construtor Opcional e Construtor Padrão 🏗️
  **Fundamento:** Construtores são métodos especiais responsáveis por inicializar objetos quando são criados.

  **Construtor Padrão:** Geralmente, não recebe parâmetros e pode definir valores padrão ou deixar a configuração para depois.

  **Construtor Opcional:** Recebe apenas os parâmetros essenciais (por exemplo, nome e preço) e inicializa outros atributos (como quantidade) com um valor padrão (nesse caso, zero).

  **Exemplo Lúdico:** Pense em montar um quebra-cabeça 🧩: você começa com as peças principais (nome e preço) e as peças faltantes (quantidade) já vêm configuradas com um valor inicial (zero), facilitando a montagem inicial.

  **Exemplo Prático:**
  ```java
    package entities;

    public class Product {
        public String name;
        public double price;
        public int quantity;

        // Construtor padrão: não recebe parâmetros
        public Product() {
        }

        // Construtor que inicializa todos os atributos
        public Product(String name, double price, int quantity) {
            this.name = name;
            this.price = price;
            this.quantity = quantity;
        }

        // Construtor opcional: inicializa apenas nome e preço, 
        // com quantidade iniciada em zero
        public Product(String name, double price) {
            this.name = name;
            this.price = price;
            this.quantity = 0;
        }
    }
  ```

Explore esses cartões para fixar os conceitos e transformar a teoria em prática. Continue praticando e testando seus conhecimentos em Java! 🚀📚