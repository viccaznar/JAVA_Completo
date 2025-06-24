# Cartões de Resumo: FileWriter e BufferedWriter em Java ✍️📄

  Este cartão aborda como escrever arquivos de texto em Java utilizando as classes **FileWriter** e **BufferedWriter**, explicando seus conceitos, aplicações e demonstrando um exemplo prático.


## 1. Conceitos e Fundamentos

### FileWriter 📁
 
  - **O que é:**  
    Uma classe que fornece um fluxo de escrita de caracteres para arquivos.
  
  - **Funcionalidades:**  
  

    - **Criação/Recriação do Arquivo:**  
      Usar `new FileWriter(path)` cria ou recria o arquivo especificado.
  
  
    - **Acrescentar ao Arquivo Existente:**  
      Usar `new FileWriter(path, true)` abre o arquivo em modo de adição (append).
  
  
  - **Documentação:**  
    [FileWriter API](https://docs.oracle.com/javase/10/docs/api/java/io/FileWriter.html)


### BufferedWriter 🔎
 
  - **O que é:**  
    Uma classe que, quando utilizada em conjunto com um `FileWriter`, fornece um buffer para a escrita, tornando o processo muito mais rápido.
 
  - **Funcionalidades:**  
 
 
    - **Melhor Performance:**  
      Armazena dados em um buffer e os escreve em blocos, reduzindo o número de operações de I/O.
 
 
    - **Método Confortável:**  
      Possui métodos úteis como `newLine()` para adicionar quebras de linha facilmente.
 
 
  - **Documentação:**  
    [BufferedWriter API](https://docs.oracle.com/javase/10/docs/api/java/io/BufferedWriter.html)



### Exemplo Lúdico 🎨
  Imagine que você precisa enviar mensagens para seus amigos:
    
  - **FileWriter** é como escrever cada mensagem individualmente em post-its, que serão colados um a um em um mural.
  
  - **BufferedWriter** funciona como agrupar várias mensagens em um único bloco (como um folheto) e depois colar tudo de uma vez, tornando o trabalho muito mais rápido e organizado.



### Exemplo Prático 💻
  O código abaixo demonstra como utilizar `FileWriter` e `BufferedWriter` para escrever um conjunto de mensagens em um arquivo. Note o uso do bloco *try-with-resources* para garantir que o recurso seja fechado automaticamente.

  ```java
    package application;

    import java.io.BufferedWriter;
    import java.io.FileWriter;
    import java.io.IOException;

    public class Program {
        public static void main(String[] args) {
            // Conjunto de linhas para escrever no arquivo
            String[] lines = new String[] { "Good morning", "Good afternoon", "Good night" };
            // Definindo o caminho do arquivo
            String path = "C:\\temp\\out.txt";
            
            // O try-with-resources garante que o BufferedWriter seja fechado automaticamente
            try (BufferedWriter bw = new BufferedWriter(new FileWriter(path))) {
                // Para cada linha, escrevemos no arquivo e adicionamos uma nova linha
                for (String line : lines) {
                    bw.write(line);
                    bw.newLine();
                }
            } catch (IOException e) {
                // Em caso de erro de I/O, a mensagem de erro é impressa e a stack trace é exibida
                e.printStackTrace();
            }
        }
    }
  ```

**Conclusão** 🏁
  
  - FileWriter permite escrever caracteres em arquivos e oferece flexibilidade para recriar ou anexar conteúdo.

  - BufferedWriter melhora o desempenho ao armazenar dados temporariamente em buffer, diminuindo as operações I/O e facilitando a escrita de linhas de texto.

  - O uso combinado dessas classes com try-with-resources garante que os recursos sejam sempre fechados, evitando vazamentos e promovendo um código mais robusto e eficiente.

Domine essas ferramentas para criar aplicações que escrevem dados em arquivos de forma rápida, segura e organizada! 😊🚀