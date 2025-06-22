# Cartões de Resumo: Instanciação, Memória, Classes e Objetos em Java 🚀📚

## 1. Instanciação (Alocação Dinâmica de Memória) 🏗️
- **Conceito:**  
  Instanciação é o processo de criar um novo objeto em tempo de execução usando a palavra-chave `new`, que aloca memória dinamicamente no heap.

- **Exemplo Lúdico:**  
  Imagine que você tem uma receita secreta (a classe) e decide preparar um prato (objeto) na hora; cada prato novo precisa de seu espaço na cozinha (heap). 
 
- **Exemplo Prático:**  
  ```java
  Triangle x, y;       // Declaração de referências para objetos do tipo Triangle
  x = new Triangle();  // Instanciação: reserva memória para um novo Triangle no heap
  ```

## 2. Memória: Heap vs. Stack 🔢
  - **Conceito:**
    - **Stack:** Área de memória que armazena variáveis locais e referências, organizada em uma estrutura de pilha e gerenciada automaticamente.
  
    - **Heap:** Área de memória destinada a objetos criados dinamicamente, onde o gerenciamento é mais flexível e controlado através do new.

  - **Exemplo Lúdico:**
    Imagine o stack como uma pilha de livros (variáveis temporárias) que você usa rapidamente, e o heap como uma biblioteca (objetos) onde cada volume é guardado para uso posterior.

  - **Representação Visual Simplificada:**
  
    **Stack:**
        ┌────────────────────┐
        │ areaX, areaY, p    │  <- Variáveis primitivas
        │ Referências x, y   │  <- Ponteiros para objetos
        └────────────────────┘

    **Heap:**
        ┌─────────────────────────────┐
        │ Objeto Triangle (x)         │  <- Guardado em um endereço (ex.: 0x100358)
        │   A   B   C  (atributos)      │
        └─────────────────────────────┘



## 3. Classes, Objetos e Atributos 👩‍🏫
  - **Classe:**
    É o molde ou definição que descreve um tipo de objeto, incluindo seus atributos (características) e, potencialmente, seus comportamentos (métodos).

  - **Objeto:**
    Uma instância de uma classe. Quando uma classe é instanciada, cria-se um objeto com os atributos definidos, com valores que podem ser atribuídos.

  - **Atributos:**
    São as variáveis ou características que compõem uma classe e que armazenam os dados dos objetos.

  - **Exemplo Lúdico:**
    Imagine uma classe como um molde de biscoito. Cada biscoito (objeto) feito a partir desse molde terá a mesma forma básica, mas pode ter variações (atributos) como sabor ou tamanho.

  - **Exemplo Prático:**
    ```java
        package course;

        public class Triangle {
            public double a;
            public double b;
            public double c;
        }

        // Exemplo de uso:
        Triangle x = new Triangle();
        x.a = 3.0;
        x.b = 4.0;
        x.c = 5.0;
        // O objeto 'x' agora tem os atributos a, b e c definidos.
    ```

Este resumo abrange os principais conceitos relacionados à instanciação (alocação dinâmica de memória), a distinção entre heap e stack, e os fundamentos de classes, objetos e atributos em Java. Esses elementos são essenciais para entender como o Java organiza e gerencia a memória e como os dados são estruturados e manipulados dentro dos programas! 😎📘


