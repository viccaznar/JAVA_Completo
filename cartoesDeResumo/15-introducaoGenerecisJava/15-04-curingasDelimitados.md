# Cartões de Resumo: Curingas Delimitados (Bounded Wildcards) em Java 🎯🔀

  Os **curingas delimitados** são uma extensão dos generics que permitem especificar limites (bounds) para os tipos que podem ser utilizados em parâmetros genéricos. Eles ajudam a escrever métodos mais flexíveis e seguros, seguindo os princípios **get/put** (covariância e contravariância).


## 1. Conceitos Fundamentais

  ### Generics e Invariância
  

  - **Generics são invariantes:**  
    Uma `List<Integer>` **não** é um subtipo de `List<Object>`.  
  

    ```java
      List<Object> myObjs = new ArrayList<Object>();
      List<Integer> myNumbers = new ArrayList<Integer>();
      // myObjs = myNumbers; // Erro de compilação!
     ```

## 2. Tipos Curinga com Limites (Bounded Wildcards)
 
  - **Curinga Extendido (<? extends T>):**
  Permite ler (get) elementos de uma coleção que é de um tipo T ou de um subtipo de T, mas não permite inserir (put).


    - **Uso típico:** métodos que apenas leem de uma coleção.


  - **Curinga Super (<? super T>):** Permite escrever (put) elementos em uma coleção que aceita T ou qualquer supertipo de T, mas a leitura (get) pode retornar apenas Object.


    - **Uso típico:** métodos que inserem elementos.


## 3. Problema 1 – Soma das Áreas de Figuras
  
  - **Objetivo:** Criar um método que retorne a soma das áreas de uma lista de figuras.


  - **Soluções impróprias:**


    ```java
      public double totalArea(List<Shape> list) → Não aceita listas de subclasses de Shape.
    ```


    ```java
      public double totalArea(List<?> list) → Permite leitura, mas não é possível adicionar elementos.
    ```


  - **Solução com Wildcard Delimitado:**
  
    -  Usar List<? extends Shape> pode ser a alternativa ideal para métodos que só precisam ler dados da lista.


    - **Exemplo conceitual:**
    Imagine que você tem uma coleção de desenhos (formas) onde algumas são círculos, outras retângulos. Usar um curinga com <? extends Shape> permite tratar qualquer forma que seja um Shape sem precisar saber exatamente qual delas, possibilitando somar suas áreas.


## 4. Problema 2 – Princípio get/put e Cópia de Listas

  - **Objetivo:** Criar um método que copie elementos de uma lista para outra, onde a lista de destino pode ser de um tipo mais genérico.


    - **Exemplo de código (Get/Put):**


  ```java
    public static void copy(List<? extends Number> source, List<? super Number> destiny) {
        for (Number number : source) {
            destiny.add(number);
        }
    }
    ```


  - **Explicação dos Princípios:**


    - **Covariância (<? extends Number>):** Permite obter elementos da lista com segurança de tipo. Exemplo: Se temos uma List<Integer>, podemos atribuí-la a uma variável do tipo List<? extends Number> e ler seus elementos.


    - **Contravariância (<? super Number>):** Permite inserir elementos na lista de destino que pode ser do tipo Number ou supertipo de Number (como Object).


    - **Resumindo o Get/Put:**


      - **get - OK:** Você pode extrair e armazenar no tipo Number (para listas com <? extends Number>).


      - **put - ERRO:** Não é possível adicionar elementos a uma lista do tipo <? extends Number> porque o compilador não sabe o tipo exato.


      - **get - ERRO e put - OK:** Para listas do tipo <? super Number>, você consegue inserir elementos, mas a leitura retorna Object.


  ### Exemplo Lúdico 🎲
  
  - Imagine uma caixa mágica:


    - **Covariância (<? extends T>):** Você tem uma caixa que pode conter "qualquer tipo de fruta" (subtipos de Fruta). Você pode pegar uma fruta e saber que ela é, no mínimo, uma Fruta, mas você não pode garantir qual fruta deve ser inserida na caixa porque ela pode estar preparada para um tipo específico.


    - **Contravariância (<? super T>):** Agora imagine uma caixa que aceita "qualquer recipiente que possa conter Frutas", ou seja, ela pode receber uma Fruta sem problemas. Você consegue colocar uma fruta na caixa, mas se for para pegar um item, você só sabe que ele é de um tipo muito geral (um Object).


### Exemplo Prático 💻

  - Código Completo (Get/Put com Curingas Delimitados)


  ```java
    package application;

    import java.util.ArrayList;
    import java.util.Arrays;
    import java.util.List;

    public class Program {
        public static void main(String[] args) {
            // Listas de exemplo: inteiros e doubles
            List<Integer> myInts = Arrays.asList(1, 2, 3, 4);
            List<Double> myDoubles = Arrays.asList(3.14, 6.28);
            // Lista de destino para receber elementos de tipos numéricos
            List<Object> myObjs = new ArrayList<Object>();
            
            // Copia os elementos de cada lista para a lista de objetos
            copy(myInts, myObjs);
            printList(myObjs);
            copy(myDoubles, myObjs);
            printList(myObjs);
        }
        
        // Método que copia elementos da lista fonte para a lista destino
        public static void copy(List<? extends Number> source, List<? super Number> destiny) {
            for (Number number : source) {
                destiny.add(number);
            }
        }
        
        // Método para imprimir qualquer lista
        public static void printList(List<?> list) {
            for (Object obj : list) {
                System.out.print(obj + " ");
            }
            System.out.println();
        }
    }
    ```


  - **O que o exemplo faz:**


    - **Cria duas listas:** uma com Integer e outra com Double.


    - **Usa o método copy** para copiar os números de cada lista para uma lista de Object (destino).


    - **O método copy utiliza:**


      - **? extends Number** para garantir que a lista fonte contenha objetos que são pelo menos do tipo Number.


      - **? super Number** para garantir que na lista destino seja possível inserir objetos do tipo Number.


      - **O método printList** demonstra a leitura de qualquer lista usando List<?>.


### Conclusão


  - **Curingas Delimitados (Bounded Wildcards):** Permitem maior flexibilidade quando se trabalha com coleções genéricas, facilitando a implementação de métodos que podem:


    - Somar áreas (leitura exclusiva) usando <? extends T>.


    - Copiar elementos entre listas (get/put) utilizando uma combinação de <? extends T> e <? super T>.


    - **Princípio Get/Put:**


      - **Covariância:** Permite ler elementos com segurança.


      - **Contravariância:** Permite inserir elementos, mas as leituras podem ser menos precisas.



  - **Benefícios:**


    - **Reuso:** Métodos genéricos podem ser aplicados a vários tipos.


    - **Type Safety:** As restrições em tempo de compilação previnem erros.


    - **Flexibilidade e Performance:** Evita castings desnecessários e adapta o código a hierarquias de tipos.


Domine os curingas delimitados para escrever métodos genéricos robustos e flexíveis, tornando seu código Java ainda mais seguro e reutilizável! 😊🚀