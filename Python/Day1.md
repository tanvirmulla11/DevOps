# 🐍 Python – What, Why, How (DevOps Perspective)
## 🔹 What is Python?

### Python is a high-level, interpreted programming language that allows you to:

- Write code faster

- Read and maintain code easily

- Integrate systems and automate tasks effectively

## 🔹 Why Python?

- Simple syntax (easy for beginners)

- Large ecosystem (libraries & tools)

- Widely used in DevOps, Cloud, Automation, CI/CD

- Supported by all major platforms (Linux, Windows, macOS)

## 🔹How to Learn Python (Beginner Roadmap)
### Step 1: Learn Python Scripting

- Variables

- Data types

- Input & Output

- Conditions

- Loops

- Functions

### Step 2: Do “Magic” with Code

- Automate small tasks

- Write reusable logic

- Handle real-world scenarios (DevOps environments)

### Step 3: Run & Practice

- Run scripts multiple times

- Modify inputs

- Observe outputs
  
## 🔹 Variables & Data Types
```
env = "dev"
env = "test"
env = "prod"
```
- env is a variable
- "dev", "test", "prod" are strings

## 🔹 Python Input & Typecasting
### Important Rule
- By default, user input in Python is always a string

### Typecasting
```
Converting one data type into another is called Typecasting
```
```
env = input("Enter the environment (dev/staging/prod): ")
print(f"Selected environment: {env}")

Integer Typecasting Example
a = int(input("Enter first number: "))
b = int(input("Enter second number: "))

sum_result = a + b
print(f"The sum of {a} and {b} is: {sum_result}")
print(type(sum_result))
```
