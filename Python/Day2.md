# 🐍 Day 2 – Python Fundamentals

This document covers **Day 2 of Python learning**, focusing on **Virtual Environments** and **Python Data Structures**, specifically the **List** data structure.  
All examples are written clearly for beginners and practical understanding.

---

## 🔹 Virtual Environment in Python

A **virtual environment** is used to create an isolated Python workspace.  
It helps manage dependencies separately for each project and avoids version conflicts.

### 📌 Commands Used

```bash
python -m venv venv
.\venv\Scripts\activate.bat
deactivate
```
- python -m venv venv → Creates a virtual environment named venv

- activate.bat → Activates the environment (Windows)

- deactivate → Exits the virtual environment

## 🔹 Python Data Structures

### Python provides four main built-in data structures:

- List

- Dictionary

- Set

- Tuple

This session focuses on the List data structure.

## 📘 List Data Structure

### A List is:

- Ordered

- Mutable (can be modified)

- Can store multiple data types

## 🧪 Complete Python Code (Single File)
```
# First Way: Creating a List
a = [100, 200, 300, True, 4.6]
print("Type of a:", type(a))

a.append(500)
print("Updated list a:", a)

print("-" * 40)

# Second Way: Creating a List using list()
clouds = list()
clouds.append("aws")
clouds.append("azure")
clouds.append("GCP")

print("Type of clouds:", type(clouds))
print("Cloud list:", clouds)

print("Length of List is:", len(clouds))
print("World leader cloud service provider is:", clouds[0])
print("Indian cloud service provider is:", clouds[-1])

print("-" * 40)

# Exploring List Methods
print("List methods available:")
print(dir(clouds))

print("-" * 40)

# Documentation of extend() method
print("Documentation of extend() method:")
print(clouds.extend.__doc__)
```
