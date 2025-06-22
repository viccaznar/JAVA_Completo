# Expressão Condicional Ternária 🎯

## 1. Conceito 🤓
- **Definição:**  
  A expressão condicional ternária é uma estrutura opcional ao `if-else` usada para decidir um **valor** com base em uma condição. Ela torna o código mais compacto e legível quando se quer atribuir um valor conforme o resultado de uma verificação.


## 2. Sintaxe 🛠️
- **Forma Geral:**  
  ```java
  (condição) ? valor_se_verdadeiro : valor_se_falso
  ```
- **Funcionamento:**
  - A condição é avaliada.
  - Se a condição for verdadeira, o resultado retornado é o valor_se_verdadeiro.
  - Se a condição for falsa, o resultado será o valor_se_falso.

- **Exemplo Simples:**
  ```java
  (2 > 4) ? 50 : 80
  ```
  - Como (2 > 4) é falso, o resultado é 80. 😊


## 3. Exemplo Lúdico 🎲- Contexto:
  Imagine uma máquina de doces inteligente que decide qual doce entregar com base na sua energia:
  - Se você estiver com muita energia (condição verdadeira), a máquina entrega um doce de chocolate.
  - Se estiver com baixa energia (condição falsa), ela entrega um doce de goma.
  
  - **Representação com Ternário:**
    ```java
    (energiaAlta) ? "Chocolate" : "Goma"
    ```

    - Essa expressão decide o doce a ser entregue de forma rápida e direta!
    🍫 vs 🍬


## 4. Exemplo Prático 💻- Contexto:
  Um programa para calcular o desconto em um produto:
  - Se o preço for menor que R$20.00, o desconto é de 10%.
  - Caso contrário, o desconto é de 5%.

- **Código em Java:**
  ```java
  double preco = 34.5;
  double desconto = (preco < 20.0) ? preco * 0.1 : preco * 0.05;
  // Como 34.5 não é menor que 20.0, desconto será 34.5 * 0.05 = 1.725
  ```

- **Comparação com if-else:**
  ```java
  if (preco < 20.0) {
      desconto = preco * 0.1;
  } else {
      desconto = preco * 0.05;
  }
  ```

  - Ambas as abordagens produzem o mesmo resultado, mas a expressão ternária deixa o código mais enxuto.
  💡

Esta estrutura é bastante útil quando se deseja escolher rapidamente entre dois valores com base em uma condição, tornando o código mais direto e menos verboso. 🚀