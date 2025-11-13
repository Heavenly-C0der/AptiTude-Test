# Object-Oriented Programming (OOP) Study Guide

Object-Oriented Programming is a programming paradigm based on the concept of "objects", which can contain data and code. For an ML Engineer role, understanding OOP is crucial for writing modular, reusable, and maintainable code, especially when building complex models or data pipelines.

---

### 1. The Four Pillars of OOP

You must understand these four core concepts and be able to explain them with clear code examples.

#### A. Encapsulation
- **Concept:** The bundling of data (attributes) and the methods (functions) that operate on that data into a single unit, or "class." It also involves restricting direct access to some of an object's components, which is a key principle of data hiding.
- **Why it's useful:** It protects the data from accidental modification and makes the code easier to maintain and understand. You expose a public interface (methods) and hide the complex implementation details.
- **Example (Python):**
  ```python
  class Car:
      def __init__(self, make, model):
          self.__make = make  # Private attribute
          self.__speed = 0

      def accelerate(self):
          self.__speed += 10

      def get_speed(self):
          return self.__speed
  ```

#### B. Abstraction
- **Concept:** Hiding the complex implementation details and showing only the essential features of the object. It's about simplifying a complex system by modeling classes appropriate to the problem.
- **Why it's useful:** It reduces complexity and allows for easier-to-understand code. You can change the internal implementation without affecting the code that uses the object.
- **Example:** When you drive a car, you use the steering wheel and pedals (the interface). You don't need to know how the engine or transmission works internally (the implementation). Abstract classes and methods help enforce this.

#### C. Inheritance
- **Concept:** A mechanism where a new class (child/subclass) derives attributes and methods from an existing class (parent/superclass).
- **Why it's useful:** It promotes code reusability ("Don't Repeat Yourself" - DRY principle). You can create a more specific version of a class without rewriting all the code.
- **Example (Python):**
  ```python
  class ElectricCar(Car):  # Inherits from Car
      def __init__(self, make, model, battery_size):
          super().__init__(make, model)
          self.battery_size = battery_size

      def charge(self):
          print("Charging...")
  ```

#### D. Polymorphism
- **Concept:** The ability of an object to take on many forms. In practice, it means that a single interface (like a method name) can be used for different types of objects.
- **Why it's useful:** It allows for flexibility and writing generic code that can work with different objects.
- **Types:**
  - **Method Overriding (Runtime Polymorphism):** A child class provides its own implementation of a method that is already defined in its parent class.
  - **Method Overloading (Compile-time Polymorphism):** A class has multiple methods with the same name but different parameters (number or type). *Note: Python does not support method overloading in the traditional sense but achieves similar results with default arguments.*
- **Example (Python - Overriding):**
  ```python
  class Animal:
      def speak(self):
          print("Some generic sound")

  class Dog(Animal):
      def speak(self):
          print("Woof!")

  class Cat(Animal):
      def speak(self):
          print("Meow!")

  # Polymorphism in action
  for animal in [Dog(), Cat()]:
      animal.speak()
  ```

---

### 2. How to Prepare

- **Choose a Language:** Be prepared to demonstrate OOP concepts in a language you are comfortable with (Python is highly recommended for ML roles).
- **Code Examples:** Don't just memorize definitions. Write small, clear code examples for each of the four pillars.
- **Relate to ML:** Think about how OOP is used in ML frameworks. For example, a `Model` in Keras or PyTorch is a class. You create your own model by inheriting from this base class and overriding methods like `forward()`.

---

### 3. Recommended Resources

- **GeeksforGeeks:** Has excellent articles on OOP concepts for various languages.
- **Real Python:** Provides in-depth tutorials on Python OOP with practical examples.
- **YouTube:** Search for "OOP in Python" (or your language of choice) for visual explanations. Corey Schafer's Python OOP series is highly regarded.
