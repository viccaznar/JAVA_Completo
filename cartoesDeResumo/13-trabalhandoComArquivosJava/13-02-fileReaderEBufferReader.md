# Cartões de Resumo: Lendo Arquivo Texto com FileReader e BufferedReader 📖🚀

  Este cartão aborda como ler arquivos de texto em Java utilizando as classes **FileReader** e **BufferedReader**, explicando seus conceitos, diferenças e mostrando um exemplo prático.


## 1. Conceitos das Classes


### FileReader 📁
  
  - **Definição:**  
    É uma classe que cria um fluxo de leitura de caracteres a partir de um arquivo, permitindo ler o conteúdo de forma sequencial (caractere a caractere).

  - **Uso:**  
    Útil para operações simples de leitura de arquivo.

  - **Documentação:**  
    [FileReader API](https://docs.oracle.com/javase/10/docs/api/java/io/FileReader.html)


### BufferedReader 🔎
  
  - **Definição:**  
    É uma classe que envolve um `FileReader` (ou outro `Reader`) para fornecer um buffer; isto é, ela armazena temporariamente os dados lidos do arquivo.
  

  - **Vantagens:**  
  
      - **Performance:** Lê grandes blocos de dados de uma só vez, diminuindo a quantidade de operações de leitura.  
    
      - **Facilidade:** Possui métodos convenientes, como `readLine()`, que lê uma linha inteira de texto.
    

  - **Documentação:**  
    [BufferedReader API](https://docs.oracle.com/javase/10/docs/api/java/io/BufferedReader.html)


  - **Diferença Principal:**
    - **FileReader** lê dados diretamente, caractere por caractere.
    - **BufferedReader** melhora a performance através do buffering e oferece métodos utilitários (como `readLine()`) para facilitar o processamento do texto.


### Exemplo Lúdico 🎢

  Imagine que você precisa ler um livro:

  - **FileReader** é como ler cada letra do livro cuidadosamente, uma de cada vez.
  
  - **BufferedReader** é como usar uma máquina que digitaliza várias páginas de uma vez e te mostra todas as linhas prontas, tornando a leitura muito mais dinâmica e rápida!
  

### Exemplo Prático 💻

  O código abaixo demonstra como utilizar as classes `FileReader` e `BufferedReader` para ler um arquivo de texto e imprimir suas linhas no console. Observe o tratamento de exceções e o fechamento dos recursos no bloco `finally`:

    ```java
      package application;

      import java.io.BufferedReader;
      import java.io.FileReader;
      import java.io.IOException;

      public class Program {
          public static void main(String[] args) {
              // Define o caminho do arquivo
              String path = "C:\\temp\\in.txt";
              
              // Declarando variáveis para os leitores
              BufferedReader br = null;
              FileReader fr = null;
              
              try {
                  // Inicializa o FileReader e o BufferedReader
                  fr = new FileReader(path);
                  br = new BufferedReader(fr);
                  
                  // Lê a primeira linha do arquivo
                  String line = br.readLine();
                  
                  // Continua lendo e imprimindo cada linha até o fim do arquivo
                  while(line != null) {
                      System.out.println(line);
                      line = br.readLine();
                  }
              } catch (IOException e) {
                  // Trata exceções relacionadas à entrada/saída
                  System.out.println("Error: " + e.getMessage());
              } finally {
                  // Garante o fechamento dos recursos, evitando vazamentos de memória
                  try {
                      if (br != null) {
                          br.close();
                      }
                      if (fr != null) {
                          fr.close();
                      }
                  } catch (IOException e) {
                      e.printStackTrace();
                  }
              }
          }
      }
  ```
  

**Conclusão** 🏁
  
  - **Objetivo:** 
    As classes FileReader e BufferedReader possibilitam a leitura eficiente de arquivos de texto, sendo fundamentais para o processamento de dados armazenados em arquivos.

  - **Boas Práticas:** 
    Utilize BufferedReader para melhorar a performance e sempre feche os streams no bloco finally para liberar os recursos.

  - **Aplicação:** 
    São amplamente usadas em sistemas que necessitam ler configurações, processar logs ou qualquer outra forma de arquivo texto.

Domine estas ferramentas para construir aplicações robustas e eficientes no processamento de dados textuais! 😊🚀