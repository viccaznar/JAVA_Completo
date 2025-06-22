# Curso de Java Completo: Conceitos de Expressões Aritméticas

## 😊 Expressões Aritméticas  
- **Definição:**  
  Uma expressão aritmética é uma combinação de números, operadores e, se necessário, parênteses que, quando avaliados, retornam um valor numérico.  
- **Exemplo Lúdico:**  
  Imagine que cada número é um ingrediente e os operadores são as instruções de uma receita. Juntando-os, você "cozinha" um resultado saboroso!  
- **Exemplo Prático:**  
  `4 + 5` resulta em `9`.



## 🔢 Operadores Aritméticos
 
### ➕ Adição (+)  
- **Descrição:** Soma dois valores.  
- **Exemplo Lúdico:**  
  Somar pontos em um jogo para subir de nível.  
- **Exemplo Prático:**  
  `2 + 3` resulta em `5`.

### ➖ Subtração (-)  
- **Descrição:** Subtrai um valor de outro.  
- **Exemplo Lúdico:**  
  Retirar peças de um quebra-cabeça para ver somente a imagem principal.  
- **Exemplo Prático:**  
  `10 - 4` resulta em `6`.

### ✖️ Multiplicação (*)  
- **Descrição:** Multiplica dois números.  
- **Exemplo Lúdico:**  
  Imagine multiplicar os amigos que entram numa brincadeira – quanto mais, melhor!  
- **Exemplo Prático:**  
  `3 * 4` resulta em `12`.

### ➗ Divisão (/)  
- **Descrição:** Divide um número pelo outro de forma igualitária.  
- **Exemplo Lúdico:**  
  Dividir uma pizza em fatias iguais para todos os amigos.  
- **Exemplo Prático:**  
  `12 / 3` resulta em `4`.

### 🔄 Módulo (% ou "mod")  
- **Descrição:** Retorna o resto da divisão entre dois números.  
- **Exemplo Lúdico:**  
  Imagine dividir confeitos igualmente e ficar com alguns sobrando para um "extra" saboroso!  
- **Exemplo Prático:**  
  `14 % 3` resulta em `2`.



## 📏 Precedência dos Operadores  
- **Descrição:**  
  Em uma expressão, alguns operadores são executados antes de outros, a menos que haja parênteses para indicar a ordem.  
  - **Nível 1:** Multiplicação, Divisão e Módulo (`*`, `/`, `%`) são executados primeiro.  
  - **Nível 2:** Adição e Subtração (`+`, `-`) são executados depois.  
- **Exemplo Lúdico:**  
  Pense em uma corrida onde os corredores mais rápidos (operadores com maior precedência) começam primeiro. Se você quiser mudar a ordem, os parênteses funcionam como um sinal de trânsito que reorganiza a largada!  
- **Exemplo Prático:**  
  - Sem parênteses:  
    `3 + 2 * 4` primeiro calcula `2 * 4 = 8`, depois soma `3 + 8 = 11`.  
  - Com parênteses:  
    `(3 + 2) * 4` primeiro calcula `3 + 2 = 5`, depois multiplica `5 * 4 = 20`.



## 🔍 Exemplos de Expressões Aritméticas  
- **Exemplo 1:**  
  `2 * 6 / 3`  
  - Cálculo: `2 * 6 = 12` e `12 / 3 = 4`  
  - Resultado: `4`
  
- **Exemplo 2:**  
  `60 / (3 + 2) * 4`  
  - Cálculo: Dentro dos parênteses, `3 + 2 = 5`; depois, `60 / 5 = 12`; em seguida, `12 * 4 = 48`  
  - Resultado: `48`
  
- **Exemplo 3:**  
  `60 / ((3 + 2) * 4)`  
  - Cálculo: Dentro dos parênteses, `3 + 2 = 5`; depois, `5 * 4 = 20`; por fim, `60 / 20 = 3`  
  - Resultado: `3`



## 🧮 Exemplos com o Operador "mod"  
- **Exemplo 1:**  
  `14 % 3`  
  - Cálculo: 14 dividido por 3 resulta em 4 (pois 3×4 = 12) e sobra `14 - 12 = 2`.  
  - Resultado: `2`
  
- **Exemplo 2:**  
  `19 % 5`  
  - Cálculo: 19 dividido por 5 resulta em 3 (pois 5×3 = 15) e sobra `19 - 15 = 4`.  
  - Resultado: `4`