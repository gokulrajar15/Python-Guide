# Python Loops

Loops are one of the most powerful features in programming! They allow you to repeat code multiple times without writing it over and over again. Think of them as a way to automate repetitive tasks - just like setting a timer to remind you to take a break every hour.

## What are Loops?

Imagine you need to:
- Count from 1 to 100
- Print each item in a shopping list
- Ask a user for input until they enter the correct password
- Process every student's grade in a class

Without loops, you'd have to write hundreds of lines of repetitive code. With loops, you can do all of this with just a few lines!

```python
# Without loops - Very repetitive!
print("Welcome user 1")
print("Welcome user 2") 
print("Welcome user 3")
print("Welcome user 4")
print("Welcome user 5")
# ... this would go on forever!

# With loops - Clean and efficient!
for i in range(1, 6):
    print(f"Welcome user {i}")
```

## Types of Loops in Python

Python has two main types of loops:

1. **`for` loops**: When you know how many times to repeat or when iterating through collections
2. **`while` loops**: When you want to repeat until a condition becomes False

---

## 1. For Loops

The `for` loop is perfect when you want to iterate through something (like a list, string, or range of numbers).

### Basic Syntax:
```python
for item in collection:
    # code to repeat for each item
```

### Example 1: Iterating through a list

```python
# Print each fruit in the list
fruits = ["apple", "banana", "cherry", "date"]

for fruit in fruits:
    print(f"I like {fruit}")

# Output:
# I like apple
# I like banana
# I like cherry
# I like date
```

### Example 2: Iterating through a string

```python
# Print each character in a string
name = "Python"

for letter in name:
    print(f"Letter: {letter}")

# Output:
# Letter: P
# Letter: y
# Letter: t
# Letter: h
# Letter: o
# Letter: n
```

### Example 3: Iterating through numbers with range()

```python
# Print numbers from 0 to 4
for number in range(5):
    print(f"Number: {number}")

# Output:
# Number: 0
# Number: 1
# Number: 2
# Number: 3
# Number: 4

# Print numbers from 1 to 5
for number in range(1, 6):
    print(f"Count: {number}")

# Output:
# Count: 1
# Count: 2
# Count: 3
# Count: 4
# Count: 5
```

---

## 2. The range() Function

The `range()` function is your best friend when working with `for` loops and numbers!

### Three ways to use range():

```python
# 1. range(stop) - starts at 0, stops before 'stop'
for i in range(5):
    print(i)  # Prints: 0, 1, 2, 3, 4

# 2. range(start, stop) - starts at 'start', stops before 'stop'  
for i in range(2, 8):
    print(i)  # Prints: 2, 3, 4, 5, 6, 7

# 3. range(start, stop, step) - starts at 'start', stops before 'stop', increments by 'step'
for i in range(0, 10, 2):
    print(i)  # Prints: 0, 2, 4, 6, 8

# Counting backwards
for i in range(10, 0, -1):
    print(i)  # Prints: 10, 9, 8, 7, 6, 5, 4, 3, 2, 1
```

### Practical Examples with range():

```python
# Example 1: Multiplication table
number = int(input("Enter a number: "))
print(f"\nMultiplication table for {number}:")

for i in range(1, 11):
    result = number * i
    print(f"{number} × {i} = {result}")

# Example 2: Sum of numbers
total = 0
for i in range(1, 101):
    total += i
print(f"Sum of numbers 1 to 100: {total}")

# Example 3: Countdown timer
print("Countdown starting...")
for i in range(10, 0, -1):
    print(f"{i}...")
print("🚀 Blast off!")
```

---

## 3. While Loops

The `while` loop continues running as long as a condition is True. It's perfect for situations where you don't know exactly how many times you need to loop.

### Basic Syntax:
```python
while condition:
    # code to repeat while condition is True
    # don't forget to update the condition!
```

### Example 1: Basic counting

```python
# Count from 1 to 5
counter = 1

while counter <= 5:
    print(f"Count: {counter}")
    counter += 1  # Very important! Update the counter

print("Done counting!")

# Output:
# Count: 1
# Count: 2
# Count: 3
# Count: 4
# Count: 5
# Done counting!
```

### Example 2: User input validation

```python
# Keep asking until user enters valid input
password = ""

while password != "secret123":
    password = input("Enter the password: ")
    
    if password != "secret123":
        print("Incorrect password! Try again.")
    else:
        print("Access granted!")

# This will keep running until the user enters "secret123"
```

### Example 3: Number guessing game

```python
import random

# Computer picks a random number between 1 and 10
secret_number = random.randint(1, 10)
guess = 0
attempts = 0

print("I'm thinking of a number between 1 and 10!")

while guess != secret_number:
    guess = int(input("Enter your guess: "))
    attempts += 1
    
    if guess < secret_number:
        print("Too low! Try again.")
    elif guess > secret_number:
        print("Too high! Try again.")
    else:
        print(f"🎉 Congratulations! You guessed it in {attempts} attempts!")
```

### ⚠️ **Infinite Loop Warning!**

Be very careful with while loops! If the condition never becomes False, you'll create an infinite loop:

```python
# DON'T DO THIS - Infinite loop!
counter = 1
while counter <= 5:
    print(f"Count: {counter}")
    # Missing: counter += 1
    # This will print "Count: 1" forever!

# ALWAYS make sure to update your condition variable!
counter = 1
while counter <= 5:
    print(f"Count: {counter}")
    counter += 1  # This makes the loop end eventually
```

---

## 4. Loop Control: break and continue

Sometimes you need to modify how loops behave. Python provides two special keywords:

### `break` - Exit the loop immediately

```python
# Example 1: Stop when we find what we're looking for
fruits = ["apple", "banana", "cherry", "date", "elderberry"]

for fruit in fruits:
    print(f"Checking: {fruit}")
    
    if fruit == "cherry":
        print("Found cherry! Stopping search.")
        break  # Exit the loop immediately
        
    print(f"{fruit} is not cherry")

print("Loop ended")

# Output:
# Checking: apple
# apple is not cherry
# Checking: banana
# banana is not cherry
# Checking: cherry
# Found cherry! Stopping search.
# Loop ended
```

```python
# Example 2: Password attempts with limit
attempts = 0
max_attempts = 3

while attempts < max_attempts:
    password = input("Enter password: ")
    attempts += 1
    
    if password == "secret123":
        print("Login successful!")
        break  # Exit the loop - no need to continue
    else:
        remaining = max_attempts - attempts
        if remaining > 0:
            print(f"Incorrect! {remaining} attempts remaining.")
        else:
            print("Too many failed attempts. Account locked!")
```

### `continue` - Skip the rest of this iteration and go to the next one

```python
# Example 1: Print only positive numbers
numbers = [-2, -1, 0, 1, 2, 3, 4, 5]

print("Positive numbers only:")
for number in numbers:
    if number <= 0:
        continue  # Skip negative numbers and zero
    
    print(f"Positive: {number}")

# Output:
# Positive numbers only:
# Positive: 1
# Positive: 2  
# Positive: 3
# Positive: 4
# Positive: 5
```

```python
# Example 2: Process valid student grades only
grades = [85, -5, 92, 150, 78, 88, 45, 200]

total = 0
valid_count = 0

for grade in grades:
    # Skip invalid grades (less than 0 or greater than 100)
    if grade < 0 or grade > 100:
        print(f"Skipping invalid grade: {grade}")
        continue  # Skip this iteration
    
    # Process valid grade
    total += grade
    valid_count += 1
    print(f"Valid grade: {grade}")

if valid_count > 0:
    average = total / valid_count
    print(f"\nAverage of valid grades: {average:.1f}")
```

---

## 5. Nested Loops

You can put loops inside other loops! This is called nesting and is useful for working with multi-dimensional data.

### Example 1: Multiplication table

```python
print("Multiplication Table (1-5):")
print("=" * 30)

for i in range(1, 6):      # Outer loop: rows
    for j in range(1, 6):  # Inner loop: columns
        result = i * j
        print(f"{result:3}", end=" ")  # Print with spacing
    print()  # New line after each row

# Output:
# Multiplication Table (1-5):
# ==============================
#   1   2   3   4   5 
#   2   4   6   8  10 
#   3   6   9  12  15 
#   4   8  12  16  20 
#   5  10  15  20  25
```

### Example 2: Pattern printing

```python
# Print a triangle pattern
rows = 5

for i in range(1, rows + 1):      # Outer loop: number of rows
    for j in range(i):            # Inner loop: number of stars per row
        print("*", end="")
    print()  # New line after each row

# Output:
# *
# **
# ***
# ****
# *****
```

### Example 3: Finding pairs

```python
# Find all pairs of numbers that add up to 10
target = 10
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9]

print(f"Pairs that add up to {target}:")

for i in range(len(numbers)):          # First number
    for j in range(i + 1, len(numbers)): # Second number (avoid duplicates)
        if numbers[i] + numbers[j] == target:
            print(f"{numbers[i]} + {numbers[j]} = {target}")

# Output:
# Pairs that add up to 10:
# 1 + 9 = 10
# 2 + 8 = 10
# 3 + 7 = 10
# 4 + 6 = 10
```

---

## 6. Looping with Different Data Structures

### Looping through Lists

```python
# Different ways to loop through lists
fruits = ["apple", "banana", "cherry"]

# Method 1: Direct iteration (most common)
for fruit in fruits:
    print(f"Fruit: {fruit}")

# Method 2: Using indices
for i in range(len(fruits)):
    print(f"Index {i}: {fruits[i]}")

# Method 3: Using enumerate (gets both index and item)
for index, fruit in enumerate(fruits):
    print(f"Index {index}: {fruit}")
```

### Looping through Dictionaries

```python
student_grades = {
    "Alice": 85,
    "Bob": 92, 
    "Charlie": 78,
    "Diana": 96
}

# Loop through keys only
print("Students:")
for name in student_grades:
    print(f"- {name}")

# Loop through values only
print("\nGrades:")
for grade in student_grades.values():
    print(f"- {grade}")

# Loop through both keys and values
print("\nStudent Grades:")
for name, grade in student_grades.items():
    print(f"{name}: {grade}")
    
    # Add pass/fail status
    if grade >= 60:
        print("  ✓ PASS")
    else:
        print("  ✗ FAIL")
```

### Looping through Strings

```python
message = "Hello World"

# Count vowels using a loop
vowels = "aeiouAEIOU"
vowel_count = 0

for char in message:
    if char in vowels:
        vowel_count += 1
        print(f"Found vowel: {char}")

print(f"Total vowels: {vowel_count}")
```

---

## 7. Real-World Examples

### Example 1: Grade Calculator

```python
print("=== Class Grade Calculator ===")

students = []
total_grades = 0
grade_count = 0

# Collect student data
while True:
    name = input("Enter student name (or 'done' to finish): ")
    
    if name.lower() == 'done':
        break
    
    # Get grades for this student
    student_total = 0
    subject_count = 0
    
    subjects = ["Math", "Science", "English", "History"]
    
    for subject in subjects:
        while True:
            try:
                grade = float(input(f"Enter {name}'s {subject} grade (0-100): "))
                if 0 <= grade <= 100:
                    student_total += grade
                    subject_count += 1
                    break
                else:
                    print("Grade must be between 0 and 100!")
            except ValueError:
                print("Please enter a valid number!")
    
    # Calculate student average
    student_average = student_total / subject_count
    students.append({"name": name, "average": student_average})
    
    total_grades += student_average
    grade_count += 1

# Display results
if grade_count > 0:
    print("\n=== Grade Report ===")
    print("-" * 40)
    
    for student in students:
        name = student["name"]
        avg = student["average"]
        
        # Determine letter grade
        if avg >= 90:
            letter = "A"
        elif avg >= 80:
            letter = "B"
        elif avg >= 70:
            letter = "C"
        elif avg >= 60:
            letter = "D"
        else:
            letter = "F"
        
        print(f"{name:15} | {avg:5.1f} | {letter}")
    
    # Class statistics
    class_average = total_grades / grade_count
    print("-" * 40)
    print(f"Class Average: {class_average:.1f}")
    
    # Find highest and lowest performers
    highest = max(students, key=lambda x: x["average"])
    lowest = min(students, key=lambda x: x["average"])
    
    print(f"Highest: {highest['name']} ({highest['average']:.1f})")
    print(f"Lowest: {lowest['name']} ({lowest['average']:.1f})")
```

### Example 2: Simple Shopping Cart

```python
print("=== Shopping Cart ===")

cart = []
prices = {
    "apple": 1.50,
    "banana": 0.75,
    "bread": 2.25,
    "milk": 3.50,
    "eggs": 2.75,
    "cheese": 4.00
}

print("Available items:")
for item, price in prices.items():
    print(f"- {item.title()}: ${price:.2f}")

# Shopping loop
while True:
    print(f"\nCurrent cart: {len(cart)} items")
    
    action = input("\nWhat would you like to do? (add/remove/view/checkout/quit): ").lower()
    
    if action == "add":
        item = input("Enter item name: ").lower()
        
        if item in prices:
            quantity = int(input(f"How many {item}s? "))
            
            # Add items to cart
            for _ in range(quantity):
                cart.append(item)
            
            print(f"Added {quantity} {item}(s) to cart!")
        else:
            print("Sorry, we don't have that item.")
            
    elif action == "remove":
        if not cart:
            print("Cart is empty!")
            continue
            
        item = input("Remove which item? ").lower()
        
        if item in cart:
            cart.remove(item)  # Remove one instance
            print(f"Removed {item} from cart!")
        else:
            print("That item is not in your cart.")
            
    elif action == "view":
        if not cart:
            print("Your cart is empty!")
        else:
            print("\nYour cart:")
            
            # Count items in cart
            item_counts = {}
            for item in cart:
                item_counts[item] = item_counts.get(item, 0) + 1
            
            total = 0
            for item, count in item_counts.items():
                price = prices[item]
                item_total = price * count
                total += item_total
                print(f"- {item.title()}: {count} × ${price:.2f} = ${item_total:.2f}")
            
            print(f"\nTotal: ${total:.2f}")
            
    elif action == "checkout":
        if not cart:
            print("Your cart is empty!")
            continue
            
        print("\n=== CHECKOUT ===")
        
        # Calculate final total
        item_counts = {}
        for item in cart:
            item_counts[item] = item_counts.get(item, 0) + 1
        
        total = 0
        print("Final Receipt:")
        print("-" * 30)
        
        for item, count in item_counts.items():
            price = prices[item]
            item_total = price * count
            total += item_total
            print(f"{item.title():12} {count:2} × ${price:5.2f} = ${item_total:6.2f}")
        
        print("-" * 30)
        print(f"{'TOTAL':>26} ${total:6.2f}")
        
        print(f"\nThank you for shopping! Your total is ${total:.2f}")
        break
        
    elif action == "quit":
        print("Thanks for visiting!")
        break
        
    else:
        print("Invalid action! Try: add, remove, view, checkout, or quit")
```

### Example 3: Password Generator

```python
import random

print("=== Secure Password Generator ===")

# Character sets
lowercase = "abcdefghijklmnopqrstuvwxyz"
uppercase = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
digits = "0123456789"
symbols = "!@#$%^&*"

while True:
    # Get user preferences
    length = int(input("Password length (8-50): "))
    
    if length < 8 or length > 50:
        print("Length must be between 8 and 50!")
        continue
    
    use_uppercase = input("Include uppercase letters? (y/n): ").lower() == 'y'
    use_digits = input("Include numbers? (y/n): ").lower() == 'y'
    use_symbols = input("Include symbols? (y/n): ").lower() == 'y'
    
    # Build character set
    char_set = lowercase  # Always include lowercase
    
    if use_uppercase:
        char_set += uppercase
    if use_digits:
        char_set += digits
    if use_symbols:
        char_set += symbols
    
    # Generate password
    password = ""
    
    for _ in range(length):
        password += random.choice(char_set)
    
    # Analyze password strength
    score = 0
    feedback = []
    
    if len(password) >= 12:
        score += 2
        feedback.append("✓ Good length")
    elif len(password) >= 8:
        score += 1
        feedback.append("⚠ Minimum length")
    
    # Check character types
    has_lower = any(c in lowercase for c in password)
    has_upper = any(c in uppercase for c in password)
    has_digit = any(c in digits for c in password)
    has_symbol = any(c in symbols for c in password)
    
    if has_lower: score += 1
    if has_upper: score += 1
    if has_digit: score += 1
    if has_symbol: score += 1
    
    # Display results
    print(f"\n=== Generated Password ===")
    print(f"Password: {password}")
    print(f"Length: {len(password)} characters")
    
    # Strength assessment
    if score >= 6:
        strength = "Very Strong 🟢"
    elif score >= 4:
        strength = "Strong 🟡"
    elif score >= 3:
        strength = "Medium 🟠"
    else:
        strength = "Weak 🔴"
    
    print(f"Strength: {strength}")
    
    # Generate another?
    again = input("\nGenerate another password? (y/n): ").lower()
    if again != 'y':
        break

print("Thanks for using Password Generator!")
```

---

## 8. Common Mistakes and Best Practices

### Mistake 1: Infinite While Loops

```python
# Wrong - This will run forever!
count = 0
while count < 5:
    print(f"Count: {count}")
    # Missing: count += 1

# Correct - Always update your condition variable
count = 0
while count < 5:
    print(f"Count: {count}")
    count += 1  # Don't forget this!
```

### Mistake 2: Off-by-One Errors

```python
# Be careful with range boundaries
numbers = [10, 20, 30, 40, 50]

# Wrong - This will cause an IndexError
for i in range(len(numbers) + 1):  # Goes one too far!
    print(numbers[i])

# Correct - Use the exact length
for i in range(len(numbers)):
    print(numbers[i])

# Even better - Direct iteration
for number in numbers:
    print(number)
```

### Mistake 3: Modifying a List While Iterating

```python
numbers = [1, 2, 3, 4, 5]

# Wrong - Modifying list while iterating can cause issues
for num in numbers:
    if num % 2 == 0:
        numbers.remove(num)  # Don't do this!

# Correct - Create a new list or iterate backwards
numbers = [1, 2, 3, 4, 5]
odd_numbers = []
for num in numbers:
    if num % 2 == 1:
        odd_numbers.append(num)

print(odd_numbers)  # [1, 3, 5]
```

### Best Practices:

1. **Use descriptive variable names**
```python
# Poor
for i in students:
    print(i)

# Better
for student in students:
    print(student)
```

2. **Choose the right loop type**
```python
# Use for loops when iterating through collections
for item in shopping_list:
    print(item)

# Use while loops for unknown iterations
while user_input != "quit":
    user_input = input("Enter command: ")
```

3. **Keep loops simple and readable**
```python
# Complex nested loop - hard to read
for i in range(len(matrix)):
    for j in range(len(matrix[i])):
        for k in range(len(matrix[i][j])):
            if matrix[i][j][k] > 0:
                matrix[i][j][k] = matrix[i][j][k] * 2

# Better - break into functions or use descriptive names
for row_index, row in enumerate(matrix):
    for col_index, cell in enumerate(row):
        for value_index, value in enumerate(cell):
            if value > 0:
                matrix[row_index][col_index][value_index] = value * 2
```

---

## 9. Practice Exercises

### Exercise 1: Number Analysis
Write a program that:
1. Asks the user for 10 numbers
2. Counts how many are positive, negative, and zero
3. Finds the largest and smallest numbers
4. Calculates the average

```python
# Your code here
print("=== Number Analysis ===")
print("Please enter 10 numbers:")

numbers = []

# Collect 10 numbers

# Analyze the numbers

# Display results

# Expected output format:
# You entered: [1, -2, 0, 5, -1, 8, 0, 3, -4, 7]
# Positive numbers: 5
# Negative numbers: 3  
# Zero count: 2
# Largest number: 8
# Smallest number: -4
# Average: 1.7
```

### Exercise 2: Pattern Generator
Create a program that generates various patterns based on user input:

```python
# Your code here
print("=== Pattern Generator ===")

# Pattern 1: Right Triangle
# *
# **
# ***
# ****
# *****

# Pattern 2: Inverted Triangle  
# *****
# ****
# ***
# **
# *

# Pattern 3: Diamond (challenging!)
#   *
#  ***
# *****
#  ***
#   *

# Ask user which pattern they want and how many rows
```

### Exercise 3: Word Game
Create a word guessing game:
1. Create a list of words
2. Computer randomly selects one
3. Show blanks for each letter
4. User guesses letters one at a time
5. Track correct and incorrect guesses
6. End when word is guessed or too many wrong guesses

```python
# Your code here
import random

print("=== Word Guessing Game ===")

words = ["python", "computer", "programming", "challenge", "learning"]

# Select random word

# Initialize game variables

# Main game loop

# Expected interaction:
# Word: _ _ _ _ _ _
# Guess a letter: p
# Good guess! Word: p _ _ _ _ _
# Guess a letter: x  
# Wrong! Tries left: 5
# ... continue until word is guessed or no tries left
```

### Exercise 4: Prime Number Finder
Write a program that finds all prime numbers up to a given limit:

```python
# Your code here
print("=== Prime Number Finder ===")

# Get limit from user
limit = int(input("Find primes up to: "))

# Find all prime numbers up to the limit
primes = []

# A prime number is only divisible by 1 and itself
# Test each number from 2 to limit

# Display results

# Expected output for limit = 20:
# Prime numbers up to 20: [2, 3, 5, 7, 11, 13, 17, 19]
# Found 8 prime numbers
```

### Exercise 5: Text Statistics
Create a program that analyzes text input and provides statistics:

```python
# Your code here
print("=== Text Statistics ===")

text = input("Enter some text: ")

# Count different things using loops:
# - Total characters (including spaces)
# - Total characters (excluding spaces)  
# - Total words
# - Total sentences (count . ! ?)
# - Most common letter
# - Vowel count

# Display all statistics

# Expected output for "Hello World!":
# Text: Hello World!
# Characters (with spaces): 12
# Characters (without spaces): 10
# Words: 2
# Sentences: 1  
# Vowels: 3 (e, o, o)
# Most common letter: l (appears 3 times)
```

### Exercise 6: Simple Calculator with History
Build a calculator that:
1. Shows a menu of operations
2. Performs calculations 
3. Keeps a history of all calculations
4. Allows user to view history
5. Continues until user quits

```python
# Your code here
print("=== Calculator with History ===")

history = []

# Main calculator loop

# Menu options:
# 1. Addition
# 2. Subtraction  
# 3. Multiplication
# 4. Division
# 5. View History
# 6. Clear History
# 7. Exit

# Keep track of all calculations in history list
# Format: "5 + 3 = 8"
```

---

## Solutions (Try the exercises first!)

<details>
<summary>Click to see Exercise 1 Solution</summary>

```python
# Exercise 1: Number Analysis Solution
print("=== Number Analysis ===")
print("Please enter 10 numbers:")

numbers = []
positive_count = 0
negative_count = 0
zero_count = 0

# Collect 10 numbers
for i in range(10):
    num = float(input(f"Number {i+1}: "))
    numbers.append(num)
    
    # Count positive/negative/zero
    if num > 0:
        positive_count += 1
    elif num < 0:
        negative_count += 1
    else:
        zero_count += 1

# Find largest and smallest
largest = numbers[0]
smallest = numbers[0]

for num in numbers:
    if num > largest:
        largest = num
    if num < smallest:
        smallest = num

# Calculate average
total = 0
for num in numbers:
    total += num
average = total / len(numbers)

# Display results
print(f"\nYou entered: {numbers}")
print(f"Positive numbers: {positive_count}")
print(f"Negative numbers: {negative_count}")
print(f"Zero count: {zero_count}")
print(f"Largest number: {largest}")
print(f"Smallest number: {smallest}")
print(f"Average: {average:.1f}")
```
</details>

<details>
<summary>Click to see Exercise 2 Solution</summary>

```python
# Exercise 2: Pattern Generator Solution
print("=== Pattern Generator ===")

while True:
    print("\nAvailable patterns:")
    print("1. Right Triangle")
    print("2. Inverted Triangle")
    print("3. Diamond")
    print("4. Exit")
    
    choice = input("Choose a pattern (1-4): ")
    
    if choice == "4":
        break
    
    rows = int(input("How many rows? "))
    
    if choice == "1":
        # Right Triangle
        for i in range(1, rows + 1):
            for j in range(i):
                print("*", end="")
            print()
    
    elif choice == "2":
        # Inverted Triangle
        for i in range(rows, 0, -1):
            for j in range(i):
                print("*", end="")
            print()
    
    elif choice == "3":
        # Diamond
        # Top half (including middle)
        for i in range(1, rows + 1):
            # Print spaces
            for j in range(rows - i):
                print(" ", end="")
            # Print stars
            for j in range(2 * i - 1):
                print("*", end="")
            print()
        
        # Bottom half
        for i in range(rows - 1, 0, -1):
            # Print spaces
            for j in range(rows - i):
                print(" ", end="")
            # Print stars
            for j in range(2 * i - 1):
                print("*", end="")
            print()
    
    else:
        print("Invalid choice!")
```
</details>

<details>
<summary>Click to see Exercise 3 Solution</summary>

```python
# Exercise 3: Word Game Solution
import random

print("=== Word Guessing Game ===")

words = ["python", "computer", "programming", "challenge", "learning"]
word = random.choice(words)
guessed_letters = []
wrong_guesses = []
max_tries = 6

print("Guess the word!")

while True:
    # Display current progress
    display = ""
    for letter in word:
        if letter in guessed_letters:
            display += letter + " "
        else:
            display += "_ "
    
    print(f"\nWord: {display}")
    print(f"Wrong guesses: {wrong_guesses}")
    print(f"Tries left: {max_tries - len(wrong_guesses)}")
    
    # Check win condition
    if all(letter in guessed_letters for letter in word):
        print(f"🎉 Congratulations! You guessed '{word}'!")
        break
    
    # Check lose condition
    if len(wrong_guesses) >= max_tries:
        print(f"😞 Game over! The word was '{word}'")
        break
    
    # Get user guess
    guess = input("Guess a letter: ").lower()
    
    # Validate input
    if len(guess) != 1 or not guess.isalpha():
        print("Please enter a single letter!")
        continue
    
    if guess in guessed_letters or guess in wrong_guesses:
        print("You already guessed that letter!")
        continue
    
    # Check if guess is correct
    if guess in word:
        guessed_letters.append(guess)
        print("Good guess!")
    else:
        wrong_guesses.append(guess)
        print("Wrong letter!")
```
</details>

---

## Summary

In this comprehensive guide, you learned about Python loops:

- ✅ **`for` loops** for iterating through collections and known ranges
- ✅ **`while` loops** for repeating until conditions change  
- ✅ **`range()` function** for generating number sequences
- ✅ **Loop control** with `break` and `continue` statements
- ✅ **Nested loops** for multi-dimensional problems
- ✅ **Real-world applications** including games, calculators, and data analysis
- ✅ **Common mistakes** and best practices to write clean loop code
- ✅ **Data structure iteration** with lists, dictionaries, and strings

### Key Takeaways:
- **Choose the right loop**: `for` when you know the collection, `while` for conditions
- **Avoid infinite loops**: Always update condition variables in `while` loops
- **Use descriptive names**: Make your loop variables meaningful
- **Break complex loops**: Split complicated logic into smaller functions
- **Practice with real projects**: The best way to master loops is through practice

### Next Steps:
- Practice with the exercises to reinforce your understanding
- Try combining loops with conditional statements for more complex logic
- Experiment with different data structures and loop patterns
- Start thinking about how loops can solve everyday programming problems

**Next:** Continue to learn about Functions to organize and reuse your code effectively!