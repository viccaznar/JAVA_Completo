# Cartões de Resumo: Vetores em Java 📊💻

  Explore os conceitos fundamentais dos **vetores** em Java, desde sua definição até a manipulação prática dos seus elementos, tanto para tipos primitivos quanto para tipos referência.


## 1. Conceito de Vetor 🗂️
  - **Definição:**  
    Um vetor é um arranjo unidimensional de dados.  
  - **Características:**  
    - **Homogêneo:** Todos os elementos são do mesmo tipo;  
    - **Ordenado:** Cada elemento é acessado por meio de uma posição (índice);  
    - **Memória Contígua:** Os elementos são alocados em um bloco único de memória.

  **Exemplo Lúdico:**
  Imagine uma estante de livros 📚, onde cada prateleira (índice) guarda um livro específico (elemento). Você consulta um livro pelo número da prateleira, sempre com acesso rápido.


## 2. Declaração e Instanciação 📝
  - **Declaração:**
    Define o tipo dos elementos e o nome do vetor.  
  - **Instanciação:**  
    Cria o vetor com um tamanho fixo, definindo quantos elementos ele pode armazenar.

  **Exemplo Prático:**
  ```java
    // Declarando e instanciando um vetor de double para armazenar alturas
    double[] heights = new double[5];
  ```

## 3. Manipulação de Vetor com Elementos Tipo Valor (Primitivo) 🔢
  **Fundamento:** Vetores de tipos primitivos armazenam os valores diretamente na posição do vetor.

  **Atribuição:** Ao atribuir ou copiar, o valor é transferido, não o endereço.

  **Exemplo Lúdico:**
  Imagine uma caixa de correio onde cada compartimento guarda uma carta com um número escrito. Ao copiar uma carta, você está transferindo o conteúdo, e não o local da carta original.

  **Exemplo Prático:**

  ```java
    int[] numeros = new int[3];
    numeros[0] = 10;
    numeros[1] = 20;
    numeros[2] = 30;
    int copia = numeros[1];  // copia recebe 20, valor de números[1]
  ```

## 4. Manipulação de Vetores com Elementos Tipo Referência (Classe) 🚀
  **Fundamento:** Vetores de tipos referência armazenam endereços de objetos alocados no heap. Quando você atribui ou copia um elemento, está copiando o ponteiro para o mesmo objeto.

  **Exemplo Lúdico:**
  Imagine que cada elemento do vetor é como um marcador de endereço 💌 que aponta para uma casa (objeto) em um bairro. Dois marcadores podem apontar para a mesma casa.

  **Exemplo Prático:**
  ```java
    // Supondo que exista uma classe Product
    Product[] products = new Product[2];
    products[0] = new Product("TV", 900.00, 0);
    products[1] = new Product("Mouse", 30.00, 0);

    // Atribuição de referência: ambos os índices apontarão para o mesmo objeto
    Product p = products[0];
  ```

## 5. Acesso aos Elementos 🏹
  **Acesso Direto:** Elementos são acessados por meio de seus índices, que começam em 0.

  **Exemplo:** Para acessar o primeiro elemento, usamos vetor[0].

  **Exemplo Lúdico:**
  Considere um corredor com caixas numeradas. Você abre a caixa número 0 para pegar o que precisa, depois a 1, e assim por diante.

  **Exemplo Prático:**
  ```java
    double firstHeight = heights[0];  // Acessa o primeiro valor do vetor heights
  ```

## 6. Propriedade length 📏
  **Definição:** A propriedade length indica o tamanho (número de elementos) do vetor.

  **Uso:** Útil para iterar sobre todos os elementos do vetor com laços (loops).

  **Exemplo Prático:**
  ```java
    for (int i = 0; i < heights.length; i++) {
        System.out.println("Altura " + i + ": " + heights[i]);
    }
  ```

## 7. Vantagens e Desvantagens dos Vetores 👍👎
  **Vantagens:**

  **Acesso Imediato:** Permite acesso rápido e direto a qualquer posição do vetor.

  **Desvantagens:**

  **Tamanho Fixo:** O tamanho é definido na instanciação e não pode ser alterado posteriormente;

  **Inserções e Deleções:** São operações mais complicadas e custosas, já que podem requerer o reposicionamento de elementos.


## 8. Exemplo Prático: Cálculo da Altura Média 🧮
  **Problema:**
  Ler um número N representando a quantidade de pessoas, armazenar as alturas em um vetor, e calcular a altura média.

  **Código de Exemplo:**
  ```java
    package application;

    import java.util.Locale;
    import java.util.Scanner;

    public class Program {
        public static void main(String[] args) {
            Locale.setDefault(Locale.US);
            Scanner sc = new Scanner(System.in);
            
            // Lê o número de pessoas
            int n = sc.nextInt();
            double[] heights = new double[n];

            // Armazena cada altura no vetor
            for (int i = 0; i < n; i++) {
                heights[i] = sc.nextDouble();
            }
            
            // Calcula a soma das alturas
            double sum = 0.0;
            for (int i = 0; i < n; i++) {
                sum += heights[i];
            }
            
            // Calcula e exibe a altura média
            double avg = sum / n;
            System.out.printf("AVERAGE HEIGHT: %.2f%n", avg);
            
            sc.close();
        }
    }
  ```

  **Exemplo Lúdico:**
  Imagine uma turma de amigos 🎈, onde cada amigo tem um balão representando sua altura. Você recolhe todos os balões, soma as alturas e divide pela quantidade de balões para descobrir a altura média do grupo.

Utilize estes cartões para consolidar seu entendimento sobre vetores em Java. Dominar esses conceitos é essencial para manipular dados de forma eficiente e eficaz em seus programas! 🚀😊