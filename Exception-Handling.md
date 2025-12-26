# Python Exception Handling

Exception handling is like having safety nets in your code! Just like how safety nets catch circus performers if they fall, exception handling catches errors in your program before they crash everything. It helps your program handle unexpected situations gracefully instead of stopping completely.

## What are Exceptions?

In real life, unexpected things happen:
- Your car runs out of gas 🚗
- You try to open a door but it's locked 🚪
- You ask someone their age but they don't answer 🤷

In programming, exceptions are unexpected events that occur while your program is running:
- Dividing by zero
- Opening a file that doesn't exist
- Converting text that isn't a number to an integer

```python
# Without exception handling - program crashes! 💥
number = int(input("Enter a number: "))  # User types "hello"
result = 10 / number
print(f"Result: {result}")
# Program stops with an error!

# With exception handling - program continues! 😊
try:
    number = int(input("Enter a number: "))
    result = 10 / number
    print(f"Result: {result}")
except ValueError:
    print("That's not a valid number!")
except ZeroDivisionError:
    print("Cannot divide by zero!")
print("Program continues running...")
```

## Why Exception Handling is Important

- **Prevents crashes**: Your program keeps running even when errors occur
- **Better user experience**: Show helpful error messages instead of scary technical errors
- **Robust code**: Handle edge cases and unexpected input gracefully
- **Debugging**: Help identify where and why errors occur
- **Professional software**: Real applications must handle errors properly

---

## 1. Basic Exception Handling with `try` and `except`

### The Basic Structure

```python
try:
    # Code that might cause an error
    risky_code()
except:
    # Code to run if an error occurs
    handle_error()
```

### Example 1: Handling Input Errors

```python
# Basic number input with error handling
try:
    age = int(input("Enter your age: "))
    print(f"You are {age} years old")
except:
    print("That's not a valid number!")

# The program continues even if user enters invalid input
print("Thank you for using our program!")
```

### Example 2: Handling Division Errors

```python
# Safe division calculator
try:
    num1 = float(input("Enter first number: "))
    num2 = float(input("Enter second number: "))
    result = num1 / num2
    print(f"{num1} ÷ {num2} = {result}")
except:
    print("Something went wrong with the calculation!")

print("Calculator finished.")
```

### Example 3: Handling File Errors

```python
# Safe file reading
try:
    with open("data.txt", "r") as file:
        content = file.read()
        print("File content:")
        print(content)
except:
    print("Could not read the file. It might not exist.")

print("Program completed.")
```

---

## 2. Specific Exception Types

Instead of catching all errors, you can catch specific types of exceptions to handle different problems differently.

### Common Exception Types

| Exception Type | What Causes It | Example |
|---------------|----------------|---------|
| `ValueError` | Invalid value for operation | `int("hello")` |
| `ZeroDivisionError` | Dividing by zero | `10 / 0` |
| `FileNotFoundError` | File doesn't exist | `open("missing.txt")` |
| `IndexError` | List index out of range | `my_list[999]` |
| `KeyError` | Dictionary key doesn't exist | `my_dict["missing"]` |
| `TypeError` | Wrong data type | `"hello" + 5` |

### Example 1: Catching Specific Exceptions

```python
# Number input with specific error handling
try:
    user_input = input("Enter a number: ")
    number = int(user_input)
    result = 100 / number
    print(f"100 ÷ {number} = {result}")

except ValueError:
    print(f"'{user_input}' is not a valid number!")
    print("Please enter only digits.")

except ZeroDivisionError:
    print("Cannot divide by zero!")
    print("Please enter a number other than 0.")

print("Program continues...")
```

### Example 2: File Operations with Specific Exceptions

```python
# Safe file operations
filename = input("Enter filename to read: ")

try:
    with open(filename, "r") as file:
        lines = file.readlines()
        print(f"File '{filename}' has {len(lines)} lines")
        
        # Show first few lines
        for i, line in enumerate(lines[:3]):
            print(f"Line {i+1}: {line.strip()}")

except FileNotFoundError:
    print(f"Sorry, the file '{filename}' was not found.")
    print("Please check the filename and try again.")

except PermissionError:
    print(f"Permission denied to read '{filename}'.")
    print("You don't have access to this file.")

except Exception as e:
    print(f"An unexpected error occurred: {e}")
```

### Example 3: List and Dictionary Access

```python
# Safe list and dictionary operations
students = ["Alice", "Bob", "Charlie"]
grades = {"Alice": 85, "Bob": 92, "Charlie": 78}

# Safe list access
try:
    index = int(input("Enter student index (0-2): "))
    student = students[index]
    print(f"Student at index {index}: {student}")
    
except ValueError:
    print("Please enter a valid number!")
    
except IndexError:
    print(f"Index must be between 0 and {len(students)-1}")

# Safe dictionary access
try:
    name = input("Enter student name: ")
    grade = grades[name]
    print(f"{name}'s grade: {grade}")
    
except KeyError:
    print(f"No grade found for '{name}'")
    print(f"Available students: {list(grades.keys())}")
```

---

## 3. Multiple Exception Handling

You can handle different exceptions in different ways using multiple `except` blocks.

### Example 1: Calculator with Multiple Exceptions

```python
def safe_calculator():
    print("=== Safe Calculator ===")
    
    try:
        # Get input
        num1 = float(input("Enter first number: "))
        operation = input("Enter operation (+, -, *, /): ")
        num2 = float(input("Enter second number: "))
        
        # Perform calculation
        if operation == "+":
            result = num1 + num2
        elif operation == "-":
            result = num1 - num2
        elif operation == "*":
            result = num1 * num2
        elif operation == "/":
            result = num1 / num2
        else:
            print("Invalid operation!")
            return
        
        print(f"{num1} {operation} {num2} = {result}")
        
    except ValueError:
        print("Error: Please enter valid numbers!")
        
    except ZeroDivisionError:
        print("Error: Cannot divide by zero!")
        
    except KeyboardInterrupt:
        print("\nCalculation cancelled by user.")
        
    print("Calculator session ended.")

# Test the calculator
safe_calculator()
```

### Example 2: Grade Book with Error Handling

```python
def grade_book_system():
    """Grade book with comprehensive error handling"""
    grades = {}
    
    while True:
        print("\n=== Grade Book System ===")
        print("1. Add grade")
        print("2. View grade")
        print("3. Calculate average")
        print("4. Exit")
        
        try:
            choice = input("Choose an option (1-4): ")
            
            if choice == "1":
                # Add grade
                name = input("Student name: ")
                grade_str = input("Grade (0-100): ")
                grade = float(grade_str)
                
                # Validate grade range
                if 0 <= grade <= 100:
                    grades[name] = grade
                    print(f"Added grade {grade} for {name}")
                else:
                    print("Grade must be between 0 and 100!")
                    
            elif choice == "2":
                # View grade
                name = input("Student name: ")
                grade = grades[name]  # This might raise KeyError
                print(f"{name}'s grade: {grade}")
                
            elif choice == "3":
                # Calculate average
                if grades:
                    average = sum(grades.values()) / len(grades)
                    print(f"Class average: {average:.1f}")
                else:
                    print("No grades entered yet!")
                    
            elif choice == "4":
                print("Goodbye!")
                break
                
            else:
                print("Invalid choice! Please enter 1-4.")
                
        except ValueError:
            print("Please enter a valid number for the grade!")
            
        except KeyError:
            print(f"No grade found for '{name}'.")
            print(f"Available students: {list(grades.keys())}")
            
        except KeyboardInterrupt:
            print("\nExiting program...")
            break
            
        except Exception as e:
            print(f"An unexpected error occurred: {e}")

# Run the grade book system
grade_book_system()
```

---

## 4. The `else` Clause

The `else` clause runs only if NO exception occurred in the `try` block.

### Syntax:
```python
try:
    # Risky code
    pass
except SomeException:
    # Handle exception
    pass
else:
    # This runs only if NO exception occurred
    pass
```

### Example 1: File Processing with `else`

```python
def process_file(filename):
    """Process a file with proper error handling"""
    
    try:
        # Try to open and read the file
        with open(filename, "r") as file:
            content = file.read()
            
    except FileNotFoundError:
        print(f"Error: File '{filename}' not found!")
        
    except PermissionError:
        print(f"Error: Permission denied to read '{filename}'!")
        
    else:
        # This runs only if file was successfully opened
        print(f"Successfully read '{filename}'")
        print(f"File size: {len(content)} characters")
        
        # Count lines
        lines = content.split('\n')
        print(f"Number of lines: {len(lines)}")
        
        # Count words
        words = content.split()
        print(f"Number of words: {len(words)}")

# Test with different files
process_file("existing_file.txt")  # If file exists, shows statistics
process_file("missing_file.txt")   # If file doesn't exist, shows error
```

### Example 2: Number Processing with `else`

```python
def analyze_number():
    """Analyze a number with error handling"""
    
    try:
        # Get user input
        user_input = input("Enter a number: ")
        number = float(user_input)
        
    except ValueError:
        print(f"'{user_input}' is not a valid number!")
        
    else:
        # This runs only if conversion was successful
        print(f"Successfully converted: {number}")
        
        # Analyze the number
        if number > 0:
            print("The number is positive")
        elif number < 0:
            print("The number is negative")
        else:
            print("The number is zero")
            
        # Check if it's a whole number
        if number.is_integer():
            print("The number is a whole number")
            
            # Check if even or odd
            if int(number) % 2 == 0:
                print("The number is even")
            else:
                print("The number is odd")

# Test the function
analyze_number()
```

---

## 5. The `finally` Clause

The `finally` clause ALWAYS runs, whether an exception occurred or not. It's perfect for cleanup tasks.

### Syntax:
```python
try:
    # Risky code
    pass
except SomeException:
    # Handle exception
    pass
else:
    # Runs if no exception
    pass
finally:
    # ALWAYS runs (cleanup code)
    pass
```

### Example 1: File Operations with Cleanup

```python
def safe_file_operation(filename):
    """Demonstrate finally clause with file operations"""
    
    file_handle = None
    
    try:
        print(f"Opening file: {filename}")
        file_handle = open(filename, "r")
        content = file_handle.read()
        print(f"File content: {content[:50]}...")  # Show first 50 characters
        
        # Simulate potential error
        if len(content) == 0:
            raise ValueError("File is empty!")
            
    except FileNotFoundError:
        print(f"Error: Could not find file '{filename}'")
        
    except ValueError as e:
        print(f"Error: {e}")
        
    except Exception as e:
        print(f"Unexpected error: {e}")
        
    else:
        print("File processed successfully!")
        
    finally:
        # This ALWAYS runs - cleanup
        if file_handle and not file_handle.closed:
            file_handle.close()
            print("File closed properly.")
        print("Cleanup completed.")

# Test the function
safe_file_operation("test.txt")
```

### Example 2: Database Connection Simulation

```python
class DatabaseConnection:
    """Simulate a database connection"""
    
    def __init__(self, db_name):
        self.db_name = db_name
        self.connected = False
        
    def connect(self):
        print(f"Connecting to database: {self.db_name}")
        self.connected = True
        
    def disconnect(self):
        if self.connected:
            print(f"Disconnecting from database: {self.db_name}")
            self.connected = False

def database_operation(db_name, query):
    """Perform database operation with proper cleanup"""
    
    db = DatabaseConnection(db_name)
    
    try:
        # Connect to database
        db.connect()
        
        print(f"Executing query: {query}")
        
        # Simulate query execution
        if "DROP" in query.upper():
            raise PermissionError("DROP operations not allowed!")
            
        if "SELECT" not in query.upper():
            raise ValueError("Only SELECT queries are supported!")
            
        print("Query executed successfully!")
        
    except PermissionError as e:
        print(f"Permission error: {e}")
        
    except ValueError as e:
        print(f"Query error: {e}")
        
    except Exception as e:
        print(f"Unexpected database error: {e}")
        
    else:
        print("Database operation completed successfully!")
        
    finally:
        # Always disconnect, even if there was an error
        db.disconnect()
        print("Database cleanup completed.")

# Test database operations
database_operation("users_db", "SELECT * FROM users")
database_operation("users_db", "DROP TABLE users")  # This will cause an error
```

---

## 6. Catching and Re-raising Exceptions

Sometimes you want to catch an exception, do something with it, and then let it continue up to be handled elsewhere.

### Example 1: Logging Errors Before Re-raising

```python
import datetime

def log_error(error_message):
    """Log error to a file"""
    timestamp = datetime.datetime.now().strftime("%Y-%m-%d %H:%M:%S")
    with open("error_log.txt", "a") as log_file:
        log_file.write(f"[{timestamp}] {error_message}\n")

def risky_calculation(x, y):
    """Perform calculation with error logging"""
    
    try:
        if y == 0:
            raise ZeroDivisionError("Cannot divide by zero")
        result = x / y
        return result
        
    except ZeroDivisionError as e:
        # Log the error
        log_error(f"Division error: {x} ÷ {y} - {str(e)}")
        
        # Re-raise the exception for caller to handle
        raise  # This passes the exception up to the caller

def main_program():
    """Main program that handles the re-raised exception"""
    
    try:
        result = risky_calculation(10, 0)
        print(f"Result: {result}")
        
    except ZeroDivisionError:
        print("Error handled in main program: Cannot perform division by zero!")

# Run the program
main_program()
```

### Example 2: Adding Context to Exceptions

```python
def validate_age(age):
    """Validate age input with detailed error info"""
    
    try:
        # Convert to integer
        age_num = int(age)
        
        # Validate range
        if age_num < 0:
            raise ValueError(f"Age cannot be negative: {age_num}")
        if age_num > 150:
            raise ValueError(f"Age seems unrealistic: {age_num}")
            
        return age_num
        
    except ValueError as e:
        # Add more context to the error
        if "invalid literal" in str(e):
            raise ValueError(f"'{age}' is not a valid number") from e
        else:
            # Re-raise with original message
            raise

def create_user_account():
    """Create user account with validation"""
    
    try:
        name = input("Enter your name: ")
        age_input = input("Enter your age: ")
        
        age = validate_age(age_input)
        
        print(f"Account created for {name}, age {age}")
        
    except ValueError as e:
        print(f"Account creation failed: {e}")

# Test account creation
create_user_account()
```

---

## 7. Custom Exceptions

You can create your own exception types for specific situations in your program.

### Creating Custom Exceptions

```python
# Define custom exception classes
class InvalidPasswordError(Exception):
    """Raised when password doesn't meet requirements"""
    pass

class AccountLockedError(Exception):
    """Raised when account is locked due to failed attempts"""
    pass

class InsufficientFundsError(Exception):
    """Raised when trying to withdraw more money than available"""
    def __init__(self, requested, available):
        self.requested = requested
        self.available = available
        super().__init__(f"Insufficient funds: requested ${requested}, available ${available}")

# Using custom exceptions
class BankAccount:
    def __init__(self, account_number, initial_balance=0):
        self.account_number = account_number
        self.balance = initial_balance
        self.failed_attempts = 0
        self.locked = False
    
    def validate_password(self, password):
        """Validate password strength"""
        if len(password) < 6:
            raise InvalidPasswordError("Password must be at least 6 characters long")
        
        if not any(char.isdigit() for char in password):
            raise InvalidPasswordError("Password must contain at least one number")
    
    def authenticate(self, password):
        """Authenticate user"""
        if self.locked:
            raise AccountLockedError("Account is locked due to failed login attempts")
        
        # Simulate password check
        if password != "secret123":
            self.failed_attempts += 1
            if self.failed_attempts >= 3:
                self.locked = True
                raise AccountLockedError("Account locked after 3 failed attempts")
            raise InvalidPasswordError("Incorrect password")
        
        self.failed_attempts = 0  # Reset on successful login
    
    def withdraw(self, amount):
        """Withdraw money from account"""
        if amount > self.balance:
            raise InsufficientFundsError(amount, self.balance)
        
        self.balance -= amount
        return self.balance

# Using the custom exceptions
def banking_demo():
    account = BankAccount("12345", 500.00)
    
    while True:
        try:
            print(f"\n=== Bank Account System ===")
            print(f"Account: {account.account_number}")
            print(f"Balance: ${account.balance:.2f}")
            
            action = input("Choose action (login/withdraw/quit): ").lower()
            
            if action == "login":
                password = input("Enter password: ")
                account.authenticate(password)
                print("Login successful!")
                
            elif action == "withdraw":
                amount = float(input("Withdrawal amount: $"))
                new_balance = account.withdraw(amount)
                print(f"Withdrawal successful! New balance: ${new_balance:.2f}")
                
            elif action == "quit":
                break
                
        except InvalidPasswordError as e:
            print(f"Authentication error: {e}")
            
        except AccountLockedError as e:
            print(f"Account error: {e}")
            
        except InsufficientFundsError as e:
            print(f"Transaction error: {e}")
            
        except ValueError:
            print("Please enter a valid number for withdrawal amount")
            
        except KeyboardInterrupt:
            print("\nExiting banking system...")
            break

# Run banking demo
banking_demo()
```

---

## 8. Best Practices for Exception Handling

### 1. Be Specific with Exception Types

```python
# Poor - catches everything
try:
    number = int(input("Enter a number: "))
    result = 10 / number
except:  # Too broad!
    print("Something went wrong")

# Better - catch specific exceptions
try:
    number = int(input("Enter a number: "))
    result = 10 / number
except ValueError:
    print("That's not a valid number")
except ZeroDivisionError:
    print("Cannot divide by zero")
```

### 2. Don't Ignore Exceptions

```python
# Poor - silently ignores errors
try:
    risky_operation()
except:
    pass  # Never do this!

# Better - handle appropriately
try:
    risky_operation()
except SpecificError as e:
    print(f"Operation failed: {e}")
    # Log the error, notify user, etc.
```

### 3. Use Exception Information

```python
# Good - use exception details
try:
    with open("config.txt", "r") as file:
        data = file.read()
except FileNotFoundError as e:
    print(f"Configuration file not found: {e.filename}")
    print("Using default settings...")
except PermissionError as e:
    print(f"Permission denied: {e}")
    print("Please check file permissions.")
```

### 4. Validate Input Early

```python
def safe_divide(a, b):
    """Safe division with input validation"""
    
    # Validate inputs early
    if not isinstance(a, (int, float)):
        raise TypeError(f"First argument must be a number, got {type(a)}")
    
    if not isinstance(b, (int, float)):
        raise TypeError(f"Second argument must be a number, got {type(b)}")
    
    if b == 0:
        raise ZeroDivisionError("Cannot divide by zero")
    
    return a / b

# Usage
try:
    result = safe_divide(10, 2)
    print(f"Result: {result}")
    
    result = safe_divide(10, "2")  # This will raise TypeError
    
except TypeError as e:
    print(f"Type error: {e}")
except ZeroDivisionError as e:
    print(f"Math error: {e}")
```

---

## 9. Real-World Examples

### Example 1: Safe File Configuration Reader

```python
import json

class ConfigReader:
    """Safe configuration file reader"""
    
    def __init__(self, config_file="config.json"):
        self.config_file = config_file
        self.config = {}
        self.load_config()
    
    def load_config(self):
        """Load configuration with comprehensive error handling"""
        
        try:
            with open(self.config_file, "r") as file:
                self.config = json.load(file)
                
        except FileNotFoundError:
            print(f"Config file '{self.config_file}' not found.")
            self.create_default_config()
            
        except json.JSONDecodeError as e:
            print(f"Invalid JSON in config file: {e}")
            print("Using default configuration...")
            self.create_default_config()
            
        except PermissionError:
            print(f"Permission denied reading '{self.config_file}'")
            print("Using default configuration...")
            self.create_default_config()
            
        else:
            print(f"Configuration loaded from '{self.config_file}'")
            
        finally:
            # Ensure we have basic configuration
            self.ensure_required_settings()
    
    def create_default_config(self):
        """Create default configuration"""
        self.config = {
            "database_url": "localhost",
            "debug_mode": False,
            "max_connections": 10,
            "timeout": 30
        }
        
        # Try to save default config
        try:
            self.save_config()
            print("Default configuration created and saved.")
        except Exception as e:
            print(f"Could not save default config: {e}")
    
    def ensure_required_settings(self):
        """Ensure all required settings exist"""
        required_settings = {
            "database_url": "localhost",
            "debug_mode": False,
            "max_connections": 10,
            "timeout": 30
        }
        
        for key, default_value in required_settings.items():
            if key not in self.config:
                self.config[key] = default_value
                print(f"Added missing setting: {key} = {default_value}")
    
    def get(self, key, default=None):
        """Get configuration value safely"""
        return self.config.get(key, default)
    
    def save_config(self):
        """Save configuration to file"""
        try:
            with open(self.config_file, "w") as file:
                json.dump(self.config, file, indent=2)
            return True
        except Exception as e:
            print(f"Failed to save config: {e}")
            return False

# Usage example
config = ConfigReader("app_config.json")
print(f"Database URL: {config.get('database_url')}")
print(f"Debug mode: {config.get('debug_mode')}")
```

### Example 2: Robust Web Data Fetcher

```python
import urllib.request
import urllib.error
import json

class WebDataFetcher:
    """Safely fetch and process web data"""
    
    def __init__(self, timeout=10):
        self.timeout = timeout
    
    def fetch_json_data(self, url):
        """Fetch JSON data from URL with comprehensive error handling"""
        
        try:
            print(f"Fetching data from: {url}")
            
            # Make the web request
            with urllib.request.urlopen(url, timeout=self.timeout) as response:
                # Check if request was successful
                if response.getcode() != 200:
                    raise urllib.error.HTTPError(
                        url, response.getcode(), 
                        f"HTTP {response.getcode()}", None, None
                    )
                
                # Read and decode the response
                data = response.read().decode('utf-8')
                
                # Parse JSON
                json_data = json.loads(data)
                
                return json_data
                
        except urllib.error.URLError as e:
            if hasattr(e, 'code'):
                print(f"HTTP Error {e.code}: {e.reason}")
            else:
                print(f"URL Error: {e.reason}")
            return None
            
        except urllib.error.HTTPError as e:
            print(f"HTTP Error {e.code}: Server returned an error")
            return None
            
        except json.JSONDecodeError as e:
            print(f"JSON parsing error: {e}")
            print("The server response is not valid JSON")
            return None
            
        except TimeoutError:
            print(f"Request timed out after {self.timeout} seconds")
            return None
            
        except Exception as e:
            print(f"Unexpected error: {e}")
            return None
    
    def fetch_weather_data(self, city):
        """Fetch weather data for a city"""
        # This is a mock example - replace with real weather API
        url = f"https://api.weather.com/v1/current/{city}"
        
        data = self.fetch_json_data(url)
        
        if data:
            try:
                temperature = data['current']['temperature']
                condition = data['current']['condition']
                humidity = data['current']['humidity']
                
                print(f"Weather in {city}:")
                print(f"Temperature: {temperature}°F")
                print(f"Condition: {condition}")
                print(f"Humidity: {humidity}%")
                
                return data
                
            except KeyError as e:
                print(f"Expected data not found in response: {e}")
                return None
        
        return None

# Usage example
fetcher = WebDataFetcher(timeout=15)
weather = fetcher.fetch_weather_data("New York")
```

---

## 10. Common Mistakes to Avoid

### Mistake 1: Catching Too Broad Exceptions

```python
# Wrong - too broad
try:
    process_data()
except Exception:  # This catches EVERYTHING!
    print("Something went wrong")

# Better - be specific
try:
    process_data()
except ValueError:
    print("Invalid data format")
except FileNotFoundError:
    print("Required file missing")
except KeyError:
    print("Required data field missing")
```

### Mistake 2: Empty Exception Handlers

```python
# Wrong - hides all errors
try:
    risky_operation()
except:
    pass  # Silent failure - very dangerous!

# Better - always handle appropriately
try:
    risky_operation()
except SpecificError as e:
    print(f"Operation failed: {e}")
    # Log error, clean up, notify user, etc.
```

### Mistake 3: Not Using Exception Information

```python
# Poor - generic error message
try:
    age = int(input("Enter age: "))
except ValueError:
    print("Invalid input")  # Not helpful!

# Better - use exception information
try:
    user_input = input("Enter age: ")
    age = int(user_input)
except ValueError as e:
    print(f"'{user_input}' is not a valid number: {e}")
```

### Mistake 4: Incorrect Exception Order

```python
# Wrong - specific exception after general one
try:
    risky_operation()
except Exception as e:  # This catches everything first!
    print(f"General error: {e}")
except ValueError:  # This will never be reached!
    print("Value error")

# Correct - specific exceptions first
try:
    risky_operation()
except ValueError:
    print("Value error")
except KeyError:
    print("Key error")
except Exception as e:  # General exception last
    print(f"Unexpected error: {e}")
```

---

## 11. Practice Exercises

### Exercise 1: Safe Number Input
Create a function that safely gets a number from user:

```python
# Your code here
def get_number():
    # Keep asking until user enters a valid number
    # Handle ValueError for invalid input
    # Return the number when successful
    pass

# Test your function
number = get_number()
print(f"You entered: {number}")
```

### Exercise 2: Safe Division
Create a function that safely divides two numbers:

```python
# Your code here
def safe_divide(a, b):
    # Handle ZeroDivisionError
    # Return the result or None if error occurs
    pass

# Test your function
result = safe_divide(10, 2)  # Should work
result = safe_divide(10, 0)  # Should handle error
```

### Exercise 3: Safe File Reader
Create a function that safely reads a file:

```python
# Your code here
def read_file_safely(filename):
    # Handle FileNotFoundError
    # Return file content or None if error occurs
    pass

# Test your function
content = read_file_safely("test.txt")
if content:
    print(f"File content: {content}")
```

---

## Summary

In this comprehensive guide, you learned about Python exception handling:

- ✅ **Basic try/except** structure to catch and handle errors gracefully
- ✅ **Specific exception types** to handle different errors appropriately
- ✅ **Multiple exception handling** for complex error scenarios
- ✅ **else clause** to run code only when no exceptions occur
- ✅ **finally clause** for cleanup code that always runs
- ✅ **Custom exceptions** for application-specific error handling
- ✅ **Best practices** for writing robust, error-resistant code
- ✅ **Real-world examples** showing practical exception handling
- ✅ **Common mistakes** and how to avoid them

### Key Takeaways:
- **Always anticipate potential errors** and handle them gracefully
- **Be specific** with exception types rather than catching everything
- **Provide helpful error messages** that guide users to solutions
- **Use finally blocks** for cleanup code that must always run
- **Don't suppress errors** - handle them appropriately
- **Test error conditions** to ensure your exception handling works

### Next Steps:
- Practice with the exercises to build exception handling skills
- Apply error handling to all your existing Python programs
- Learn about logging to track errors in production applications
- Explore testing frameworks to verify your error handling works correctly

**Next:** Continue to learn about Object-Oriented Programming to organize your code with classes and objects!