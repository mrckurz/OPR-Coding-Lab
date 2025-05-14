# 🧪 OPR Coding Lab zur Vertiefung von Java Lambda Expressions in Java

## 🎯 Ziel
Du lernst in diesem Lab:
- den Einsatz von **Lambda Expressions** zur Vereinfachung von Code.
- wie man Listen sortiert, filtert und transformiert.
- den Umgang mit funktionalen Interfaces wie `Comparator`, `Predicate`, `Consumer` und `Function`.

---

## 🧰 Vorbereitung

### 1. Lege eine Java-Klasse `Person.java` an:

```java
public class Person {
    private String name;
    private int alter;

    public Person(String name, int alter) {
        this.name = name;
        this.alter = alter;
    }

    public String getName() {
        return name;
    }

    public int getAlter() {
        return alter;
    }

    @Override
    public String toString() {
        return name + " (" + alter + ")";
    }
}
```

---

### 2. Lege die Hauptklasse `LambdaLab.java` an:

```java
import java.util.*;
import java.util.function.*;

public class LambdaLab {
    public static void main(String[] args) {
        List<Person> personen = Arrays.asList(
            new Person("Anna", 23),
            new Person("Bernd", 30),
            new Person("Clara", 25),
            new Person("David", 20)
        );

        // Lösungen folgen hier
    }

    public static void filterUndZeige(List<Person> personen, Predicate<Person> kriterium) {
        for (Person p : personen) {
            if (kriterium.test(p)) {
                System.out.println(p);
            }
        }
    }
}
```

---

## 🔄 Übungen mit Musterlösungen

### 🧩 **Übung 1: Sortierung mit Lambdas**

```java
// 1. Nach Alter aufsteigend
personen.sort((p1, p2) -> Integer.compare(p1.getAlter(), p2.getAlter()));

// 2. Nach Name absteigend
personen.sort((p1, p2) -> p2.getName().compareTo(p1.getName()));

// 3. Nach Alter, dann Name
personen.sort((p1, p2) -> {
    int cmp = Integer.compare(p1.getAlter(), p2.getAlter());
    return (cmp != 0) ? cmp : p1.getName().compareTo(p2.getName());
});
```

---

### 🧩 **Übung 2: Ausgabe mit `forEach`**

```java
// 1. Namen in Großbuchstaben
personen.forEach(p -> System.out.println(p.getName().toUpperCase()));

// 2. Hinweis bei Alter > 25
personen.forEach(p -> {
    if (p.getAlter() > 25) {
        System.out.println(p + " 👴");
    } else {
        System.out.println(p);
    }
});
```

---

### 🧩 **Übung 3: Filter mit Predicate**

```java
// 1. Jünger als 25
filterUndZeige(personen, p -> p.getAlter() < 25);

// 2. Name beginnt mit „A“
filterUndZeige(personen, p -> p.getName().startsWith("A"));

// 3. Alter zwischen 22 und 28
filterUndZeige(personen, p -> p.getAlter() >= 22 && p.getAlter() <= 28);
```

---

### 🧩 **[Optional] Übung 4: Streams kombinieren**

```java
personen.stream()
        .filter(p -> p.getAlter() >= 25)
        .map(p -> p.getName().toUpperCase())
        .forEach(System.out::println);
```

---

## ✅ Bonusideen (Beispiel-Lösung)

```java
// Funktion zur Generierung einer E-Mail-Adresse
Function<Person, String> emailGenerator = p -> p.getName().toLowerCase() + "@example.com";
personen.forEach(p -> System.out.println(emailGenerator.apply(p)));

// Kombination mehrerer Predicate
Predicate<Person> isAdult = p -> p.getAlter() >= 18;
Predicate<Person> nameStartsWithA = p -> p.getName().startsWith("A");

filterUndZeige(personen, isAdult.and(nameStartsWithA));
```
