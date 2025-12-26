# Python Functions

Functions are like little machines in your code that take inputs, do something useful with them, and often give you back a result. Think of them as reusable pieces of code that help you organize your program and avoid repeating yourself!

## What are Functions?

Imagine you're cooking and you keep making sandwiches. Instead of writing down the sandwich-making steps every single time, you create a "recipe" (function) that you can follow whenever you want to make a sandwich. Functions work the same way in programming!

```python
# Without functions - lots of repetitive code
name1 = "Alice"
print(f"Hello, {name1}!")
print(f"Welcome to our program, {name1}!")
print(f"Have a great day, {name1}!")

name2 = "Bob"
print(f"Hello, {name2}!")
print(f"Welcome to our program, {name2}!")
print(f"Have a great day, {name2}!")

# With functions - clean and reusable
def greet_user(name):
    print(f"Hello, {name}!")
    print(f"Welcome to our program, {name}!")
    print(f"Have a great day, {name}!")

greet_user("Alice")
greet_user("Bob")
```

## Benefits of Functions

- **Reusability**: Write once, use many times
- **Organization**: Keep your code neat and organized
- **Easier debugging**: Fix bugs in one place
- **Readability**: Make code easier to understand
- **Modularity**: Break big problems into smaller pieces

---

## 1. Defining and Calling Functions

### Basic Syntax:
```python
def function_name():
    # code to execute when function is called
    pass  # placeholder - does nothing
```

### Example 1: Simple function with no parameters

```python
# Define the function
def say_hello():
    print("Hello, World!")
    print("Welcome to Python functions!")

# Call the function
say_hello()  # Don't forget the parentheses!

# Output:
# Hello, World!
# Welcome to Python functions!

# You can call it multiple times
say_hello()
say_hello()
```

### Example 2: Functions that perform tasks

```python
# Function to draw a line
def draw_line():
    print("=" * 40)

# Function to display menu
def show_menu():
    draw_line()
    print("1. Add numbers")
    print("2. Subtract numbers") 
    print("3. Exit")
    draw_line()

# Using the functions
print("Welcome to Calculator!")
show_menu()

# Output:
# Welcome to Calculator!
# ========================================
# 1. Add numbers
# 2. Subtract numbers
# 3. Exit
# ========================================
```

### Example 3: Functions with loops

```python
# Function to count to a number
def count_to_ten():
    print("Counting to 10:")
    for i in range(1, 11):
        print(f"{i}...")
    print("Done!")

# Function to display multiplication table
def times_table_five():
    print("5 Times Table:")
    for i in range(1, 11):
        result = 5 * i
        print(f"5 × {i} = {result}")

# Using the functions
count_to_ten()
print()
times_table_five()
```

---

## 2. Functions with Parameters

Parameters allow you to pass information into functions, making them more flexible and powerful!

### Basic Syntax:
```python
def function_name(parameter1, parameter2):
    # code that uses the parameters
    pass
```

### Example 1: Function with one parameter

```python
# Function that greets a specific person
def greet_person(name):
    print(f"Hello, {name}!")
    print(f"Nice to meet you, {name}!")

# Call with different names
greet_person("Alice")
greet_person("Bob") 
greet_person("Charlie")

# Output:
# Hello, Alice!
# Nice to meet you, Alice!
# Hello, Bob!
# Nice to meet you, Bob!
# Hello, Charlie!
# Nice to meet you, Charlie!
```

### Example 2: Function with multiple parameters

```python
# Function to introduce someone with their age
def introduce_person(name, age, city):
    print(f"This is {name}")
    print(f"They are {age} years old")
    print(f"They live in {city}")
    print("-" * 20)

# Call with different people
introduce_person("Alice", 25, "New York")
introduce_person("Bob", 30, "Los Angeles")
introduce_person("Diana", 28, "Chicago")
```

### Example 3: Mathematical functions

```python
# Function to calculate rectangle area
def calculate_rectangle_area(length, width):
    area = length * width
    print(f"Rectangle: {length} × {width}")
    print(f"Area: {area} square units")

# Function to calculate circle circumference
def calculate_circle_circumference(radius):
    pi = 3.14159
    circumference = 2 * pi * radius
    print(f"Circle radius: {radius}")
    print(f"Circumference: {circumference:.2f} units")

# Using the functions
calculate_rectangle_area(5, 3)
print()
calculate_circle_circumference(7)
```

---

## 3. Return Values

Functions can give back results using the `return` statement. This makes them even more powerful!

### Basic Syntax:
```python
def function_name(parameters):
    # do some calculations
    return result  # send result back to caller
```

### Example 1: Simple return values

```python
# Function that returns a calculation
def add_numbers(a, b):
    result = a + b
    return result

# Use the returned value
sum1 = add_numbers(5, 3)
sum2 = add_numbers(10, 7)

print(f"5 + 3 = {sum1}")
print(f"10 + 7 = {sum2}")

# You can also use the result directly
print(f"15 + 25 = {add_numbers(15, 25)}")
```

### Example 2: String functions

```python
# Function that returns a formatted greeting
def create_greeting(name, time_of_day):
    greeting = f"Good {time_of_day}, {name}! Have a wonderful day!"
    return greeting

# Function that counts vowels in text
def count_vowels(text):
    vowels = "aeiouAEIOU"
    count = 0
    
    for char in text:
        if char in vowels:
            count += 1
    
    return count

# Using the functions
message1 = create_greeting("Alice", "morning")
message2 = create_greeting("Bob", "evening")

print(message1)
print(message2)

text = "Hello World"
vowel_count = count_vowels(text)
print(f"'{text}' has {vowel_count} vowels")
```

### Example 3: Mathematical calculations

```python
# Function to calculate rectangle area (returning value)
def get_rectangle_area(length, width):
    return length * width

# Function to calculate circle area
def get_circle_area(radius):
    pi = 3.14159
    return pi * radius * radius

# Function to find the larger of two numbers
def get_larger_number(a, b):
    if a > b:
        return a
    else:
        return b

# Using the functions
rect_area = get_rectangle_area(8, 5)
circle_area = get_circle_area(3)
larger = get_larger_number(15, 23)

print(f"Rectangle area: {rect_area}")
print(f"Circle area: {circle_area:.2f}")
print(f"Larger number: {larger}")

# Compare areas
if rect_area > circle_area:
    print("Rectangle has larger area")
else:
    print("Circle has larger area")
```

---

## 4. Default Parameters

You can give parameters default values, making them optional when calling the function!

### Basic Syntax:
```python
def function_name(required_param, optional_param="default_value"):
    # code here
    pass
```

### Example 1: Greeting with optional title

```python
# Function with default parameter
def greet_with_title(name, title="Mr./Ms."):
    print(f"Hello, {title} {name}!")

# Call with and without the optional parameter
greet_with_title("Smith")              # Uses default title
greet_with_title("Johnson", "Dr.")     # Uses custom title
greet_with_title("Brown", "Professor") # Uses custom title

# Output:
# Hello, Mr./Ms. Smith!
# Hello, Dr. Johnson!
# Hello, Professor Brown!
```

### Example 2: Mathematical function with defaults

```python
# Function to calculate power with default exponent
def calculate_power(base, exponent=2):
    result = base ** exponent
    return result

# Function to format currency with default symbol
def format_money(amount, currency="$"):
    return f"{currency}{amount:.2f}"

# Using the functions
print(f"3 squared: {calculate_power(3)}")           # Uses default exponent=2
print(f"3 cubed: {calculate_power(3, 3)}")          # Uses custom exponent=3
print(f"2 to power 5: {calculate_power(2, 5)}")     # Uses custom exponent=5

print(format_money(25.5))                           # Uses default $
print(format_money(30, "€"))                        # Uses custom currency
```

### Example 3: Drawing function with customization

```python
# Function to draw rectangles with default characters
def draw_rectangle(width, height, char="*"):
    for row in range(height):
        print(char * width)

# Function to create separator lines
def print_separator(length=40, char="-"):
    print(char * length)

# Using the functions
print("Default rectangle:")
draw_rectangle(5, 3)

print("\nCustom rectangle:")
draw_rectangle(4, 2, "#")

print_separator()                    # Default separator
print("Custom separator:")
print_separator(20, "=")             # Custom separator
```

---

## 5. Variable Scope (Local vs Global)

Understanding where variables can be used is crucial for writing good functions!

### Local Variables

Variables created inside functions are **local** - they only exist inside that function.

```python
def calculate_tax():
    tax_rate = 0.08  # Local variable
    price = 100      # Local variable
    tax = price * tax_rate
    print(f"Tax on ${price}: ${tax}")

calculate_tax()

# This would cause an error - tax_rate doesn't exist outside the function!
# print(tax_rate)  # NameError!
```

### Global Variables

Variables created outside functions are **global** - they can be accessed anywhere.

```python
# Global variables
store_name = "Python Shop"
tax_rate = 0.08

def calculate_total(price):
    # Can access global variables
    tax = price * tax_rate
    total = price + tax
    print(f"Welcome to {store_name}")
    print(f"Price: ${price:.2f}")
    print(f"Tax: ${tax:.2f}") 
    print(f"Total: ${total:.2f}")
    return total

# Using global variables
final_cost = calculate_total(50)
print(f"\nThank you for shopping at {store_name}!")
```

### Modifying Global Variables

Use the `global` keyword to modify global variables inside functions:

```python
# Global counter
visit_count = 0

def track_visit():
    global visit_count  # Tell Python we want to modify the global variable
    visit_count += 1
    print(f"This is visit number: {visit_count}")

def show_statistics():
    print(f"Total visits so far: {visit_count}")

# Using the functions
track_visit()    # Visit 1
track_visit()    # Visit 2
show_statistics()
track_visit()    # Visit 3
show_statistics()
```

### Best Practice Example

```python
# Global configuration
COMPANY_NAME = "Tech Solutions Inc."
TAX_RATE = 0.1

def process_order(customer_name, items):
    # Local variables
    subtotal = 0
    
    print(f"\n{'='*40}")
    print(f"INVOICE - {COMPANY_NAME}")
    print(f"{'='*40}")
    print(f"Customer: {customer_name}")
    print("-" * 40)
    
    # Calculate subtotal
    for item, price in items:
        print(f"{item:<20} ${price:>8.2f}")
        subtotal += price
    
    # Calculate tax and total (using global TAX_RATE)
    tax = subtotal * TAX_RATE
    total = subtotal + tax
    
    print("-" * 40)
    print(f"{'Subtotal:':<20} ${subtotal:>8.2f}")
    print(f"{'Tax:':<20} ${tax:>8.2f}")
    print(f"{'Total:':<20} ${total:>8.2f}")
    print("=" * 40)
    
    return total

# Example usage
order_items = [
    ("Python Book", 29.99),
    ("USB Cable", 15.50),
    ("Mouse Pad", 8.75)
]

final_amount = process_order("Alice Johnson", order_items)
```

---

## 6. Real-World Examples

### Example 1: Temperature Converter

```python
def celsius_to_fahrenheit(celsius):
    """Convert Celsius to Fahrenheit"""
    fahrenheit = (celsius * 9/5) + 32
    return fahrenheit

def fahrenheit_to_celsius(fahrenheit):
    """Convert Fahrenheit to Celsius"""
    celsius = (fahrenheit - 32) * 5/9
    return celsius

def display_conversion(temp, scale):
    """Display temperature in both scales"""
    if scale.lower() == 'c':
        converted = celsius_to_fahrenheit(temp)
        print(f"{temp}°C = {converted:.1f}°F")
    elif scale.lower() == 'f':
        converted = fahrenheit_to_celsius(temp)
        print(f"{temp}°F = {converted:.1f}°C")
    else:
        print("Invalid scale! Use 'C' for Celsius or 'F' for Fahrenheit")

# Interactive temperature converter
def temperature_converter():
    print("=== Temperature Converter ===")
    
    while True:
        try:
            temp = float(input("Enter temperature: "))
            scale = input("Is this in (C)elsius or (F)ahrenheit? ").strip()
            
            display_conversion(temp, scale)
            
            again = input("Convert another? (y/n): ").lower()
            if again != 'y':
                break
                
        except ValueError:
            print("Please enter a valid number!")
    
    print("Thanks for using Temperature Converter!")

# Run the converter
temperature_converter()
```

### Example 2: Grade Calculator System

```python
def calculate_letter_grade(percentage):
    """Convert percentage to letter grade"""
    if percentage >= 90:
        return "A"
    elif percentage >= 80:
        return "B"
    elif percentage >= 70:
        return "C"
    elif percentage >= 60:
        return "D"
    else:
        return "F"

def calculate_gpa_points(letter_grade):
    """Convert letter grade to GPA points"""
    grade_points = {"A": 4.0, "B": 3.0, "C": 2.0, "D": 1.0, "F": 0.0}
    return grade_points.get(letter_grade, 0.0)

def get_student_grades():
    """Get grades for one student"""
    grades = []
    subjects = ["Math", "Science", "English", "History", "Art"]
    
    print("Enter grades for each subject:")
    for subject in subjects:
        while True:
            try:
                grade = float(input(f"{subject}: "))
                if 0 <= grade <= 100:
                    grades.append(grade)
                    break
                else:
                    print("Grade must be between 0 and 100!")
            except ValueError:
                print("Please enter a valid number!")
    
    return grades

def calculate_student_stats(grades):
    """Calculate statistics for a student"""
    total = sum(grades)
    average = total / len(grades)
    highest = max(grades)
    lowest = min(grades)
    letter = calculate_letter_grade(average)
    gpa = calculate_gpa_points(letter)
    
    return {
        "total": total,
        "average": average,
        "highest": highest,
        "lowest": lowest,
        "letter_grade": letter,
        "gpa": gpa
    }

def display_student_report(name, grades, stats):
    """Display formatted student report"""
    print(f"\n{'='*50}")
    print(f"GRADE REPORT FOR: {name.upper()}")
    print(f"{'='*50}")
    
    subjects = ["Math", "Science", "English", "History", "Art"]
    
    for i, subject in enumerate(subjects):
        grade = grades[i]
        letter = calculate_letter_grade(grade)
        print(f"{subject:<10}: {grade:6.1f} ({letter})")
    
    print("-" * 50)
    print(f"{'Average:':<10} {stats['average']:6.1f} ({stats['letter_grade']})")
    print(f"{'Highest:':<10} {stats['highest']:6.1f}")
    print(f"{'Lowest:':<10} {stats['lowest']:6.1f}")
    print(f"{'GPA:':<10} {stats['gpa']:6.1f}")
    
    if stats['average'] >= 85:
        print("\n🏆 Excellent performance! Keep up the great work!")
    elif stats['average'] >= 70:
        print("\n👍 Good work! Room for improvement in some areas.")
    else:
        print("\n📚 Consider getting additional help or tutoring.")

def grade_calculator_system():
    """Main grade calculator system"""
    print("=== Student Grade Calculator ===")
    
    while True:
        name = input("\nEnter student name (or 'quit' to exit): ").strip()
        
        if name.lower() == 'quit':
            break
        
        if not name:
            print("Please enter a valid name!")
            continue
        
        grades = get_student_grades()
        stats = calculate_student_stats(grades)
        display_student_report(name, grades, stats)

# Run the grade calculator
grade_calculator_system()
```

### Example 3: Simple Banking System

```python
# Global variables for account info
account_balance = 1000.0
transaction_history = []

def display_balance():
    """Show current account balance"""
    print(f"\nCurrent Balance: ${account_balance:.2f}")

def deposit_money(amount):
    """Deposit money into account"""
    global account_balance, transaction_history
    
    if amount > 0:
        account_balance += amount
        transaction_history.append(f"Deposit: +${amount:.2f}")
        print(f"Successfully deposited ${amount:.2f}")
        display_balance()
        return True
    else:
        print("Deposit amount must be positive!")
        return False

def withdraw_money(amount):
    """Withdraw money from account"""
    global account_balance, transaction_history
    
    if amount <= 0:
        print("Withdrawal amount must be positive!")
        return False
    
    if amount > account_balance:
        print("Insufficient funds!")
        print(f"Available balance: ${account_balance:.2f}")
        return False
    
    account_balance -= amount
    transaction_history.append(f"Withdrawal: -${amount:.2f}")
    print(f"Successfully withdrew ${amount:.2f}")
    display_balance()
    return True

def show_transaction_history():
    """Display transaction history"""
    print("\n=== Transaction History ===")
    
    if not transaction_history:
        print("No transactions yet.")
        return
    
    for i, transaction in enumerate(transaction_history, 1):
        print(f"{i}. {transaction}")

def transfer_money(recipient, amount):
    """Transfer money to another account"""
    if withdraw_money(amount):
        transaction_history[-1] = f"Transfer to {recipient}: -${amount:.2f}"
        print(f"Transfer to {recipient} completed successfully!")
        return True
    return False

def calculate_interest(rate=0.02):
    """Calculate and add interest to account"""
    global account_balance, transaction_history
    
    interest = account_balance * rate
    account_balance += interest
    transaction_history.append(f"Interest: +${interest:.2f}")
    
    print(f"Interest earned: ${interest:.2f} ({rate*100}% rate)")
    display_balance()

def banking_menu():
    """Display banking menu and handle user choice"""
    print("\n=== Simple Banking System ===")
    print("1. Check Balance")
    print("2. Deposit Money")
    print("3. Withdraw Money") 
    print("4. Transfer Money")
    print("5. Transaction History")
    print("6. Calculate Interest")
    print("7. Exit")
    
    choice = input("Choose an option (1-7): ").strip()
    return choice

def main_banking_system():
    """Main banking system loop"""
    print("Welcome to Simple Bank!")
    display_balance()
    
    while True:
        choice = banking_menu()
        
        if choice == "1":
            display_balance()
            
        elif choice == "2":
            try:
                amount = float(input("Enter deposit amount: $"))
                deposit_money(amount)
            except ValueError:
                print("Please enter a valid amount!")
                
        elif choice == "3":
            try:
                amount = float(input("Enter withdrawal amount: $"))
                withdraw_money(amount)
            except ValueError:
                print("Please enter a valid amount!")
                
        elif choice == "4":
            recipient = input("Enter recipient name: ").strip()
            if recipient:
                try:
                    amount = float(input("Enter transfer amount: $"))
                    transfer_money(recipient, amount)
                except ValueError:
                    print("Please enter a valid amount!")
            else:
                print("Please enter a valid recipient name!")
                
        elif choice == "5":
            show_transaction_history()
            
        elif choice == "6":
            try:
                rate = input("Enter interest rate (default 2%): ").strip()
                if rate:
                    rate = float(rate) / 100
                    calculate_interest(rate)
                else:
                    calculate_interest()
            except ValueError:
                print("Please enter a valid interest rate!")
                
        elif choice == "7":
            print("Thank you for using Simple Bank!")
            break
            
        else:
            print("Invalid choice! Please select 1-7.")

# Run the banking system
main_banking_system()
```

---

## 7. Common Mistakes and Best Practices

### Mistake 1: Forgetting to return values

```python
# Wrong - function doesn't return anything
def calculate_area(length, width):
    area = length * width
    print(f"Area: {area}")  # Only prints, doesn't return

result = calculate_area(5, 3)  # result will be None!

# Correct - function returns the calculated value
def calculate_area(length, width):
    area = length * width
    return area  # Return the result

result = calculate_area(5, 3)  # Now result has the actual area
print(f"The area is: {result}")
```

### Mistake 2: Modifying global variables without `global` keyword

```python
counter = 0

# Wrong - this creates a local variable instead of modifying global
def increment_wrong():
    counter = counter + 1  # Error! Can't read local variable before assignment

# Correct - use global keyword
def increment_correct():
    global counter
    counter = counter + 1

increment_correct()
print(counter)  # Now it works!
```

### Mistake 3: Functions that do too much

```python
# Wrong - function does too many things
def process_student_data_wrong(name, grades):
    # Calculating average
    total = sum(grades)
    average = total / len(grades)
    
    # Determining letter grade
    if average >= 90:
        letter = "A"
    elif average >= 80:
        letter = "B"
    else:
        letter = "C"
    
    # Printing report
    print(f"Student: {name}")
    print(f"Average: {average}")
    print(f"Letter Grade: {letter}")
    
    # Saving to file (imaginary)
    # save_to_file(name, average, letter)
    
    return average

# Better - break into smaller functions
def calculate_average(grades):
    return sum(grades) / len(grades)

def get_letter_grade(average):
    if average >= 90:
        return "A"
    elif average >= 80:
        return "B"
    else:
        return "C"

def print_student_report(name, average, letter):
    print(f"Student: {name}")
    print(f"Average: {average}")
    print(f"Letter Grade: {letter}")

def process_student_data_correct(name, grades):
    average = calculate_average(grades)
    letter = get_letter_grade(average)
    print_student_report(name, average, letter)
    return average
```

### Best Practices:

1. **Use descriptive function names**
```python
# Poor
def calc(x, y):
    return x * y

# Better
def calculate_rectangle_area(length, width):
    return length * width
```

2. **Keep functions small and focused**
```python
# Each function should do one thing well
def validate_email(email):
    return "@" in email and "." in email

def send_welcome_email(email):
    if validate_email(email):
        print(f"Sending welcome email to {email}")
        return True
    else:
        print("Invalid email address")
        return False
```

3. **Use docstrings to document functions**
```python
def calculate_bmi(weight, height):
    """
    Calculate Body Mass Index (BMI)
    
    Parameters:
    weight (float): Weight in kilograms
    height (float): Height in meters
    
    Returns:
    float: BMI value
    """
    return weight / (height * height)
```

4. **Avoid too many parameters**
```python
# Too many parameters - hard to remember
def create_user_account(first_name, last_name, email, phone, 
                       address, city, state, zip_code, country):
    pass

# Better - use a dictionary or break into smaller functions
def create_user_account(personal_info, contact_info):
    pass
```

---

## 8. Practice Exercises

### Exercise 1: Simple Calculator
Create a function that adds two numbers:

```python
# Your code here
def add_numbers(a, b):
    # Return the sum of a and b
    pass

# Test your function
result = add_numbers(5, 3)
print(f"5 + 3 = {result}")
```

### Exercise 2: Greet Function
Create a function that greets someone:

```python
# Your code here
def greet(name):
    # Print a greeting with the person's name
    pass

# Test your function
greet("Alice")
```

### Exercise 3: Check Even or Odd
Create a function that checks if a number is even:

```python
# Your code here
def is_even(number):
    # Return True if number is even, False if odd
    pass

# Test your function
print(is_even(4))  # Should print True
print(is_even(7))  # Should print False
```
# - Menu with options for +, -, *, /, exit
# - Input validation
# - Handle division by zero
# - Continue until user chooses to exit
```

### Exercise 2: Text Processing Functions
Create functions to analyze and manipulate text:

```python
# Your code here
def count_words(text):
    # Return the number of words in text
    pass

def count_characters(text, include_spaces=True):
    # Return character count (with/without spaces)
    pass

def reverse_text(text):
    # Return reversed text
    pass

def capitalize_words(text):
    # Return text with each word capitalized
    pass

def remove_vowels(text):
    # Return text with vowels removed
    pass

def text_statistics(text):
    # Return a dictionary with all statistics
    pass

# Test your functions
sample_text = "Hello World Python Programming"
stats = text_statistics(sample_text)

# Expected output:
# Words: 4
# Characters (with spaces): 29  
# Characters (without spaces): 26
# Vowels: 9
# Consonants: 17
# Reversed: gnimmargorP nohtyP dlroW olleH
```

### Exercise 3: Number Games
Create functions for different number games:

```python
# Your code here
import random

def generate_random_number(min_val=1, max_val=100):
    # Generate random number in range
    pass

def check_guess(secret, guess):
    # Return "high", "low", or "correct"
    pass

def guessing_game():
    # Main guessing game logic
    pass

def is_prime(number):
    # Check if number is prime
    pass

def find_primes_in_range(start, end):
    # Return list of primes in range
    pass

def prime_number_game():
    # Game: guess if number is prime
    pass

def math_quiz():
    # Generate random math problems
    pass

# Test your games
print("1. Number Guessing Game")
guessing_game()

print("\n2. Prime Number Game")  
prime_number_game()

print("\n3. Math Quiz")
math_quiz()
```

### Exercise 4: Personal Finance Functions
Create a personal finance management system:

```python
# Your code here

# Global variables for account data
accounts = {
    "checking": 1000.0,
    "savings": 5000.0
}

transactions = []

def display_accounts():
    # Show all account balances
    pass

def deposit(account_name, amount):
    # Deposit money to account
    pass

def withdraw(account_name, amount):
    # Withdraw money from account
    pass

def transfer(from_account, to_account, amount):
    # Transfer money between accounts
    pass

def calculate_monthly_interest(account_name, rate=0.001):
    # Calculate and add monthly interest
    pass

def show_transaction_history(limit=10):
    # Show recent transactions
    pass

def budget_tracker(income, expenses):
    # Track monthly budget
    pass

def financial_report():
    # Generate comprehensive financial report
    pass

def main_finance_system():
    # Main system loop with menu
    pass

# Test your finance system
main_finance_system()
```

### Exercise 5: Game Development Functions
Create a simple RPG character system:

```python
# Your code here

def create_character(name, character_class="Warrior"):
    # Create character dictionary with stats
    # Warrior: high strength, low magic
    # Mage: high magic, low strength  
    # Archer: balanced stats
    pass

def display_character(character):
    # Show character information nicely formatted
    pass

def attack_damage(character):
    # Calculate attack damage based on character stats
    pass

def level_up(character):
    # Increase character level and stats
    pass

def battle(char1, char2):
    # Simulate battle between two characters
    # Return winner
    pass

def save_character(character, filename):
    # Save character to text file (simple format)
    pass

def load_character(filename):
    # Load character from text file
    pass

def character_creation_menu():
    # Interactive character creation
    pass

def main_rpg_system():
    # Main RPG system with menu
    pass

# Test your RPG system
main_rpg_system()

# Expected features:
# - Character creation with different classes
# - Level up system
# - Battle system
# - Save/load characters
# - Character stats display
```

### Exercise 6: Shopping List Manager
Create a comprehensive shopping list management system:

```python
# Your code here

shopping_lists = {}  # Store multiple shopping lists

def create_list(list_name):
    # Create new empty shopping list
    pass

def add_item(list_name, item, quantity=1, price=0.0):
    # Add item to shopping list
    pass

def remove_item(list_name, item):
    # Remove item from shopping list
    pass

def update_quantity(list_name, item, new_quantity):
    # Update item quantity
    pass

def calculate_total_cost(list_name):
    # Calculate total cost of all items
    pass

def display_list(list_name):
    # Display shopping list in nice format
    pass

def search_item(list_name, search_term):
    # Search for items containing search term
    pass

def merge_lists(list1_name, list2_name, new_list_name):
    # Combine two lists into a new one
    pass

def export_list_to_text(list_name):
    # Export list to formatted text
    pass

def shopping_list_menu():
    # Main menu system
    pass

# Test your shopping system
shopping_list_menu()

# Expected features:
# - Multiple shopping lists
# - Add/remove/update items
# - Quantity and price tracking
# - Cost calculations
# - Search functionality
# - List merging
# - Text export
```

---

## Solutions (Try the exercises first!)

<details>
<summary>Click to see Exercise 1 Solution</summary>

```python
# Exercise 1: Calculator Functions Solution
def add(a, b):
    return a + b

def subtract(a, b):
    return a - b

def multiply(a, b):
    return a * b

def divide(a, b):
    if b == 0:
        return "Error: Cannot divide by zero"
    return a / b

def calculator_menu():
    print("\n=== Calculator ===")
    print("1. Addition (+)")
    print("2. Subtraction (-)")
    print("3. Multiplication (*)")
    print("4. Division (/)")
    print("5. Exit")
    return input("Choose operation (1-5): ")

def get_numbers():
    while True:
        try:
            a = float(input("Enter first number: "))
            b = float(input("Enter second number: "))
            return a, b
        except ValueError:
            print("Please enter valid numbers!")

def main_calculator():
    print("Welcome to Python Calculator!")
    
    while True:
        choice = calculator_menu()
        
        if choice == "5":
            print("Thank you for using Calculator!")
            break
        
        if choice in ["1", "2", "3", "4"]:
            a, b = get_numbers()
            
            if choice == "1":
                result = add(a, b)
                print(f"{a} + {b} = {result}")
            elif choice == "2":
                result = subtract(a, b)
                print(f"{a} - {b} = {result}")
            elif choice == "3":
                result = multiply(a, b)
                print(f"{a} * {b} = {result}")
            elif choice == "4":
                result = divide(a, b)
                if isinstance(result, str):
                    print(result)
                else:
                    print(f"{a} / {b} = {result}")
        else:
            print("Invalid choice! Please select 1-5.")

main_calculator()
```
</details>

<details>
<summary>Click to see Exercise 2 Solution</summary>

```python
# Exercise 2: Text Processing Functions Solution
def count_words(text):
    words = text.split()
    return len(words)

def count_characters(text, include_spaces=True):
    if include_spaces:
        return len(text)
    else:
        return len(text.replace(" ", ""))

def reverse_text(text):
    return text[::-1]

def capitalize_words(text):
    return text.title()

def remove_vowels(text):
    vowels = "aeiouAEIOU"
    result = ""
    for char in text:
        if char not in vowels:
            result += char
    return result

def count_vowels(text):
    vowels = "aeiouAEIOU"
    count = 0
    for char in text:
        if char in vowels:
            count += 1
    return count

def text_statistics(text):
    return {
        "words": count_words(text),
        "chars_with_spaces": count_characters(text, True),
        "chars_without_spaces": count_characters(text, False),
        "vowels": count_vowels(text),
        "consonants": count_characters(text, False) - count_vowels(text),
        "reversed": reverse_text(text)
    }

# Test the functions
sample_text = "Hello World Python Programming"
stats = text_statistics(sample_text)

print(f"Text: {sample_text}")
print(f"Words: {stats['words']}")
print(f"Characters (with spaces): {stats['chars_with_spaces']}")
print(f"Characters (without spaces): {stats['chars_without_spaces']}")
print(f"Vowels: {stats['vowels']}")
print(f"Consonants: {stats['consonants']}")
print(f"Reversed: {stats['reversed']}")
```
</details>

---

## Summary

In this comprehensive guide, you learned about Python functions:

- ✅ **Function definition and calling** with proper syntax and structure
- ✅ **Parameters and arguments** to make functions flexible and reusable
- ✅ **Return values** to get results back from functions
- ✅ **Default parameters** for optional function arguments
- ✅ **Variable scope** understanding local vs global variables
- ✅ **Real-world applications** including calculators, grade systems, and banking
- ✅ **Best practices** for writing clean, maintainable function code
- ✅ **Common mistakes** and how to avoid them

### Key Takeaways:
- **Functions organize code** and make it reusable and maintainable
- **Use descriptive names** that clearly indicate what the function does
- **Keep functions focused** - each function should do one thing well
- **Return values** instead of just printing when you need to use results
- **Understand scope** to avoid variable conflicts and unexpected behavior
- **Use default parameters** to make functions more flexible

### Next Steps:
- Practice with the exercises to reinforce your understanding
- Try breaking your existing code into functions for better organization
- Experiment with different parameter combinations and return values
- Think about how functions can solve complex problems by breaking them into smaller parts

**Next:** Continue to learn about Modules & Packages to organize and reuse code across different files!