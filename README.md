# Novidades do Java 8 ao Java 21

## **Java 8 (2014)**
O Java 8 foi uma das maiores atualizações da linguagem, trazendo recursos como Expressões Lambda, Streams, API de Data e Hora, entre outros.

### **1. Expressões Lambda**
Antes do Java 8, para definir um comportamento, usávamos classes anônimas. Agora, podemos usar expressões lambda.

**Antes (Java 7)**
```java
List<String> nomes = Arrays.asList("Ana", "Bruno", "Carlos");
Collections.sort(nomes, new Comparator<String>() {
    @Override
    public int compare(String s1, String s2) {
        return s1.compareTo(s2);
    }
});
```

**Depois (Java 8)**
```java
List<String> nomes = Arrays.asList("Ana", "Bruno", "Carlos");
nomes.sort((s1, s2) -> s1.compareTo(s2));
```

---

### **2. Interface Funcional e `java.util.function`**
O Java 8 introduziu a anotação `@FunctionalInterface` e a API `java.util.function`, que contém interfaces como `Predicate`, `Function`, `Consumer`, etc.

**Antes (Java 7)**
```java
public interface Validador {
    boolean validar(String s);
}

class ValidadorEmail implements Validador {
    @Override
    public boolean validar(String s) {
        return s.contains("@");
    }
}
```

**Depois (Java 8)**
```java
@FunctionalInterface
interface Validador {
    boolean validar(String s);
}

Validador validadorEmail = s -> s.contains("@");
System.out.println(validadorEmail.validar("email@dominio.com")); // true
```

---

### **3. Streams API**
Facilitou a manipulação de coleções de dados com operações como `map`, `filter`, `reduce`.

**Antes (Java 7)**
```java
List<String> nomes = Arrays.asList("Ana", "Bruno", "Carlos");
List<String> filtrados = new ArrayList<>();
for (String nome : nomes) {
    if (nome.startsWith("A")) {
        filtrados.add(nome);
    }
}
System.out.println(filtrados);
```

**Depois (Java 8)**
```java
List<String> nomes = Arrays.asList("Ana", "Bruno", "Carlos");
List<String> filtrados = nomes.stream()
    .filter(nome -> nome.startsWith("A"))
    .collect(Collectors.toList());
System.out.println(filtrados);
```

---

### **4. API de Data e Hora (`java.time`)**
O Java 8 introduziu uma nova API de datas que substitui `java.util.Date` e `java.util.Calendar`.

**Antes (Java 7)**
```java
Calendar calendario = Calendar.getInstance();
calendario.set(2024, Calendar.MARCH, 18);
Date data = calendario.getTime();
System.out.println(data);
```

**Depois (Java 8)**
```java
LocalDate data = LocalDate.of(2024, Month.MARCH, 18);
System.out.println(data);
```

---

## **Java 9 (2017)**

### **1. Módulos do Java (Project Jigsaw)**
O Java 9 introduziu o sistema de módulos (`module-info.java`), permitindo dividir aplicativos em partes menores.

**Antes (Java 8)**
Todos os códigos eram organizados apenas com pacotes e arquivos `.jar`.

**Depois (Java 9)**
```java
module meu.modulo {
    exports com.exemplo;
}
```

---

### **2. `List.of()`, `Set.of()`, `Map.of()`**
Facilitou a criação de coleções imutáveis.

**Antes (Java 8)**
```java
List<String> lista = new ArrayList<>();
lista.add("A");
lista.add("B");
lista.add("C");
```

**Depois (Java 9)**
```java
List<String> lista = List.of("A", "B", "C");
```

---

## **Java 10 (2018)**

### **1. `var` para inferência de tipos**
Agora podemos usar `var` para declarar variáveis locais.

**Antes (Java 9)**
```java
String nome = "João";
int idade = 25;
```

**Depois (Java 10)**
```java
var nome = "João";
var idade = 25;
```

---

## **Java 11 (2018 - LTS)**

### **1. Strings Melhoradas**
Métodos úteis foram adicionados, como `isBlank()`, `lines()`, `repeat()`.

**Antes (Java 10)**
```java
String texto = " ";
boolean vazio = texto.trim().isEmpty();
```

**Depois (Java 11)**
```java
String texto = " ";
boolean vazio = texto.isBlank(); // true
```

---

## **Java 12 (2019)**

### **1. `switch` melhorado**
Agora `switch` pode ser usado como expressão.

**Antes (Java 11)**
```java
int dia = 3;
String nomeDia;
switch (dia) {
    case 1: nomeDia = "Segunda"; break;
    case 2: nomeDia = "Terça"; break;
    default: nomeDia = "Outro";
}
```

**Depois (Java 12)**
```java
String nomeDia = switch (dia) {
    case 1 -> "Segunda";
    case 2 -> "Terça";
    default -> "Outro";
};
```

---

## **Java 14 (2020)**

### **1. `record` para classes imutáveis**
Elimina a necessidade de escrever `getters`, `setters`, `equals`, `hashCode` e `toString`.

**Antes (Java 13)**
```java
class Pessoa {
    private final String nome;
    private final int idade;

    public Pessoa(String nome, int idade) {
        this.nome = nome;
        this.idade = idade;
    }

    public String getNome() { return nome; }
    public int getIdade() { return idade; }
}
```

**Depois (Java 14)**
```java
record Pessoa(String nome, int idade) {}
```

---

## **Java 16 (2021)**

### **1. `pattern matching` no `instanceof`**
Evita cast manual após `instanceof`.

**Antes (Java 15)**
```java
if (obj instanceof String) {
    String s = (String) obj;
    System.out.println(s.length());
}
```

**Depois (Java 16)**
```java
if (obj instanceof String s) {
    System.out.println(s.length());
}
```

---

## **Java 17 (2021 - LTS)**

### **1. `sealed classes`**
Restringe quais classes podem estender uma classe.

```java
sealed class Veiculo permits Carro, Moto {}
final class Carro extends Veiculo {}
final class Moto extends Veiculo {}
```

---

## **Java 21 (2023 - LTS)**

### **1. `Pattern Matching` para `switch`**
Agora `switch` suporta padrões avançados.

```java
static String formatar(Object obj) {
    return switch (obj) {
        case Integer i -> "Número: " + i;
        case String s -> "Texto: " + s;
        default -> "Outro";
    };
}
```

---

Essas foram as principais novidades do Java 8 ao Java 21!
