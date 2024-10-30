1.Create the Project Directory (if you haven't already):
**mkdir todo_list_manager
cd todo_list_manager**

2.Create the Python Script:
**touch todo.py
chmod +x todo.py  # Make it executable**

3.Open the Script in a Text Editor:
You can use any text editor, but here we’ll use nano:

**nano todo.py**

4.writedown this code :

#!/usr/bin/env python3

import sys
import os

TODO_FILE = 'todo_list.txt'

def load_todos():
    """Load the to-do list from a file."""
    if not os.path.exists(TODO_FILE):
        return []
    with open(TODO_FILE, 'r') as f:
        return [line.strip() for line in f.readlines()]

def save_todos(todos):
    """Save the to-do list to a file."""
    with open(TODO_FILE, 'w') as f:
        for todo in todos:
            f.write(f"{todo}\n")

def add_task(task):
    """Add a new task to the to-do list."""
    todos = load_todos()
    todos.append(task)
    save_todos(todos)
    print(f"Added task: {task}")

def view_tasks():
    """View all tasks in the to-do list."""
    todos = load_todos()
    if not todos:
        print("No tasks found.")
    else:
        print("To-Do List:")
        for idx, task in enumerate(todos, start=1):
            print(f"{idx}. {task}")

def remove_task(index):
    """Remove a task from the to-do list by its index."""
    todos = load_todos()
    if 0 < index <= len(todos):
        removed_task = todos.pop(index - 1)
        save_todos(todos)
        print(f"Removed task: {removed_task}")
    else:
        print("Invalid task number.")

def main():
    """Main function to handle command line arguments."""
    if len(sys.argv) < 2:
        print("Usage: todo.py [add|view|remove] [task|task_number]")
        sys.exit(1)
    command = sys.argv[1]
    if command == 'add':
        if len(sys.argv) < 3:
            print("Please provide a task to add.")
            sys.exit(1)
        task = ' '.join(sys.argv[2:])
        add_task(task)
    elif command == 'view':
        view_tasks()
    elif command == 'remove':
        if len(sys.argv) < 3 or not sys.argv[2].isdigit():
            print("Please provide a valid task number to remove.")
            sys.exit(1)
        index = int(sys.argv[2])
        remove_task(index)
    else:
        print("Unknown command. Use 'add', 'view', or 'remove'.")

if __name__ == "__main__":
    main()



5. Save and Exit the text editor (in nano, you can do this by pressing CTRL + X, then Y, and then Enter).


6. Run the To-Do List Manager:
   To add a task:
 **./todo.py add "Buy groceries"**

7. To view tasks:
   **./todo.py view**

8. To remove a task (for example, the first task):
   **./todo.py remove 1**

  **Notes**

The tasks will be stored in a file named todo_list.txt in the same directory as your script.
Make sure you have Python 3 installed on your system. You can check this by running python3 --version.
If you encounter permission issues, ensure that the script has executable permissions (chmod +x todo.py).
Additional Features (Optional)

You can further enhance this project by adding features like:

Marking tasks as completed.
Adding due dates.
Using a database for storage (like SQLite).
Creating a user interface with libraries like curses or tkinter.
Feel free to modify and expand the code as you see fit. Happy coding!


Thank you


