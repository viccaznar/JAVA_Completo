# Cartões de Resumo: hashCode, equals e Como Set Testa Igualdade 🔍💡

  Em Java, os métodos **hashCode** e **equals** são fundamentais para determinar se dois objetos são iguais. Esses métodos são usados por coleções baseadas em hash (como `HashSet`, `HashMap`) para armazenar e recuperar objetos de forma rápida e correta. A seguir, veja como esses métodos são utilizados e como um `Set` testa a igualdade dos seus elementos.


## 1. Conceitos Básicos

  - **equals(Object obj):**  


    - **Função:** Compara o conteúdo de dois objetos.  


    - **Retorno:** `true` se os objetos são iguais e `false` caso contrário.  


    - **Observação:** Algumas classes padrão (como `String`, `Integer`, `Double`) já possuem uma implementação adequada de `equals`.



  - **hashCode():**  


    - **Função:** Retorna um número inteiro (código hash) que representa o estado do objeto.  


    - **Uso:** É usado para identificar de forma rápida se dois objetos *podem* ser iguais.  



  - **Regra Importante:**  

    - Se os `hashCode` de dois objetos forem **diferentes**, os objetos são diferentes.  

    - Se os `hashCode` forem **iguais**, é necessário chamar `equals` para confirmar a igualdade, pois colisões podem ocorrer.



  - **Implementações Padrão vs. Personalizadas:**  


    - **Padrão:** Tipos como `String` já implementam `equals` e `hashCode` corretamente.  


    - **Personalizadas:** Classes criadas pelo usuário devem sobrescrever (`override`) esses métodos para que objetos com o mesmo conteúdo sejam considerados iguais e tenham o mesmo hash.



## 2. Como as Coleções Hash Testam Igualdade

  - Ao inserir um objeto em um `HashSet` ou `HashMap`:


    1. **Calcula-se o `hashCode`:**  

      - Se dois objetos têm `hashCode` diferentes, eles são imediatamente considerados diferentes.  


    2. **Confirmação via equals:**  

      - Se os `hashCode` forem iguais, o método `equals` é chamado para confirmar se os objetos são de fato iguais.


    - **Sem Implementação Personalizada:**  
    
    
      - Se uma classe não sobrescrever `equals` e `hashCode`, a comparação será baseada nas **referências** (ponteiros) dos objetos.


### Exemplo Lúdico 🎲

  Imagine que você tem duas **chaves** de fechadura:


  - **hashCode:**  
    É como o número gravado na chave. Se o número (código) da chave for diferente, você sabe rapidamente que as chaves são diferentes.


  - **equals:**  
    Se os números forem iguais, você ainda precisa olhar o desenho (os detalhes) da chave para confirmar que elas são realmente idênticas.


  Portanto, se duas chaves têm o mesmo número, é provável que sejam iguais, mas você precisa confirmar comparando seus detalhes – similar ao que os métodos `hashCode` e `equals` fazem.


### Exemplo Prático 💻

  Considere o seguinte exemplo com uma classe `Product` (sem sobrescrever `equals` e `hashCode`):


  ```java
    package application;

    import java.util.HashSet;
    import java.util.Set;
    import entities.Product;

    public class Program {
        public static void main(String[] args) {
            Set<Product> set = new HashSet<>();
            set.add(new Product("TV", 900.0));
            set.add(new Product("Notebook", 1200.0));
            set.add(new Product("Tablet", 400.0));

            // Cria um novo objeto com os mesmos valores de um objeto existente
            Product prod = new Product("Notebook", 1200.0);

            // Testa se o set contém o objeto "prod"
            System.out.println(set.contains(prod)); // Resultado provavelmente: false
        }
    }
  ```


  ```java
    package entities;

    public class Product {
        private String name;
        private Double price;

        public Product(String name, Double price) {
            this.name = name;
            this.price = price;
        }
        // Getters e Setters...
    }
  ```


  - **Explicação:**


   - Como Product não sobrescreve equals e hashCode, a comparação é feita de acordo com as referências dos objetos.


   - Mesmo que dois produtos tenham name e price iguais, eles serão considerados diferentes se forem instâncias distintas.


   - Para que o método contains retorne true para produtos com valores iguais, é necessário sobrescrever ambos os métodos na classe Product.


### Conclusão 🏁
  
  - **hashCode e equals:** São métodos cruciais para comparar objetos e garantir seu correto armazenamento em coleções do tipo hash.


  - **Processo de Comparação:** Primeiro, o hashCode filtra rapidamente os objetos; depois, equals confirma a igualdade.


  - **Implementação Adequada é Essencial:** Classes personalizadas devem implementar esses métodos para garantir que suas instâncias sejam comparadas com base no conteúdo e não apenas na referência.


Domine os conceitos de hashCode e equals para garantir o correto funcionamento dos seus conjuntos e a eficiência das suas coleções em Java! 😊🚀