# 🎯 Entrada de Dados em Java

- 📥 **Entrada de Dados (Leitura)**  

    **Definição:** captura valores do usuário e guarda em variáveis usando comandos de leitura.

    🧚‍♂️ **Lúdico:** o ancião corvo escuta segredos sussurrados e os armazena em pergaminhos mágicos.  
  
    💻 **Prático:**
    ```java
    System.out.print("Digite um número: ");
    int x = sc.nextInt(); // programa está lendo dados
    ```

- **🕷️ Scanner**

    **Definição:** classe que lê dados de várias fontes; instancie com Scanner sc = new Scanner(System.in); e finalize com sc.close();.

    🕸️ **Lúdico:** uma aranha tece sua teia para capturar palavras no ar (System.in).

    💻 **Prático:**
    ```java
    import java.util.Scanner;
    Scanner sc = new Scanner(System.in);
    // ... leituras ...
    sc.close();
    ```

- 🔢 **nextInt()**

    **Definição:** lê o próximo token como int.
    
    ⛏️ **Lúdico:** o mineiro extrai cristais inteiros do fundo da caverna.

    💻 **Prático:**
    ```java
    int idade = sc.nextInt();
    ```

- 🧪 **nextDouble()**
    **Definição:** lê o próximo token como double.

    🧙‍♂️ **Lúdico:** o alquimista mede líquidos exatos com pontos decimais.

    💻 **Prático:**
    ```java
    double peso = sc.nextDouble();
    ```

- 🔡 **next().charAt(0)**
  
    **Definição:** lê o próximo token como String e retorna o primeiro caractere.

    🔮 **Lúdico:** o oráculo pronuncia uma palavra mística e você captura apenas a letra inicial.

    💻 **Prático:**
    ```java
    char genero = sc.next().charAt(0);
    ```

- 🌐 **Locale**
  
    **Definição:** define separador decimal antes de criar o Scanner:
    ```java    
    Locale.setDefault(Locale.US);
    Scanner sc = new Scanner(System.in);
    ```

- 🤝 **Lúdico:** o diplomata muda de dialeto para usar ponto como separador decimal.
  
- 🧵 **Leitura em Mesma Linha**
 
    **Definição:** encadeie next(), nextInt(), nextDouble() para capturar múltiplos dados de uma só vez.

    🛍️ **Lúdico:** o comerciante recolhe ouro, prata e bronze em sequência de um único saco.

    💻 **Prático:**
    ```java
    String nome    = sc.next();
    int    idade   = sc.nextInt();
    double salario = sc.nextDouble();
    ```

- 🗒️ **nextLine() e Buffer Pendente**

    **Definição:** nextLine() lê até a quebra de linha, mas tokens anteriores podem deixar \n pendente.

    **Solução:** use um sc.nextLine() extra para limpar o buffer.

    👻 **Lúdico:** um fantasma ecoa um apito invisível que fecha portas—você precisa bater nelas (limpar buffer) antes de entrar.

    💻 **Prático:**
    ```java
    int x = sc.nextInt();
    sc.nextLine();             // limpa o '\n' pendente
    String texto = sc.nextLine();
    ```

- 📝 **Resumo de Comandos**
    • Scanner sc
    • sc.next()
    • sc.nextInt()
    • sc.nextDouble()
    • sc.next().charAt(0)
    • sc.nextLine()
    • Locale.setDefault(...)
