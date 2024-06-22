# ToDoApp
This project is a simple to-do list application built with Python's Tkinter library. It allows users to add, delete, and view tasks through a graphical user interface. The tasks are saved to a text file, ensuring they persist even after the application is closed and reopened

## Explanation:
```python
import tkinter as tk
from tkinter import messagebox
import os
```
1. **tkinter**: This module is used for creating the graphical user interface (GUI). tk is a common alias for tkinter.
2. **messagebox**: This is a submodule of tkinter used to show message boxes in the application (e.g., warnings).
3. **os**: This module provides functions for interacting with the operating system, such as checking if a file exists.
