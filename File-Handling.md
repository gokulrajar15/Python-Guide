# Python File Handling

File handling is like having a filing cabinet for your computer programs! It allows you to save data permanently, read information from external sources, and share data between different programs. Think of it as teaching your program how to read books, write letters, and organize documents.

## What is File Handling?

In real life, you might:
- Read a book to get information
- Write notes in a notebook to remember things
- Save important documents in a folder
- Share files with friends

File handling in Python works the same way:
- **Reading files**: Get data from existing files (like reading a book)
- **Writing files**: Save data to files (like writing in a diary)
- **Appending files**: Add new data to existing files (like adding to a shopping list)

```python
# Instead of losing your data when the program ends...
high_score = 1500
print(f"High score: {high_score}")
# When program closes, high_score is lost forever! 😢

# You can save it to a file for next time!
with open("game_data.txt", "w") as file:
    file.write(f"High Score: {high_score}")
# Now it's saved permanently! 😊
```

## Benefits of File Handling

- **Persistence**: Data survives after your program ends
- **Sharing**: Exchange data between programs and people
- **Backup**: Keep copies of important information
- **Processing**: Work with large amounts of data
- **Configuration**: Store settings and preferences

---

## 1. Opening and Closing Files

### Basic File Operations

Every file operation follows the same pattern:
1. **Open** the file
2. **Do something** with it (read/write)
3. **Close** the file

```python
# Method 1: Manual open/close
file = open("example.txt", "r")  # Open for reading
content = file.read()            # Read the content
file.close()                     # Always close when done!

print(content)
```

### The Better Way: Using `with` Statement

The `with` statement automatically closes files, even if an error occurs:

```python
# Method 2: Using 'with' (recommended!)
with open("example.txt", "r") as file:
    content = file.read()
    print(content)
# File automatically closes here, even if there's an error!
```

### File Modes

Different modes let you do different things with files:

| Mode | Description | What it does |
|------|-------------|--------------|
| `"r"` | Read | Opens file for reading (default) |
| `"w"` | Write | Opens file for writing (overwrites existing content) |
| `"a"` | Append | Opens file for writing (adds to end of existing content) |
| `"r+"` | Read/Write | Opens file for both reading and writing |
| `"x"` | Exclusive Create | Creates new file (fails if file exists) |

```python
# Reading mode (default)
with open("data.txt", "r") as file:
    content = file.read()

# Writing mode (overwrites everything!)
with open("data.txt", "w") as file:
    file.write("New content replaces everything!")

# Append mode (adds to the end)
with open("data.txt", "a") as file:
    file.write("This gets added to the end!")
```

---

## 2. Reading Files

### Reading the Entire File

```python
# Read everything at once
with open("story.txt", "r") as file:
    entire_story = file.read()
    print(entire_story)

# Example story.txt content:
# Once upon a time, there was a Python programmer.
# They learned about file handling.
# And they lived happily ever after.
```

### Reading Line by Line

```python
# Method 1: Read all lines into a list
with open("grocery_list.txt", "r") as file:
    lines = file.readlines()
    
    print("Your grocery list:")
    for i, item in enumerate(lines, 1):
        print(f"{i}. {item.strip()}")  # strip() removes newline characters

# Method 2: Read one line at a time
with open("grocery_list.txt", "r") as file:
    print("Reading line by line:")
    for line_number, line in enumerate(file, 1):
        print(f"Line {line_number}: {line.strip()}")
```

### Reading Large Files Efficiently

```python
# For large files, read one line at a time to save memory
def process_large_file(filename):
    line_count = 0
    word_count = 0
    
    with open(filename, "r") as file:
        for line in file:
            line_count += 1
            word_count += len(line.split())
            
            # Process each line without loading entire file into memory
            if line_count % 1000 == 0:
                print(f"Processed {line_count} lines so far...")
    
    print(f"File analysis complete:")
    print(f"Total lines: {line_count}")
    print(f"Total words: {word_count}")

# This works even for files with millions of lines!
```

### Practical Reading Example

```python
def read_student_grades(filename):
    """Read and process student grades from a file"""
    students = {}
    
    try:
        with open(filename, "r") as file:
            for line_number, line in enumerate(file, 1):
                line = line.strip()  # Remove whitespace
                
                if line and not line.startswith("#"):  # Skip empty lines and comments
                    parts = line.split(",")  # Assuming CSV format
                    
                    if len(parts) >= 2:
                        name = parts[0].strip()
                        try:
                            grade = float(parts[1].strip())
                            students[name] = grade
                        except ValueError:
                            print(f"Warning: Invalid grade on line {line_number}: {line}")
                    else:
                        print(f"Warning: Invalid format on line {line_number}: {line}")
        
        return students
        
    except FileNotFoundError:
        print(f"Error: File '{filename}' not found!")
        return {}

# Example usage
grades = read_student_grades("grades.csv")
if grades:
    print("Student Grades:")
    for name, grade in grades.items():
        print(f"{name}: {grade}")
    
    average = sum(grades.values()) / len(grades)
    print(f"Class average: {average:.1f}")
```

---

## 3. Writing Files

### Writing Text to Files

```python
# Write new content (overwrites existing content)
with open("message.txt", "w") as file:
    file.write("Hello, World!")
    file.write("This is a new line.")  # This continues on same line!

# To write on separate lines, add newline characters
with open("message.txt", "w") as file:
    file.write("Hello, World!\n")     # \n creates a new line
    file.write("This is a new line.\n")
    file.write("And another line!\n")

# Alternative: use print() with file parameter
with open("message.txt", "w") as file:
    print("Hello, World!", file=file)
    print("This automatically goes on a new line!", file=file)
    print("Much easier than adding \\n everywhere!", file=file)
```

### Writing Multiple Lines

```python
# Write a list of lines
shopping_list = ["Apples", "Bananas", "Bread", "Milk", "Eggs"]

with open("shopping.txt", "w") as file:
    for item in shopping_list:
        file.write(f"{item}\n")

# Or use writelines() (but you need to add \n yourself)
with open("shopping.txt", "w") as file:
    lines = [f"{item}\n" for item in shopping_list]
    file.writelines(lines)

# Even better: join the list
with open("shopping.txt", "w") as file:
    file.write("\n".join(shopping_list))
```

### Appending to Files

```python
# Add new content without erasing existing content
with open("diary.txt", "a") as file:
    import datetime
    today = datetime.date.today()
    file.write(f"\n{today}: Today I learned about file handling!")

# Practical example: Logging events
def log_event(message):
    """Add an event to the log file with timestamp"""
    import datetime
    
    timestamp = datetime.datetime.now().strftime("%Y-%m-%d %H:%M:%S")
    log_entry = f"[{timestamp}] {message}\n"
    
    with open("activity.log", "a") as file:
        file.write(log_entry)

# Usage
log_event("Program started")
log_event("User logged in")
log_event("File processed successfully")
log_event("Program ended")
```

---

## 4. Working with CSV Files

CSV (Comma-Separated Values) files are a popular way to store structured data:

### Writing CSV Files

```python
def save_students_to_csv(students, filename):
    """Save student data to CSV file"""
    
    with open(filename, "w") as file:
        # Write header
        file.write("Name,Age,Grade,Email\n")
        
        # Write student data
        for student in students:
            line = f"{student['name']},{student['age']},{student['grade']},{student['email']}\n"
            file.write(line)

# Example data
students = [
    {"name": "Alice Johnson", "age": 20, "grade": "A", "email": "alice@email.com"},
    {"name": "Bob Smith", "age": 19, "grade": "B", "email": "bob@email.com"},
    {"name": "Charlie Brown", "age": 21, "grade": "A", "email": "charlie@email.com"}
]

save_students_to_csv(students, "students.csv")
print("Student data saved to students.csv")
```

### Reading CSV Files

```python
def read_students_from_csv(filename):
    """Read student data from CSV file"""
    students = []
    
    try:
        with open(filename, "r") as file:
            lines = file.readlines()
            
            if not lines:
                print("File is empty!")
                return []
            
            # Skip header line
            header = lines[0].strip().split(",")
            print(f"CSV columns: {header}")
            
            # Process data lines
            for line_number, line in enumerate(lines[1:], 2):
                line = line.strip()
                if line:  # Skip empty lines
                    values = line.split(",")
                    
                    if len(values) == len(header):
                        student = {}
                        for i, column in enumerate(header):
                            student[column.lower()] = values[i].strip()
                        students.append(student)
                    else:
                        print(f"Warning: Line {line_number} has wrong number of columns")
        
        return students
        
    except FileNotFoundError:
        print(f"Error: File '{filename}' not found!")
        return []

# Usage
students = read_students_from_csv("students.csv")
for student in students:
    print(f"Name: {student['name']}, Age: {student['age']}, Grade: {student['grade']}")
```

---

## 5. File Paths and Directories

### Working with File Paths

```python
import os

# Get current working directory
current_dir = os.getcwd()
print(f"Current directory: {current_dir}")

# Join paths properly (works on Windows, Mac, and Linux)
data_folder = os.path.join(current_dir, "data")
student_file = os.path.join(data_folder, "students.txt")
backup_file = os.path.join(data_folder, "backup", "students_backup.txt")

print(f"Student file path: {student_file}")
print(f"Backup file path: {backup_file}")

# Check if files and directories exist
print(f"Data folder exists: {os.path.exists(data_folder)}")
print(f"Student file exists: {os.path.exists(student_file)}")

# Create directories if they don't exist
if not os.path.exists(data_folder):
    os.makedirs(data_folder)
    print(f"Created directory: {data_folder}")

# Get file information
if os.path.exists(student_file):
    file_size = os.path.getsize(student_file)
    print(f"File size: {file_size} bytes")
```

### Organizing Files by Type

```python
def organize_files_by_type(source_folder, target_folder):
    """Organize files into subfolders by file extension"""
    
    if not os.path.exists(source_folder):
        print(f"Source folder '{source_folder}' doesn't exist!")
        return
    
    # Create target folder if it doesn't exist
    os.makedirs(target_folder, exist_ok=True)
    
    # File type categories
    file_types = {
        'images': ['.jpg', '.jpeg', '.png', '.gif', '.bmp'],
        'documents': ['.txt', '.pdf', '.doc', '.docx'],
        'data': ['.csv', '.json', '.xml'],
        'code': ['.py', '.js', '.html', '.css']
    }
    
    files_moved = 0
    
    # Get all files in source folder
    for filename in os.listdir(source_folder):
        file_path = os.path.join(source_folder, filename)
        
        if os.path.isfile(file_path):
            # Get file extension
            _, extension = os.path.splitext(filename)
            extension = extension.lower()
            
            # Find appropriate category
            category = 'other'  # default category
            for cat, extensions in file_types.items():
                if extension in extensions:
                    category = cat
                    break
            
            # Create category folder
            category_folder = os.path.join(target_folder, category)
            os.makedirs(category_folder, exist_ok=True)
            
            # Move file (in this example, we'll copy content instead of moving)
            source_file = os.path.join(source_folder, filename)
            target_file = os.path.join(category_folder, filename)
            
            try:
                # Copy file content
                with open(source_file, 'r') as src:
                    content = src.read()
                
                with open(target_file, 'w') as dst:
                    dst.write(content)
                
                print(f"Organized: {filename} -> {category}/")
                files_moved += 1
                
            except Exception as e:
                print(f"Error organizing {filename}: {e}")
    
    print(f"Organized {files_moved} files into {target_folder}")

# Example usage
# organize_files_by_type("downloads", "organized_files")
```

---

## 6. Error Handling with Files

### Common File Errors and Solutions

```python
def safe_file_operation(filename, mode="r", content=None):
    """Safely perform file operations with proper error handling"""
    
    try:
        with open(filename, mode) as file:
            if mode == "r":
                return file.read()
            elif mode in ["w", "a"]:
                if content:
                    file.write(content)
                    return True
                
    except FileNotFoundError:
        print(f"Error: File '{filename}' not found!")
        
        # Offer to create the file if we're writing
        if mode in ["w", "a"]:
            create = input(f"Create '{filename}'? (y/n): ")
            if create.lower() == 'y':
                try:
                    with open(filename, mode) as file:
                        if content:
                            file.write(content)
                        print(f"Created '{filename}' successfully!")
                        return True
                except Exception as e:
                    print(f"Failed to create file: {e}")
        
        return None
        
    except PermissionError:
        print(f"Error: Permission denied to access '{filename}'!")
        print("Make sure the file isn't open in another program.")
        return None
        
    except IsADirectoryError:
        print(f"Error: '{filename}' is a directory, not a file!")
        return None
        
    except Exception as e:
        print(f"Unexpected error: {e}")
        return None

# Examples
content = safe_file_operation("test.txt", "r")
if content:
    print("File content:", content)

success = safe_file_operation("output.txt", "w", "Hello, World!")
if success:
    print("File written successfully!")
```

### Backup and Recovery

```python
import datetime
import os

def create_backup(original_file):
    """Create a backup copy of a file"""
    
    if not os.path.exists(original_file):
        print(f"Original file '{original_file}' doesn't exist!")
        return False
    
    # Create backup filename with timestamp
    timestamp = datetime.datetime.now().strftime("%Y%m%d_%H%M%S")
    name, ext = os.path.splitext(original_file)
    backup_file = f"{name}_backup_{timestamp}{ext}"
    
    try:
        # Copy content to backup file
        with open(original_file, 'r') as src:
            content = src.read()
        
        with open(backup_file, 'w') as dst:
            dst.write(content)
        
        print(f"Backup created: {backup_file}")
        return backup_file
        
    except Exception as e:
        print(f"Failed to create backup: {e}")
        return False

def safe_file_write(filename, content, create_backup=True):
    """Safely write to file with optional backup"""
    
    # Create backup if file exists
    if create_backup and os.path.exists(filename):
        backup_file = create_backup(filename)
        if not backup_file:
            print("Backup failed! Aborting write operation.")
            return False
    
    # Write new content
    try:
        with open(filename, 'w') as file:
            file.write(content)
        print(f"File '{filename}' updated successfully!")
        return True
        
    except Exception as e:
        print(f"Failed to write file: {e}")
        
        # If backup exists, offer to restore
        if create_backup and backup_file:
            restore = input("Restore from backup? (y/n): ")
            if restore.lower() == 'y':
                try:
                    with open(backup_file, 'r') as src:
                        backup_content = src.read()
                    with open(filename, 'w') as dst:
                        dst.write(backup_content)
                    print("File restored from backup!")
                except:
                    print("Failed to restore from backup!")
        
        return False

# Example usage
content = "Important data that must not be lost!"
safe_file_write("important.txt", content, create_backup=True)
```

---

## 7. Real-World Examples

### Example 1: Simple Database System

```python
import json
import datetime

class SimpleDatabase:
    """A simple file-based database for storing records"""
    
    def __init__(self, filename):
        self.filename = filename
        self.data = self.load_data()
    
    def load_data(self):
        """Load data from file"""
        try:
            with open(self.filename, 'r') as file:
                return json.loads(file.read()) if file.read() else {}
        except FileNotFoundError:
            return {}
        except json.JSONDecodeError:
            print("Warning: Database file is corrupted. Starting fresh.")
            return {}
    
    def save_data(self):
        """Save data to file"""
        try:
            with open(self.filename, 'w') as file:
                json.dump(self.data, file, indent=2)
            return True
        except Exception as e:
            print(f"Failed to save data: {e}")
            return False
    
    def add_record(self, table, record_id, data):
        """Add a record to a table"""
        if table not in self.data:
            self.data[table] = {}
        
        # Add timestamp
        data['created_at'] = datetime.datetime.now().isoformat()
        data['updated_at'] = datetime.datetime.now().isoformat()
        
        self.data[table][record_id] = data
        return self.save_data()
    
    def get_record(self, table, record_id):
        """Get a specific record"""
        return self.data.get(table, {}).get(record_id)
    
    def get_all_records(self, table):
        """Get all records from a table"""
        return self.data.get(table, {})
    
    def update_record(self, table, record_id, updates):
        """Update an existing record"""
        if table in self.data and record_id in self.data[table]:
            self.data[table][record_id].update(updates)
            self.data[table][record_id]['updated_at'] = datetime.datetime.now().isoformat()
            return self.save_data()
        return False
    
    def delete_record(self, table, record_id):
        """Delete a record"""
        if table in self.data and record_id in self.data[table]:
            del self.data[table][record_id]
            return self.save_data()
        return False

# Example: Contact Management System
def contact_manager():
    """Simple contact management using file database"""
    db = SimpleDatabase("contacts.json")
    
    while True:
        print("\n=== Contact Manager ===")
        print("1. Add Contact")
        print("2. View Contact")
        print("3. List All Contacts")
        print("4. Update Contact")
        print("5. Delete Contact")
        print("6. Exit")
        
        choice = input("Choose an option (1-6): ")
        
        if choice == "1":
            name = input("Name: ")
            phone = input("Phone: ")
            email = input("Email: ")
            
            contact_data = {"name": name, "phone": phone, "email": email}
            if db.add_record("contacts", name.lower(), contact_data):
                print(f"Contact '{name}' added successfully!")
            else:
                print("Failed to add contact!")
        
        elif choice == "2":
            name = input("Enter name to search: ")
            contact = db.get_record("contacts", name.lower())
            
            if contact:
                print(f"\nName: {contact['name']}")
                print(f"Phone: {contact['phone']}")
                print(f"Email: {contact['email']}")
                print(f"Added: {contact['created_at']}")
            else:
                print("Contact not found!")
        
        elif choice == "3":
            contacts = db.get_all_records("contacts")
            
            if contacts:
                print("\n=== All Contacts ===")
                for contact_id, contact in contacts.items():
                    print(f"Name: {contact['name']}, Phone: {contact['phone']}")
            else:
                print("No contacts found!")
        
        elif choice == "4":
            name = input("Enter name to update: ")
            contact = db.get_record("contacts", name.lower())
            
            if contact:
                print(f"Current info - Phone: {contact['phone']}, Email: {contact['email']}")
                new_phone = input(f"New phone (current: {contact['phone']}): ")
                new_email = input(f"New email (current: {contact['email']}): ")
                
                updates = {}
                if new_phone: updates['phone'] = new_phone
                if new_email: updates['email'] = new_email
                
                if updates and db.update_record("contacts", name.lower(), updates):
                    print("Contact updated successfully!")
                else:
                    print("No changes made!")
            else:
                print("Contact not found!")
        
        elif choice == "5":
            name = input("Enter name to delete: ")
            
            if db.delete_record("contacts", name.lower()):
                print(f"Contact '{name}' deleted successfully!")
            else:
                print("Contact not found!")
        
        elif choice == "6":
            print("Goodbye!")
            break
        
        else:
            print("Invalid choice!")

# Run the contact manager
contact_manager()
```

### Example 2: Log File Analyzer

```python
import re
import datetime
from collections import defaultdict

class LogAnalyzer:
    """Analyze log files for patterns and statistics"""
    
    def __init__(self, log_file):
        self.log_file = log_file
        self.entries = []
        self.load_logs()
    
    def load_logs(self):
        """Load and parse log entries"""
        try:
            with open(self.log_file, 'r') as file:
                for line_number, line in enumerate(file, 1):
                    line = line.strip()
                    if line:
                        entry = self.parse_log_entry(line, line_number)
                        if entry:
                            self.entries.append(entry)
        
        except FileNotFoundError:
            print(f"Log file '{self.log_file}' not found!")
    
    def parse_log_entry(self, line, line_number):
        """Parse a single log entry"""
        # Common log format: [YYYY-MM-DD HH:MM:SS] LEVEL: Message
        pattern = r'\[(\d{4}-\d{2}-\d{2} \d{2}:\d{2}:\d{2})\] (\w+): (.+)'
        match = re.match(pattern, line)
        
        if match:
            timestamp_str, level, message = match.groups()
            try:
                timestamp = datetime.datetime.strptime(timestamp_str, "%Y-%m-%d %H:%M:%S")
                return {
                    'timestamp': timestamp,
                    'level': level.upper(),
                    'message': message,
                    'line_number': line_number
                }
            except ValueError:
                print(f"Invalid timestamp on line {line_number}: {timestamp_str}")
        else:
            print(f"Invalid log format on line {line_number}: {line}")
        
        return None
    
    def get_statistics(self):
        """Get basic log statistics"""
        if not self.entries:
            return None
        
        stats = {
            'total_entries': len(self.entries),
            'level_counts': defaultdict(int),
            'time_range': {
                'start': min(entry['timestamp'] for entry in self.entries),
                'end': max(entry['timestamp'] for entry in self.entries)
            },
            'errors': [],
            'warnings': []
        }
        
        for entry in self.entries:
            stats['level_counts'][entry['level']] += 1
            
            if entry['level'] == 'ERROR':
                stats['errors'].append(entry)
            elif entry['level'] == 'WARNING':
                stats['warnings'].append(entry)
        
        return stats
    
    def find_patterns(self, pattern, case_sensitive=False):
        """Find entries matching a specific pattern"""
        flags = 0 if case_sensitive else re.IGNORECASE
        compiled_pattern = re.compile(pattern, flags)
        
        matches = []
        for entry in self.entries:
            if compiled_pattern.search(entry['message']):
                matches.append(entry)
        
        return matches
    
    def filter_by_level(self, level):
        """Filter entries by log level"""
        level = level.upper()
        return [entry for entry in self.entries if entry['level'] == level]
    
    def filter_by_time_range(self, start_time, end_time):
        """Filter entries within a time range"""
        return [entry for entry in self.entries 
                if start_time <= entry['timestamp'] <= end_time]
    
    def generate_report(self, output_file=None):
        """Generate a comprehensive log analysis report"""
        stats = self.get_statistics()
        
        if not stats:
            report = "No log entries found!"
        else:
            report = f"""Log Analysis Report
{'='*50}
File: {self.log_file}
Analysis Date: {datetime.datetime.now().strftime('%Y-%m-%d %H:%M:%S')}

SUMMARY:
Total Entries: {stats['total_entries']}
Time Range: {stats['time_range']['start']} to {stats['time_range']['end']}
Duration: {stats['time_range']['end'] - stats['time_range']['start']}

LOG LEVELS:
"""
            
            for level, count in sorted(stats['level_counts'].items()):
                percentage = (count / stats['total_entries']) * 100
                report += f"{level:10}: {count:5} ({percentage:5.1f}%)\n"
            
            if stats['errors']:
                report += f"\nRECENT ERRORS ({len(stats['errors'])}):\n"
                for error in stats['errors'][-5:]:  # Show last 5 errors
                    report += f"[{error['timestamp']}] {error['message']}\n"
            
            if stats['warnings']:
                report += f"\nRECENT WARNINGS ({len(stats['warnings'])}):\n"
                for warning in stats['warnings'][-5:]:  # Show last 5 warnings
                    report += f"[{warning['timestamp']}] {warning['message']}\n"
        
        # Output report
        if output_file:
            try:
                with open(output_file, 'w') as file:
                    file.write(report)
                print(f"Report saved to {output_file}")
            except Exception as e:
                print(f"Failed to save report: {e}")
                print(report)
        else:
            print(report)

# Example: Create sample log and analyze it
def create_sample_log():
    """Create a sample log file for testing"""
    import random
    
    log_entries = []
    start_time = datetime.datetime.now() - datetime.timedelta(hours=24)
    
    levels = ['INFO', 'WARNING', 'ERROR', 'DEBUG']
    messages = {
        'INFO': ['User logged in', 'Request processed', 'Data saved', 'Cache updated'],
        'WARNING': ['Low disk space', 'Slow query detected', 'High memory usage'],
        'ERROR': ['Database connection failed', 'File not found', 'Permission denied'],
        'DEBUG': ['Function called', 'Variable set', 'Loop iteration']
    }
    
    for i in range(100):
        timestamp = start_time + datetime.timedelta(minutes=random.randint(1, 1440))
        level = random.choice(levels)
        message = random.choice(messages[level])
        
        log_entry = f"[{timestamp.strftime('%Y-%m-%d %H:%M:%S')}] {level}: {message}"
        log_entries.append(log_entry)
    
    # Sort by timestamp
    log_entries.sort()
    
    with open("sample.log", "w") as file:
        file.write("\n".join(log_entries))
    
    print("Sample log file created: sample.log")

# Usage example
create_sample_log()
analyzer = LogAnalyzer("sample.log")
analyzer.generate_report("log_analysis.txt")

# Find specific patterns
errors = analyzer.filter_by_level("ERROR")
print(f"\nFound {len(errors)} error entries")

database_issues = analyzer.find_patterns("database")
print(f"Found {len(database_issues)} database-related entries")
```

### Example 3: Configuration File Manager

```python
class ConfigManager:
    """Manage application configuration using files"""
    
    def __init__(self, config_file="config.txt"):
        self.config_file = config_file
        self.config = {}
        self.load_config()
    
    def load_config(self):
        """Load configuration from file"""
        try:
            with open(self.config_file, 'r') as file:
                for line_number, line in enumerate(file, 1):
                    line = line.strip()
                    
                    # Skip empty lines and comments
                    if line and not line.startswith('#'):
                        if '=' in line:
                            key, value = line.split('=', 1)
                            key = key.strip()
                            value = value.strip()
                            
                            # Convert common types
                            self.config[key] = self.convert_value(value)
                        else:
                            print(f"Warning: Invalid format on line {line_number}: {line}")
        
        except FileNotFoundError:
            print(f"Config file '{self.config_file}' not found. Using defaults.")
            self.create_default_config()
    
    def convert_value(self, value):
        """Convert string values to appropriate types"""
        # Boolean
        if value.lower() in ('true', 'false'):
            return value.lower() == 'true'
        
        # Integer
        if value.isdigit() or (value.startswith('-') and value[1:].isdigit()):
            return int(value)
        
        # Float
        try:
            return float(value)
        except ValueError:
            pass
        
        # String (remove quotes if present)
        if (value.startswith('"') and value.endswith('"')) or \
           (value.startswith("'") and value.endswith("'")):
            return value[1:-1]
        
        return value
    
    def save_config(self):
        """Save current configuration to file"""
        try:
            with open(self.config_file, 'w') as file:
                file.write("# Configuration File\n")
                file.write(f"# Generated on {datetime.datetime.now().strftime('%Y-%m-%d %H:%M:%S')}\n\n")
                
                for key, value in sorted(self.config.items()):
                    # Format value based on type
                    if isinstance(value, str):
                        formatted_value = f'"{value}"'
                    elif isinstance(value, bool):
                        formatted_value = str(value).lower()
                    else:
                        formatted_value = str(value)
                    
                    file.write(f"{key} = {formatted_value}\n")
            
            return True
        
        except Exception as e:
            print(f"Failed to save config: {e}")
            return False
    
    def get(self, key, default=None):
        """Get configuration value"""
        return self.config.get(key, default)
    
    def set(self, key, value):
        """Set configuration value"""
        self.config[key] = value
    
    def create_default_config(self):
        """Create default configuration"""
        self.config = {
            'app_name': 'My Python Application',
            'debug_mode': False,
            'max_users': 100,
            'timeout': 30.0,
            'database_url': 'sqlite://local.db',
            'log_level': 'INFO'
        }
        self.save_config()
        print(f"Default config created: {self.config_file}")
    
    def display_config(self):
        """Display current configuration"""
        print(f"\nCurrent Configuration ({self.config_file}):")
        print("=" * 40)
        
        for key, value in sorted(self.config.items()):
            print(f"{key:20}: {value} ({type(value).__name__})")
    
    def interactive_editor(self):
        """Interactive configuration editor"""
        while True:
            print("\n=== Configuration Editor ===")
            print("1. View Configuration")
            print("2. Set Value")
            print("3. Delete Key")
            print("4. Save Configuration")
            print("5. Reload from File")
            print("6. Reset to Defaults")
            print("7. Exit")
            
            choice = input("Choose an option (1-7): ")
            
            if choice == "1":
                self.display_config()
            
            elif choice == "2":
                key = input("Enter key: ")
                value = input(f"Enter value for '{key}': ")
                
                # Try to convert to appropriate type
                converted_value = self.convert_value(value)
                self.set(key, converted_value)
                print(f"Set {key} = {converted_value} ({type(converted_value).__name__})")
            
            elif choice == "3":
                key = input("Enter key to delete: ")
                if key in self.config:
                    del self.config[key]
                    print(f"Deleted '{key}'")
                else:
                    print(f"Key '{key}' not found!")
            
            elif choice == "4":
                if self.save_config():
                    print("Configuration saved successfully!")
                else:
                    print("Failed to save configuration!")
            
            elif choice == "5":
                self.load_config()
                print("Configuration reloaded from file!")
            
            elif choice == "6":
                confirm = input("Reset to defaults? (y/n): ")
                if confirm.lower() == 'y':
                    self.create_default_config()
                    print("Configuration reset to defaults!")
            
            elif choice == "7":
                save = input("Save changes before exit? (y/n): ")
                if save.lower() == 'y':
                    self.save_config()
                print("Goodbye!")
                break
            
            else:
                print("Invalid choice!")

# Example usage
config = ConfigManager("app_config.txt")
config.display_config()

# Use configuration in your app
app_name = config.get('app_name', 'Default App')
debug_mode = config.get('debug_mode', False)
max_users = config.get('max_users', 50)

print(f"\nStarting {app_name}...")
print(f"Debug mode: {debug_mode}")
print(f"Max users: {max_users}")

# Interactive configuration
config.interactive_editor()
```

---

## 8. Best Practices

### 1. Always Use Context Managers

```python
# Wrong - can leak file handles
file = open("data.txt", "r")
content = file.read()
# If an error occurs here, file.close() never gets called!
file.close()

# Correct - automatically closes file
with open("data.txt", "r") as file:
    content = file.read()
# File is always closed, even if an error occurs
```

### 2. Handle Encoding Issues

```python
# Better to specify encoding explicitly
with open("text.txt", "r", encoding="utf-8") as file:
    content = file.read()

# When working with different languages or special characters
with open("unicode_text.txt", "w", encoding="utf-8") as file:
    file.write("Hello 世界 🌍")
```

### 3. Use Appropriate File Modes

```python
# Reading existing files
with open("data.txt", "r") as file:  # Fails if file doesn't exist

# Writing new files (overwrites existing!)
with open("output.txt", "w") as file:  # Creates new or overwrites

# Appending to existing files
with open("log.txt", "a") as file:  # Creates new or appends

# Creating new files only
with open("new_file.txt", "x") as file:  # Fails if file exists
```

### 4. Process Large Files Efficiently

```python
# Wrong - loads entire file into memory
with open("huge_file.txt", "r") as file:
    content = file.read()  # Could use GB of RAM!

# Better - process line by line
with open("huge_file.txt", "r") as file:
    for line in file:
        process_line(line)  # Uses minimal memory
```

### 5. Validate Data When Reading

```python
def read_grades_safely(filename):
    """Read student grades with validation"""
    grades = {}
    
    with open(filename, "r") as file:
        for line_number, line in enumerate(file, 1):
            line = line.strip()
            
            if line and not line.startswith('#'):
                try:
                    name, grade_str = line.split(',')
                    grade = float(grade_str.strip())
                    
                    # Validate grade range
                    if 0 <= grade <= 100:
                        grades[name.strip()] = grade
                    else:
                        print(f"Warning: Invalid grade {grade} on line {line_number}")
                        
                except ValueError as e:
                    print(f"Error on line {line_number}: {e}")
                except Exception as e:
                    print(f"Unexpected error on line {line_number}: {e}")
    
    return grades
```

---

## 9. Common Mistakes to Avoid

### Mistake 1: Forgetting to Close Files

```python
# Wrong - file handle leaks
def bad_file_reading():
    file = open("data.txt", "r")
    content = file.read()
    # Forgot file.close()!
    return content

# Correct - always use 'with'
def good_file_reading():
    with open("data.txt", "r") as file:
        content = file.read()
    return content
```

### Mistake 2: Overwriting Important Files

```python
# Dangerous - immediately overwrites file!
with open("important_data.txt", "w") as file:
    file.write("This replaces everything!")

# Better - create backup first
def safe_write(filename, content):
    # Create backup
    backup_name = f"{filename}.backup"
    try:
        with open(filename, "r") as src:
            with open(backup_name, "w") as dst:
                dst.write(src.read())
    except FileNotFoundError:
        pass  # Original file doesn't exist
    
    # Write new content
    with open(filename, "w") as file:
        file.write(content)
```

### Mistake 3: Not Handling Missing Files

```python
# Wrong - crashes if file doesn't exist
with open("config.txt", "r") as file:
    config = file.read()

# Better - handle gracefully
try:
    with open("config.txt", "r") as file:
        config = file.read()
except FileNotFoundError:
    print("Config file not found. Using defaults.")
    config = "default configuration"
```

### Mistake 4: Incorrect Path Handling

```python
# Wrong - only works on specific operating systems
file_path = "data\\files\\input.txt"  # Windows only!

# Better - use os.path.join()
import os
file_path = os.path.join("data", "files", "input.txt")  # Works everywhere!
```

---

## 10. Practice Exercises

### Exercise 1: Personal Diary
Create a personal diary application:

```python
# Your code here
import datetime

def create_diary_app():
    """Create a personal diary application"""
    
    def add_entry():
        """Add a new diary entry"""
        # Get today's date
        # Ask user for diary entry
        # Save to file with date
        pass
    
    def view_entries():
        """View all diary entries"""
        # Read all entries from file
        # Display with dates
        pass
    
    def search_entries(keyword):
        """Search entries containing a keyword"""
        # Search through all entries
        # Return matching entries with dates
        pass
    
    def diary_stats():
        """Show diary statistics"""
        # Count total entries
        # Show date range
        # Count words written
        pass

# Test your diary app
create_diary_app()

# Expected features:
# - Add dated entries to diary.txt
# - View all entries chronologically
# - Search for specific words/phrases
# - Show statistics about diary usage
```

### Exercise 2: Grade Book Manager
Create a grade book for teachers:

```python
# Your code here

def create_gradebook():
    """Create a digital gradebook for teachers"""
    
    def add_student(name, student_id):
        """Add a new student to the gradebook"""
        pass
    
    def add_grade(student_id, assignment, grade):
        """Add a grade for a student"""
        pass
    
    def calculate_averages():
        """Calculate averages for all students"""
        pass
    
    def generate_report():
        """Generate a grade report"""
        pass
    
    def export_grades(filename):
        """Export grades to CSV file"""
        pass

# Test your gradebook
create_gradebook()

# Expected features:
# - Store student info and grades in files
# - Calculate individual and class averages
# - Generate formatted reports
# - Import/export CSV data
# - Handle multiple assignments
```

### Exercise 3: Expense Tracker
Create a personal expense tracking system:

```python
# Your code here
import datetime

def create_expense_tracker():
    """Create personal expense tracker"""
    
    def add_expense(amount, category, description):
        """Add a new expense"""
        pass
    
    def view_expenses(start_date=None, end_date=None):
        """View expenses in date range"""
        pass
    
    def expenses_by_category():
        """Show expenses grouped by category"""
        pass
    
    def monthly_summary(year, month):
        """Show summary for specific month"""
        pass
    
    def budget_tracker(monthly_budget):
        """Track spending against budget"""
        pass

# Test your expense tracker
create_expense_tracker()

# Expected features:
# - Record expenses with date, amount, category
# - View expenses by date range or category
# - Calculate monthly/yearly totals
# - Budget tracking and warnings
# - Export data for analysis
```

### Exercise 4: Simple File Backup System
Create a file backup and synchronization tool:

```python
# Your code here
import os
import datetime

def create_backup_system():
    """Create file backup system"""
    
    def backup_file(source, destination):
        """Backup a single file"""
        pass
    
    def backup_directory(source_dir, backup_dir):
        """Backup entire directory"""
        pass
    
    def compare_files(file1, file2):
        """Compare two files for differences"""
        pass
    
    def restore_backup(backup_file, restore_location):
        """Restore from backup"""
        pass
    
    def cleanup_old_backups(backup_dir, days_to_keep):
        """Remove old backup files"""
        pass

# Test your backup system
create_backup_system()

# Expected features:
# - Create timestamped backups
# - Compare files to detect changes
# - Restore files from backups
# - Automatic cleanup of old backups
# - Progress reporting for large operations
```

### Exercise 5: Log File Monitor
Create a tool to monitor and analyze log files:

```python
# Your code here
import time
import re

def create_log_monitor():
    """Create real-time log file monitor"""
    
    def watch_log_file(filename):
        """Watch log file for new entries"""
        pass
    
    def alert_on_pattern(pattern, action):
        """Alert when specific pattern is found"""
        pass
    
    def count_error_frequency():
        """Count how often errors occur"""
        pass
    
    def generate_daily_report():
        """Generate daily log summary"""
        pass
    
    def archive_old_logs(max_age_days):
        """Archive logs older than specified days"""
        pass

# Test your log monitor
create_log_monitor()

# Expected features:
# - Real-time log file monitoring
# - Pattern-based alerts
# - Error frequency analysis
# - Automated reporting
# - Log rotation and archiving
```

### Exercise 6: Text Processing Toolkit
Create a comprehensive text processing tool:

```python
# Your code here

def create_text_processor():
    """Create comprehensive text processing toolkit"""
    
    def word_frequency_analysis(filename):
        """Analyze word frequency in text file"""
        pass
    
    def find_and_replace(filename, find_text, replace_text):
        """Find and replace text in file"""
        pass
    
    def merge_text_files(file_list, output_file):
        """Merge multiple text files"""
        pass
    
    def extract_emails(filename):
        """Extract email addresses from text"""
        pass
    
    def text_statistics(filename):
        """Calculate comprehensive text statistics"""
        pass

# Test your text processor
create_text_processor()

# Expected features:
# - Word frequency analysis with charts
# - Find and replace with backup
# - File merging with formatting
# - Pattern extraction (emails, phones, etc.)
# - Detailed text statistics
```

---

## Solutions (Try the exercises first!)

<details>
<summary>Click to see Exercise 1 Solution</summary>

```python
# Exercise 1: Personal Diary Solution
import datetime
import os

def create_diary_app():
    diary_file = "personal_diary.txt"
    
    def add_entry():
        today = datetime.date.today().strftime("%Y-%m-%d")
        entry = input("What's on your mind today? ")
        
        with open(diary_file, "a") as file:
            file.write(f"\n[{today}]\n{entry}\n")
        
        print("Diary entry added!")
    
    def view_entries():
        try:
            with open(diary_file, "r") as file:
                content = file.read()
                print("\n=== Your Diary Entries ===")
                print(content)
        except FileNotFoundError:
            print("No diary entries found!")
    
    def search_entries(keyword):
        try:
            with open(diary_file, "r") as file:
                lines = file.readlines()
                
                found_entries = []
                current_date = ""
                current_entry = ""
                
                for line in lines:
                    if line.startswith("[") and line.endswith("]\n"):
                        if current_entry and keyword.lower() in current_entry.lower():
                            found_entries.append((current_date, current_entry))
                        current_date = line.strip()
                        current_entry = ""
                    else:
                        current_entry += line
                
                # Check last entry
                if current_entry and keyword.lower() in current_entry.lower():
                    found_entries.append((current_date, current_entry))
                
                if found_entries:
                    print(f"\nFound {len(found_entries)} entries containing '{keyword}':")
                    for date, entry in found_entries:
                        print(f"{date}\n{entry}")
                else:
                    print(f"No entries found containing '{keyword}'")
        
        except FileNotFoundError:
            print("No diary entries found!")
    
    def diary_stats():
        try:
            with open(diary_file, "r") as file:
                content = file.read()
                
                entry_count = content.count("[")
                word_count = len(content.split())
                
                print(f"\n=== Diary Statistics ===")
                print(f"Total entries: {entry_count}")
                print(f"Total words: {word_count}")
                print(f"Average words per entry: {word_count//entry_count if entry_count > 0 else 0}")
        
        except FileNotFoundError:
            print("No diary entries found!")
    
    # Main menu loop
    while True:
        print("\n=== Personal Diary ===")
        print("1. Add Entry")
        print("2. View All Entries")
        print("3. Search Entries")
        print("4. Diary Statistics")
        print("5. Exit")
        
        choice = input("Choose an option (1-5): ")
        
        if choice == "1":
            add_entry()
        elif choice == "2":
            view_entries()
        elif choice == "3":
            keyword = input("Enter search keyword: ")
            search_entries(keyword)
        elif choice == "4":
            diary_stats()
        elif choice == "5":
            print("Happy writing!")
            break
        else:
            print("Invalid choice!")

create_diary_app()
```
</details>

---

## Summary

In this comprehensive guide, you learned about Python file handling:

- ✅ **File operations** including opening, reading, writing, and closing files
- ✅ **File modes** for different types of file access and manipulation
- ✅ **Error handling** to gracefully manage file-related errors
- ✅ **CSV file processing** for structured data storage and retrieval
- ✅ **Path management** using os module for cross-platform compatibility
- ✅ **Real-world applications** including databases, log analyzers, and config managers
- ✅ **Best practices** for safe and efficient file operations
- ✅ **Common mistakes** and how to avoid them

### Key Takeaways:
- **Always use `with` statements** to ensure files are properly closed
- **Handle errors gracefully** to prevent crashes from missing or corrupted files
- **Validate data** when reading from files to ensure program stability
- **Use appropriate file modes** for your specific needs
- **Consider encoding** when working with text files, especially international content
- **Process large files efficiently** by reading line-by-line instead of loading everything into memory

### Next Steps:
- Practice with the exercises to build real-world file handling skills
- Explore more advanced file formats like JSON and XML
- Learn about binary file handling for images and other media
- Experiment with file compression and encryption
- Build larger applications that combine file handling with other concepts you've learned

**Next:** Continue to learn about Exception Handling to make your programs more robust and user-friendly!