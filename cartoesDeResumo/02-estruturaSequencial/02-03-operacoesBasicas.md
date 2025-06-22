# 🚀 Três Operações Básicas de Programação em Java

- **📥 Entrada de Dados (Leitura)**  
  • Conceito: captura valores do usuário ou de dispositivos externos e armazena em variáveis.  
  • Como funciona: geralmente usamos `Scanner` (ou outra API) para ler texto, números etc.  
  • Exemplo Lúdico: imagine um dragão que pergunta seu nome antes de deixá-lo passar pela porta. Você digita “Marcos” e o dragão guarda o valor em sua bolsa mágica (variável).  
  • Exemplo Prático:
    ```java
    Scanner sc = new Scanner(System.in);
    System.out.print("Digite sua idade: ");
    int idade = sc.nextInt(); // o programa está lendo dados
    ```

- **⚙️ Processamento de Dados (Atribuição)**  
  • Conceito: aplica operações (cálculos, concatenações, comparações) aos dados lidos e armazena resultados.  
  • Como funciona: o operador de atribuição `=` associa o resultado de uma expressão a uma variável.  
  • Exemplo Lúdico: três elfos dividem 10 cristais igualitariamente. Cada elfo faz `cristaisPorElfo = 10 / 3`, guardando o quociente em seu saquinho.  
  • Exemplo Prático:
    ```java
    double x = 7.5, y = 8.3;
    double media = (x + y) / 2.0; // processamento via atribuição
    ```

- **📤 Saída de Dados (Escrita)**  
  • Conceito: exibe resultados ao usuário ou envia informações a outros sistemas ou dispositivos.  
  • Como funciona: usamos `System.out.println`, gravação em arquivos, APIs de rede etc.  
  • Exemplo Lúdico: a fada madrinha lê o valor “media” do seu pergaminho (variável) e anuncia em voz alta: “Sua média foi 7.9!”.  
  • Exemplo Prático:
    ```java
    System.out.println("Sua média é: " + media); // o programa está escrevendo dados
    ```