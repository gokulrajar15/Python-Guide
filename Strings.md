
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
# Format a person's name properly using string methods
first_name = "  alice  "
last_name = "  johnson  "

# Clean and format the names
first_clean = first_name.strip().title()
last_clean = last_name.strip().title()
full_name = first_clean + " " + last_clean

print(f"Original: '{first_name}' '{last_name}'")
print(f"Formatted: {full_name}")  # Alice Johnson
```

### Example 2: Email Parts Extractor
```python
# Extract username and domain from an email address
email = "user@example.com"

# Clean the email
email_clean = email.strip().lower()

# Find the @ symbol position
at_position = email_clean.find("@")

# Extract parts using slicing
username = email_clean[:at_position]
domain = email_clean[at_position + 1:]

print(f"Email: {email_clean}")
print(f"Username: {username}")
print(f"Domain: {domain}")
print(f"Has @ symbol: {'@' in email_clean}")
print(f"Ends with .com: {email_clean.endswith('.com')}")
```

### Example 3: Text Statistics
```python
# Analyze text using string methods
sample_text = "Hello world! This is a sample text. How are you today?"

# Clean the text
cleaned_text = sample_text.strip()

# Calculate basic statistics
char_count = len(cleaned_text)
word_list = cleaned_text.split()
word_count = len(word_list)
sentence_count = cleaned_text.count('.') + cleaned_text.count('!') + cleaned_text.count('?')

# Display results
print("Text Analysis Report:")
print("====================")
print(f"Original text: {sample_text}")
print(f"Characters: {char_count}")
print(f"Words: {word_count}")
print(f"Sentences: {sentence_count}")
print(f"First word: {word_list[0]}")
print(f"Last word: {word_list[-1]}")
print(f"Contains 'sample': {'sample' in cleaned_text}")
```

### Example 4: Text Formatter
```python
# Format text using string methods
original_text = "python string manipulation"

# Different formatting examples
uppercase_text = original_text.upper()
title_text = original_text.title()
capitalized_text = original_text.capitalize()
reversed_text = original_text[::-1]

# Replace and modify
modified_text = original_text.replace("python", "PYTHON")
spaced_text = original_text.replace(" ", "_")

# Display all formats
print(f"Original: {original_text}")
print(f"Uppercase: {uppercase_text}")
print(f"Title: {title_text}")
print(f"Capitalized: {capitalized_text}")
print(f"Reversed: {reversed_text}")
print(f"Modified: {modified_text}")
print(f"Underscored: {spaced_text}")
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
# Different ways to check string content
user_input = "Hello123"

# Basic checks
print(f"Text: '{user_input}'")
print(f"Length: {len(user_input)}")
print(f"Is empty: {user_input == ''}")
print(f"Has only spaces: {user_input.strip() == ''}")
print(f"Is all digits: {user_input.isdigit()}")
print(f"Is all letters: {user_input.isalpha()}")
print(f"Is alphanumeric: {user_input.isalnum()}")
print(f"Is lowercase: {user_input.islower()}")
print(f"Is uppercase: {user_input.isupper()}")
print(f"Starts with 'Hello': {user_input.startswith('Hello')}")
print(f"Ends with '123': {user_input.endswith('123')}")
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
# Clean and format text using string methods
messy_text = "  hello    WORLD!!!   how are YOU??  "

# Your task: Use string methods to clean this text
# Step 1: Remove extra whitespace from beginning and end
# Step 2: Convert to proper title case
# Step 3: Remove exclamation marks and question marks
# Expected output: "Hello World How Are You"

# Write your solution here:
cleaned = # Your code here
print(f"Original: '{messy_text}'")
print(f"Cleaned: '{cleaned}'")
```

### Exercise 2: Vowel Counter
```python
# Count vowels in a string using string methods
test_text = "Hello World"
vowels = "aeiouAEIOU"

# Your task: Count how many vowels are in the text
# Hint: Use a combination of lower() and counting

# Write your solution here:
vowel_count = # Your code here
print(f"Text: '{test_text}'")
print(f"Vowels found: {vowel_count}")
# Expected output: 3 (e, o, o)
```

### Exercise 3: String Reverser
```python
# Reverse each word in a sentence using string methods
test_sentence = "Hello World Python"

# Your task: Reverse each word but keep the word order
# Hint: Use split(), slicing [::-1], and join()

# Write your solution here:
words = test_sentence.split()
reversed_words = # Your code here
result = # Your code here

print(f"Original: '{test_sentence}'")
print(f"Reversed words: '{result}'")
# Expected output: "olleH dlroW nohtyP"
```

### Exercise 4: Text Analyzer
```python
# Analyze text using basic string methods
test_text = "Python is great for string manipulation"

# Your task: Extract information using string methods
# Find: number of words, longest word, shortest word

# Write your solution here:
words = test_text.split()
word_count = len(words)
longest_word = # Your code here (hint: use max() with key=len)
shortest_word = # Your code here (hint: use min() with key=len)

print(f"Text: '{test_text}'")
print(f"Word count: {word_count}")
print(f"Longest word: '{longest_word}'")
print(f"Shortest word: '{shortest_word}'")
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
