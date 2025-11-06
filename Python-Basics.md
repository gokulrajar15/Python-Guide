# Python Basics

Welcome to Python Basics! This guide will teach you the fundamental concepts of Python programming with simple examples.

## Variables

Variables are like containers that store data. Think of them as labeled boxes where you can put different things.

### Creating Variables

```python
# Creating variables
name = "Alice"          # String (text)
age = 25               # Integer (whole number)
height = 5.6           # Float (decimal number)
is_student = True      # Boolean (True/False)

# Print the variables
print(name)
print(age)
print(height)
print(is_student)
```

### Variable Rules
- Variable names can contain letters, numbers, and underscores
- Cannot start with a number
- Case sensitive (`name` and `Name` are different)
- Use descriptive names

```python
# Good variable names
first_name = "John"
user_age = 30
total_score = 95

# Avoid these
x = "John"        # Not descriptive
2name = "John"    # Starts with number (ERROR!)
```

## Data Types

Python has several built-in data types. Here are the most common ones:

### 1. Integer (int)
Whole numbers without decimal points.

```python
# Integer examples
score = 100
temperature = -5
year = 2024

print(type(score))  # Output: <class 'int'>
```

### 2. Float (float)
Numbers with decimal points.

```python
# Float examples
price = 19.99
pi = 3.14159
weight = 65.5

print(type(price))  # Output: <class 'float'>
```

### 3. String (str)
Text data enclosed in quotes.

```python
# String examples
message = "Hello, World!"
city = 'New York'
address = """123 Main Street
Apartment 4B"""

print(type(message))  # Output: <class 'str'>
```

### 4. Boolean (bool)
True or False values.

```python
# Boolean examples
is_sunny = True
is_raining = False
has_homework = True

print(type(is_sunny))  # Output: <class 'bool'>
```

### Checking Data Types

```python
# Using type() function
name = "Python"
age = 30

print(f"{name} is of type: {type(name)}")
print(f"{age} is of type: {type(age)}")
```

## Input and Output

### Output with print()
The `print()` function displays information to the user.

```python
# Basic printing
print("Hello, World!")
print("Welcome to Python!")

# Printing variables
name = "Sarah"
age = 22
print(name)
print(age)

# Printing multiple items
print("My name is", name, "and I am", age, "years old")

# Using f-strings (recommended for formatting)
print(f"My name is {name} and I am {age} years old")
```

### Input with input()
The `input()` function gets information from the user.

```python
# Getting user input
name = input("What is your name? ")
print(f"Hello, {name}!")

# Note: input() always returns a string
age_str = input("How old are you? ")
print(f"You entered: {age_str}")
print(f"Type: {type(age_str)}")

# Converting input to numbers
age = int(input("Enter your age: "))
height = float(input("Enter your height in feet: "))

print(f"Age: {age}, Type: {type(age)}")
print(f"Height: {height}, Type: {type(height)}")
```

## Type Conversion

Sometimes you need to convert between different data types.

```python
# String to Integer
age_str = "25"
age_int = int(age_str)
print(f"String: {age_str}, Integer: {age_int}")

# String to Float
price_str = "19.99"
price_float = float(price_str)
print(f"String: {price_str}, Float: {price_float}")

# Integer to String
score = 95
score_str = str(score)
print(f"Integer: {score}, String: '{score_str}'")

# Float to Integer (removes decimal part)
pi = 3.14159
pi_int = int(pi)
print(f"Float: {pi}, Integer: {pi_int}")
```

## Practical Examples

### Example 1: Personal Information
```python
# Getting personal information
print("=== Personal Information ===")
name = input("Enter your name: ")
age = int(input("Enter your age: "))
city = input("Enter your city: ")

print(f"\nHello {name}!")
print(f"You are {age} years old")
print(f"You live in {city}")
```

### Example 2: Simple Calculator
```python
# Simple addition calculator
print("=== Simple Calculator ===")
num1 = float(input("Enter first number: "))
num2 = float(input("Enter second number: "))

result = num1 + num2
print(f"{num1} + {num2} = {result}")
```

### Example 3: Temperature Converter
```python
# Celsius to Fahrenheit converter
print("=== Temperature Converter ===")
celsius = float(input("Enter temperature in Celsius: "))
fahrenheit = (celsius * 9/5) + 32

print(f"{celsius}°C = {fahrenheit}°F")
```

### Example 4: Age Calculator
```python
# Calculate age from birth year
print("=== Age Calculator ===")
current_year = 2024
birth_year = int(input("Enter your birth year: "))

age = current_year - birth_year
print(f"You are approximately {age} years old")
```

## Common Mistakes to Avoid

### 1. Forgetting to convert input()
```python
# Wrong way
age = input("Enter your age: ")
next_year = age + 1  # ERROR! Can't add string and integer

# Correct way
age = int(input("Enter your age: "))
next_year = age + 1
print(f"Next year you'll be {next_year}")
```

### 2. Using undefined variables
```python
# Wrong way
print(username)  # ERROR! username is not defined

# Correct way
username = "john_doe"
print(username)
```

### 3. Mixing data types incorrectly
```python
# Be careful with mixing types
name = "Alice"
age = 25

# Wrong way
message = name + age  # ERROR! Can't add string and integer

# Correct ways
message1 = name + str(age)  # Convert number to string
message2 = f"{name} is {age} years old"  # Use f-string
```

## Practice Exercises

Try these exercises to practice what you've learned:

### Exercise 1: Student Information
Create a program that:
1. Asks for student's name
2. Asks for student's grade (as a number)
3. Asks if they have homework (True/False)
4. Prints all information in a formatted way

### Exercise 2: Shopping Calculator
Create a program that:
1. Asks for item price
2. Asks for quantity
3. Calculates total cost
4. Displays the result

### Exercise 3: BMI Calculator
Create a program that:
1. Asks for weight in kg
2. Asks for height in meters
3. Calculates BMI (weight / height²)
4. Displays the BMI value

## Summary

In this section, you learned:
- ✅ How to create and use variables
- ✅ The main data types: int, float, string, boolean
- ✅ How to get input from users with `input()`
- ✅ How to display output with `print()`
- ✅ How to convert between different data types
- ✅ Common mistakes to avoid

**Next:** Continue to learn about Operators to perform calculations and comparisons!