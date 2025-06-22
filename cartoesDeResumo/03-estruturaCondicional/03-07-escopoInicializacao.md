# Escopo e Inicialização 🛠️

## 1. Escopo de uma Variável 📍  
- **Definição:**  
  O **escopo** de uma variável é a região do programa onde ela é válida e pode ser referenciada. Isso significa que a variável só poderá ser usada dentro do bloco de código onde foi declarada.

- **Exemplo Lúdico:**  
  Imagine uma sala de aula onde cada aluno (variável) só pode estar presente na sala onde foi alocado; se sair da sala, já não é considerado parte daquela turma. 🚪👩‍🎓

- **Exemplo Prático:**  
  Se você declarar uma variável dentro de um bloco `if` em Java, ela não poderá ser acessada fora desse bloco:
  ```java
  if (price > 100.0) {
      double discount = price * 0.1;
  }
  System.out.println(discount);  // Erro: 'discount' está fora do escopo.
  ```


## 2. Inicialização de Variáveis 🔄
- **Definição:**
  Inicialização é o processo de atribuir um valor a uma variável antes ou no momento de seu uso. Uma variável sem valor definido ("não inicializada") pode causar erros ou comportamentos inesperados.

- **Exemplo Lúdico:**
  Imagine que você tem uma lanterna (variável) que só pode acender (ser usada) se as baterias estiverem inseridas (inicializadas). Sem as baterias, a lanterna não funciona! 🔦🔋

- **Exemplo Prático:**
  Para corrigir o problema de escopo citado anteriormente, declare a variável fora do bloco:
  ```java
  double price = sc.nextDouble();
  double discount = 0.0;  // Inicialização obrigatória
  if (price > 100.0) {
      discount = price * 0.1;
  }
  System.out.println(discount);  // Agora 'discount' está no escopo e inicializado.
  ```

**Resumo:**
  - **Escopo:** Determina onde uma variável pode ser utilizada.
  - **Inicialização:** Assegura que a variável tem um valor definido antes de seu uso, evitando erros.
  Ambos conceitos são fundamentais para garantir que os programas funcionem corretamente e de forma previsível. 🚀