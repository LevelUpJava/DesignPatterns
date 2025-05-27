
# SOLID Principles in Java

- **S** – Single Responsibility  
- **O** – Open/Closed  
- **L** – Liskov Substitution  
- **I** – Interface Segregation  
- **D** – Dependency Inversion

## ✨ S – Single Responsibility Principle

**Definition:** A class should have only one reason to change.

### ❌ Bad Example
```java
class Chef {
    void cook() {
        System.out.println("Cooking food");
    }
    void takeOrder() {
        System.out.println("Taking order");
    }
    void deliverFood() {
        System.out.println("Delivering food");
    }
    void washDishes() {
        System.out.println("Washing dishes");
    }
}
```

### ✅ Good Example
```java
class Chef {
    void cook() {
        System.out.println("Cooking food");
    }
}

class Waiter {
    void takeOrder() {
        System.out.println("Taking order");
    }
}

class Dishwasher {
    void washDishes() {
        System.out.println("Washing dishes");
    }
}
```

---

## 🔐 O – Open/Closed Principle

**Definition:** Software should be open for extension, but closed for modification.

### ❌ Bad Example
```java
class NotificationService {
    void send(String type) {
        if (type.equals("email")) {
            System.out.println("Sending Email");
        } else if (type.equals("sms")) {
            System.out.println("Sending SMS");
        } else if (type.equals("whatsapp")) {
            System.out.println("Sending WhatsApp message");
        }
    }
}
```

### ✅ Good Example
```java
interface Notification {
    void send();
}

class EmailNotification implements Notification {
    public void send() {
        System.out.println("Sending Email");
    }
}

class SMSNotification implements Notification {
    public void send() {
        System.out.println("Sending SMS");
    }
}

class WhatsappNotification implements Notification {
    public void send() {
        System.out.println("Sending Whatsapp Notification");
    }
}
```

---

## 📍 L – Liskov Substitution Principle

**Definition:** Objects of a superclass should be replaceable with objects of its subclasses without breaking the program.

```java
interface RemoteControl {
    void turnOn();
}

class SamsungTV implements RemoteControl {
    public void turnOn() {
        System.out.println("Samsung TV turned on");
    }
}

class LGTV implements RemoteControl {
    public void turnOn() {
        System.out.println("LG TV turned on");
    }
}

class RemoteTest {
    public static void main(String[] args) {
        RemoteControl remote1 = new SamsungTV();
        RemoteControl remote2 = new LGTV();
        remote1.turnOn();
        remote2.turnOn();
    }
}
```

---

## 🔌 I – Interface Segregation Principle

**Definition:** A class should not be forced to implement methods it doesn't use.

### ❌ Bad Example
```java
interface JobApplication {
    void provideResume();
    void askIfCanFlyPlane();
    void askGOTSeasonCount();
}

class SoftwareEngineer implements JobApplication {
    public void provideResume() {
        System.out.println("Uploading resume for Software Engineer role.");
    }

    public void askIfCanFlyPlane() {
        System.out.println("Can you fly a plane?");
    }

    public void askGOTSeasonCount() {
        System.out.println("How many seasons of Game of Thrones have you watched?");
    }
}
```

### ✅ Good Example
```java
interface JobApplication {
    void provideResume();
}

class SoftwareEngineer implements JobApplication {
    public void provideResume() {
        System.out.println("Uploading resume for Software Engineer role.");
    }
}
```

---

## ⚙️ D – Dependency Inversion Principle

**Definition:** High-level modules should depend on abstractions, not on concrete implementations.

### ❌ Bad Example
```java
class Editor {
    void openTxtFile(String fileName) {
        System.out.println("Opening TXT file: " + fileName);
    }

    void openJsonFile(String fileName) {
        System.out.println("Opening JSON file: " + fileName);
    }

    public static void main(String[] args) {
        Editor editor = new Editor();
        editor.openTxtFile("notes.txt");
        editor.openJsonFile("data.json");
    }
}
```

### ✅ Good Example
```java
interface FileParser {
    void parse(String fileName);
}

class TxtParser implements FileParser {
    public void parse(String fileName) {
        System.out.println("Parsing TXT file: " + fileName);
    }
}

class JsonParser implements FileParser {
    public void parse(String fileName) {
        System.out.println("Parsing JSON file: " + fileName);
    }
}

class Editor {
    void openFile(FileParser parser, String fileName) {
        parser.parse(fileName);
    }

    public static void main(String[] args) {
        Editor editor = new Editor();
        editor.openFile(new TxtParser(), "notes.txt");
        editor.openFile(new JsonParser(), "data.json");
    }
}
```

---
