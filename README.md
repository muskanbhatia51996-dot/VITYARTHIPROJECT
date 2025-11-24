# VITYARTHIPROJECT
#VITYARTHI flipped course project based on solving challenges faced while organising and planning, this simple command line task manager helps them in keeping track of their day to day tasks and enhances productivity. 
import json
import os

# Define the file path for task persistence
TASK_FILE = 'tasks.json'

def load_tasks():
    """
    Loads tasks from the local JSON file.
    Uses the 'json' and 'os' modules for persistence (a key concept).
    """
    if not os.path.exists(TASK_FILE):
        return []
    try:
        with open(TASK_FILE, 'r') as f:
            # Load the list of task dictionaries from the file
            tasks = json.load(f)
            print(f"Loaded {len(tasks)} tasks from {TASK_FILE}.")
            return tasks
    except (json.JSONDecodeError, FileNotFoundError):
        # Handle cases where the file is empty or corrupted
        print("Warning: Could not load tasks file. Starting with an empty list.")
        return []

def save_tasks(tasks):
    """
    Saves the current list of tasks to the local JSON file.
    """
    try:
        with open(TASK_FILE, 'w') as f:
            # UPDATE the list of task dictionaries to the file
            json.dump(tasks, f, indent=4)
        print(f"\nSuccessfully saved {len(tasks)} tasks to {TASK_FILE}.")
    except IOError as e:
        print(f"Error saving tasks: {e}")

def view_tasks(tasks):
    """
    Displays the current list of tasks with their status.
    """
    if not tasks:
        print("\n--- Task List is Empty ---\n")
        return

    print("\n==================================")
    print("      YOUR CURRENT TASK LIST      ")
    print("==================================")
    for i, task in enumerate(tasks):
        # Determine the status string and color for display
        status = "[DONE]" if task['done'] else "[PENDING]"
        
        # Format output clearly with index, status, and description
        print(f"{i + 1}. {status:<10} - {task['description']}")
    print("==================================\n")

def add_task(tasks, description):
    """
    Adds a new task to the list.
    Tasks are stored as dictionaries: {'description': str, 'done': bool}
    """
    new_task = {
        'description': description.strip(),
        'done': False
    }
    tasks.append(new_task)
    print(f"\nAdded task: '{new_task['description']}'")

def complete_task(tasks, index):
    """
    Marks a task as complete using its 1-based index (user input).
    Handles index bounds checking and type validation.
    """
    try:
        # Convert users 1-based index to 0-based list index
        task_index = int(index) - 1

        if 0 <= task_index < len(tasks):
            if tasks[task_index]['done']:
                print(f"Task {task_index + 1} is already marked as DONE.")
            else:
                tasks[task_index]['done'] = True
                print(f"\nTask {task_index + 1}: '{tasks[task_index]['description']}' marked as DONE!")
        else:
            print(f"Error: Task index {index} is out of range.")
    except ValueError:
        print("Error: Invalid input. Please enter a valid number for the task index.")


def main():
    """
    The main function that handles the program's execution flow and user interface.
    This demonstrates Top-Down Design by orchestrating calls to the smaller functions.
    """
    # 1. Implementation (Load)
    tasks = load_tasks()
    running = True

    while running:
        # Display the menu
        print("\n--- Task Manager Menu ---")
        print(" [v] View Tasks")
        print(" [a] Add New Task")
        print(" [c] Complete Task")
        print(" [e] Exit and Save")
        print("-------------------------")

        choice = input("Enter your choice (v/a/c/e): ").lower()

        if choice == 'v':
            # View Tasks
            view_tasks(tasks)

        elif choice == 'a':
            # Add Task
            description = input("Enter the new task description: ")
            if description:
                add_task(tasks, description)
            else:
                print("Task description cannot be empty.")

        elif choice == 'c':
            # Complete Task
            if not tasks:
                print("No tasks to complete. Add a task first.")
                continue
            
            view_tasks(tasks) # Show list before asking for index
            index = input("Enter the number of the task to mark as complete: ")
            complete_task(tasks, index)

        elif choice == 'e':
            # Exit and Save
            running = False
            # 2. Implementation (Save before exit)
            save_tasks(tasks)

        else:
            print("Invalid choice. Please try again.")
            
    print("\nTask Manager closed. Have a productive day!")

# Standard Python execution block
if __name__ == "__main__":
    main()
