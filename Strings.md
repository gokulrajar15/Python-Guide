
# Python Strings

Strings are sequences of characters used to represent text in Python. They're one of the most commonly used data types and are essential for handling any kind of textual data.

## What are Strings?

A string is a collection of characters enclosed in quotes. Think of it as a sequence of letters, numbers, symbols, and spaces that form words, sentences, or any text.

```python
# Different ways to create strings
name = "Alice"           # Double quotes
city = 'New York'        # Single quotes
message = """This is a
multi-line string"""     # Triple quotes for multiple lines

print(name)     # Alice
print(city)     # New York
print(message)  # This is a
                # multi-line string
```

## Creating Strings

### Single vs Double Quotes
Both single (`'`) and double (`"`) quotes work the same way. Choose one style and be consistent!

```python
# These are identical
greeting1 = "Hello, World!"
greeting2 = 'Hello, World!'

print(greeting1 == greeting2)  # True

# Use different quotes when you need quotes inside the string
sentence1 = "She said, 'Hello there!'"
sentence2 = 'He replied, "Nice to meet you!"'

print(sentence1)  # She said, 'Hello there!'
print(sentence2)  # He replied, "Nice to meet you!"
```

### Triple Quotes for Multi-line Strings
Use triple quotes (`"""` or `'''`) for strings that span multiple lines:

```python
poem = """Roses are red,
Violets are blue,
Python is awesome,
And so are you!"""

print(poem)

# Also useful for docstrings (documentation)
def greet(name):
    """
    This function greets a person
    with their name.
    """
    return f"Hello, {name}!"
```

### Escape Characters
Use backslash (`\`) to include special characters:

```python
# Common escape characters
text = "Line 1\nLine 2"          # \n = new line
path = "C:\\Users\\Documents"     # \\ = backslash
quote = "He said, \"Hello!\""     # \" = double quote
tab_text = "Name:\tJohn"          # \t = tab

print(text)    # Line 1
               # Line 2
print(path)    # C:\Users\Documents
print(quote)   # He said, "Hello!"
print(tab_text) # Name:    John
```

## String Indexing and Slicing

### Indexing
Access individual characters using square brackets. Python uses **0-based indexing**!

```python
word = "Python"

# Positive indexing (left to right)
print(word[0])   # P (first character)
print(word[1])   # y
print(word[2])   # t
print(word[5])   # n (last character)

# Negative indexing (right to left)
print(word[-1])  # n (last character)
print(word[-2])  # o (second to last)
print(word[-6])  # P (first character)
```

### Slicing
Extract parts of a string using `[start:end]` notation:

```python
text = "Hello, World!"

# Basic slicing [start:end] (end is not included)
print(text[0:5])    # Hello
print(text[7:12])   # World
print(text[7:])     # World! (from index 7 to end)
print(text[:5])     # Hello (from start to index 5)
print(text[:])      # Hello, World! (entire string)

# Negative slicing
print(text[-6:-1])  # World (from 6th last to 2nd last)
print(text[-6:])    # World! (from 6th last to end)

# Step slicing [start:end:step]
print(text[::2])    # Hlo ol! (every 2nd character)
print(text[::-1])   # !dlroW ,olleH (reverse string)
```

### Visual Example
```
String: "Python"
Index:   0 1 2 3 4 5    (positive)
        -6-5-4-3-2-1    (negative)

word[1:4] → "yth"    (characters at index 1, 2, 3)
word[2:]  → "thon"   (from index 2 to end)
word[:3]  → "Pyt"    (from start to index 3)
word[-3:] → "hon"    (last 3 characters)
```

## String Methods

Python strings have many built-in methods for manipulation:

### Case Methods
```python
text = "Hello World"

print(text.lower())      # hello world
print(text.upper())      # HELLO WORLD
print(text.title())      # Hello World
print(text.capitalize()) # Hello world
print(text.swapcase())   # hELLO wORLD

# Checking case
print(text.islower())    # False
print(text.isupper())    # False
print(text.istitle())    # True
```

### Finding and Checking
```python
sentence = "Python is awesome and Python is fun"

# Finding substrings
print(sentence.find("Python"))     # 0 (first occurrence)
print(sentence.find("is"))         # 7 (first occurrence)
print(sentence.find("Java"))       # -1 (not found)
print(sentence.count("Python"))    # 2 (appears twice)

# Checking content
print(sentence.startswith("Python"))  # True
print(sentence.endswith("fun"))       # True
print("123".isdigit())               # True
print("abc".isalpha())               # True
print("abc123".isalnum())            # True
```

### Splitting and Joining
```python
# Splitting strings
sentence = "apple,banana,cherry"
fruits = sentence.split(",")
print(fruits)  # ['apple', 'banana', 'cherry']

words = "Hello world Python"
word_list = words.split()  # Split by whitespace (default)
print(word_list)  # ['Hello', 'world', 'Python']

# Joining strings
fruits = ["apple", "banana", "cherry"]
result = ", ".join(fruits)
print(result)  # apple, banana, cherry

numbers = ["1", "2", "3", "4", "5"]
number_string = "-".join(numbers)
print(number_string)  # 1-2-3-4-5
```

### Cleaning Strings
```python
text = "  Hello World  "

print(text.strip())      # "Hello World" (remove spaces from both ends)
print(text.lstrip())     # "Hello World  " (remove from left)
print(text.rstrip())     # "  Hello World" (remove from right)

# Remove specific characters
data = "###Hello World###"
print(data.strip("#"))   # "Hello World"

# Replace text
message = "I love Java programming"
new_message = message.replace("Java", "Python")
print(new_message)  # I love Python programming
```

## String Formatting

### 1. f-strings (Recommended - Python 3.6+)
The most modern and readable way to format strings:

```python
name = "Alice"
age = 25
score = 95.67

# Basic f-string formatting
message = f"Hello, my name is {name} and I am {age} years old"
print(message)

# With expressions
print(f"{name} will be {age + 1} years old next year")

# Formatting numbers
print(f"Score: {score:.1f}%")     # Score: 95.7%
print(f"Score: {score:.2f}%")     # Score: 95.67%

# Formatting with width and alignment
print(f"|{name:>10}|")           # |     Alice| (right-aligned, width 10)
print(f"|{name:<10}|")           # |Alice     | (left-aligned, width 10)
print(f"|{name:^10}|")           # |  Alice   | (center-aligned, width 10)
```

### 2. .format() Method
```python
name = "Bob"
age = 30

# Basic formatting
message = "Hello, my name is {} and I am {} years old".format(name, age)
print(message)

# With indices
message = "Hello, my name is {0} and I am {1} years old".format(name, age)
print(message)

# With named placeholders
message = "Hello, my name is {name} and I am {age} years old".format(name=name, age=age)
print(message)
```

### 3. % Formatting (Old style)
```python
name = "Charlie"
age = 35

message = "Hello, my name is %s and I am %d years old" % (name, age)
print(message)
```

## Real-World Examples

### Example 1: Name Formatter
```python
def format_name(first, last):
    """Format a person's name properly"""
    # Convert to title case and strip whitespace
    first = first.strip().title()
    last = last.strip().title()
    return f"{first} {last}"

# Test the function
name = format_name("  alice  ", "  johnson  ")
print(name)  # Alice Johnson
```

### Example 2: Email Validator (Basic)
```python
def is_valid_email(email):
    """Basic email validation"""
    email = email.strip().lower()
    
    # Check if @ symbol is present and not at start/end
    if email.count("@") != 1:
        return False
    
    # Split by @ symbol
    parts = email.split("@")
    username, domain = parts[0], parts[1]
    
    # Basic checks
    if len(username) == 0 or len(domain) == 0:
        return False
    
    if "." not in domain:
        return False
    
    return True

# Test the validator
emails = ["user@example.com", "invalid.email", "user@@domain.com"]
for email in emails:
    print(f"{email}: {is_valid_email(email)}")
```

### Example 3: Text Statistics
```python
def analyze_text(text):
    """Analyze text and return statistics"""
    # Clean the text
    cleaned = text.strip()
    
    # Calculate statistics
    char_count = len(cleaned)
    word_count = len(cleaned.split())
    sentence_count = cleaned.count('.') + cleaned.count('!') + cleaned.count('?')
    
    # Create report
    report = f"""
Text Analysis Report:
====================
Characters: {char_count}
Words: {word_count}
Sentences: {sentence_count}
Average words per sentence: {word_count/sentence_count:.1f}
"""
    
    return report

# Test the analyzer
sample_text = "Hello world! This is a sample text. How are you today?"
print(analyze_text(sample_text))
```

### Example 4: Password Generator
```python
import random
import string

def generate_password(length=12):
    """Generate a random password"""
    # Define character sets
    lowercase = string.ascii_lowercase
    uppercase = string.ascii_uppercase
    digits = string.digits
    symbols = "!@#$%^&*"
    
    # Combine all characters
    all_chars = lowercase + uppercase + digits + symbols
    
    # Generate password
    password = ''.join(random.choice(all_chars) for _ in range(length))
    
    return password

# Generate passwords
for i in range(3):
    password = generate_password(10)
    print(f"Password {i+1}: {password}")
```

## String Immutability

**Important**: Strings in Python are **immutable** - they cannot be changed after creation!

```python
text = "Hello"

# This doesn't change the original string
# text[0] = "h"  # This would cause an ERROR!

# Instead, create a new string
new_text = "h" + text[1:]  # "hello"
print(text)      # Hello (original unchanged)
print(new_text)  # hello (new string)

# String methods also return new strings
original = "python"
uppercase = original.upper()  # Creates new string
print(original)   # python (unchanged)
print(uppercase)  # PYTHON (new string)
```

## Common String Operations

### Checking String Content
```python
def validate_input(text):
    """Validate user input"""
    if not text:
        return "Input cannot be empty"
    
    if not text.strip():
        return "Input cannot be just whitespace"
    
    if len(text) < 3:
        return "Input must be at least 3 characters"
    
    if text.isdigit():
        return "Input cannot be just numbers"
    
    return "Valid input"

# Test validation
inputs = ["Hello", "  ", "Hi", "123", ""]
for inp in inputs:
    print(f"'{inp}': {validate_input(inp)}")
```

### String Comparison
```python
# String comparison is case-sensitive
print("hello" == "Hello")     # False
print("hello" == "hello")     # True

# Case-insensitive comparison
def compare_ignore_case(str1, str2):
    return str1.lower() == str2.lower()

print(compare_ignore_case("Hello", "HELLO"))  # True

# Sorting strings
names = ["Charlie", "alice", "Bob"]
print(sorted(names))                    # ['Bob', 'Charlie', 'alice']
print(sorted(names, key=str.lower))     # ['alice', 'Bob', 'Charlie']
```

## Practice Exercises

### Exercise 1: Text Cleaner
```python
# Create a function that cleans text by:
# - Removing extra whitespace
# - Converting to proper title case
# - Removing special characters except spaces

def clean_text(text):
    # Your code here
    pass

# Test
messy_text = "  hello    WORLD!!!   how are YOU??  "
# Expected output: "Hello World How Are You"
```

### Exercise 2: Word Counter
```python
# Create a function that counts word frequency in a text
def count_words(text):
    # Your code here
    pass

# Test
sample = "python is great and python is fun python rocks"
# Expected output: {'python': 3, 'is': 2, 'great': 1, 'and': 1, 'fun': 1, 'rocks': 1}
```

### Exercise 3: Palindrome Checker
```python
# Check if a string is a palindrome (reads the same forwards and backwards)
def is_palindrome(text):
    # Your code here
    pass

# Test
test_strings = ["racecar", "hello", "A man a plan a canal Panama"]
# Expected: True, False, True (ignoring spaces and case)
```

### Exercise 4: String Encoder
```python
# Create a simple Caesar cipher encoder
def encode_message(message, shift=3):
    # Your code here
    pass

# Test
original = "Hello World"
encoded = encode_message(original, 3)
print(f"Original: {original}")
print(f"Encoded: {encoded}")
```

## Summary

In this section, you learned:

- ✅ **Creating strings** with different quote types
- ✅ **Indexing and slicing** to access parts of strings
- ✅ **String methods** for manipulation and analysis
- ✅ **String formatting** with f-strings, .format(), and % formatting
- ✅ **String immutability** and why it matters
- ✅ **Real-world applications** of string processing
- ✅ **Common operations** for text validation and comparison

### Key Takeaways:
- Strings are **immutable** - operations create new strings
- **f-strings** are the recommended way to format strings in modern Python
- **Indexing starts at 0**, and negative indices count from the end
- String **methods are powerful** tools for text processing
- Always **validate and clean** user input

**Next:** Continue to learn about Conditional Statements to make decisions in your programs!
