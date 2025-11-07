# Python Operators

Operators are special symbols that perform operations on variables and values. Think of them as tools that help you calculate, compare, and make decisions in your programs.

## 1. Arithmetic Operators

These operators help you do math calculations, just like a calculator!

| Operator | Name | Example | Result |
|----------|------|---------|---------|
| `+` | Addition | `5 + 3` | `8` |
| `-` | Subtraction | `10 - 4` | `6` |
| `*` | Multiplication | `6 * 7` | `42` |
| `/` | Division | `15 / 3` | `5.0` |
| `//` | Floor Division | `17 // 5` | `3` |
| `%` | Modulus (Remainder) | `17 % 5` | `2` |
| `**` | Power | `2 ** 3` | `8` |

### Examples:
```python
# Basic math
a = 10
b = 3

print(a + b)    # 13 (addition)
print(a - b)    # 7 (subtraction)
print(a * b)    # 30 (multiplication)
print(a / b)    # 3.333... (division - always gives decimal)
print(a // b)   # 3 (floor division - removes decimal part)
print(a % b)    # 1 (remainder when 10 is divided by 3)
print(a ** b)   # 1000 (10 to the power of 3)
```

### Real-world example:
```python
# Calculate total cost with tax
item_price = 25.50
tax_rate = 0.08  # 8% tax
total_cost = item_price + (item_price * tax_rate)
print(f"Total cost: ${total_cost:.2f}")  # Total cost: $27.54
```

## 2. Comparison Operators

These operators compare two values and give you `True` or `False` as an answer.

| Operator | Name | Example | Result |
|----------|------|---------|---------|
| `==` | Equal to | `5 == 5` | `True` |
| `!=` | Not equal to | `5 != 3` | `True` |
| `>` | Greater than | `8 > 5` | `True` |
| `<` | Less than | `3 < 7` | `True` |
| `>=` | Greater than or equal | `5 >= 5` | `True` |
| `<=` | Less than or equal | `4 <= 6` | `True` |

### Examples:
```python
age = 18
required_age = 21

print(age == required_age)  # False
print(age != required_age)  # True
print(age > required_age)   # False
print(age < required_age)   # True
print(age >= 18)           # True
print(age <= 25)           # True
```

### Real-world example:
```python
# Check if someone can vote
age = 17
voting_age = 18

if age >= voting_age:
    print("You can vote!")
else:
    print("You're too young to vote.")
```

## 3. Logical Operators

These operators help you combine multiple conditions or flip True/False values.

| Operator | Description | Example |
|----------|-------------|---------|
| `and` | Both conditions must be True | `True and True` → `True` |
| `or` | At least one condition must be True | `True or False` → `True` |
| `not` | Flips True to False (and vice versa) | `not True` → `False` |

### Truth Tables:

**`and` operator:**
```
True and True   = True
True and False  = False
False and True  = False
False and False = False
```

**`or` operator:**
```
True or True   = True
True or False  = True
False or True  = True
False or False = False
```

**`not` operator:**
```
not True  = False
not False = True
```

### Examples:
```python
age = 20
has_license = True
has_car = False

# Using 'and' - both conditions must be true
can_drive_legally = age >= 18 and has_license
print(can_drive_legally)  # True

# Using 'or' - at least one condition must be true
can_travel = has_car or age >= 18  # Can use public transport if 18+
print(can_travel)  # True

# Using 'not' - flips the boolean value
is_minor = not (age >= 18)
print(is_minor)  # False
```

### Real-world example:
```python
# Bank loan approval system
income = 50000
credit_score = 750
has_job = True

# Loan approved if: good credit AND (high income OR has job)
loan_approved = credit_score >= 700 and (income >= 40000 or has_job)
print(f"Loan approved: {loan_approved}")  # True
```

## 4. Assignment Operators

These operators assign values to variables and can perform operations at the same time.

| Operator | Same as | Example | Result |
|----------|---------|---------|---------|
| `=` | | `x = 5` | `x` becomes `5` |
| `+=` | `x = x + value` | `x += 3` | `x` becomes `x + 3` |
| `-=` | `x = x - value` | `x -= 2` | `x` becomes `x - 2` |
| `*=` | `x = x * value` | `x *= 4` | `x` becomes `x * 4` |
| `/=` | `x = x / value` | `x /= 2` | `x` becomes `x / 2` |
| `%=` | `x = x % value` | `x %= 3` | `x` becomes `x % 3` |
| `**=` | `x = x ** value` | `x **= 2` | `x` becomes `x ** 2` |

### Examples:
```python
# Basic assignment
score = 100

# Compound assignments
score += 10    # Same as: score = score + 10
print(score)   # 110

score -= 5     # Same as: score = score - 5
print(score)   # 105

score *= 2     # Same as: score = score * 2
print(score)   # 210

score /= 3     # Same as: score = score / 3
print(score)   # 70.0
```

### Real-world example:
```python
# Shopping cart total
total = 0.0

# Adding items to cart
total += 15.99  # Add shirt
total += 29.50  # Add jeans
total += 8.75   # Add socks

print(f"Cart total: ${total:.2f}")  # Cart total: $54.24

# Apply 10% discount
total *= 0.9
print(f"After discount: ${total:.2f}")  # After discount: $48.82
```

## 5. Operator Precedence

When you have multiple operators in one expression, Python follows a specific order (just like in math class!).

**Order from highest to lowest priority:**
1. `**` (Power)
2. `*`, `/`, `//`, `%` (Multiplication, Division)
3. `+`, `-` (Addition, Subtraction)
4. `==`, `!=`, `>`, `<`, `>=`, `<=` (Comparison)
5. `not` (Logical NOT)
6. `and` (Logical AND)
7. `or` (Logical OR)

### Examples:
```python
# Without parentheses - follows precedence rules
result = 2 + 3 * 4    # 3 * 4 happens first, then + 2
print(result)         # 14 (not 20!)

# With parentheses - forces order
result = (2 + 3) * 4  # Parentheses first, then multiplication
print(result)         # 20

# Complex example
result = 10 + 5 * 2 ** 3 - 4 / 2
# Step by step:
# 1. 2 ** 3 = 8
# 2. 5 * 8 = 40
# 3. 4 / 2 = 2.0
# 4. 10 + 40 = 50
# 5. 50 - 2.0 = 48.0
print(result)  # 48.0
```

### Best Practice:
**Always use parentheses when you're unsure!** It makes your code clearer and prevents mistakes.

```python
# Hard to read
total = price + price * tax_rate + shipping

# Clear and easy to understand
total = price + (price * tax_rate) + shipping
```

## Practice Exercises

Try these exercises to test your understanding:

### Exercise 1: Calculator
```python
# Create a simple calculator
num1 = float(input("Enter first number: "))
num2 = float(input("Enter second number: "))

print(f"{num1} + {num2} = {num1 + num2}")
print(f"{num1} - {num2} = {num1 - num2}")
print(f"{num1} * {num2} = {num1 * num2}")
print(f"{num1} / {num2} = {num1 / num2}")
```

### Exercise 2: Grade Checker
```python
# Check if a student passes (needs >= 60% AND >= 50% attendance)
grade = float(input("Enter your grade: "))
attendance = float(input("Enter your attendance percentage: "))

passed = grade >= 60 and attendance >= 50
print(f"Did you pass? {passed}")
```

### Exercise 3: Even or Odd
```python
# Check if a number is even or odd using modulus operator
number = int(input("Enter a number: "))
is_even = number % 2 == 0

print(f"{number} is {'even' if is_even else 'odd'}")
```

## Summary

- **Arithmetic operators** do math calculations
- **Comparison operators** compare values and return True/False
- **Logical operators** combine or flip boolean values
- **Assignment operators** store values and perform operations
- **Operator precedence** determines the order of operations
- Use **parentheses** to make your code clear and control the order

Remember: Practice makes perfect! Try using these operators in your own programs to get comfortable with them.