# 🎥 Java Design Pattern Tutorial: Prototype Pattern

---

## 1. 🌟 Definition

> *The Prototype Pattern is a creational design pattern that allows you to clone existing objects instead of creating new ones from scratch.*
>
> *It helps in creating copies of objects while keeping performance and memory efficiency in mind.*

---

## 2. 💻 Code Example – Zombie Prototype

```java
// Prototype Interface
interface Zombie extends Cloneable {
    Zombie clone();
    void showStats();
}

// Concrete Prototype
class BasicZombie implements Zombie {
    private String type;
    private int health;
    private int speed;

    public BasicZombie(String type, int health, int speed) {
        this.type = type;
        this.health = health;
        this.speed = speed;
    }

    @Override
    public Zombie clone() {
        return new BasicZombie(type, health, speed);
    }

    @Override
    public void showStats() {
        System.out.println("Zombie Type: " + type);
        System.out.println("Health: " + health);
        System.out.println("Speed: " + speed);
    }

    public void setHealth(int health) {
        this.health = health;
    }

    public void setSpeed(int speed) {
        this.speed = speed;
    }
}

// Client
public class GameClient {
    public static void main(String[] args) {
        BasicZombie baseZombie = new BasicZombie("Walker", 100, 10);

        BasicZombie fastZombie = (BasicZombie) baseZombie.clone();
        fastZombie.setSpeed(20);

        BasicZombie tankZombie = (BasicZombie) baseZombie.clone();
        tankZombie.setHealth(300);
        tankZombie.setSpeed(5);

        System.out.println("-- Base Zombie --");
        baseZombie.showStats();

        System.out.println("\n-- Fast Zombie --");
        fastZombie.showStats();

        System.out.println("\n-- Tank Zombie --");
        tankZombie.showStats();
    }
}
```

---

## 3. 🔍 Which SOLID Principles Are Used?

| SOLID Principle                   | How It’s Applied                                                           |
| --------------------------------- | -------------------------------------------------------------------------- |
| ✅ Single Responsibility Principle | Cloning logic is encapsulated in each class, separate from creation logic. |
| ✅ Open/Closed Principle           | You can introduce new types of zombies without modifying existing code.    |
| ✅ Liskov Substitution Principle   | You can use cloned objects anywhere original prototypes are expected.      |
| ✅ Dependency Inversion Principle  | Clients depend on the interface (`Zombie`), not the concrete class.        |

---

## 4. 📦 Where It’s Used in the JDK

### 1. `Object.clone()`

```java
MyClass obj2 = (MyClass) obj1.clone();
```

Clones an object without reinitializing its fields. Frequently used for custom object copies.

### 2. `ArrayList.clone()`

```java
ArrayList<String> listCopy = (ArrayList<String>) originalList.clone();
```

Returns a shallow copy of the original list, useful for temporary data duplication.

### 3. `HashMap.clone()`

```java
HashMap<K, V> clonedMap = (HashMap<K, V>) originalMap.clone();
```

Produces a shallow copy of key-value pairs for quick reuse without rebuilding.

### 4. `Calendar.clone()`

```java
Calendar newCal = (Calendar) oldCal.clone();
```

Used to duplicate complex date-time configurations efficiently.

### 5. `Locale.clone()`

```java
Locale newLocale = (Locale) originalLocale.clone();
```

Creates a duplicate locale object for region-based configuration reuse.

---

## 5. 🌟 Key Benefits

* **Avoids repetitive setup**
* **Reduces object creation cost**
* **Simplifies logic**
* **Preserves base state**
* **Improves performance**

---
