Creational = How objects are created

Structural = How objects are composed/organized

Behavioral = How objects communicate/interact


## 🎨 Creational Patterns (Object Creation)


### Singleton Pattern 🔐

Ensures only ONE instance of a class exists

Global access point to that instance

Use: Database connections, logging, configuration

### Factory Pattern 🏭

Creates objects without specifying exact class

Delegates instantiation logic to subclasses

Use: When object creation is complex or conditional

### Builder Pattern 🔨

Constructs complex objects step-by-step

Separates construction from representation

Use: Objects with many optional parameters (e.g., building a Pizza)

### Prototype Pattern 🧬

Creates new objects by cloning existing ones

Avoids costly creation operations

Use: When object creation is expensive

## 🏗️ Structural Patterns (Object Composition)

### Decorator Pattern 🎁

Adds new functionality to objects dynamically

Wraps objects without modifying their structure

Use: Adding features to objects at runtime (e.g., adding toppings to coffee)

## 🎭 Behavioral Patterns (Object Interaction)


### Memento Pattern 💾
Captures and restores object's previous state

Implements undo/redo functionality

Use: Text editors, game save states, transaction rollbacks