# Cartões de Resumo: Listas em Java 📚📝

  As listas são estruturas de dados dinâmicas usadas para armazenar coleções homogêneas (mesmo tipo) de forma ordenada e com tamanho variável. A seguir, veja os conceitos fundamentais, aplicações e exemplos práticos!


## 1. Conceito de Lista 🔍

  - **Definição:**  
    Uma lista é uma estrutura de dados ordenada onde os elementos são armazenados em "nós" (ou nodos). Ela é homogênea e, diferentemente dos vetores, inicia vazia, alocando seus elementos sob demanda.
  
  - **Características:**  
    - **Homogênea:** Todos os elementos são do mesmo tipo;  
    - **Ordenada:** Elementos são acessados por meio de suas posições;  
    - **Dinâmica:** Cresce à medida que elementos são adicionados;  
    - **Implementações:** É definida pela interface `List` e implementada por classes como `ArrayList` e `LinkedList`.

  **Exemplo Lúdico:**  
  Imagine uma fila de pessoas 🎟️ em uma estação de trem, onde cada pessoa (elemento) ocupa um lugar específico (índice). Conforme pessoas chegam ou saem, a fila se reorganiza dinamicamente.


## 2. Declaração e Instanciação 🔧

  - **Declaração:**  
    Utiliza-se a interface `List` para criar uma variável que armazenará a lista.
  
  - **Instanciação:**  
    São usadas classes como `ArrayList` ou `LinkedList` para efetivamente criar a lista.

  **Exemplo Lúdico:**  
  Pense em uma prateleira ajustável 📚 que começa vazia e, à medida que você adiciona livros, a prateleira se expande automaticamente para acomodar cada novo volume.

  **Exemplo Prático:**
   ```java
    List<String list = new ArrayList<();
    list.add("Maria");
    list.add("Alex");
    list.add("Bob");
    list.add("Anna");
    list.add(2, "Marco"); // Insere "Marco" na posição 2
   ```


## 3. Operações Comuns em Listas 🛠️

  - **Tamanho da Lista:**  
    - `size()`: Retorna o número de elementos na lista.
  
  - **Acesso aos Elementos:**  
    - `get(position)`: Obtém o elemento na posição especificada.
  
  - **Inserção de Elementos:**  
    - `add(obj)` ou `add(int, obj)`: Adiciona um elemento ao final ou em uma posição específica.
  
  - **Remoção de Elementos:**  
    - `remove(obj)` ou `remove(int)`: Remove elementos da lista.  
    - `removeIf(Predicate)`: Remove elementos que satisfaçam uma condição.
  
  - **Busca de Elementos:**  
    - `indexOf(obj)` e `lastIndexOf(obj)`: Retornam a posição do elemento.
  
  - **Filtragem e Predicados (Lambda):**  
    - Uso da *Stream API* para filtrar a lista com base em condições:
      ```java
        List<Integer result = list.stream().filter(x - x  4).collect(Collectors.toList());
        Integer firstMatch = list.stream().filter(x - x  4).findFirst().orElse(null);
       ```

  **Exemplo Lúdico:**  
  Imagine uma lista de compras 🛒 onde você adiciona itens, remove aqueles que já comprou e procura por produtos específicos. As operações da lista facilitam a gestão e atualização contínua da sua "lista de compras".

 **Exemplo Prático (Código Completo):**
  ```java
    package application;
    
    import java.util.ArrayList;
    import java.util.List;
    import java.util.stream.Collectors;
    
    public class Program {
        public static void main(String[] args) {
            List<String list = new ArrayList<();
            list.add("Maria");
            list.add("Alex");
            list.add("Bob");
            list.add("Anna");
            list.add(2, "Marco");
            
            System.out.println("Tamanho da lista: " + list.size());
            for (String x : list) {
                System.out.println(x);
            }
            System.out.println("---------------------");
            
            // Remover elementos que começam com 'M'
            list.removeIf(x - x.charAt(0) == 'M');
            for (String x : list) {
                System.out.println(x);
            }
            System.out.println("---------------------");
            
            System.out.println("Index of Bob: " + list.indexOf("Bob"));
            System.out.println("Index of Marco: " + list.indexOf("Marco"));
            System.out.println("---------------------");
            
            // Filtrar elementos que começam com 'A'
            List<String result = list.stream()
                                        .filter(x - x.charAt(0) == 'A')
                                        .collect(Collectors.toList());
            for (String x : result) {
                System.out.println(x);
            }
            System.out.println("---------------------");
            
            // Encontrar a primeira ocorrência de um elemento que começa com 'J'
            String name = list.stream()
                              .filter(x - x.charAt(0) == 'J')
                              .findFirst()
                              .orElse(null);
            System.out.println("Nome encontrado: " + name);
        }
    }
 ```


## 4. Pontos Pendentes e Considerações Futuras 📝

  - **Interfaces:**  
    A interface `List` define os métodos e propriedades que todas as listas devem possuir.
  
  - **Generics:**  
    Permitem que você defina o tipo dos elementos contidos na lista, garantindo segurança em tempo de compilação.
  
  - **Predicados (Lambda):**  
    Usados para passar condições (filtros) de forma concisa e funcional via expressões lambda.

  Para mais detalhes, consulte a [documentação oficial do List](https://docs.oracle.com/javase/10/docs/api/java/util/List.html).


Domine as listas para trabalhar com coleções de dados de forma dinâmica e eficiente, aproveitando o poder da programação orientada a objetos em Java! 😊🚀
