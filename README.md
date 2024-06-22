# ToDoApp
This project is a simple to-do list application built with Python's Tkinter library. It allows users to add, delete, and view tasks through a graphical user interface. The tasks are saved to a text file, ensuring they persist even after the application is closed and reopened

## Explanation

### Importing Packages
```python
import tkinter as tk
from tkinter import messagebox
import os
```
1. **tkinter**: This module is used for creating the graphical user interface (GUI). tk is a common alias for tkinter.
2. **messagebox**: This is a submodule of tkinter used to show message boxes in the application (e.g., warnings).
3. **os**: This module provides functions for interacting with the operating system, such as checking if a file exists.

### Defining the ToDoApp Class
```python
class ToDoApp:
    def __init__(self, root):
        self.root = root
        self.root.title("To-Do List")

        self.tasks = []
        self.tasks_file = "tasks.txt"
        self.load_tasks()

        # UI setup
        self.frame = tk.Frame(root)
        self.frame.pack(pady=10)

        self.task_listbox = tk.Listbox(self.frame, width=50, height=10, bd=0, selectmode=tk.SINGLE)
        self.task_listbox.pack(side=tk.LEFT, fill=tk.BOTH)

        self.scrollbar = tk.Scrollbar(self.frame)
        self.scrollbar.pack(side=tk.RIGHT, fill=tk.BOTH)

        self.task_listbox.config(yscrollcommand=self.scrollbar.set)
        self.scrollbar.config(command=self.task_listbox.yview)

        self.task_entry = tk.Entry(root, width=50)
        self.task_entry.pack(pady=10)

        self.add_task_button = tk.Button(root, text="Add Task", command=self.add_task)
        self.add_task_button.pack(pady=5)

        self.delete_task_button = tk.Button(root, text="Delete Task", command=self.delete_task)
        self.delete_task_button.pack(pady=5)

        self.update_task_listbox()
```
* **Class ToDoApp**: This class encapsulates all the functionality for the to-do list application.
* **__init__ method**: This is the constructor method which is called when an instance of the class is created.
* **self.root**: Reference to the root window of the application.
* **self.root.title("To-Do List")**: Sets the title of the application window.
* **self.tasks**: A list to store the tasks.
* **self.tasks_file**: Name of the file where tasks will be saved.
* **self.load_tasks()**: Loads tasks from the file when the application starts.
* **UI setup**: Creates and packs various Tkinter widgets for the GUI.
* **self.frame**: A Frame widget to contain the listbox and scrollbar.
* **self.task_listbox**: A Listbox widget to display the tasks.
* **self.scrollbar**: A Scrollbar widget to scroll through the tasks in the listbox.
* **self.task_entry**: An Entry widget to input new tasks.
* **self.add_task_button*: A Button widget to add new tasks.
* **self.delete_task_button*: A Button widget to delete selected tasks.
* **self.update_task_listbox()*: Updates the listbox with current tasks.

### Adding a Task
```python
def add_task(self):
    task = self.task_entry.get()
    if task != "":
        self.tasks.append(task)
        self.update_task_listbox()
        self.task_entry.delete(0, tk.END)
        self.save_tasks()
    else:
        messagebox.showwarning("Warning", "You must enter a task.")
```
* 'add_task' **method**: Handles adding a new task.
* **'task = self.task_entry.get()': Retrieves the text from the entry widget.
* **'if task != "":'**: Checks if the input is not empty.
- **'self.tasks.append(task)'**: Adds the task to the list.
- **'self.update_task_listbox()'**: Updates the listbox to reflect the new task.
- **'self.task_entry.delete(0, tk.END)'**: Clears the entry widget.
- **'self.save_tasks()'**: Saves the tasks to the file.
* **'else': Shows a warning message if the input is empty.
