# 🎮 Catch the Ball Game

> A simple Java desktop game where you control a player and catch falling objects before you run out of lives.

[![Java](https://img.shields.io/badge/Java-8%2B-orange?logo=openjdk)](https://www.oracle.com/java/)
[![Swing](https://img.shields.io/badge/GUI-Java%20Swing-blue)](https://docs.oracle.com/javase/tutorial/uiswing/)
[![AWT](https://img.shields.io/badge/Graphics-Java%20AWT-green)](https://docs.oracle.com/javase/8/docs/api/java/awt/package-summary.html)
[![Status](https://img.shields.io/badge/Status-Completed-success)](#)

## ✨ About the Game

**Catch the Ball** is a small Java-based arcade game created to practice fundamental Java programming and object-oriented programming concepts.

The player controls a paddle at the bottom of the game window and moves it from left to right using the keyboard. Red objects continuously fall from the top of the screen. The goal is to catch as many objects as possible while keeping all three lives.

Every successful catch increases the score. Missing a falling object costs one life. When all lives are lost, the game displays a **Game Over** message.

---

## 🕹️ How to Play

1. Start the game.
2. Use the **Left Arrow ←** key to move the player left.
3. Use the **Right Arrow →** key to move the player right.
4. Position the player underneath the falling object.
5. Catch the object to increase your score.
6. If an object reaches the bottom without being caught, you lose one life.
7. The game ends when all **3 lives** are gone.

### 🎯 Game Rules

| Action          | Result    |
| --------------- | --------- |
| Catch an object | +1 score  |
| Miss an object  | -1 life   |
| Start game      | 3 lives   |
| Lose all lives  | Game Over |

---

## 🚀 Features

* 🎮 Simple keyboard-controlled gameplay
* 🔴 Continuously falling objects
* 🧲 Collision detection between the player and falling objects
* 🏆 Score tracking
* ❤️ Three-life system
* 📦 Generic inventory system
* ⚠️ Custom game exception handling
* 🖥️ Java Swing desktop interface
* 🎨 Java AWT graphics
* 🧱 Object-oriented class structure
* 🔄 Real-time screen updates
* 📍 Player movement restricted within the game window

---

## 🛠️ Technologies Used

* **Java**
* **Java Swing** — used to create the game window and GUI
* **Java AWT** — used for drawing game objects and handling graphics
* **ArrayList** — used to store falling objects
* **Generics** — used in the inventory system
* **Inheritance** — used through the `GameObject` base class
* **Custom Exception Handling** — implemented with `GameException`
* **Keyboard Events** — used for player movement
* **Swing Timer** — used to refresh the game screen

---

## 📁 Project Structure

```text
catch-the-ball-game/
│
├── CatchGame.java
├── FallingItem.java
├── GameException.java
├── GameObject.java
├── Inventory.java
├── Player.java
│
└── README.md
```

### 📄 Class Overview

| File                 | Responsibility                                                                       |
| -------------------- | ------------------------------------------------------------------------------------ |
| `CatchGame.java`     | Main game window, game loop, score, lives, object generation, and overall game logic |
| `GameObject.java`    | Abstract parent class containing the common `x` and `y` position of game objects     |
| `Player.java`        | Represents the player, handles movement and collision detection                      |
| `FallingItem.java`   | Represents the falling red objects and controls their downward movement              |
| `Inventory.java`     | Generic inventory class used to store collected items                                |
| `GameException.java` | Custom exception used to display a message when the final score is low               |

---

## 🧠 How the Game Works

The game is built around a simple update-and-render process.

### 1. Player Creation

When the game starts, a `Player` object is created near the bottom of the window.

```java
player = new Player(170, 500);
```

The player is represented by a rectangle and can move horizontally.

---

### 2. Falling Objects

A new `FallingItem` is generated approximately every second.

```java
FallingItem item = new FallingItem(
    (int) (Math.random() * 360),
    0
);
```

Each object starts near the top of the screen and moves downward.

---

### 3. Player Movement

The player uses the keyboard:

```text
← Left Arrow   → Right Arrow
```

The `Player` class prevents the player from moving outside the game window.

---

### 4. Falling Movement

Every falling object moves downward by increasing its `y` position.

```java
y += 5;
```

This creates the falling animation.

---

### 5. Collision Detection

The game checks whether the player and falling object overlap.

Conceptually:

```text
Player rectangle
       ↓
 ┌─────────────┐
 │    PLAYER   │
 └─────────────┘
        ▲
        │ collision
        ▼
      ┌───┐
      │ ● │
      └───┘
    Falling Item
```

Java's `Rectangle.intersects()` method is used to determine whether the two objects collide.

---

### 6. Score and Lives

When the player catches an object:

```text
Score + 1
Object removed
Item added to inventory
```

When an object falls past the bottom of the screen:

```text
Lives - 1
Object removed
```

The game continues until:

```text
Lives = 0
```

---

## 🧩 Object-Oriented Programming Concepts

This project also demonstrates several important Java OOP concepts.

### 🔹 Inheritance

`Player` and `FallingItem` both extend `GameObject`.

```text
             GameObject
              /      \
             /        \
        Player      FallingItem
```

The parent class provides common position data and the `draw()` method structure.

---

### 🔹 Abstraction

`GameObject` is declared as an abstract class.

```java
public abstract class GameObject
```

It defines common behavior that can be shared by different objects in the game.

---

### 🔹 Polymorphism

Different game objects provide their own implementation of the `draw()` method.

For example:

* `Player` draws a rectangle.
* `FallingItem` draws a circle.

---

### 🔹 Encapsulation

The classes keep their responsibilities separated.

For example:

* `Player` handles player-related behavior.
* `FallingItem` handles falling-object behavior.
* `Inventory` handles collected items.
* `CatchGame` manages the overall game.

---

### 🔹 Generics

The inventory class uses a generic type:

```java
public class Inventory<T>
```

This allows the inventory to work with different types of objects.

---

### 🔹 Exception Handling

The project includes a custom exception:

```java
public class GameException extends Exception
```

When the game ends with a low score, the exception is used to display a message such as:

```text
Better luck next time!
```

---

## 💻 Getting Started

### Prerequisites

You need:

* Java Development Kit (**JDK 8 or newer**)
* A Java-compatible IDE or terminal
* A desktop environment that supports Java Swing

You can check whether Java is installed with:

```bash
java -version
```

And check the Java compiler with:

```bash
javac -version
```

---

## 📥 Installation

### 1. Clone the repository

```bash
git clone https://github.com/tniha10/catch-the-ball-game.git
```

### 2. Open the project

```bash
cd catch-the-ball-game
```

### 3. Compile the Java files

```bash
javac *.java
```

### 4. Run the game

```bash
java CatchGame
```

The game window should open automatically.

---

## 🎮 Controls

| Key | Action            |
| --- | ----------------- |
| `←` | Move player left  |
| `→` | Move player right |

That's it — keep moving and catch as many falling objects as possible!

---

## 📸 Game Flow

```text
        GAME START
             │
             ▼
       Player appears
             │
             ▼
      Objects start falling
             │
             ▼
      ┌───────────────┐
      │ Did player    │
      │ catch object? │
      └───────┬───────┘
          YES │     │ NO
              │     │
              ▼     ▼
           Score   Object
            +1     reaches
              │     bottom
              │       │
              │       ▼
              │     Life -1
              │       │
              └───┬───┘
                  ▼
            More lives?
             /       \
           YES       NO
            │         │
            ▼         ▼
       Continue    GAME OVER
```

---

## 🎯 Learning Goals

This project was designed to practice:

* Java fundamentals
* Classes and objects
* Inheritance
* Abstract classes
* Polymorphism
* Generics
* Collections
* Exception handling
* GUI programming
* Keyboard event handling
* Basic game loops
* Collision detection
* Real-time object movement

---

## 🔮 Possible Future Improvements

The current game provides a simple foundation that can be expanded with features such as:

* 🔊 Sound effects
* 🎵 Background music
* 🏅 High-score tracking
* ⏱️ A countdown timer
* 📈 Increasing difficulty
* 🎨 Better graphics and animations
* 🔄 Restart button
* ⏸️ Pause/resume functionality
* 🎯 Different types of falling objects
* ❤️ Visual life indicators
* 🏆 A leaderboard
* 🖼️ Custom game background

---

## 📌 Project Status

**Completed — basic playable version**

The current version focuses on demonstrating core Java programming, GUI development, object-oriented design, and basic game mechanics.

---

## 👩‍💻 Author

**Niha**

GitHub: [@tniha10](https://github.com/tniha10)

---

## ⭐ Support

If you found this project interesting, feel free to explore the code, experiment with the game mechanics, and build your own improvements.

⭐ **Star the repository if you enjoyed it!**

---

### 📜 License

This project does not currently include a license file.
