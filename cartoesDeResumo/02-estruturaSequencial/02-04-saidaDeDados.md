# 📤 Saída de Dados em Java

- 🖨️ **System.out.print**  
  Escrita sem quebra de linha – permite exibir texto ou valores de forma contínua no console.

- 🖨️ **System.out.println**  
  Escrita com quebra de linha ao final – imprime e adiciona automaticamente uma nova linha (`\n` ou `%n`).

- 🎨 **System.out.printf**  
  Escrita formatada – mistura texto e valores usando _placeholders_ (`%d`, `%f`, `%s`) e `%n` para nova linha.

- 🔢 **Especificadores de Formato**  
  • `%d` → inteiro  
  • `%f` → ponto flutuante  
  • `%s` → texto  
  • `%n` → nova linha (independente de plataforma)

- 🌐 **Locale**  
  Controla o separador decimal em `printf`.  
  Exemplo:  
  ```java
  Locale.setDefault(Locale.US); // usa ponto como separador decimal
  ```

- ➕ **Concatenação de Elementos**
        • **Com print/println:**
            "Resultado = " + x + " metros"
        • **Com printf:**
            "Resultado = %.2f metros%n", x

- 🔧 **Comentários e Atalhos**
    • Linha única: // seu comentário
    • Importar classes: Ctrl + Shift + O
    • Auto-indentação: Ctrl + Shift + F
    • Atalho para sysout: digite sysout + Ctrl + Espaço

- 🎈 **Exemplo Lúdico**
    // A fada exibe sua mensagem mágica sem quebrar linha:
```java
    System.out.print("Abra-kadabra, ");
    System.out.println("o coelho está no chapéu!");
    System.out.printf("Você tem %d vidas de dragão e %.1f poções.%n", 3, 4.5);
```

- 💼 **Exemplo Prático**
```java
import java.util.Locale;
public class Relatorio
{
  public static void main(String[] args)
  {
    Locale.setDefault(Locale.US);
    String nome = "Maria";
    int idade = 31;
    double renda = 4000.0;
    System.out.println("----- RELATÓRIO -----");
    System.out.printf("%s tem %d anos e ganha R$ %.2f%n", nome, idade, renda);
  }
}
```



