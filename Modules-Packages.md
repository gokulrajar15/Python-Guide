# Python Modules & Packages

Modules and packages are like toolboxes that contain pre-written code you can use in your programs. Instead of writing everything from scratch, you can import and use code that others have already written and tested. It's like using a calculator app instead of building one yourself!

## What are Modules and Packages?

Think of modules as individual tools, and packages as complete toolboxes:

- **Module**: A single Python file (`.py`) containing functions, variables, and classes
- **Package**: A collection of related modules grouped together
- **Library**: A collection of packages (often used interchangeably with "package")

```python
# Instead of writing this complex math yourself...
def calculate_square_root(number):
    # Complex algorithm here...
    pass

# You can simply import and use it!
import math
result = math.sqrt(25)  # Much easier!
print(result)  # 5.0
```

## Benefits of Using Modules

- **Save time**: Don't reinvent the wheel
- **Reliability**: Well-tested code by experts
- **Organization**: Keep your code organized and modular
- **Reusability**: Use the same module in multiple projects
- **Collaboration**: Share code with other developers

---

## 1. Importing Modules

Python provides several ways to import and use modules. Let's explore each method!

### Method 1: Basic Import

```python
# Import the entire module
import math

# Use functions with module name prefix
result1 = math.sqrt(16)      # 4.0
result2 = math.pi            # 3.141592653589793
result3 = math.factorial(5)  # 120

print(f"Square root of 16: {result1}")
print(f"Value of Pi: {result2}")
print(f"5 factorial: {result3}")
```

### Method 2: Import Specific Functions

```python
# Import only specific functions
from math import sqrt, pi, factorial

# Use functions directly (no module name needed)
result1 = sqrt(16)      # 4.0
result2 = pi            # 3.141592653589793
result3 = factorial(5)  # 120

print(f"Square root of 16: {result1}")
print(f"Value of Pi: {result2}")
print(f"5 factorial: {result3}")
```

### Method 3: Import with Alias

```python
# Import module with a shorter name
import math as m

# Use the alias
result1 = m.sqrt(25)     # 5.0
result2 = m.cos(m.pi)    # -1.0

print(f"Square root of 25: {result1}")
print(f"Cosine of Pi: {result2}")

# Import specific functions with aliases
from math import sqrt as square_root, pi as PI

result = square_root(36)  # 6.0
print(f"Using alias - Square root of 36: {result}")
print(f"Pi value: {PI}")
```

### Method 4: Import Everything (Use with Caution!)

```python
# Import all functions from a module
from math import *

# Use any function without module name
result1 = sqrt(49)       # 7.0
result2 = sin(pi/2)      # 1.0
result3 = log(10)        # 2.302585092994046

print(f"Square root of 49: {result1}")
print(f"Sin(π/2): {result2}")
print(f"Natural log of 10: {result3}")

# Warning: This can cause naming conflicts!
# Only use this when you're sure there won't be conflicts
```

---

## 2. Built-in Modules

Python comes with many useful modules pre-installed. Let's explore the most important ones!

### Math Module - Mathematical Operations

```python
import math

# Basic mathematical operations
print("=== Math Module Examples ===")

# Square root and power functions
print(f"Square root of 25: {math.sqrt(25)}")           # 5.0
print(f"2 to the power of 8: {math.pow(2, 8)}")        # 256.0
print(f"Absolute value of -15: {math.fabs(-15)}")      # 15.0

# Rounding functions
print(f"Ceiling of 4.3: {math.ceil(4.3)}")             # 5
print(f"Floor of 4.7: {math.floor(4.7)}")              # 4

# Trigonometric functions (in radians)
print(f"Sin of π/2: {math.sin(math.pi/2)}")            # 1.0
print(f"Cos of 0: {math.cos(0)}")                      # 1.0
print(f"Tan of π/4: {math.tan(math.pi/4)}")            # 1.0

# Logarithmic functions
print(f"Natural log of e: {math.log(math.e)}")         # 1.0
print(f"Base-10 log of 100: {math.log10(100)}")        # 2.0

# Constants
print(f"Value of π (Pi): {math.pi}")                   # 3.141592653589793
print(f"Value of e: {math.e}")                         # 2.718281828459045

# Practical example: Calculate circle area
def calculate_circle_area(radius):
    return math.pi * radius * radius

radius = 5
area = calculate_circle_area(radius)
print(f"Area of circle with radius {radius}: {area:.2f}")
```

### Random Module - Generate Random Numbers

```python
import random

print("\n=== Random Module Examples ===")

# Generate random integers
random_int = random.randint(1, 10)              # Random integer between 1 and 10
print(f"Random integer (1-10): {random_int}")

# Generate random floating-point numbers
random_float = random.random()                  # Random float between 0 and 1
print(f"Random float (0-1): {random_float:.3f}")

# Random float in a specific range
random_range = random.uniform(5.0, 10.0)       # Random float between 5 and 10
print(f"Random float (5-10): {random_range:.2f}")

# Choose random items from a list
colors = ["red", "blue", "green", "yellow", "purple"]
random_color = random.choice(colors)
print(f"Random color: {random_color}")

# Shuffle a list
numbers = [1, 2, 3, 4, 5]
print(f"Original list: {numbers}")
random.shuffle(numbers)
print(f"Shuffled list: {numbers}")

# Select multiple random items
students = ["Alice", "Bob", "Charlie", "Diana", "Eve", "Frank"]
selected = random.sample(students, 3)          # Select 3 random students
print(f"Randomly selected students: {selected}")

# Practical example: Dice roller
def roll_dice(num_dice=2, sides=6):
    rolls = []
    for _ in range(num_dice):
        roll = random.randint(1, sides)
        rolls.append(roll)
    return rolls

dice_result = roll_dice(2, 6)
print(f"Rolling 2 dice: {dice_result} (Total: {sum(dice_result)})")
```

### Datetime Module - Work with Dates and Times

```python
import datetime

print("\n=== Datetime Module Examples ===")

# Get current date and time
now = datetime.datetime.now()
print(f"Current date and time: {now}")

# Get just the date
today = datetime.date.today()
print(f"Today's date: {today}")

# Create specific dates
birthday = datetime.date(1990, 5, 15)  # Year, Month, Day
print(f"Birthday: {birthday}")

# Calculate age
age_days = today - birthday
age_years = age_days.days // 365
print(f"Age in days: {age_days.days}")
print(f"Age in years (approx): {age_years}")

# Format dates
formatted_date = now.strftime("%B %d, %Y at %I:%M %p")
print(f"Formatted: {formatted_date}")

# Working with time
specific_time = datetime.time(14, 30, 0)  # Hour, Minute, Second
print(f"Specific time: {specific_time}")

# Practical example: Event countdown
def days_until_event(event_date):
    today = datetime.date.today()
    delta = event_date - today
    return delta.days

new_year = datetime.date(2026, 1, 1)
days_left = days_until_event(new_year)
print(f"Days until New Year 2026: {days_left}")
```

### OS Module - Operating System Interface

```python
import os

print("\n=== OS Module Examples ===")

# Get current working directory
current_dir = os.getcwd()
print(f"Current directory: {current_dir}")

# List files in current directory
files = os.listdir('.')
print(f"Files in current directory: {files[:5]}...")  # Show first 5 files

# Get environment variables
username = os.getenv('USERNAME', 'Unknown')  # Windows
# username = os.getenv('USER', 'Unknown')    # macOS/Linux
print(f"Current user: {username}")

# Path operations
file_path = "documents/my_file.txt"
print(f"Directory name: {os.path.dirname(file_path)}")
print(f"File name: {os.path.basename(file_path)}")
print(f"File exists: {os.path.exists(file_path)}")

# Create directories (be careful with this!)
# os.makedirs('test_folder', exist_ok=True)
print("OS module loaded successfully!")
```

---

## 3. Creating Your Own Modules

You can create your own modules to organize your code better!

### Example: Creating a Utilities Module

Create a file called `my_utils.py`:

```python
# File: my_utils.py
"""
My personal utility functions
"""

import math
import random

def calculate_circle_area(radius):
    """Calculate the area of a circle"""
    return math.pi * radius * radius

def calculate_rectangle_area(length, width):
    """Calculate the area of a rectangle"""
    return length * width

def generate_password(length=8):
    """Generate a random password"""
    characters = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789"
    password = ""
    for _ in range(length):
        password += random.choice(characters)
    return password

def celsius_to_fahrenheit(celsius):
    """Convert Celsius to Fahrenheit"""
    return (celsius * 9/5) + 32

def fahrenheit_to_celsius(fahrenheit):
    """Convert Fahrenheit to Celsius"""
    return (fahrenheit - 32) * 5/9

# Module variables
PI = math.pi
GOLDEN_RATIO = (1 + math.sqrt(5)) / 2

if __name__ == "__main__":
    # This code only runs when the module is executed directly
    print("Testing my_utils module...")
    print(f"Circle area (radius=5): {calculate_circle_area(5):.2f}")
    print(f"Random password: {generate_password(12)}")
    print(f"25°C in Fahrenheit: {celsius_to_fahrenheit(25):.1f}")
```

Using your custom module:

```python
# File: main.py
import my_utils

# Use functions from your module
area = my_utils.calculate_circle_area(10)
password = my_utils.generate_password(16)
temp_f = my_utils.celsius_to_fahrenheit(20)

print(f"Circle area: {area:.2f}")
print(f"Generated password: {password}")
print(f"20°C = {temp_f:.1f}°F")

# Access module variables
print(f"Value of Pi: {my_utils.PI}")
print(f"Golden Ratio: {my_utils.GOLDEN_RATIO:.3f}")
```

---

## 4. Installing External Packages

Python has thousands of external packages you can install using `pip`!

### What is pip?

`pip` is Python's package installer. It downloads and installs packages from the Python Package Index (PyPI).

### Basic pip Commands

```bash
# Install a package
pip install package_name

# Install a specific version
pip install package_name==1.2.3

# Upgrade a package
pip install --upgrade package_name

# List installed packages
pip list

# Show package information
pip show package_name

# Uninstall a package
pip uninstall package_name

# Install from requirements file
pip install -r requirements.txt

# Save current packages to requirements file
pip freeze > requirements.txt
```

### Popular External Packages for Beginners

#### 1. Requests - Easy HTTP Requests

```python
# First install: pip install requests
import requests

# Make a simple web request
response = requests.get('https://api.github.com/users/octocat')

if response.status_code == 200:
    data = response.json()
    print(f"User: {data['name']}")
    print(f"Public repos: {data['public_repos']}")
else:
    print("Failed to fetch data")
```

#### 2. Colorama - Colored Terminal Output

```python
# First install: pip install colorama
from colorama import Fore, Back, Style, init

# Initialize colorama
init()

# Print colored text
print(Fore.RED + "This is red text")
print(Fore.GREEN + "This is green text")
print(Fore.BLUE + Back.YELLOW + "Blue text on yellow background")
print(Style.RESET_ALL + "Back to normal")

# Useful for making terminal output more attractive
print(Fore.CYAN + "=== Welcome to My App ===" + Style.RESET_ALL)
```

#### 3. Rich - Beautiful Terminal Output

```python
# First install: pip install rich
from rich.console import Console
from rich.table import Table

console = Console()

# Print with styling
console.print("Hello", style="bold red")
console.print("World!", style="bold blue")

# Create a beautiful table
table = Table(title="Student Grades")
table.add_column("Name", style="cyan")
table.add_column("Math", style="magenta")
table.add_column("Science", style="green")

table.add_row("Alice", "95", "88")
table.add_row("Bob", "87", "92")
table.add_row("Charlie", "91", "85")

console.print(table)
```

---

## 5. Real-World Examples

### Example 1: Password Generator with Multiple Options

```python
import random
import string
import math

def generate_simple_password(length=8):
    """Generate a simple password with letters and numbers"""
    characters = string.ascii_letters + string.digits
    return ''.join(random.choice(characters) for _ in range(length))

def generate_secure_password(length=12, include_symbols=True):
    """Generate a secure password with various character types"""
    characters = string.ascii_letters + string.digits
    
    if include_symbols:
        characters += "!@#$%^&*"
    
    # Ensure at least one of each type
    password = []
    password.append(random.choice(string.ascii_lowercase))
    password.append(random.choice(string.ascii_uppercase))
    password.append(random.choice(string.digits))
    
    if include_symbols:
        password.append(random.choice("!@#$%^&*"))
    
    # Fill the rest randomly
    for _ in range(length - len(password)):
        password.append(random.choice(characters))
    
    # Shuffle the password
    random.shuffle(password)
    return ''.join(password)

def check_password_strength(password):
    """Analyze password strength"""
    score = 0
    feedback = []
    
    # Check length
    if len(password) >= 12:
        score += 3
        feedback.append("✓ Good length")
    elif len(password) >= 8:
        score += 2
        feedback.append("⚠ Acceptable length")
    else:
        score += 0
        feedback.append("✗ Too short")
    
    # Check character types
    has_lower = any(c.islower() for c in password)
    has_upper = any(c.isupper() for c in password)
    has_digit = any(c.isdigit() for c in password)
    has_symbol = any(c in "!@#$%^&*" for c in password)
    
    if has_lower: score += 1
    if has_upper: score += 1
    if has_digit: score += 1
    if has_symbol: score += 1
    
    feedback.append(f"Character types: {sum([has_lower, has_upper, has_digit, has_symbol])}/4")
    
    # Determine strength
    if score >= 7:
        strength = "Very Strong"
    elif score >= 5:
        strength = "Strong"
    elif score >= 3:
        strength = "Medium"
    else:
        strength = "Weak"
    
    return strength, score, feedback

def password_manager():
    """Interactive password generator"""
    print("=== Password Generator ===")
    
    while True:
        print("\nOptions:")
        print("1. Generate simple password")
        print("2. Generate secure password")
        print("3. Check password strength")
        print("4. Exit")
        
        choice = input("Choose an option (1-4): ")
        
        if choice == "1":
            length = int(input("Password length (default 8): ") or 8)
            password = generate_simple_password(length)
            print(f"Generated password: {password}")
            
        elif choice == "2":
            length = int(input("Password length (default 12): ") or 12)
            symbols = input("Include symbols? (y/n): ").lower() == 'y'
            password = generate_secure_password(length, symbols)
            print(f"Generated password: {password}")
            
        elif choice == "3":
            password = input("Enter password to check: ")
            strength, score, feedback = check_password_strength(password)
            print(f"Strength: {strength} (Score: {score}/8)")
            for item in feedback:
                print(f"  {item}")
                
        elif choice == "4":
            print("Goodbye!")
            break
        else:
            print("Invalid choice!")

# Run the password manager
password_manager()
```

### Example 2: Weather Data Simulator

```python
import random
import datetime
import math

class WeatherSimulator:
    """Simulate weather data for different cities"""
    
    def __init__(self):
        self.cities = {
            "New York": {"base_temp": 15, "humidity_base": 60},
            "Los Angeles": {"base_temp": 22, "humidity_base": 45},
            "Chicago": {"base_temp": 10, "humidity_base": 65},
            "Miami": {"base_temp": 26, "humidity_base": 75},
            "Seattle": {"base_temp": 12, "humidity_base": 70}
        }
    
    def generate_temperature(self, city, season="spring"):
        """Generate realistic temperature for a city"""
        base_temp = self.cities[city]["base_temp"]
        
        # Seasonal adjustments
        season_adjustments = {
            "spring": 0,
            "summer": 8,
            "autumn": -3,
            "winter": -10
        }
        
        adjusted_temp = base_temp + season_adjustments.get(season, 0)
        
        # Add some randomness
        variation = random.uniform(-5, 5)
        
        return round(adjusted_temp + variation, 1)
    
    def generate_humidity(self, city):
        """Generate realistic humidity for a city"""
        base_humidity = self.cities[city]["humidity_base"]
        variation = random.uniform(-15, 15)
        humidity = base_humidity + variation
        
        # Keep within realistic bounds
        return max(20, min(95, round(humidity)))
    
    def generate_weather_condition(self, temperature, humidity):
        """Determine weather condition based on temp and humidity"""
        if temperature > 30:
            return "Hot"
        elif temperature < 0:
            return "Freezing"
        elif humidity > 80:
            return "Rainy" if random.random() > 0.5 else "Cloudy"
        elif humidity < 30:
            return "Sunny"
        else:
            conditions = ["Partly Cloudy", "Clear", "Overcast"]
            return random.choice(conditions)
    
    def get_weather_report(self, city, season="spring"):
        """Generate complete weather report"""
        if city not in self.cities:
            return None
        
        temperature = self.generate_temperature(city, season)
        humidity = self.generate_humidity(city)
        condition = self.generate_weather_condition(temperature, humidity)
        
        # Calculate "feels like" temperature
        if humidity > 70 and temperature > 20:
            feels_like = temperature + 2  # Humidity makes it feel warmer
        elif humidity < 30 and temperature > 25:
            feels_like = temperature - 2  # Dry air feels cooler
        else:
            feels_like = temperature
        
        return {
            "city": city,
            "temperature": temperature,
            "feels_like": round(feels_like, 1),
            "humidity": humidity,
            "condition": condition,
            "timestamp": datetime.datetime.now().strftime("%Y-%m-%d %H:%M")
        }
    
    def weekly_forecast(self, city, season="spring"):
        """Generate 7-day forecast"""
        forecast = []
        
        for day in range(7):
            date = datetime.date.today() + datetime.timedelta(days=day)
            weather = self.get_weather_report(city, season)
            weather["date"] = date.strftime("%A, %B %d")
            forecast.append(weather)
        
        return forecast

def weather_app():
    """Interactive weather application"""
    simulator = WeatherSimulator()
    
    print("=== Weather Simulator ===")
    
    while True:
        print("\nAvailable cities:", list(simulator.cities.keys()))
        print("\nOptions:")
        print("1. Current weather")
        print("2. 7-day forecast")
        print("3. Compare cities")
        print("4. Exit")
        
        choice = input("\nChoose an option (1-4): ")
        
        if choice == "1":
            city = input("Enter city name: ").title()
            season = input("Enter season (spring/summer/autumn/winter): ").lower()
            
            weather = simulator.get_weather_report(city, season)
            if weather:
                print(f"\n=== Current Weather in {weather['city']} ===")
                print(f"Time: {weather['timestamp']}")
                print(f"Temperature: {weather['temperature']}°C")
                print(f"Feels like: {weather['feels_like']}°C")
                print(f"Humidity: {weather['humidity']}%")
                print(f"Condition: {weather['condition']}")
            else:
                print("City not found!")
        
        elif choice == "2":
            city = input("Enter city name: ").title()
            season = input("Enter season (spring/summer/autumn/winter): ").lower()
            
            if city in simulator.cities:
                forecast = simulator.weekly_forecast(city, season)
                print(f"\n=== 7-Day Forecast for {city} ===")
                
                for day_weather in forecast:
                    print(f"{day_weather['date']}")
                    print(f"  {day_weather['temperature']}°C, {day_weather['humidity']}%, {day_weather['condition']}")
            else:
                print("City not found!")
        
        elif choice == "3":
            season = input("Enter season (spring/summer/autumn/winter): ").lower()
            print(f"\n=== Weather Comparison ({season.title()}) ===")
            
            for city in simulator.cities:
                weather = simulator.get_weather_report(city, season)
                print(f"{city:12}: {weather['temperature']:5.1f}°C, {weather['humidity']:2d}%, {weather['condition']}")
        
        elif choice == "4":
            print("Thanks for using Weather Simulator!")
            break
        else:
            print("Invalid choice!")

# Run the weather app
weather_app()
```

### Example 3: File Organizer

```python
import os
import datetime
import shutil

def get_file_extension(filename):
    """Get the file extension from filename"""
    return os.path.splitext(filename)[1].lower()

def get_file_category(extension):
    """Categorize files based on extension"""
    categories = {
        'images': ['.jpg', '.jpeg', '.png', '.gif', '.bmp', '.svg'],
        'documents': ['.pdf', '.doc', '.docx', '.txt', '.rtf'],
        'spreadsheets': ['.xls', '.xlsx', '.csv'],
        'presentations': ['.ppt', '.pptx'],
        'videos': ['.mp4', '.avi', '.mov', '.wmv', '.flv'],
        'audio': ['.mp3', '.wav', '.flac', '.aac'],
        'archives': ['.zip', '.rar', '.7z', '.tar', '.gz'],
        'code': ['.py', '.js', '.html', '.css', '.java', '.cpp']
    }
    
    for category, extensions in categories.items():
        if extension in extensions:
            return category
    
    return 'other'

def get_file_info(filepath):
    """Get detailed information about a file"""
    try:
        stat = os.stat(filepath)
        size = stat.st_size
        modified_time = datetime.datetime.fromtimestamp(stat.st_mtime)
        
        # Convert size to human readable format
        if size < 1024:
            size_str = f"{size} B"
        elif size < 1024 * 1024:
            size_str = f"{size/1024:.1f} KB"
        elif size < 1024 * 1024 * 1024:
            size_str = f"{size/(1024*1024):.1f} MB"
        else:
            size_str = f"{size/(1024*1024*1024):.1f} GB"
        
        return {
            'name': os.path.basename(filepath),
            'size': size,
            'size_str': size_str,
            'modified': modified_time,
            'extension': get_file_extension(filepath),
            'category': get_file_category(get_file_extension(filepath))
        }
    except:
        return None

def analyze_directory(directory_path):
    """Analyze all files in a directory"""
    if not os.path.exists(directory_path):
        print(f"Directory '{directory_path}' not found!")
        return None
    
    files_info = []
    categories = {}
    total_size = 0
    
    try:
        for filename in os.listdir(directory_path):
            filepath = os.path.join(directory_path, filename)
            
            if os.path.isfile(filepath):
                file_info = get_file_info(filepath)
                if file_info:
                    files_info.append(file_info)
                    
                    # Update category counts
                    category = file_info['category']
                    if category not in categories:
                        categories[category] = {'count': 0, 'size': 0}
                    
                    categories[category]['count'] += 1
                    categories[category]['size'] += file_info['size']
                    total_size += file_info['size']
    
    except PermissionError:
        print(f"Permission denied to access '{directory_path}'")
        return None
    
    return {
        'files': files_info,
        'categories': categories,
        'total_size': total_size,
        'total_files': len(files_info)
    }

def display_analysis(analysis):
    """Display the directory analysis results"""
    if not analysis:
        return
    
    print(f"\n=== Directory Analysis ===")
    print(f"Total files: {analysis['total_files']}")
    
    # Convert total size to human readable
    total_size = analysis['total_size']
    if total_size < 1024:
        size_str = f"{total_size} B"
    elif total_size < 1024 * 1024:
        size_str = f"{total_size/1024:.1f} KB"
    elif total_size < 1024 * 1024 * 1024:
        size_str = f"{total_size/(1024*1024):.1f} MB"
    else:
        size_str = f"{total_size/(1024*1024*1024):.1f} GB"
    
    print(f"Total size: {size_str}")
    
    print(f"\n=== File Categories ===")
    for category, info in analysis['categories'].items():
        cat_size = info['size']
        if cat_size < 1024:
            cat_size_str = f"{cat_size} B"
        elif cat_size < 1024 * 1024:
            cat_size_str = f"{cat_size/1024:.1f} KB"
        elif cat_size < 1024 * 1024 * 1024:
            cat_size_str = f"{cat_size/(1024*1024):.1f} MB"
        else:
            cat_size_str = f"{cat_size/(1024*1024*1024):.1f} GB"
        
        print(f"{category.title():12}: {info['count']:3d} files, {cat_size_str}")

def find_large_files(analysis, min_size_mb=10):
    """Find files larger than specified size"""
    if not analysis:
        return []
    
    min_size_bytes = min_size_mb * 1024 * 1024
    large_files = []
    
    for file_info in analysis['files']:
        if file_info['size'] > min_size_bytes:
            large_files.append(file_info)
    
    # Sort by size (largest first)
    large_files.sort(key=lambda x: x['size'], reverse=True)
    
    return large_files

def find_old_files(analysis, days_old=30):
    """Find files older than specified days"""
    if not analysis:
        return []
    
    cutoff_date = datetime.datetime.now() - datetime.timedelta(days=days_old)
    old_files = []
    
    for file_info in analysis['files']:
        if file_info['modified'] < cutoff_date:
            old_files.append(file_info)
    
    # Sort by date (oldest first)
    old_files.sort(key=lambda x: x['modified'])
    
    return old_files

def file_organizer():
    """Interactive file organizer application"""
    print("=== File Organizer ===")
    
    while True:
        print("\nOptions:")
        print("1. Analyze directory")
        print("2. Find large files")
        print("3. Find old files")
        print("4. List files by category")
        print("5. Exit")
        
        choice = input("\nChoose an option (1-5): ")
        
        if choice == "1":
            directory = input("Enter directory path (or '.' for current): ")
            if directory == '.':
                directory = os.getcwd()
            
            analysis = analyze_directory(directory)
            if analysis:
                display_analysis(analysis)
                # Store analysis for other operations
                current_analysis = analysis
        
        elif choice == "2":
            try:
                min_size = float(input("Minimum file size in MB (default 10): ") or 10)
                large_files = find_large_files(current_analysis, min_size)
                
                if large_files:
                    print(f"\n=== Files larger than {min_size} MB ===")
                    for file_info in large_files[:10]:  # Show top 10
                        print(f"{file_info['name']:30} {file_info['size_str']:>10} {file_info['modified'].strftime('%Y-%m-%d')}")
                else:
                    print(f"No files found larger than {min_size} MB")
            except:
                print("Please analyze a directory first!")
        
        elif choice == "3":
            try:
                days = int(input("Files older than how many days (default 30): ") or 30)
                old_files = find_old_files(current_analysis, days)
                
                if old_files:
                    print(f"\n=== Files older than {days} days ===")
                    for file_info in old_files[:10]:  # Show top 10
                        print(f"{file_info['name']:30} {file_info['size_str']:>10} {file_info['modified'].strftime('%Y-%m-%d')}")
                else:
                    print(f"No files found older than {days} days")
            except:
                print("Please analyze a directory first!")
        
        elif choice == "4":
            try:
                print(f"\n=== Files by Category ===")
                categories = current_analysis['categories']
                
                for category in categories:
                    print(f"\n{category.title()}:")
                    category_files = [f for f in current_analysis['files'] if f['category'] == category]
                    
                    for file_info in category_files[:5]:  # Show first 5 files
                        print(f"  {file_info['name']:25} {file_info['size_str']:>8}")
                    
                    if len(category_files) > 5:
                        print(f"  ... and {len(category_files) - 5} more files")
            except:
                print("Please analyze a directory first!")
        
        elif choice == "5":
            print("Thanks for using File Organizer!")
            break
        else:
            print("Invalid choice!")

# Initialize variables
current_analysis = None

# Run the file organizer
file_organizer()
```

---

## 6. Best Practices

### 1. Import Organization

```python
# Good import organization:

# Standard library imports first
import os
import sys
import datetime

# Third-party imports second
import requests
import numpy as np

# Local application imports last
from my_utils import calculate_area
from config import DATABASE_URL

# Avoid wildcard imports in production code
# from module import *  # Don't do this!
```

### 2. Use Virtual Environments

```bash
# Create virtual environment
python -m venv myproject_env

# Activate virtual environment
# Windows:
myproject_env\Scripts\activate

# macOS/Linux:
source myproject_env/bin/activate

# Install packages in virtual environment
pip install requests numpy

# Save requirements
pip freeze > requirements.txt

# Deactivate when done
deactivate
```

### 3. Handle Import Errors

```python
# Handle missing optional modules gracefully
try:
    import requests
    HAS_REQUESTS = True
except ImportError:
    HAS_REQUESTS = False
    print("Warning: 'requests' module not available. Some features disabled.")

def download_file(url):
    if not HAS_REQUESTS:
        print("Cannot download: requests module not installed")
        return None
    
    response = requests.get(url)
    return response.content
```

### 4. Module Documentation

```python
"""
My Utilities Module

This module provides utility functions for common tasks including:
- Mathematical calculations
- String processing
- File operations

Example usage:
    import my_utils
    area = my_utils.calculate_circle_area(5)
"""

__author__ = "Your Name"
__version__ = "1.0.0"
__email__ = "your.email@example.com"

def calculate_circle_area(radius):
    """
    Calculate the area of a circle.
    
    Args:
        radius (float): The radius of the circle
        
    Returns:
        float: The area of the circle
        
    Example:
        >>> calculate_circle_area(5)
        78.53981633974483
    """
    import math
    return math.pi * radius * radius
```

---

## 7. Common Mistakes to Avoid

### Mistake 1: Circular Imports

```python
# file1.py
import file2

def function1():
    return file2.function2()

# file2.py
import file1  # This creates a circular import!

def function2():
    return file1.function1()

# Solution: Restructure your code to avoid circular dependencies
```

### Mistake 2: Modifying sys.path Incorrectly

```python
# Wrong way to add module paths
import sys
sys.path.append('/some/random/path')  # Avoid this!

# Better: Use proper package structure and virtual environments
```

### Mistake 3: Not Handling Missing Modules

```python
# Wrong - will crash if module is missing
import some_optional_module

# Better - handle gracefully
try:
    import some_optional_module
except ImportError:
    print("Optional module not available")
    some_optional_module = None
```

---

## 8. Practice Exercises

### Exercise 1: Math Toolkit
Create a comprehensive math toolkit using various modules:

```python
# Your code here
import math
import random
import statistics

def create_math_toolkit():
    """Create a comprehensive math toolkit"""
    
    def basic_stats(numbers):
        """Calculate basic statistics for a list of numbers"""
        # Use statistics module to calculate:
        # - mean, median, mode
        # - standard deviation
        # - min, max, range
        pass
    
    def geometry_calculator():
        """Calculate areas and volumes of shapes"""
        # Implement functions for:
        # - Circle area and circumference
        # - Rectangle area and perimeter
        # - Triangle area (using Heron's formula)
        # - Sphere volume and surface area
        pass
    
    def probability_simulator():
        """Simulate probability experiments"""
        # Implement:
        # - Coin flip simulation
        # - Dice roll simulation
        # - Card draw simulation
        # - Random walk simulation
        pass
    
    def number_theory():
        """Number theory functions"""
        # Implement:
        # - Prime number checker
        # - GCD and LCM calculator
        # - Fibonacci sequence generator
        # - Perfect number checker
        pass

# Test your toolkit
create_math_toolkit()
```

### Exercise 2: Date and Time Utilities
Create useful date and time utilities:

```python
# Your code here
import datetime
import calendar

def create_datetime_utilities():
    """Create comprehensive date/time utilities"""
    
    def age_calculator(birth_date):
        """Calculate age in years, months, days"""
        pass
    
    def business_days_calculator(start_date, end_date):
        """Calculate business days between two dates"""
        pass
    
    def time_zone_converter(time_str, from_tz, to_tz):
        """Convert time between time zones"""
        pass
    
    def calendar_generator(year, month):
        """Generate a formatted calendar for display"""
        pass
    
    def deadline_tracker(deadlines):
        """Track upcoming deadlines and show urgency"""
        pass

# Test your utilities
create_datetime_utilities()
```

### Exercise 3: File Management System
Create a file management system using os and other modules:

```python
# Your code here
import os
import shutil
import datetime

def create_file_manager():
    """Create a comprehensive file management system"""
    
    def duplicate_finder(directory):
        """Find duplicate files in a directory"""
        pass
    
    def file_organizer(source_dir, target_dir):
        """Organize files into folders by type"""
        pass
    
    def disk_usage_analyzer(directory):
        """Analyze disk usage by file type"""
        pass
    
    def backup_creator(source_dir, backup_dir):
        """Create incremental backups"""
        pass
    
    def log_file_analyzer(log_file):
        """Analyze log files for patterns"""
        pass

# Test your file manager
create_file_manager()
```

### Exercise 4: Random Data Generator
Create a system to generate realistic test data:

```python
# Your code here
import random
import string
import datetime

def create_data_generator():
    """Create realistic test data generator"""
    
    def generate_person():
        """Generate realistic person data"""
        # Include: name, age, email, phone, address
        pass
    
    def generate_company():
        """Generate company data"""
        # Include: name, industry, employees, revenue
        pass
    
    def generate_transaction():
        """Generate financial transaction data"""
        # Include: amount, date, description, category
        pass
    
    def generate_product():
        """Generate product data"""
        # Include: name, price, category, description
        pass
    
    def export_to_csv(data, filename):
        """Export generated data to CSV file"""
        pass

# Test your data generator
create_data_generator()
```

### Exercise 5: System Information Tool
Create a tool to gather system information:

```python
# Your code here
import os
import datetime
import platform

def create_system_info_tool():
    """Create comprehensive system information tool"""
    
    def get_system_info():
        """Get basic system information"""
        # Include: OS, Python version, architecture
        pass
    
    def get_directory_info(path):
        """Get detailed directory information"""
        # Include: file count, size, permissions
        pass
    
    def get_environment_info():
        """Get environment variables"""
        pass
    
    def generate_system_report():
        """Generate comprehensive system report"""
        pass
    
    def monitor_resources():
        """Basic resource monitoring"""
        pass

# Test your system tool
create_system_info_tool()
```

### Exercise 6: Package Installation Helper
Create a tool to help manage Python packages:

```python
# Your code here
import subprocess
import sys

def create_package_manager():
    """Create package management helper"""
    
    def list_installed_packages():
        """List all installed packages"""
        pass
    
    def check_package_info(package_name):
        """Get information about a package"""
        pass
    
    def install_package(package_name):
        """Install a package safely"""
        pass
    
    def create_requirements_file(filename="requirements.txt"):
        """Create requirements.txt file"""
        pass
    
    def check_outdated_packages():
        """Find outdated packages"""
        pass

# Test your package manager
create_package_manager()
```

---

## Summary

In this comprehensive guide, you learned about Python modules and packages:

- ✅ **Module concepts** and the benefits of code organization
- ✅ **Import methods** including basic import, specific imports, and aliases
- ✅ **Built-in modules** like math, random, datetime, and os
- ✅ **Creating custom modules** to organize your own code
- ✅ **External packages** and how to install them with pip
- ✅ **Real-world applications** including password generators and file organizers
- ✅ **Best practices** for imports, virtual environments, and documentation
- ✅ **Common mistakes** and how to avoid them

### Key Takeaways:
- **Use modules** to avoid reinventing the wheel and organize code better
- **Import only what you need** to keep your namespace clean
- **Explore built-in modules** before looking for external packages
- **Use virtual environments** to manage dependencies properly
- **Document your modules** to help others (and future you) understand them
- **Handle import errors** gracefully for optional dependencies

### Next Steps:
- Practice with the exercises to reinforce your understanding
- Explore the Python standard library documentation
- Try installing and using popular external packages
- Create your own modules to organize larger projects
- Learn about package distribution when you're ready to share your code

**Next:** Continue to learn about File Handling to work with external data and persist information!