# Cartões de Resumo: Comentários em Java (Básico) 😃

## 📝 O que São Comentários?
Comentários são trechos do código que o compilador ignora. Eles servem para explicar funcionalidades, registrar observações e auxiliar na manutenção, tornando o código mais legível.

---

## 🔹 Comentários de Múltiplas Linhas
- **Fundamento**: Delimitados por `/*` e `*/`, permitem escrever explicações longas ou detalhadas que podem ocupar várias linhas.
- **Exemplo Lúdico**: Imagine uma carta secreta, escrita com muito carinho, que fica guardada em um baú do tesouro e nunca é lida durante a execução do programa.
- **Exemplo Prático**:
  ```java
  /*
   Este programa calcula as raízes de uma equação do segundo grau.
   Os valores dos coeficientes devem ser digitados um por linha.
  */
  ```


## 🔹 Comentários de Linha Única
- **Fundamento:** Iniciados com //, esses comentários permitem anotações rápidas e diretas, geralmente para destacar uma única linha ou trechos curtos.

- **Exemplo Lúdico:** Imagine um post-it deixado sobre um livro, onde você anota uma dica rápida sem atrapalhar a leitura da história.

- **Exemplo Prático:**
  ```java
  delta = b * b - 4 * a * c; // cálculo do valor de delta
  ```


## 📌 Estrutura Básica de um Programa Java (Bônus)
  - Além dos comentários, a estrutura do código apresentado abrange:
  - Declaração de Pacote: Define onde o código está organizado (ex. package course;).
  - Importações: Permitem utilizar classes de outras bibliotecas, como:
  - import java.util.Locale; para configurações regionais.
  - import java.util.Scanner; para ler entradas do usuário.
  - Definição da Classe e do Método Main: O ponto de entrada do programa.

- **Exemplo Prático:**
  ```java
    package course; // Declaração do pacote

    import java.util.Locale;
    import java.util.Scanner;

    public class Program {
        public static void main(String[] args) {
            Locale.setDefault(Locale.US);
            Scanner sc = new Scanner(System.in);
            // Cálculo do delta e demais operações seguem abaixo...
        }
    }
  ```

Comentários são ferramentas essenciais para documentar o código, facilitando o entendimento próprio e colaborativo. Aproveite esses conceitos para manter seu código organizado e de fácil manutenção! 😎


