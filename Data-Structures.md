# Python Data Structures

Data structures are ways to organize and store data so you can use it efficiently. Python provides four built-in data structures that are essential for every programmer: **Lists**, **Tuples**, **Sets**, and **Dictionaries**.

## What are Data Structures?

Think of data structures as different types of containers:
- **List**: Like a shopping list - ordered items you can modify
- **Tuple**: Like a coordinate (x,y) - ordered items you cannot change
- **Set**: Like a bag of unique marbles - no duplicates, no specific order
- **Dictionary**: Like a phone book - pairs of names and phone numbers

```python
# Quick overview of all four data structures
my_list = ["apple", "banana", "cherry"]          # List - ordered, changeable
my_tuple = ("red", "green", "blue")              # Tuple - ordered, unchangeable
my_set = {"cat", "dog", "bird"}                  # Set - unordered, no duplicates
my_dict = {"name": "Alice", "age": 25}           # Dictionary - key-value pairs

print("List:", my_list)
print("Tuple:", my_tuple)
print("Set:", my_set)
print("Dictionary:", my_dict)
```

---

## 1. Lists

Lists are **ordered collections** that can store multiple items. They are **mutable** (changeable) and can contain different data types.

### Creating Lists

```python
# Different ways to create lists
empty_list = []                           # Empty list
fruits = ["apple", "banana", "cherry"]    # List with strings
numbers = [1, 2, 3, 4, 5]                # List with numbers
mixed = ["Alice", 25, True, 3.14]        # List with different types
nested = [[1, 2], [3, 4], [5, 6]]        # List of lists

print(fruits)    # ['apple', 'banana', 'cherry']
print(numbers)   # [1, 2, 3, 4, 5]
print(mixed)     # ['Alice', 25, True, 3.14]
print(nested)    # [[1, 2], [3, 4], [5, 6]]
```

### Accessing List Elements

```python
fruits = ["apple", "banana", "cherry", "date", "elderberry"]

# Positive indexing (0-based)
print(fruits[0])    # apple (first item)
print(fruits[1])    # banana
print(fruits[4])    # elderberry (last item)

# Negative indexing (from the end)
print(fruits[-1])   # elderberry (last item)
print(fruits[-2])   # date (second to last)

# Slicing [start:end:step]
print(fruits[1:4])     # ['banana', 'cherry', 'date']
print(fruits[:3])      # ['apple', 'banana', 'cherry'] (first 3)
print(fruits[2:])      # ['cherry', 'date', 'elderberry'] (from index 2)
print(fruits[::2])     # ['apple', 'cherry', 'elderberry'] (every 2nd item)
print(fruits[::-1])    # ['elderberry', 'date', 'cherry', 'banana', 'apple'] (reversed)
```

### List Methods

```python
# Starting with a list
fruits = ["apple", "banana"]

# Adding items
fruits.append("cherry")           # Add one item at the end
print(fruits)  # ['apple', 'banana', 'cherry']

fruits.insert(1, "orange")       # Insert at specific position
print(fruits)  # ['apple', 'orange', 'banana', 'cherry']

fruits.extend(["grape", "kiwi"])  # Add multiple items
print(fruits)  # ['apple', 'orange', 'banana', 'cherry', 'grape', 'kiwi']

# Removing items
fruits.remove("orange")           # Remove first occurrence
print(fruits)  # ['apple', 'banana', 'cherry', 'grape', 'kiwi']

removed_item = fruits.pop()       # Remove and return last item
print(f"Removed: {removed_item}") # Removed: kiwi
print(fruits)  # ['apple', 'banana', 'cherry', 'grape']

removed_at_index = fruits.pop(1)  # Remove and return item at index
print(f"Removed: {removed_at_index}") # Removed: banana
print(fruits)  # ['apple', 'cherry', 'grape']

# Finding items
print(fruits.index("cherry"))     # 1 (position of cherry)
print(fruits.count("apple"))      # 1 (how many times apple appears)

# Sorting and organizing
numbers = [3, 1, 4, 1, 5, 9, 2]
numbers.sort()                    # Sort in place
print(numbers)  # [1, 1, 2, 3, 4, 5, 9]

fruits.reverse()                  # Reverse in place
print(fruits)  # ['grape', 'cherry', 'apple']

# Getting list info
print(len(fruits))                # 3 (length of list)
print("apple" in fruits)          # True (check if item exists)
```

### List Comprehensions (Advanced)

```python
# Create lists using comprehensions
numbers = [1, 2, 3, 4, 5]

# Traditional way
squares = []
for num in numbers:
    squares.append(num ** 2)
print(squares)  # [1, 4, 9, 16, 25]

# List comprehension way (more Pythonic)
squares = [num ** 2 for num in numbers]
print(squares)  # [1, 4, 9, 16, 25]

# With conditions
even_squares = [num ** 2 for num in numbers if num % 2 == 0]
print(even_squares)  # [4, 16] (squares of even numbers only)
```

---

## 2. Tuples

Tuples are **ordered collections** like lists, but they are **immutable** (cannot be changed after creation). Perfect for storing related data that shouldn't change.

### Creating Tuples

```python
# Different ways to create tuples
empty_tuple = ()                          # Empty tuple
single_item = (42,)                       # Single item (comma needed!)
coordinates = (10, 20)                    # Two items
colors = ("red", "green", "blue")         # Multiple items
mixed_tuple = ("Alice", 25, True)         # Different types
nested_tuple = ((1, 2), (3, 4))          # Nested tuples

# Parentheses are optional (but recommended for clarity)
point = 5, 10                             # Same as (5, 10)

print(coordinates)    # (10, 20)
print(colors)         # ('red', 'green', 'blue')
print(point)          # (5, 10)
```

### Accessing Tuple Elements

```python
colors = ("red", "green", "blue", "yellow", "purple")

# Indexing (same as lists)
print(colors[0])      # red
print(colors[-1])     # purple

# Slicing (same as lists)
print(colors[1:4])    # ('green', 'blue', 'yellow')
print(colors[:2])     # ('red', 'green')
print(colors[2:])     # ('blue', 'yellow', 'purple')

# Tuple unpacking (very useful!)
point = (10, 20)
x, y = point          # Assign values to variables
print(f"X: {x}, Y: {y}")  # X: 10, Y: 20

# Unpacking with more values
person = ("Alice", 25, "Engineer")
name, age, job = person
print(f"{name} is {age} years old and works as an {job}")
```

### Tuple Methods

```python
numbers = (1, 2, 3, 2, 4, 2, 5)

# Limited methods (tuples are immutable)
print(numbers.count(2))      # 3 (how many times 2 appears)
print(numbers.index(4))      # 4 (position of first 4)

# Useful operations
print(len(numbers))          # 7 (length)
print(3 in numbers)          # True (check if item exists)
print(max(numbers))          # 5 (maximum value)
print(min(numbers))          # 1 (minimum value)
print(sum(numbers))          # 19 (sum of all numbers)

# Converting between lists and tuples
my_list = [1, 2, 3]
my_tuple = tuple(my_list)    # Convert list to tuple
back_to_list = list(my_tuple) # Convert tuple back to list

print(f"List: {my_list}")
print(f"Tuple: {my_tuple}")
print(f"Back to list: {back_to_list}")
```

### When to Use Tuples

```python
# Good uses for tuples:

# 1. Coordinates and points
point_2d = (10, 20)
point_3d = (10, 20, 30)

# 2. RGB color values
red = (255, 0, 0)
green = (0, 255, 0)
blue = (0, 0, 255)

# 3. Database records
student = ("Alice", 20, "Computer Science", 3.8)

# 4. Function returning multiple values
def get_name_age():
    return "Bob", 25  # Returns a tuple

name, age = get_name_age()  # Unpack the tuple

# 5. Dictionary keys (tuples can be keys, lists cannot)
locations = {
    (0, 0): "Origin",
    (10, 20): "Point A",
    (30, 40): "Point B"
}
```

---

## 3. Sets

Sets are **unordered collections** of **unique items**. No duplicates allowed! Perfect for removing duplicates and mathematical operations.

### Creating Sets

```python
# Different ways to create sets
empty_set = set()                         # Empty set (not {} - that's a dict!)
fruits = {"apple", "banana", "cherry"}    # Set with curly braces
numbers = {1, 2, 3, 4, 5}                # Set of numbers

# Creating from other collections
list_with_duplicates = [1, 2, 2, 3, 3, 3, 4, 5]
unique_numbers = set(list_with_duplicates)
print(unique_numbers)  # {1, 2, 3, 4, 5} (duplicates removed)

# Sets automatically remove duplicates
duplicate_fruits = {"apple", "banana", "apple", "cherry", "banana"}
print(duplicate_fruits)  # {'banana', 'cherry', 'apple'} (order may vary)
```

### Set Operations

```python
fruits = {"apple", "banana", "cherry"}

# Adding items
fruits.add("date")                # Add single item
print(fruits)  # {'apple', 'banana', 'cherry', 'date'}

fruits.update(["elderberry", "fig"])  # Add multiple items
print(fruits)  # {'apple', 'banana', 'cherry', 'date', 'elderberry', 'fig'}

# Removing items
fruits.remove("banana")           # Remove item (raises error if not found)
print(fruits)  # {'apple', 'cherry', 'date', 'elderberry', 'fig'}

fruits.discard("grape")           # Remove item (no error if not found)
print(fruits)  # Same as before (grape wasn't there)

removed_item = fruits.pop()       # Remove and return random item
print(f"Removed: {removed_item}")

# Checking membership
print("apple" in fruits)          # True
print(len(fruits))                # Number of items in set
```

### Mathematical Set Operations

```python
# Set operations (like in mathematics)
set_a = {1, 2, 3, 4, 5}
set_b = {4, 5, 6, 7, 8}

# Union (all items from both sets)
union_result = set_a | set_b      # or set_a.union(set_b)
print(f"Union: {union_result}")   # {1, 2, 3, 4, 5, 6, 7, 8}

# Intersection (items in both sets)
intersection_result = set_a & set_b  # or set_a.intersection(set_b)
print(f"Intersection: {intersection_result}")  # {4, 5}

# Difference (items in first set but not second)
difference_result = set_a - set_b    # or set_a.difference(set_b)
print(f"Difference A-B: {difference_result}")  # {1, 2, 3}

# Symmetric difference (items in either set, but not both)
sym_diff_result = set_a ^ set_b      # or set_a.symmetric_difference(set_b)
print(f"Symmetric difference: {sym_diff_result}")  # {1, 2, 3, 6, 7, 8}
```

### Practical Set Examples

```python
# Example 1: Remove duplicates from a list
shopping_list = ["milk", "bread", "eggs", "milk", "butter", "bread", "cheese"]
unique_items = list(set(shopping_list))
print(f"Original: {shopping_list}")
print(f"Unique: {unique_items}")

# Example 2: Find common interests
alice_hobbies = {"reading", "swimming", "coding", "painting"}
bob_hobbies = {"swimming", "gaming", "coding", "music"}

common_hobbies = alice_hobbies & bob_hobbies
print(f"Alice and Bob both enjoy: {common_hobbies}")

# Example 3: Check if all required skills are present
required_skills = {"Python", "SQL", "Git"}
candidate_skills = {"Python", "Java", "SQL", "Git", "Docker"}

has_all_skills = required_skills.issubset(candidate_skills)
print(f"Candidate has all required skills: {has_all_skills}")
```

---

## 4. Dictionaries

Dictionaries store **key-value pairs**. Think of them as real dictionaries where you look up a word (key) to find its definition (value).

### Creating Dictionaries

```python
# Different ways to create dictionaries
empty_dict = {}                           # Empty dictionary
person = {"name": "Alice", "age": 25}     # Dictionary with data

# Different value types
student = {
    "name": "Bob",
    "age": 20,
    "grades": [85, 92, 78],
    "is_enrolled": True
}

# Using dict() constructor
colors = dict(red="#FF0000", green="#00FF00", blue="#0000FF")

# From lists of tuples
pairs = [("a", 1), ("b", 2), ("c", 3)]
letters = dict(pairs)

print(person)    # {'name': 'Alice', 'age': 25}
print(student)   # {'name': 'Bob', 'age': 20, 'grades': [85, 92, 78], 'is_enrolled': True}
print(colors)    # {'red': '#FF0000', 'green': '#00FF00', 'blue': '#0000FF'}
print(letters)   # {'a': 1, 'b': 2, 'c': 3}
```

### Accessing Dictionary Values

```python
person = {
    "name": "Alice",
    "age": 25,
    "city": "New York",
    "occupation": "Engineer"
}

# Accessing values by key
print(person["name"])         # Alice
print(person["age"])          # 25

# Safe access with .get() (returns None if key doesn't exist)
print(person.get("name"))     # Alice
print(person.get("country"))  # None (key doesn't exist)
print(person.get("country", "Unknown"))  # Unknown (default value)

# Check if key exists
print("age" in person)        # True
print("salary" in person)     # False
```

### Dictionary Methods

```python
person = {"name": "Alice", "age": 25}

# Adding/updating values
person["city"] = "New York"              # Add new key-value pair
person["age"] = 26                       # Update existing value
person.update({"occupation": "Engineer", "salary": 75000})  # Add multiple

print(person)  # {'name': 'Alice', 'age': 26, 'city': 'New York', 'occupation': 'Engineer', 'salary': 75000}

# Removing items
removed_salary = person.pop("salary")    # Remove and return value
print(f"Removed salary: {removed_salary}")

del person["city"]                       # Delete key-value pair
print(person)  # {'name': 'Alice', 'age': 26, 'occupation': 'Engineer'}

# Getting dictionary parts
keys = person.keys()                     # Get all keys
values = person.values()                 # Get all values
items = person.items()                   # Get all key-value pairs

print(f"Keys: {list(keys)}")            # ['name', 'age', 'occupation']
print(f"Values: {list(values)}")        # ['Alice', 26, 'Engineer']
print(f"Items: {list(items)}")          # [('name', 'Alice'), ('age', 26), ('occupation', 'Engineer')]
```

### Looping Through Dictionaries

```python
student_grades = {
    "Math": 85,
    "Science": 92,
    "English": 78,
    "History": 88
}

# Loop through keys
print("Subjects:")
for subject in student_grades:
    print(f"- {subject}")

# Loop through values
print("\nGrades:")
for grade in student_grades.values():
    print(f"- {grade}")

# Loop through key-value pairs
print("\nSubject and Grades:")
for subject, grade in student_grades.items():
    print(f"{subject}: {grade}")

# Calculate average grade
total = sum(student_grades.values())
average = total / len(student_grades)
print(f"\nAverage grade: {average:.1f}")
```

### Nested Dictionaries

```python
# Dictionary containing other dictionaries
company = {
    "employees": {
        "alice": {"age": 25, "department": "Engineering", "salary": 75000},
        "bob": {"age": 30, "department": "Marketing", "salary": 65000},
        "charlie": {"age": 35, "department": "Sales", "salary": 70000}
    },
    "departments": {
        "Engineering": {"budget": 500000, "head": "alice"},
        "Marketing": {"budget": 300000, "head": "bob"},
        "Sales": {"budget": 400000, "head": "charlie"}
    }
}

# Accessing nested data
print(company["employees"]["alice"]["age"])           # 25
print(company["departments"]["Engineering"]["budget"]) # 500000

# Adding to nested structure
company["employees"]["diana"] = {
    "age": 28,
    "department": "HR",
    "salary": 60000
}

print(f"Diana's info: {company['employees']['diana']}")
```

---

## Real-World Examples

### Example 1: Contact Book
```python
# Contact book using dictionary
contacts = {
    "Alice": {"phone": "555-0001", "email": "alice@email.com", "city": "New York"},
    "Bob": {"phone": "555-0002", "email": "bob@email.com", "city": "Los Angeles"},
    "Charlie": {"phone": "555-0003", "email": "charlie@email.com", "city": "Chicago"}
}

# Function to display contact info
def show_contact(name):
    if name in contacts:
        info = contacts[name]
        print(f"\n{name}'s Contact Information:")
        print(f"Phone: {info['phone']}")
        print(f"Email: {info['email']}")
        print(f"City: {info['city']}")
    else:
        print(f"Contact '{name}' not found.")

# Function to add new contact
def add_contact(name, phone, email, city):
    contacts[name] = {"phone": phone, "email": email, "city": city}
    print(f"Added {name} to contacts.")

# Usage examples
show_contact("Alice")
add_contact("Diana", "555-0004", "diana@email.com", "Miami")
show_contact("Diana")
```

### Example 2: Inventory Management
```python
# Store inventory using different data structures
inventory = {
    "fruits": ["apple", "banana", "orange", "grape"],
    "quantities": {"apple": 50, "banana": 30, "orange": 25, "grape": 40},
    "prices": {"apple": 1.20, "banana": 0.80, "orange": 1.50, "grape": 2.00}
}

# Function to show inventory
def show_inventory():
    print("Current Inventory:")
    print("-" * 30)
    for fruit in inventory["fruits"]:
        qty = inventory["quantities"][fruit]
        price = inventory["prices"][fruit]
        total_value = qty * price
        print(f"{fruit.capitalize():10} | Qty: {qty:2} | Price: ${price:.2f} | Value: ${total_value:.2f}")

# Function to calculate total inventory value
def calculate_total_value():
    total = 0
    for fruit in inventory["fruits"]:
        qty = inventory["quantities"][fruit]
        price = inventory["prices"][fruit]
        total += qty * price
    return total

# Usage
show_inventory()
print(f"\nTotal Inventory Value: ${calculate_total_value():.2f}")
```

### Example 3: Student Grade Tracker
```python
# Grade tracking system combining all data structures
class_grades = {
    "Alice": [85, 92, 78, 90],
    "Bob": [76, 88, 82, 85],
    "Charlie": [91, 87, 94, 89],
    "Diana": [88, 90, 85, 92]
}

# Calculate individual student average
def student_average(student_name):
    if student_name in class_grades:
        grades = class_grades[student_name]
        return sum(grades) / len(grades)
    return None

# Find class statistics
def class_statistics():
    all_averages = []
    
    print("Student Grade Report:")
    print("=" * 40)
    
    for student, grades in class_grades.items():
        average = sum(grades) / len(grades)
        all_averages.append(average)
        
        # Convert grades list to tuple for display
        grade_tuple = tuple(grades)
        print(f"{student:10} | Grades: {grade_tuple} | Average: {average:.1f}")
    
    # Class statistics using set operations
    all_grades = []
    for grades in class_grades.values():
        all_grades.extend(grades)
    
    unique_grades = set(all_grades)
    
    print("\nClass Statistics:")
    print(f"Class Average: {sum(all_averages) / len(all_averages):.1f}")
    print(f"Highest Grade: {max(all_grades)}")
    print(f"Lowest Grade: {min(all_grades)}")
    print(f"Unique Grades Given: {sorted(unique_grades)}")

# Usage
class_statistics()
```

---

## Choosing the Right Data Structure

| **Use Case** | **Best Choice** | **Why** |
|--------------|----------------|---------|
| Shopping list that changes | **List** | Ordered, can add/remove items |
| GPS coordinates | **Tuple** | Fixed pair of values, won't change |
| Unique user IDs | **Set** | No duplicates, fast membership testing |
| User profile information | **Dictionary** | Key-value pairs, easy lookup |
| Configuration settings | **Dictionary** | Named settings with values |
| RGB color values | **Tuple** | Fixed set of 3 values |
| Collection of unique tags | **Set** | No duplicate tags |
| Menu items with prices | **Dictionary** | Item name → price mapping |

### Performance Comparison

```python
# Quick performance comparison example
import time

# List vs Set for membership testing
large_list = list(range(10000))
large_set = set(range(10000))

# Test finding item 9999
start_time = time.time()
9999 in large_list  # Slow - checks each item
list_time = time.time() - start_time

start_time = time.time()
9999 in large_set   # Fast - hash lookup
set_time = time.time() - start_time

print(f"List search time: {list_time:.6f} seconds")
print(f"Set search time: {set_time:.6f} seconds")
print(f"Set is {list_time/set_time:.1f}x faster for membership testing!")
```

---

## Practice Exercises

### Exercise 1: List Manipulation
```python
# Starting list of numbers
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

# Your tasks:
# 1. Create a new list with only even numbers
# 2. Create a new list with squares of odd numbers
# 3. Find the sum of all numbers greater than 5

# Write your solutions here:
even_numbers = # Your code here
odd_squares = # Your code here
sum_greater_than_5 = # Your code here

print(f"Original: {numbers}")
print(f"Even numbers: {even_numbers}")
print(f"Odd squares: {odd_squares}")
print(f"Sum > 5: {sum_greater_than_5}")

# Expected output:
# Even numbers: [2, 4, 6, 8, 10]
# Odd squares: [1, 9, 25, 49, 81]
# Sum > 5: 40
```

### Exercise 2: Tuple Operations
```python
# Student data as tuples
students = [
    ("Alice", 85, "Computer Science"),
    ("Bob", 78, "Mathematics"),
    ("Charlie", 92, "Physics"),
    ("Diana", 88, "Computer Science"),
    ("Eve", 76, "Mathematics")
]

# Your tasks:
# 1. Find all students in "Computer Science"
# 2. Calculate the average grade of all students
# 3. Find the student with the highest grade
# 4. Create a list of just the names

# Write your solutions here:
cs_students = # Your code here
average_grade = # Your code here
top_student = # Your code here
student_names = # Your code here

print(f"CS Students: {cs_students}")
print(f"Average Grade: {average_grade:.1f}")
print(f"Top Student: {top_student}")
print(f"All Names: {student_names}")
```

### Exercise 3: Set Operations
```python
# Movie preferences
alice_movies = {"Inception", "The Matrix", "Interstellar", "The Prestige", "Memento"}
bob_movies = {"The Matrix", "Avatar", "Inception", "Titanic", "The Dark Knight"}
charlie_movies = {"Interstellar", "Avatar", "The Prestige", "Gravity", "Martian"}

# Your tasks:
# 1. Find movies all three friends like
# 2. Find movies only Alice likes
# 3. Find movies at least two friends like
# 4. Create a set of all unique movies

# Write your solutions here:
all_three_like = # Your code here
only_alice_likes = # Your code here
at_least_two_like = # Your code here
all_unique_movies = # Your code here

print(f"All three like: {all_three_like}")
print(f"Only Alice likes: {only_alice_likes}")
print(f"At least two like: {at_least_two_like}")
print(f"Total unique movies: {len(all_unique_movies)}")
```

### Exercise 4: Dictionary Practice
```python
# Sales data for a small store
sales_data = {
    "Monday": {"coffee": 23, "tea": 15, "pastry": 18},
    "Tuesday": {"coffee": 31, "tea": 12, "pastry": 22},
    "Wednesday": {"coffee": 28, "tea": 18, "pastry": 15},
    "Thursday": {"coffee": 35, "tea": 14, "pastry": 25},
    "Friday": {"coffee": 42, "tea": 20, "pastry": 30}
}

# Your tasks:
# 1. Calculate total sales for each day
# 2. Find which day had the highest coffee sales
# 3. Calculate average daily sales for each item
# 4. Find the total week's revenue (coffee=$3, tea=$2, pastry=$4)

# Write your solutions here:
daily_totals = {}  # Your code here
best_coffee_day = # Your code here
item_averages = {}  # Your code here
total_revenue = # Your code here

print("Daily totals:")
for day, total in daily_totals.items():
    print(f"  {day}: {total} items")

print(f"\nBest coffee day: {best_coffee_day}")
print(f"Item averages: {item_averages}")
print(f"Total week revenue: ${total_revenue}")
```

### Exercise 5: Combined Challenge
```python
# Library book management system
# Using all data structures together

library_books = [
    {"title": "Python Programming", "author": "John Doe", "genre": "Technology", "available": True},
    {"title": "Data Science Basics", "author": "Jane Smith", "genre": "Technology", "available": False},
    {"title": "The Great Novel", "author": "Bob Writer", "genre": "Fiction", "available": True},
    {"title": "History Matters", "author": "Alice Historian", "genre": "History", "available": True},
    {"title": "Python Advanced", "author": "John Doe", "genre": "Technology", "available": False}
]

# Your tasks:
# 1. Create a set of all unique authors
# 2. Create a dictionary grouping books by genre
# 3. Find all available books (return list of titles)
# 4. Count books per author (return dictionary)
# 5. Find the most popular genre (genre with most books)

# Write your solutions here:
unique_authors = # Your code here
books_by_genre = {}  # Your code here
available_books = # Your code here
books_per_author = {}  # Your code here
most_popular_genre = # Your code here

print(f"Unique authors: {unique_authors}")
print(f"Available books: {available_books}")
print(f"Books per author: {books_per_author}")
print(f"Most popular genre: {most_popular_genre}")
```

## Solutions (Try the exercises first!)

<details>
<summary>Click to see Exercise 1 Solution</summary>

```python
# Exercise 1 Solutions
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

even_numbers = [num for num in numbers if num % 2 == 0]
odd_squares = [num ** 2 for num in numbers if num % 2 == 1]
sum_greater_than_5 = sum([num for num in numbers if num > 5])

print(f"Even numbers: {even_numbers}")      # [2, 4, 6, 8, 10]
print(f"Odd squares: {odd_squares}")        # [1, 9, 25, 49, 81]
print(f"Sum > 5: {sum_greater_than_5}")     # 40
```
</details>

<details>
<summary>Click to see Exercise 2 Solution</summary>

```python
# Exercise 2 Solutions
students = [
    ("Alice", 85, "Computer Science"),
    ("Bob", 78, "Mathematics"),
    ("Charlie", 92, "Physics"),
    ("Diana", 88, "Computer Science"),
    ("Eve", 76, "Mathematics")
]

cs_students = [student for student in students if student[2] == "Computer Science"]
average_grade = sum(student[1] for student in students) / len(students)
top_student = max(students, key=lambda x: x[1])
student_names = [student[0] for student in students]

print(f"CS Students: {cs_students}")         # [('Alice', 85, 'Computer Science'), ('Diana', 88, 'Computer Science')]
print(f"Average Grade: {average_grade:.1f}") # 83.8
print(f"Top Student: {top_student}")         # ('Charlie', 92, 'Physics')
print(f"All Names: {student_names}")         # ['Alice', 'Bob', 'Charlie', 'Diana', 'Eve']
```
</details>

<details>
<summary>Click to see Exercise 3 Solution</summary>

```python
# Exercise 3 Solutions
alice_movies = {"Inception", "The Matrix", "Interstellar", "The Prestige", "Memento"}
bob_movies = {"The Matrix", "Avatar", "Inception", "Titanic", "The Dark Knight"}
charlie_movies = {"Interstellar", "Avatar", "The Prestige", "Gravity", "Martian"}

all_three_like = alice_movies & bob_movies & charlie_movies
only_alice_likes = alice_movies - bob_movies - charlie_movies
at_least_two_like = (alice_movies & bob_movies) | (alice_movies & charlie_movies) | (bob_movies & charlie_movies)
all_unique_movies = alice_movies | bob_movies | charlie_movies

print(f"All three like: {all_three_like}")           # set() (no movies all three like)
print(f"Only Alice likes: {only_alice_likes}")       # {'Memento'}
print(f"At least two like: {at_least_two_like}")     # {'Inception', 'The Matrix', 'Interstellar', 'The Prestige', 'Avatar'}
print(f"Total unique movies: {len(all_unique_movies)}") # 10
```
</details>

---

## Summary

In this comprehensive guide, you learned about Python's four essential data structures:

- ✅ **Lists**: Ordered, mutable collections perfect for sequences that change
- ✅ **Tuples**: Ordered, immutable collections ideal for fixed data
- ✅ **Sets**: Unordered collections of unique items, great for eliminating duplicates
- ✅ **Dictionaries**: Key-value pairs perfect for mapping and lookup operations

### Key Takeaways:
- **Choose the right tool**: Each data structure has specific use cases
- **Lists are versatile**: Use for most ordered collections that need modification
- **Tuples are safe**: Use for data that shouldn't change
- **Sets eliminate duplicates**: Perfect for unique collections and mathematical operations
- **Dictionaries map relationships**: Excellent for lookups and structured data

### Next Steps:
- Practice with the exercises to reinforce your learning
- Combine different data structures for complex problems
- Learn about more advanced topics like list comprehensions and dictionary comprehensions
- Explore how to optimize performance by choosing the right data structure

**Next:** Continue to learn about Functions to organize and reuse your code effectively!