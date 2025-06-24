# Cartões de Resumo: Manipulando Pastas com File em Java 📂🚀

  Neste cartão, vamos explorar como utilizar a classe `File` para manipular pastas (diretórios) e arquivos em Java. Você aprenderá a listar pastas e arquivos, além de criar novos diretórios, tornando o gerenciamento do sistema de arquivos mais simples e eficiente.


## 1. Conceitos Principais

  - **Classe File 📁**

    - **Definição:**  
      A classe `File` é uma representação abstrata de um arquivo ou diretório no sistema operacional, permitindo manipular caminhos, verificar existência, e gerenciar arquivos.


    - **Funções Importantes:**  
      - Criar objetos que representam um caminho (arquivo ou pasta).
      - Obter listas de arquivos e diretórios com o método `listFiles()`.


  - **Métodos Utilizados:**
    - `listFiles(File::isDirectory)`:  
      Retorna um array de objetos `File` que são diretórios.
    - `listFiles(File::isFile)`:  
      Retorna um array de objetos `File` que são arquivos.
    - `mkdir()`:  
      Cria um novo diretório especificado no caminho.


  - **Tratamento de Input com Scanner:**
    - Usado para ler o caminho da pasta que o usuário deseja manipular.


### Exemplo Lúdico 🎲
  Imagine que você é um explorador em busca de tesouros escondidos 🏴‍☠️.  

   - **Pastas (Diretórios):** São como cavernas misteriosas onde podem estar guardados segredos e riquezas.  
  
   - **Arquivos:** São os baús de tesouro que você encontra dentro dessas cavernas.  
  
   - **Criar um Novo Diretório:** É como fundar uma nova caverna onde você pode guardar seus achados.
  
   - **Scanner:** É como uma bússola que te ajuda a encontrar o caminho para essas cavernas e baús.
  
  -  Com a classe `File`, você pode explorar e organizar seu mundo de arquivos e pastas como um verdadeiro aventureiro digital! 🗺️


### Exemplo Prático 💻
  O exemplo a seguir demonstra como ler o caminho de uma pasta fornecido pelo usuário, listar os diretórios e arquivos contidos nela, e, em seguida, criar um novo subdiretório:

  ```java
    package application;

    import java.io.File;
    import java.util.Scanner;

    public class Program {
        public static void main(String[] args) {
            Scanner sc = new Scanner(System.in);
            System.out.println("Enter a folder path: ");
            String strPath = sc.nextLine();
            
            // Cria um objeto File representando o caminho informado pelo usuário
            File path = new File(strPath);
            
            // Lista os diretórios dentro do caminho
            File[] folders = path.listFiles(File::isDirectory);
            System.out.println("FOLDERS:");
            for (File folder : folders) {
                System.out.println(folder);
            }
            
            // Lista os arquivos dentro do caminho
            File[] files = path.listFiles(File::isFile);
            System.out.println("FILES:");
            for (File file : files) {
                System.out.println(file);
            }
            
            // Cria um novo diretório chamado "subdir" dentro do caminho informado
            boolean success = new File(strPath + "\\subdir").mkdir();
            System.out.println("Directory created successfully: " + success);
            
            sc.close();
        }
    }
  ```

- **Explicação:**
  - O código acima realiza as seguintes operações:
    1. Solicita ao usuário o caminho de uma pasta.
    2. Cria um objeto `File` com esse caminho.
    3. Lista todos os diretórios e arquivos dentro da pasta especificada.
    4. Cria um novo subdiretório chamado "subdir" dentro da pasta informada.


  - O programa solicita ao usuário o caminho de uma pasta.

  - Cria um objeto File a partir deste caminho.

  - Utiliza listFiles(File::isDirectory) para listar todos os diretórios e listFiles(File::isFile) para listar todos os arquivos.

  - Cria um novo subdiretório (chamado "subdir") com o método mkdir(), retornando um valor booleano que indica se a operação foi bem-sucedida.


**Conclusão**🏁

- **Gerenciamento de Diretórios e Arquivos:** 
  A classe File possibilita a manipulação robusta e flexível dos caminhos no sistema, permitindo listar e criar pastas e arquivos com facilidade.


- **Facilidade de Uso:**
  Com métodos como listFiles() e a capacidade de criar diretórios com mkdir(), você pode desenvolver aplicações que interagem diretamente com o sistema de arquivos.


- **Aplicações Práticas:**
  Útil para sistemas que precisam gerenciar configurações, organizar recursos, armazenar logs e muito mais.


Domine o uso da classe File para explorar e gerenciar o sistema de arquivos em suas aplicações Java de forma eficiente e segura! 😊🚀