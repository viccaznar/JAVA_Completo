# Cartões de Resumo: hashCode e equals em Java 📏🧩

  Os métodos **hashCode** e **equals** são fundamentais para a comparação e armazenamento correto de objetos em coleções. Eles fazem parte da classe `Object` e, por isso, precisam ser sobrepostos (override) em classes personalizadas para garantir que os objetos sejam comparados com base no conteúdo, não apenas na referência.


## 1. Conceitos Gerais

- **equals:**  

  - Compara o conteúdo de dois objetos para verificar se são iguais.  


  - Retorna `true` se todos os atributos relevantes forem idênticos; caso contrário, retorna `false`.  


  - **Exemplo de uso:**


    ```java
      String a = "Maria";
      String b = "Alex";
      System.out.println(a.equals(b)); // false
      ```


- **hashCode:**  

  - Retorna um número inteiro (código hash) que representa o estado do objeto.  


  - É utilizado por coleções baseadas em hash (como `HashMap` e `HashSet`) para armazenar e localizar objetos de maneira eficiente.  


  - **Importante:**

    - Se dois objetos possuem **hashCode** diferentes, eles são definitivamente diferentes.

    - Se possuem o mesmo **hashCode**, é provável que sejam iguais, mas pode ocorrer colisão; portanto, é necessário o uso de **equals** para a confirmação.


  - **Exemplo de uso:**
 
 
    ```java
      String a = "Maria";
      String b = "Alex";
      System.out.println(a.hashCode());
      System.out.println(b.hashCode());
    ```


## 2. Regra de Ouro

- **Regra:**  

  - Se os **hashCodes** de dois objetos forem diferentes, os objetos são diferentes.  


  - Se os **hashCodes** forem iguais, os objetos podem ser iguais (verifique com **equals**).  


- **Lembre-se:**  

  - A implementação de **hashCode** deve ser consistente com **equals**: se dois objetos são iguais pelo método **equals**, eles **devem** retornar o mesmo **hashCode**.



## 3. Implementação Personalizada

  - Para classes personalizadas (exemplo: `Client`), as implementações de **equals** e **hashCode** devem ser sobrepostas para comparar os atributos desejados. Veja o exemplo:


  ```java
    public class Client {
        private String name;
        private String email;
        
        // Sobrescreve equals para comparar name e email
        @Override
        public boolean equals(Object obj) {
            if (this == obj)
                return true;
            if (obj == null || getClass() != obj.getClass())
                return false;
            Client other = (Client) obj;
            return (name != null ? name.equals(other.name) : other.name == null) &&
                  (email != null ? email.equals(other.email) : other.email == null);
        }
        
        // Sobrescreve hashCode de maneira consistente com equals
        @Override
        public int hashCode() {
            int result = 17;
            result = 31 * result + (name != null ? name.hashCode() : 0);
            result = 31 * result + (email != null ? email.hashCode() : 0);
            return result;
        }
    }
  ```

## 4. Exemplo Prático🎲

  Imagine que você tem dois livros e precisa verificar se eles são verdadeiramente idênticos:


  - **equals:** É como ler cada página dos livros para verificar se o conteúdo é exatamente igual. Esse método é preciso, mas pode ser demorado.


  - **hashCode:** É como conferir a etiqueta (código de barras) dos livros. Se as etiquetas são diferentes, você sabe rapidamente que os livros são diferentes. Se as etiquetas forem iguais, pode ser que os livros sejam idênticos, mas você ainda pode precisar verificar o conteúdo completo (usando equals) para confirmar.


### Conclusão 🏁
  
  - equals e hashCode são essenciais para o correto funcionamento de coleções baseadas em hash e para a comparação precisa de objetos.


  - equals oferece uma comparação completa de conteúdo, enquanto hashCode fornece uma verificação rápida que, se diferente, garante que os objetos não são iguais.


  - Em classes personalizadas, é fundamental sobrescrever ambos para garantir que a lógica de comparação seja feita com base nos atributos que realmente definem a identidade dos objetos.


Domine esses métodos para garantir que seus objetos sejam comparados e armazenados de maneira eficiente e correta nas coleções Java! 😊🚀