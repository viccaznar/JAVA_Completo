# 💡 Cartão de Resumo: Restrições e Convenções para Nomes em Java

## 🔒 Restrições para Nomes de Variáveis
- **Não pode começar com dígito:**  
  Use uma letra ou o caractere underscore (_) no início.  
- **Evitar acentos ou til:**  
  Utilize apenas caracteres sem acentuação para garantir compatibilidade.  
- **Sem espaços em branco:**  
  Nomes não devem conter espaços; opte por unir as palavras.  
- **Uso de nomes significativos:**  
  Prefira nomes que descrevam o propósito da variável, facilitando a compreensão do código.  

 **Exemplo Lúdico:**  
 Imagine que você está batizando um super-herói. Um nome como `"45Hero"` perde toda a identidade e charme. Usar `"hero45"` ou `"superHero"` garante que o personagem seja único e reconhecível! 😃

 **Exemplo Prático:**  
 Errado:
 ```java
 int 5minutes;          // Inicia com dígito
 int salário;            // Possui acento
 int salario do funcionario;  // Contém espaços
 ```
 Correto:
 ```java
 int_5minutes;
 intsalario;
 intsalarioDoFuncionario;
 ```



## 🎨 Convenções de Nomenclatura
- **CamelCase:**  
  - **Aplicação:** Utilizado para pacotes, atributos, métodos, variáveis e parâmetros.  
  - **Exemplo:** `lastName`
  
- **PascalCase:**  
  - **Aplicação:** Utilizado na nomeação de classes.  
  - **Exemplo:** `ProductService`

 **Exemplo Lúdico:**  
 Imagine sua equipe de super-heróis: os atributos e métodos são como os membros com nomes simples e funcionais (ex.: `lastName`), enquanto a classe principal, a força motriz do grupo, ganha um nome de destaque, como `ProductService` – algo que imediatamente transmita sua importância e papel! ⚡

 **Exemplo Prático:**  
 ```java
 package entities;
 
 public class Account {
     private String holder;
     private Double balance;
 
     public Account(String holder, Double balance) {
         this.holder = holder;
         this.balance = balance;
     }
 
     public String getHolder() {
         return holder;
     }
 
     public void deposit(double amount) {
         balance += amount;
     }
 
     public void withdraw(double amount) {
         balance -= amount;
     }
 }
 ```



## 📚 Resumo Final
- **Restrições:**  
  - Variáveis não podem começar com dígitos, usar acentos ou conter espaços em branco.  
  - Opte sempre por nomes claros e com significado.
  
- **Convenções:**  
  - **CamelCase** para pacotes, atributos, métodos, variáveis e parâmetros (ex.: `lastName`).  
  - **PascalCase** para classes (ex.: `ProductService`).

Adotar essas práticas mantém o código **organizado**, **legível** e **fácil de manter**, facilitando o trabalho em equipe e a escalabilidade dos projetos em Java. 🚀