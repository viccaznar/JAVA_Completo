# Cartões de Resumo: Funções Interessantes para String em Java 😃

## 🔤 Formatar Strings
- **toLowerCase()**: Converte todos os caracteres de uma string para letras minúsculas.  
- **toUpperCase()**: Converte todos os caracteres de uma string para letras maiúsculas.  
- **trim()**: Remove os espaços em branco que estão no início e no final da string.

**Exemplo Lúdico:**  
Imagine que uma mensagem secreta precisa desaparecer dos holofotes. A string `"   SUPER HERO   "` é "disfarçada" ao ser transformada em `"super hero"`, garantindo o sigilo.

**Exemplo Prático:**  
```java
String frase = "   Hello, World!   ";
System.out.println(frase.trim().toLowerCase()); // Saída: "hello, world!"
```

## ✂️ Recortar Strings
- **substring(inicio):** Extrai uma parte da string a partir do índice especificado até o final.

- **substring(inicio, fim):** Extrai uma parte da string entre os índices inicio (inclusivo) e fim (exclusivo).

- **Exemplo Lúdico:**
    Imagine cortar uma fatia de bolo: da mesma forma, o método substring() permite "pegar" somente a parte desejada de uma string, como selecionar o pedaço perfeito do bolo.

- **Exemplo Prático:**
  ```java
    String saudacao = "HelloWorld";
    System.out.println(saudacao.substring(5));    // Saída: "World"
    System.out.println(saudacao.substring(0, 5));   // Saída: "Hello"
  ```


## 🔄 Substituir Conteúdo na String
- **replace(char antigo, char novo):** Substitui todas as ocorrências de um caractere específico por outro.

- **replace(String antiga, String nova):** Substitui todas as ocorrências de uma substring por outra.

- **Exemplo Lúdico:**
  Pense em uma pintura onde você decide trocar todas as pinceladas azuis por vermelhas para mudar o clima da obra. Assim, replace() permite transformar a string ao substituir pedaços por outros desejados.

- **Exemplo Prático:**
  ```java
    String mensagem = "Java é divertido!";
    System.out.println(mensagem.replace("divertido", "poderoso"));
    // Saída: "Java é poderoso!"
  ```


## 🔍 Buscar Caracteres ou Substrings
- **indexOf():** Retorna o índice da primeira ocorrência de um caractere ou substring dentro da string.

- **lastIndexOf():** Retorna o índice da última ocorrência de um caractere ou substring.

- **Exemplo Lúdico:**
  Imagine procurar a primeira e a última estrela em um céu repleto de brilhos; com indexOf() e lastIndexOf(), você localiza o início e o fim da constelação na sua string.

- **Exemplo Prático:**
  ```java
    String palavra = "abracadabra";
    System.out.println(palavra.indexOf("a"));      // Saída: 0
    System.out.println(palavra.lastIndexOf("a"));  // Saída: 10
  ```


## 📊 Dividir Strings
- **split(" "):** Divide a string em um vetor de substrings utilizando o delimitador especificado, neste caso, o espaço em branco.

- **Exemplo Lúdico:**
  Imagine uma deliciosa pizza sendo fatiada para compartilhar com amigos. Cada palavra da frase é uma "fatia" separada, obtida através do método split().

- **Exemplo Prático:**
  ```java
  String frase = "Aprendendo Java é muito legal";
  String[] palavras = frase.split(" ");
  System.out.println(Arrays.toString(palavras));
  // Saída: ["Aprendendo", "Java", "é", "muito", "legal"]
  ```