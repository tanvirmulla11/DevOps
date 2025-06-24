# 1. Basic Hello World and Date Script (from Page 2)
# Description: A simple script to print a greeting and the current date.
#!/bin/bash

echo "Hello, Connections!"
date

# ---
# 2. Example Script with Variables (from Page 6)
# Description: Demonstrates declaring and using variables, and taking user input.
#!/bin/bash

name="Tanvir Mulla"
age=21

echo "My name is $name"
echo "I am $age years old"

# You can even take input like this:
# read username
# echo "Welcome, $username!"

# ---
# 3. Script with Comments (from Page 7)
# Description: Shows how to use comments in shell scripts for explanations.
#!/bin/bash

# This script greets the user

name="Tanvir Mulla" # Storing name

echo "Hello, $name" # Printing greeting

# ---
# 4. If-Else Example Script (from Page 8)
# Description: Demonstrates conditional logic using if-else to check age.
#!/bin/bash

echo "Enter your age:"
read age

if [ "$age" -ge 18 ]; then
  echo "You are an adult."
else
  echo "You are a minor."
fi

# ---
# 5. Elif (Else If) Example Script (from Page 9)
# Description: Shows how to use elif for multiple conditions (e.g., grading system).
#!/bin/bash

echo "Enter your marks:"
read marks

if [ "$marks" -ge 90 ]; then
  echo "Grade: A+"
elif [ "$marks" -ge 75 ]; then
  echo "Grade: A"
elif [ "$marks" -ge 60 ]; then
  echo "Grade: B"
else
  echo "Grade: C or below"
fi

# ---
# 6. For Loop Example Script (from Page 10)
# Description: Iterates through a fixed list of numbers using a for loop.
#!/bin/bash

for i in 1 2 3 4 5; do
  echo "Number: $i"
done

# ---
# 7. While Loop Example Script (from Page 10)
# Description: Repeats a block of code while a condition remains true.
#!/bin/bash

count=1
while [ "$count" -le 5 ]; do
  echo "Count is: $count"
  count=$((count + 1))
done

# ---
# 8. Until Loop Example Script (from Page 11)
# Description: Repeats a block of code until a condition becomes true.
#!/bin/bash

x=1
until [ "$x" -gt 5 ]; do
  echo "x is: $x"
  x=$((x + 1))
done

# ---
# 9. Basic Function Example (from Page 12)
# Description: Defines and calls a simple function without arguments.
#!/bin/bash

greet() {
  echo "Hello, Connections!"
}

greet # Calling the function

# ---
# 10. Function with Arguments Example (from Page 12)
# Description: Defines and calls a function that accepts an argument.
#!/bin/bash

say_hello() {
  echo "Hello, $1!"
}

say_hello "Tanvir" # Calling the function with an argument

# ---
# 11. Array Declaration and Access (from Page 13)
# Description: Demonstrates how to declare an array and access its elements.
#!/bin/bash

fruits=("apple" "banana" "cherry")

echo "First fruit: ${fruits[0]}" # apple
echo "Second fruit: ${fruits[1]}" # banana

# ---
# 12. Array Length and Looping (from Page 13)
# Description: Shows how to get the length of an array and loop through its elements.
#!/bin/bash

fruits=("apple" "banana" "cherry")

echo "Number of fruits: ${#fruits[@]}" # 3

echo "Looping through fruits:"
for fruit in "${fruits[@]}"; do
  echo "$fruit"
done

# ---
# 13. Adding and Removing Array Elements (from Page 13-14)
# Description: Demonstrates adding an element and removing an element using unset.
#!/bin/bash

fruits=("apple" "banana" "cherry")
echo "Original: ${fruits[@]}"

# Add element
fruits+=("orange")
echo "After adding: ${fruits[@]}"

# Remove element (by index)
unset fruits[1] # removes banana
echo "After removing 'banana': ${fruits[@]}"

# ---
# 14. String Declaration and Concatenation (from Page 14-15)
# Description: Basic string usage, including strings with spaces and concatenation.
#!/bin/bash

name="Tanvir"
echo "Hello, $name"

# String with spaces (always use quotes)
greet="Hello World"
echo "$greet"

# Concatenation
full="$name is learning Shell"
echo "$full"

# ---
# 15. Comparing Strings (from Page 15)
# Description: Demonstrates how to compare two strings using if-else.
#!/bin/bash

name="Tanvir"

if [ "$name" == "Tanvir" ]; then
  echo "Match!"
else
  echo "No match."
fi

# ---
# 16. Substring Extraction (from Page 16)
# Description: Extracts parts of a string using position and length.
#!/bin/bash

str="DevOpsRocks"

echo "Substring from index 0, length 6: ${str:0:6}" # DevOps
echo "Substring from index 6, length 5: ${str:6:5}" # Rocks
echo "Substring from index 6 to end: ${str:6}"      # Rocks

# Want last 2 chars? (space after ':' is required!)
echo "Last 2 characters: ${str: -2}" # ks

# ---
# 17. File Handling: Reading Line by Line (from Page 17)
# Description: Reads the content of a file line by line.
#!/bin/bash

# Create a dummy file for this example
echo -e "Hello\nWorld\nTanvir" > file.txt

filename="file.txt"
echo "Reading file '$filename' line by line:"
while read line; do
  echo "Line: $line"
done < "$filename"

# Clean up dummy file
rm file.txt

# ---
# 18. File Handling: Writing and Appending (from Page 17)
# Description: Demonstrates overwriting and appending content to a file.
#!/bin/bash

echo "Writing to output.txt (overwrites existing content):"
echo "This is a new line" > output.txt
cat output.txt

echo -e "\nAppending to output.txt:"
echo "Another line" >> output.txt
cat output.txt

# Clean up dummy file
rm output.txt

# ---
# 19. File Handling: Checking if File Exists (from Page 17)
# Description: Checks if a specified file exists.
#!/bin/bash

echo "Checking if file.txt exists:"
if [ -f "file.txt" ]; then
  echo "File exists"
else
  echo "File not found"
fi

# Create a dummy file for the next check
touch existing_file.txt
echo "Checking if existing_file.txt exists:"
if [ -f "existing_file.txt" ]; then
  echo "File exists"
else
  echo "File not found"
fi

# Clean up dummy file
rm existing_file.txt
