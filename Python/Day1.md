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
## 🔹 Environments in DevOps
| Environment | Purpose                                                |
| ----------- | ------------------------------------------------------ |
| **Dev**     | Developers test new features                           |
| **Staging** | Pre-release testing                                    |
| **Prod**    | Final live release (freshers usually don’t get access) |

## 🔹 Conditional Statements (if–elif–else)
```
env = input("Enter the environment (dev/staging/prod): ")

if env == "prod":
    print("Don't deploy on production")
elif env == "staging":
    print("Take extra caution while deploying on staging")
else:
    print("Safe to deploy")
```

## 🔹 Operators in Python
| Operator | Meaning               |
| -------- | --------------------- |
| `=`      | Assignment            |
| `==`     | Equality              |
| `!=`     | Not equal             |
| `>=`     | Greater than or equal |
| `<=`     | Less than or equal    |

## 🔹 Loops in Python
- for Loop Structure
 ```
for i in range(5):
    print(i)
```

### Explanation
```
for → loop
i → variable
in → flow control
range(5) → runs from 0 to 4
```
### Multiplication Table Example
```
num = int(input("Enter a number: "))

for i in range(1, 11):
    product = num * i
    print(f"{num} x {i} = {product}")
```

## 🔹 while Loop Example
```
choice = input("Enter your choice : ")

while choice != "q":
    num = int(input("Enter a number: "))

    for i in range(1, 11):
        print(f"{num} x {i} = {num * i}")

    choice = input("Enter your choice : ")
```
## 🔹 Functions in Python
### Why Functions?
- Reusability
- Clean code
- Better automation
### Example:
```
def sum_of_numbers():
    num1 = int(input("Enter first number: "))
    num2 = int(input("Enter second number: "))
    total = num1 + num2
    print(total)
```
- Calling Function Based on Environment
```
env = input("Enter the environment (dev/staging/prod): ")

if env == "prod":
    sum_of_numbers()
```
## 🔹 PyPI (Python Package Index)
- Official platform for Python libraries
- Website: pypi.org
  -You can:
    - Install others’ libraries
    - Publish your own library
### Example:
```
pip install requests
```


