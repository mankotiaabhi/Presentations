# SOLID Principles 
------------------------------------------------------------------------

# What is SOLID?

SOLID = 5 Design Principles that make code:

-   Easy to understand
-   Easy to maintain
-   Easy to extend
-   Easy to test

------------------------------------------------------------------------

# 1️⃣ Single Responsibility Principle (SRP)

👉 One class = One responsibility

❌ Wrong Example

``` python
class Report:
    def generate(self):
        print("Generating report")

    def save(self):
        print("Saving to file")
```

✅ Correct Example

``` python
class ReportGenerator:
    def generate(self):
        print("Generating report")

class ReportSaver:
    def save(self):
        print("Saving to file")
```

------------------------------------------------------------------------

# 2️⃣ Open/Closed Principle (OCP)

👉 Open for extension, Closed for modification

❌ Wrong Example

``` python
class Discount:
    def calculate(self, type):
        if type == "regular":
            return 10
        elif type == "premium":
            return 20
```

✅ Correct Example

``` python
class Discount:
    def calculate(self):
        pass

class RegularDiscount(Discount):
    def calculate(self):
        return 10

class PremiumDiscount(Discount):
    def calculate(self):
        return 20
```

------------------------------------------------------------------------

# 3️⃣ Liskov Substitution Principle (LSP)

👉 Child class should properly replace parent class

❌ Wrong Example

``` python
class Bird:
    def fly(self):
        print("Flying")

class Ostrich(Bird):
    def fly(self):
        raise Exception("Ostrich can't fly")
```

✅ Correct Example

``` python
class Bird:
    pass

class FlyingBird(Bird):
    def fly(self):
        print("Flying")

class Sparrow(FlyingBird):
    pass

class Ostrich(Bird):
    pass
```

------------------------------------------------------------------------

# 4️⃣ Interface Segregation Principle (ISP)

👉 Don't force classes to implement unused methods

❌ Wrong Example

``` python
class Worker:
    def work(self):
        pass
    def eat(self):
        pass

class Robot(Worker):
    def eat(self):
        raise Exception("Robot doesn't eat")
```

✅ Correct Example

``` python
class Workable:
    def work(self):
        pass

class Eatable:
    def eat(self):
        pass

class Human(Workable, Eatable):
    pass

class Robot(Workable):
    pass
```

------------------------------------------------------------------------

# 5️⃣ Dependency Inversion Principle (DIP)

👉 Depend on abstraction, not concrete class

❌ Wrong Example

``` python
class MySQLDatabase:
    def connect(self):
        print("MySQL Connected")

class Application:
    def __init__(self):
        self.db = MySQLDatabase()
```

✅ Correct Example

``` python
class Database:
    def connect(self):
        pass

class MySQLDatabase(Database):
    def connect(self):
        print("MySQL Connected")

class Application:
    def __init__(self, db: Database):
        self.db = db

    def start(self):
        self.db.connect()

db = MySQLDatabase()
app = Application(db)
app.start()
```

------------------------------------------------------------------------

# Final Summary

S -- Single Responsibility
O -- Open/Closed
L -- Liskov Substitution
I -- Interface Segregation
D -- Dependency Inversion

## ✅ Why SOLID is Important

-   Makes code clean and structured
-   Reduces complexity
-   Prevents tight coupling
-   Makes code easier to test
-   Helps in large-scale project development
-   Improves teamwork and collaboration
-   Makes future changes easier
-   Increases software stability
