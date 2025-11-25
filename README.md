Simple Command-Line Task Manager (SCTM)
Overview of the Project

The Simple Command-Line Task Manager is a lightweight, Python-based productivity application designed for users who prefer a fast, distraction-free environment.
Its primary purpose is to allow users to quickly capture, track, and manage their daily tasks directly from the terminal. 
The project's core focus is on automation and data persistence, ensuring that the to-do list is automatically saved between program sessions, eliminating the need for manual file management.
Target User: Individuals comfortable with the command line who require a robust, local, and low-friction tool for personal task management.
Features

The SCTM provides the following core functionalities:
Data Persistence-Automatically saves the entire task list to a local JSON file (tasks.json) upon exit and loads it back on startup.
Add Tasks- Allows the user to input a new task description and append it to the master list.
View Tasks-Displays all tasks in a formatted list, showing the index number, description, and status ([PENDING] or [DONE]).
Complete Tasks-Allows the user to mark a specific task as finished by entering its corresponding index number.
Robust Handling-Implements error trapping to prevent application crashes from invalid inputs (e.g., non-numeric index) or corrupted save files.

Technologies/Tools Used
Primary Language: Python 3.x
Storage Mechanism: JSON (JavaScript Object Notation)

Key Python Modules:
json: Used for serialization (saving) and deserialization (loading) of the list data structure.
os: Used to check for the existence of the tasks.json file on startup.

Steps to Install & Run the Project
The project is highly portable and requires no external libraries.

A. Installation Steps

Prerequisite: Ensure you have Python 3.x installed on your system.

Download: Save the project code into a file named task_manager.py.

No Dependencies: No pip installations are required

B. Running the Project

Open Terminal: Open your command prompt, terminal, or PowerShell.

Navigate: Change the directory to the location where you saved task_manager.py.

Execute: Run the script using the Python interpreter command:
python task_manager.py
The interactive menu will appear, prompting you for a choice (v/a/c/e).

instructions for Testing
Testing should focus on verifying core functionality and robustness, as defined by the Functional (FR) and Non-Functional (NFR) Requirements.

A. Functional Testing (Core Operations)
Add Task 

Steps: Run the application, select the a option, and enter a new task description (e.g., "Test Item 1").

Expected Result: The task is successfully added, and a confirmation message is displayed.

Verification: Select v (View) to confirm "Test Item 1" appears in the list with the status [PENDING].

Complete Task 

Steps: Ensure a task exists (e.g., "Test Item 2"). Select the c option, and enter the index number corresponding to the task (e.g., 2).

Expected Result: The task's status is successfully updated to [DONE].

Verification: Select v (View) to confirm the status change in the displayed list.

Data Persistence 

Steps: Add a new task, then select e to Exit and Save. Immediately rerun the application using the python task_manager.py command.

Expected Result: All tasks added in the previous session must be present in the list upon the second launch.

Verification: Select v immediately after relaunching the application to confirm the list integrity.

B. Robustness Testing (Error Handling)
1. Invalid Index Input (NFR-002)

Steps: Select the c (Complete Task) option and enter non-numeric text (e.g., "hello") when prompted for the task index.

Expected Result: The program catches the ValueError and prints an informative error message (e.g., "Invalid input. Please enter a valid number...").

Verification: The application must not crash and should return gracefully to the main menu.

2. Out-of-Bounds Index

Steps: If the current list contains 2 tasks, select c and enter an index far outside the valid range (e.g., 99).

Expected Result: The program prints an "Index out of range." error message.

Verification: The application must not crash and should return to the main menu; the status of existing tasks must remain unchanged.

3. Missing Data File

Steps: Manually delete the tasks.json file from the project directory. Rerun the application.

Expected Result: The program initializes with an empty task list ([]) without generating a critical FileNotFoundError crash.

Verification: The application starts normally and displays the empty list message.

