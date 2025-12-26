# Python Conditional Statements

Conditional statements are the decision-making tools in programming. They allow your program to choose different paths based on certain conditions. Think of them as the "if this, then that" logic we use in everyday life!

## What are Conditional Statements?

Imagine you're getting ready in the morning and you look outside:
- **If** it's raining → take an umbrella
- **If** it's sunny → wear sunglasses
- **If** it's cold → wear a jacket

Conditional statements work the same way in programming - they let your code make decisions based on different situations.

```python
# Real-world example in Python
weather = "raining"

if weather == "raining":
    print("Take an umbrella!")
elif weather == "sunny":
    print("Wear sunglasses!")
elif weather == "cold":
    print("Wear a jacket!")
else:
    print("Enjoy the weather!")
```

## Basic Structure

All conditional statements in Python follow this pattern:
```python
if condition:
    # code to run if condition is True
elif another_condition:  # optional
    # code to run if another_condition is True
else:  # optional
    # code to run if no conditions are True
```

**Important**: Notice the **colon (`:`)** at the end of each condition and the **indentation** (4 spaces) for the code blocks!

---

## 1. Simple `if` Statements

The `if` statement is the most basic form of conditional logic.

### Syntax:
```python
if condition:
    # code to execute if condition is True
```

### Examples:

```python
# Example 1: Age check
age = 18

if age >= 18:
    print("You are an adult!")
    print("You can vote!")

# Example 2: Grade check
score = 85

if score >= 60:
    print("Congratulations! You passed!")

# Example 3: Number check
number = 10

if number > 0:
    print("The number is positive")

# Example 4: String check
name = "Alice"

if len(name) > 3:
    print("Your name has more than 3 characters")
```

### Using Different Comparison Operators:

```python
# Different ways to check conditions
temperature = 25
password = "python123"
is_logged_in = True

# Equal to
if temperature == 25:
    print("Perfect temperature!")

# Not equal to
if password != "123456":
    print("Strong password!")

# Greater than or equal to
if temperature >= 20:
    print("It's warm outside")

# Less than
if len(password) < 8:
    print("Password is too short")

# Boolean check
if is_logged_in:
    print("Welcome back!")

# Check if something exists in a string
if "python" in password:
    print("Password contains 'python'")
```

---

## 2. `if-else` Statements

The `else` statement provides an alternative action when the `if` condition is False.

### Syntax:
```python
if condition:
    # code if condition is True
else:
    # code if condition is False
```

### Examples:

```python
# Example 1: Age verification
age = int(input("Enter your age: "))

if age >= 18:
    print("You are an adult. You can vote!")
else:
    print("You are a minor. Wait a few more years to vote.")

# Example 2: Even or odd number
number = int(input("Enter a number: "))

if number % 2 == 0:
    print(f"{number} is an even number")
else:
    print(f"{number} is an odd number")

# Example 3: Pass or fail
grade = float(input("Enter your grade: "))

if grade >= 60:
    print("Congratulations! You passed the exam!")
else:
    print("Sorry, you failed. Keep studying!")

# Example 4: Password strength
password = input("Create a password: ")

if len(password) >= 8:
    print("Strong password!")
else:
    print("Password is too short. Use at least 8 characters.")
```

### Real-world Example: Simple ATM

```python
# Simple ATM simulation
balance = 1000
withdraw_amount = float(input("How much would you like to withdraw? $"))

if withdraw_amount <= balance:
    balance = balance - withdraw_amount
    print(f"Transaction successful!")
    print(f"You withdrew ${withdraw_amount}")
    print(f"Remaining balance: ${balance}")
else:
    print("Insufficient funds!")
    print(f"Your current balance is ${balance}")
```

---

## 3. `elif` Statements

When you need to check multiple conditions, use `elif` (else if). Python checks conditions from top to bottom and executes the first True condition.

### Syntax:
```python
if first_condition:
    # code for first condition
elif second_condition:
    # code for second condition
elif third_condition:
    # code for third condition
else:
    # code if none of the conditions are True
```

### Examples:

```python
# Example 1: Grade system
score = int(input("Enter your score: "))

if score >= 90:
    print("Grade: A (Excellent!)")
elif score >= 80:
    print("Grade: B (Good job!)")
elif score >= 70:
    print("Grade: C (Not bad!)")
elif score >= 60:
    print("Grade: D (You passed!)")
else:
    print("Grade: F (Study harder next time!)")

# Example 2: Weather recommendations
temperature = float(input("What's the temperature? "))

if temperature > 30:
    print("It's hot! Wear light clothes and stay hydrated.")
elif temperature > 20:
    print("Nice weather! Perfect for outdoor activities.")
elif temperature > 10:
    print("A bit cool. Consider wearing a light jacket.")
elif temperature > 0:
    print("It's cold! Wear warm clothes.")
else:
    print("Freezing! Stay indoors and bundle up!")

# Example 3: Age categories
age = int(input("Enter your age: "))

if age < 13:
    print("You are a child.")
elif age < 20:
    print("You are a teenager.")
elif age < 60:
    print("You are an adult.")
else:
    print("You are a senior citizen.")
```

### Traffic Light Simulator

```python
# Traffic light system
light_color = input("What color is the traffic light? ").lower()

if light_color == "green":
    print("GO! Drive safely.")
elif light_color == "yellow":
    print("CAUTION! Slow down and prepare to stop.")
elif light_color == "red":
    print("STOP! Wait for the green light.")
else:
    print("Invalid color. Traffic lights are red, yellow, or green.")
```

---

## 4. Nested Conditions

You can put `if` statements inside other `if` statements. This is called nesting.

### Syntax:
```python
if outer_condition:
    if inner_condition:
        # code if both conditions are True
    else:
        # code if outer is True but inner is False
else:
    # code if outer condition is False
```

### Examples:

```python
# Example 1: Age and license check
age = int(input("Enter your age: "))

if age >= 18:
    has_license = input("Do you have a driving license? (yes/no): ").lower()
    
    if has_license == "yes":
        print("You can drive a car!")
    else:
        print("You need to get a driving license first.")
else:
    print("You are too young to drive.")

# Example 2: Login system
username = input("Enter username: ")

if username == "admin":
    password = input("Enter password: ")
    
    if password == "secret123":
        print("Welcome, Admin! Access granted.")
    else:
        print("Incorrect password!")
else:
    print("Username not found!")

# Example 3: Number analysis
number = float(input("Enter a number: "))

if number > 0:
    print("The number is positive.")
    
    if number > 100:
        print("It's also a large number!")
    else:
        print("It's a small to medium number.")
        
elif number < 0:
    print("The number is negative.")
    
    if number < -100:
        print("It's a large negative number!")
    else:
        print("It's a small negative number.")
else:
    print("The number is zero.")
```

### Complex Example: Bank Account

```python
# Advanced bank account system
account_balance = 1500
pin = "1234"

print("Welcome to Simple Bank!")
entered_pin = input("Enter your PIN: ")

if entered_pin == pin:
    print("PIN accepted!")
    
    print("\nWhat would you like to do?")
    print("1. Check Balance")
    print("2. Withdraw Money")
    print("3. Deposit Money")
    
    choice = input("Enter your choice (1, 2, or 3): ")
    
    if choice == "1":
        print(f"Your current balance is: ${account_balance}")
        
    elif choice == "2":
        amount = float(input("Enter withdrawal amount: $"))
        
        if amount <= account_balance:
            if amount > 0:
                account_balance = account_balance - amount
                print(f"Withdrawal successful! You withdrew ${amount}")
                print(f"Remaining balance: ${account_balance}")
            else:
                print("Please enter a positive amount!")
        else:
            print("Insufficient funds!")
            
    elif choice == "3":
        amount = float(input("Enter deposit amount: $"))
        
        if amount > 0:
            account_balance = account_balance + amount
            print(f"Deposit successful! You deposited ${amount}")
            print(f"New balance: ${account_balance}")
        else:
            print("Please enter a positive amount!")
            
    else:
        print("Invalid choice! Please select 1, 2, or 3.")
        
else:
    print("Incorrect PIN! Access denied.")
```

---

## 5. Logical Operators in Conditions

You can combine multiple conditions using logical operators: `and`, `or`, `not`.

### Using `and` - Both conditions must be True

```python
# Example 1: Age and income check for loan
age = int(input("Enter your age: "))
income = float(input("Enter your annual income: $"))

if age >= 21 and income >= 30000:
    print("Loan approved!")
else:
    print("Loan denied. You must be 21+ with $30,000+ income.")

# Example 2: Username and password check
username = input("Username: ")
password = input("Password: ")

if username == "user123" and password == "pass456":
    print("Login successful!")
else:
    print("Invalid credentials!")

# Example 3: Grade requirements
math_grade = float(input("Enter math grade: "))
english_grade = float(input("Enter English grade: "))

if math_grade >= 70 and english_grade >= 70:
    print("You qualify for the advanced program!")
else:
    print("You need at least 70 in both subjects.")
```

### Using `or` - At least one condition must be True

```python
# Example 1: Weekend check
day = input("What day is it? ").lower()

if day == "saturday" or day == "sunday":
    print("It's the weekend! Time to relax!")
else:
    print("It's a weekday. Back to work/school!")

# Example 2: Emergency contact
relationship = input("What's your relationship? ").lower()

if relationship == "parent" or relationship == "spouse" or relationship == "sibling":
    print("Valid emergency contact.")
else:
    print("Please provide a family member as emergency contact.")

# Example 3: Discount eligibility
age = int(input("Enter your age: "))
is_student = input("Are you a student? (yes/no): ").lower()

if age >= 65 or is_student == "yes":
    print("You qualify for a discount!")
else:
    print("Regular pricing applies.")
```

### Using `not` - Flips True/False

```python
# Example 1: Access control
is_banned = False
username = input("Enter username: ")

if not is_banned:
    print("Welcome! You can access the system.")
else:
    print("Sorry, you are banned from the system.")

# Example 2: File validation
filename = input("Enter filename: ")

if not filename == "":
    print(f"Processing file: {filename}")
else:
    print("Error: Filename cannot be empty!")

# Example 3: Input validation
password = input("Create password: ")

if not len(password) < 8:
    print("Password accepted!")
else:
    print("Password must be at least 8 characters!")
```

### Complex Logical Combinations

```python
# Example: Employee bonus calculation
years_worked = int(input("Years worked: "))
performance_rating = float(input("Performance rating (1-5): "))
is_manager = input("Are you a manager? (yes/no): ").lower()

# Complex condition with multiple logical operators
if (years_worked >= 5 and performance_rating >= 4) or is_manager == "yes":
    if performance_rating >= 4.5:
        bonus = 5000
    elif performance_rating >= 4:
        bonus = 3000
    else:
        bonus = 2000
        
    print(f"Congratulations! You earned a ${bonus} bonus!")
else:
    print("You don't qualify for a bonus this year.")
```

---

## 6. Common Patterns and Best Practices

### Pattern 1: Input Validation

```python
# Validate user input
while True:
    age = input("Enter your age: ")
    
    if age.isdigit():  # Check if input contains only numbers
        age = int(age)
        if age >= 0 and age <= 120:
            print(f"Valid age: {age}")
            break
        else:
            print("Age must be between 0 and 120!")
    else:
        print("Please enter a valid number!")
```

### Pattern 2: Menu Systems

```python
# Simple menu system
print("=== Calculator Menu ===")
print("1. Addition")
print("2. Subtraction")
print("3. Multiplication")
print("4. Division")
print("5. Exit")

choice = input("Enter your choice (1-5): ")

if choice == "1":
    a = float(input("Enter first number: "))
    b = float(input("Enter second number: "))
    print(f"Result: {a + b}")
    
elif choice == "2":
    a = float(input("Enter first number: "))
    b = float(input("Enter second number: "))
    print(f"Result: {a - b}")
    
elif choice == "3":
    a = float(input("Enter first number: "))
    b = float(input("Enter second number: "))
    print(f"Result: {a * b}")
    
elif choice == "4":
    a = float(input("Enter first number: "))
    b = float(input("Enter second number: "))
    
    if b != 0:
        print(f"Result: {a / b}")
    else:
        print("Error: Cannot divide by zero!")
        
elif choice == "5":
    print("Goodbye!")
    
else:
    print("Invalid choice! Please select 1-5.")
```

### Pattern 3: Range Checking

```python
# Temperature category checker
temp = float(input("Enter temperature in Celsius: "))

if -273.15 <= temp < 0:
    print("Below freezing")
elif 0 <= temp < 10:
    print("Very cold")
elif 10 <= temp < 20:
    print("Cold")
elif 20 <= temp < 30:
    print("Comfortable")
elif 30 <= temp < 40:
    print("Hot")
elif temp >= 40:
    print("Very hot")
else:
    print("Invalid temperature (below absolute zero!)")
```

---

## 7. Real-World Examples

### Example 1: Student Grade Calculator

```python
print("=== Grade Calculator ===")

# Get student information
name = input("Enter student name: ")
math_score = float(input("Enter Math score (0-100): "))
science_score = float(input("Enter Science score (0-100): "))
english_score = float(input("Enter English score (0-100): "))

# Calculate average
average = (math_score + science_score + english_score) / 3

print(f"\n=== Report Card for {name} ===")
print(f"Math: {math_score}")
print(f"Science: {science_score}")
print(f"English: {english_score}")
print(f"Average: {average:.1f}")

# Determine letter grade
if average >= 90:
    letter_grade = "A"
    message = "Excellent work!"
elif average >= 80:
    letter_grade = "B"
    message = "Good job!"
elif average >= 70:
    letter_grade = "C"
    message = "Satisfactory"
elif average >= 60:
    letter_grade = "D"
    message = "Needs improvement"
else:
    letter_grade = "F"
    message = "Please see your teacher"

print(f"Letter Grade: {letter_grade}")
print(f"Comment: {message}")

# Check for honor roll
if average >= 85 and math_score >= 80 and science_score >= 80 and english_score >= 80:
    print("🏆 Congratulations! You made the Honor Roll!")
```

### Example 2: Shopping Discount Calculator

```python
print("=== Shopping Cart Discount Calculator ===")

# Get purchase information
item_price = float(input("Enter item price: $"))
quantity = int(input("Enter quantity: "))
is_member = input("Are you a member? (yes/no): ").lower()
coupon_code = input("Enter coupon code (or 'none'): ").upper()

# Calculate subtotal
subtotal = item_price * quantity
discount = 0
total = subtotal

print(f"\n=== Receipt ===")
print(f"Item price: ${item_price:.2f}")
print(f"Quantity: {quantity}")
print(f"Subtotal: ${subtotal:.2f}")

# Apply membership discount
if is_member == "yes":
    membership_discount = subtotal * 0.10  # 10% discount
    discount += membership_discount
    print(f"Membership discount (10%): -${membership_discount:.2f}")

# Apply quantity discount
if quantity >= 10:
    bulk_discount = subtotal * 0.05  # 5% additional discount
    discount += bulk_discount
    print(f"Bulk discount (5%): -${bulk_discount:.2f}")

# Apply coupon discount
if coupon_code == "SAVE20":
    coupon_discount = subtotal * 0.20  # 20% discount
    discount += coupon_discount
    print(f"Coupon discount (20%): -${coupon_discount:.2f}")
elif coupon_code == "SAVE10":
    coupon_discount = subtotal * 0.10  # 10% discount
    discount += coupon_discount
    print(f"Coupon discount (10%): -${coupon_discount:.2f}")
elif coupon_code != "NONE":
    print(f"Invalid coupon code: {coupon_code}")

# Calculate final total
total = subtotal - discount

print(f"Total discount: -${discount:.2f}")
print(f"Final total: ${total:.2f}")

# Special offer message
if total > 100:
    print("🎉 Thank you for your large purchase! Free shipping included!")
elif total > 50:
    print("🚚 Add $" + f"{100 - total:.2f}" + " more for free shipping!")
```

### Example 3: Simple Password Manager

```python
print("=== Simple Password Strength Checker ===")

password = input("Enter your password: ")
length = len(password)

# Initialize strength score
score = 0
feedback = []

print(f"\nAnalyzing password: {'*' * length}")

# Check length
if length >= 12:
    score += 3
    feedback.append("✓ Great length (12+ characters)")
elif length >= 8:
    score += 2
    feedback.append("✓ Good length (8+ characters)")
elif length >= 6:
    score += 1
    feedback.append("⚠ Minimum length (6+ characters)")
else:
    feedback.append("✗ Too short (less than 6 characters)")

# Check for numbers
has_numbers = False
for char in password:
    if char.isdigit():
        has_numbers = True
        break

if has_numbers:
    score += 1
    feedback.append("✓ Contains numbers")
else:
    feedback.append("✗ Add some numbers")

# Check for uppercase letters
has_uppercase = False
for char in password:
    if char.isupper():
        has_uppercase = True
        break

if has_uppercase:
    score += 1
    feedback.append("✓ Contains uppercase letters")
else:
    feedback.append("✗ Add uppercase letters")

# Check for lowercase letters
has_lowercase = False
for char in password:
    if char.islower():
        has_lowercase = True
        break

if has_lowercase:
    score += 1
    feedback.append("✓ Contains lowercase letters")
else:
    feedback.append("✗ Add lowercase letters")

# Check for special characters
special_chars = "!@#$%^&*"
has_special = False
for char in password:
    if char in special_chars:
        has_special = True
        break

if has_special:
    score += 1
    feedback.append("✓ Contains special characters")
else:
    feedback.append("✗ Add special characters (!@#$%^&*)")

# Determine strength level
if score >= 6:
    strength = "Very Strong"
    color = "🟢"
elif score >= 4:
    strength = "Strong"
    color = "🟡"
elif score >= 2:
    strength = "Weak"
    color = "🟠"
else:
    strength = "Very Weak"
    color = "🔴"

# Display results
print(f"\n=== Password Analysis ===")
print(f"Strength: {color} {strength} (Score: {score}/7)")
print(f"\nFeedback:")
for comment in feedback:
    print(f"  {comment}")

# Security recommendation
if score < 4:
    print(f"\n⚠ Recommendation: Create a stronger password for better security!")
else:
    print(f"\n✅ Good password! Your account is well protected.")
```

---

## 8. Common Mistakes to Avoid

### Mistake 1: Missing Colon
```python
# Wrong - Missing colon
if age >= 18
    print("You can vote")

# Correct - Include colon
if age >= 18:
    print("You can vote")
```

### Mistake 2: Incorrect Indentation
```python
# Wrong - No indentation
if age >= 18:
print("You can vote")

# Wrong - Inconsistent indentation
if age >= 18:
    print("You can vote")
        print("You are an adult")  # Too much indentation

# Correct - Consistent 4-space indentation
if age >= 18:
    print("You can vote")
    print("You are an adult")
```

### Mistake 3: Using Assignment (=) Instead of Comparison (==)
```python
# Wrong - Assignment operator
if name = "Alice":  # This will cause an error
    print("Hello Alice")

# Correct - Comparison operator
if name == "Alice":
    print("Hello Alice")
```

### Mistake 4: Unnecessary Nested Conditions
```python
# Less efficient
if age >= 18:
    if age < 65:
        print("You are a working-age adult")

# Better - Use logical operators
if age >= 18 and age < 65:
    print("You are a working-age adult")

# Even better - Use comparison chains
if 18 <= age < 65:
    print("You are a working-age adult")
```

### Mistake 5: Not Handling Edge Cases
```python
# Problematic - What if age is exactly 18?
if age > 18:
    print("Adult")
else:
    print("Minor")

# Better - Clear about boundary conditions
if age >= 18:
    print("Adult")
else:
    print("Minor")
```

---

## 9. Practice Exercises

### Exercise 1: Simple Age Checker
Check if someone can vote:

```python
# Your code here
age = int(input("Enter your age: "))

# Check if age is 18 or older
# Print "You can vote!" or "You cannot vote yet"
```

### Exercise 2: Grade Checker
Check if a student passed:

```python
# Your code here
score = int(input("Enter your test score: "))

# If score is 60 or above, print "You passed!"
# Otherwise, print "You need to study more"
```

### Exercise 3: Number Checker
Check if a number is positive, negative, or zero:

```python
# Your code here
number = int(input("Enter a number: "))

# Check if the number is positive, negative, or zero
# Print the appropriate message
```
  # Convert letter grade to points
  # Add to totals

# Calculate GPA

# Determine academic standing:
# 3.5+: Dean's List
# 3.0+: Good Standing  
# 2.0+: Academic Probation
# Below 2.0: Academic Warning

# Expected output:
# Course 1: 3 credits, A grade (4.0 points)
# Course 2: 4 credits, B grade (3.0 points)
# ...
# GPA: 3.25
# Academic Standing: Good Standing
```

### Exercise 6: Simple Text Adventure
Create a mini text adventure game:
- Player starts in a room with multiple exits
- Each choice leads to different outcomes
- Include at least 3 decision points
- Have multiple endings

```python
# Your code here
print("=== The Mysterious House ===")
print("You find yourself in front of an old house...")

# First decision point

# Continue the story based on choices

# Include multiple decision points and endings

# Example structure:
# Choice 1: Enter house or walk away?
#   If enter: Choice 2: Go upstairs or downstairs?
#     If upstairs: Choice 3: Check bedroom or attic?
#       Different endings based on final choice
#     If downstairs: Different path...
#   If walk away: Different ending
```

---

## Solutions (Try the exercises first!)

<details>
<summary>Click to see Exercise 1 Solution</summary>

```python
# Exercise 1: Number Analyzer Solution
number = int(input("Enter a number: "))

# Check positive/negative/zero
if number > 0:
    print(f"{number} is positive")
elif number < 0:
    print(f"{number} is negative")
else:
    print(f"{number} is zero")

# Check even/odd (only if not zero)
if number != 0:
    if number % 2 == 0:
        print(f"{number} is even")
    else:
        print(f"{number} is odd")

# Check digit count
if number < 0:
    number = -number  # Make positive for digit counting

if number < 10:
    print(f"It's a single-digit number")
elif number < 100:
    print(f"It's a double-digit number")
else:
    print(f"It's a number with more than two digits")
```
</details>

<details>
<summary>Click to see Exercise 2 Solution</summary>

```python
# Exercise 2: BMI Calculator Solution
print("=== BMI Calculator ===")

height = float(input("Enter your height in meters: "))
weight = float(input("Enter your weight in kg: "))

bmi = weight / (height * height)

print(f"Your BMI is: {bmi:.1f}")

if bmi < 18.5:
    category = "Underweight"
    advice = "Consider consulting a healthcare provider about healthy weight gain."
elif bmi < 25.0:
    category = "Normal weight"
    advice = "Great! Maintain your healthy lifestyle."
elif bmi < 30.0:
    category = "Overweight"
    advice = "Consider a balanced diet and regular exercise."
else:
    category = "Obese"
    advice = "Please consult a healthcare provider for guidance."

print(f"Category: {category}")
print(f"Advice: {advice}")
```
</details>

<details>
<summary>Click to see Exercise 3 Solution</summary>

```python
# Exercise 3: Movie Ticket Pricing Solution
print("=== Movie Ticket Pricing ===")

age = int(input("Enter your age: "))
is_student = input("Are you a student? (yes/no): ").lower()
is_weekend = input("Is this a weekend show? (yes/no): ").lower()

# Determine base price
if age < 12:
    base_price = 8.00
    ticket_type = "Child"
elif age >= 65:
    base_price = 10.00
    ticket_type = "Senior"
else:
    base_price = 12.00
    ticket_type = "Regular"

print(f"\n=== Ticket Calculation ===")
print(f"Ticket type: {ticket_type}")
print(f"Base price: ${base_price:.2f}")

final_price = base_price

# Apply student discount
if is_student == "yes" and ticket_type == "Regular":
    discount = base_price * 0.15
    final_price -= discount
    print(f"Student discount (15%): -${discount:.2f}")

# Apply weekend surcharge
if is_weekend == "yes":
    surcharge = 3.00
    final_price += surcharge
    print(f"Weekend surcharge: +${surcharge:.2f}")

print(f"Final price: ${final_price:.2f}")
```
</details>

---

## Summary

In this comprehensive guide, you learned about Python conditional statements:

- ✅ **Simple `if` statements** for basic decision making
- ✅ **`if-else` statements** for binary choices
- ✅ **`elif` statements** for multiple conditions
- ✅ **Nested conditions** for complex logic
- ✅ **Logical operators** (`and`, `or`, `not`) for combining conditions
- ✅ **Real-world applications** and best practices
- ✅ **Common mistakes** and how to avoid them

### Key Takeaways:
- **Indentation matters** - Use 4 spaces consistently
- **Don't forget the colon (`:`)** after conditions
- **Use `==` for comparison**, not `=` (assignment)
- **Combine conditions** with logical operators when appropriate
- **Test edge cases** to ensure your logic is correct
- **Keep code readable** - avoid overly complex nested conditions

### Next Steps:
- Practice with the exercises to reinforce your understanding
- Try creating your own decision-making programs
- Think about how conditional statements apply to real-world problems
- Prepare for learning about loops, which often work together with conditionals

**Next:** Continue to learn about Loops to repeat actions and process collections of data!