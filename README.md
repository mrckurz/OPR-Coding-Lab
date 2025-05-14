# 🧪 Coding Lab: Einstieg in Java Lambda Expressions

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

        // Übungen folgen hier
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

## 🔄 Übungen

### 🧩 **Übung 1: Sortierung mit Lambdas**

1. Sortiere die Liste `personen` **aufsteigend nach Alter**.
2. Sortiere die Liste **absteigend nach Name**.
3. Sortiere **zuerst nach Alter, dann nach Name**.

*Hinweis: Verwende `personen.sort(...)` mit Lambdas.*

---

### 🧩 **Übung 2: Ausgabe mit `forEach`**

1. Gib alle Namen in **Großbuchstaben** aus.
2. Wenn das Alter > 25 ist, gib einen Hinweis aus (z. B. "👴").

*Hinweis: Verwende `personen.forEach(...)` mit Lambdas.*

---

### 🧩 **Übung 3: Filter mit Predicate**

1. Gib nur die Personen aus, die **jünger als 25** sind.
2. Gib nur die Personen aus, deren **Name mit „A“** beginnt.
3. Gib nur die Personen aus, deren Alter **zwischen 22 und 28** liegt.

*Hinweis: Verwende `filterUndZeige(...)` und gib Lambdas als `Predicate<Person>`.*

---

### 🧩 **[Optional] Übung 4: Streams kombinieren**

Nutze `Stream`, um folgendes zu tun:

1. Filtere alle Personen mit Alter ≥ 25.
2. Wandle ihre Namen in Großbuchstaben um.
3. Gib sie mit `forEach` aus.

```java
personen.stream()
        .filter(p -> ...)
        .map(p -> ...)
        .forEach(System.out::println);
```

---

## ✅ Bonusideen

- Erstelle eine eigene Methode, die `Function<Person, String>` annimmt und z. B. eine Visitenkarte oder E-Mail-Adresse ausgibt.
- Kombiniere mehrere `Predicate`s mit `and()`, `or()` oder `negate()`.
