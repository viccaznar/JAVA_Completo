# 💡 Cartão de Resumo: Estrutura Repetitiva "faça-enquanto" (do-while)

## 📚 Conceito
- **Definição**:  
  A estrutura "faça-enquanto" (do-while) é um laço de repetição que garante a execução do bloco de comandos **pelo menos uma vez** antes de verificar a condição.  
  Essa abordagem é útil quando a ação inicial precisa ocorrer independentemente da condição. 😊

## 📝 Sintaxe e Regras
- **Sintaxe Básica**:
  ```java
  do {
      comando1;
      comando2;
  } while (condição); // V: volta | F: pula fora
  ```
  - **Como Funciona:**
    - **V (Volta):** Se a condição for verdadeira após a execução dos comandos, o laço se repete.
    - **F (Pula Fora):** Se a condição for falsa, o laço é encerrado.

  - 🎲 **Exemplo Lúdico:**
    Imagine um jogo onde você precisa tentar acertar um alvo:
    - Você sempre tem que fazer pelo menos um disparo (a ação inicial é garantida).
    - Após cada disparo, o jogo verifica: "Acertou o alvo?"
    - Se sim **(V: volta)**, o jogador continua jogando.
    - Se não **(F: pula fora)**, o jogo termina e você não pode mais disparar.
    
    Esse cenário ilustra como o do-while garante que a tentativa ocorra ao menos uma vez antes de avaliar se continua ou não. 🎯

  - 💻 **Exemplo Prático (Código Java):**
    ```java
    import java.util.Scanner;

    public class ExemploDoWhile {
        public static void main(String[] args) {
            Scanner scanner = new Scanner(System.in);
            int numero;
            
            // O bloco será executado pelo menos uma vez
            do {
                System.out.print("Digite um número menor que 10: ");
                numero = scanner.nextInt();
            } while (numero < 10); // Continua se o número for menor que 10
            
            System.out.println("Número maior ou igual a 10, encerrando!");
            scanner.close();
        }
    }

- **Explicação:**
  O programa solicita um número do usuário e repete a solicitação enquanto o número digitado for menor que 10. Assim, a ação ocorre pelo menos uma vez, e a verificação acontece após a execução do bloco. 🔁

**- Resumo:**
  A estrutura repetitiva "faça-enquanto" é ideal quando precisamos que os comandos sejam executados inicialmente, sem uma condição pré-estabelecida. Ela garante, através de uma verificação ao final, que o laço continuará apenas enquanto a condição definida for verdadeira. Uma ferramenta poderosa para cenários onde o input ou a ação inicial não pode ser evitada. 🚀


