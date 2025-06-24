# Basic Hello World and Date Script
#!/bin/bash

echo "Hello, Connections!"
date
```bash
# Example Script with Variables
#!/bin/bash

name="Tanvir Mulla"
age=21

echo "My name is $name"
echo "I am $age years old"
```bash
# Taking user input for a variable
read username
echo "Welcome, $username!"
```bash
# Script with Comments
#!/bin/bash

# This script greets the user

name="Tanvir Mulla" # Storing name

echo "Hello, $name" # Printing greeting
```bash
# If-Else Example Script
#!/bin/bash

echo "Enter your age:"
read age

if [ "$age" -ge 18 ]
then
    echo "You are an adult."
else
    echo "You are a minor."
fi
```bash
# Elif (Else If) Example Script
#!/bin/bash

echo "Enter your marks:"
read marks

if [ "$marks" -ge 90 ]
then
    echo "Grade: A+"
elif [ "$marks" -ge 75 ]
then
    echo "Grade: A"
elif [ "$marks" -ge 60 ]
then
    echo "Grade: B"
else
    echo "Grade: C or below"
fi
```bash
# For Loop Example Script
#!/bin/bash

for i in 1 2 3 4 5
do
    echo "Number: $i"
done
```bash
# While Loop Example Script
#!/bin/bash

count=1

while [ "$count" -le 5 ]
do
    echo "Count is: $count"
    count=$((count + 1))
done
```bash
# Until Loop Example Script
#!/bin/bash

x=1
until [ "$x" -gt 5 ]
do
    echo "x is: $x"
    x=$((x + 1))
done
```bash
# Basic Function Example
#!/bin/bash

greet() {
    echo "Hello, Connections!"
}

greet # Calling the function
```bash
# Function with Arguments Example
say_hello() {
    echo "Hello, $1!"
}

say_hello "Tanvir"
```bash
# Array Declaration
fruits=("apple" "banana" "cherry")
```bash
# Access Array elements
echo ${fruits[0]} # apple
echo ${fruits[1]} # banana
```bash
# Length of Array
echo ${#fruits[@]} # 3
```bash
# Loop Through Array
for fruit in "${fruits[@]}"
do
    echo "$fruit"
done
```bash
# Add elements to Array
fruits+=("orange")
```bash
# Remove elements from Array (using unset)
unset fruits[1] # removes banana
```bash
# String Declaration
name="Tanvir"
echo "Hello, $name"
```bash
# String with spaces
greet="Hello World"
echo "$greet"
```bash
# String Length
echo ${#name} # 6
```bash
# String Concatenation
full="$name is learning Shell"
echo "$full"
```bash
# Compare Strings
if [ "$name" == "Tanvir" ]; then
    echo "Match!"
fi
```bash
# Substring Extraction
str="DevOpsRocks"
echo ${str:0:6} # DevOps
echo ${str:6:5} # Rocks
```bash
# Extract Substring till end
echo ${str:6} # From index 6 to end → Rocks
```bash
# Negative indexing for last characters
echo ${str: -2} # ks (space after `:` is required!)
```bash
# File Handling: Reading a File Line by Line
#!/bin/bash
filename="file.txt"
while read line
do
    echo "Line: $line"
done < "$filename"
```bash
# File Handling: Writing to a File (Overwrites)
echo "This is a new line" > output.txt
# Overwrites the file
```bash
# File Handling: Appending to a File
echo "Another line" >> output.txt
# Adds to the end without deleting existing content.
```bash
# File Handling: Checking if File Exists
if [ -f "file.txt" ]; then
    echo "File exists"
else
    echo "File not found"
fi
