# Cartões de Resumo: Lendo Arquivo Texto com File e Scanner 📄🔍

  Aprenda a utilizar as classes `File` e `Scanner` para ler arquivos de texto em Java. Essa técnica é essencial para trabalhar com entrada e processamento de dados em arquivos.


## 1. Classe File 📁

  - **Conceito:**  
    A classe `File` representa uma abstração de um arquivo ou diretório em um sistema de arquivos, encapsulando seu caminho e propriedades.
    
  - **Principais Pontos:**  
    - Permite verificar a existência, obter informações e gerenciar arquivos.
    - Pertence ao pacote `java.io`.

  - **Exemplo Lúdico:**  
    Imagine `File` como um mapa 📜 que descreve onde um tesouro está enterrado. Assim como o mapa mostra a localização do tesouro, a classe `File` indica onde o arquivo está no sistema.


## 2. Classe Scanner 🔎

  - **Conceito:**  
    A classe `Scanner` é um utilitário para leitura de dados de diversas fontes, como arquivos, strings e entradas do usuário.  
  - **Principais Pontos:**  
    - Facilita a divisão de texto em tokens (palavras, números, etc.).  
    - Está localizada no pacote `java.util`.

  - **Exemplo Lúdico:**  
    Pense em `Scanner` como uma lupa 🔍 que ajuda a examinar o conteúdo de um mapa, permitindo que você observe cada detalhe e leia as instruções necessárias para encontrar o tesouro.


## 3. Tratamento de Exceções: IOException ⚠️

  - **Conceito:**  
    - `IOException` é uma exceção verificada lançada quando ocorre algum problema durante operações de entrada/saída (I/O), como leitura de arquivos.
    
    - Por ser uma exceção verificada, o compilador obriga a tratá-la ou propagá-la.

  - **Exemplo Lúdico:**  
    Imagine que enquanto você segue um mapa do tesouro, pode surgir uma tempestade inesperada (erro de I/O) que impede a leitura clara do mapa. O tratamento dessa “tempestade” garante que seu programa saiba como agir mesmo se algo der errado.


  - **Exemplo Prático em Código** 💻
    O exemplo a seguir demonstra como utilizar as classes `File` e `Scanner` para ler um arquivo de texto, com o tratamento de exceções utilizando um bloco `try-catch-finally` para garantir o fechamento do recurso.

  ```java
    package application;

    import java.io.File;
    import java.io.IOException;
    import java.util.Scanner;

    public class Program {
        public static void main(String[] args) {
            // Cria uma instância de File apontando para o arquivo desejado
            File file = new File("C:\\temp\\in.txt");
            Scanner sc = null;
            try {
                // Inicializa o Scanner para ler o arquivo
                sc = new Scanner(file);
                // Lê e imprime cada linha do arquivo até que não haja mais linhas
                while (sc.hasNextLine()) {
                    System.out.println(sc.nextLine());
                }
            } catch (IOException e) {
                // Caso ocorra uma exceção de I/O, exibe a mensagem de erro
                System.out.println("Error: " + e.getMessage());
            } finally {
                // Garante que o recurso Scanner seja fechado, liberando memória e evitando vazamentos
                if (sc != null) {
                    sc.close();
                }
            }
        }
    }
  ```

  - **Explicação:**

    - **Bloco try:** Tenta abrir e ler o arquivo linha por linha.
    - **Bloco catch:** Captura e trata possíveis erros de I/O, como problema no acesso ao arquivo.
    - **Bloco finally:** Fecha o Scanner para liberar o recurso, independentemente de erros.

**Conclusão** 🏁
  Utilizar as classes File e Scanner para ler arquivos de texto em Java permite:

  - **Acesso e Manipulação de Arquivos:** Gerenciar arquivos de maneira abstrata com a classe File.

  - **Leitura Eficiente:** Utilizar Scanner para ler e processar a informação de forma prática.

  - **Robustez:** Garantir o tratamento de exceções com IOException, assegurando que os recursos sejam sempre fechados.

Domine essas ferramentas para criar aplicações que leem e processam dados de forma eficiente e segura! 

