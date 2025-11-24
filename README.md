# PyTask Scheduler

Project Title
PyTask Scheduler – A Simple Python-Based Task Management System

---

Overview of the Project
PyTask Scheduler is a beginner-friendly "command-line task manager" built using Python.  
It allows users to add tasks, view all tasks, mark them as completed, delete tasks, and sort tasks according to priority.  
The goal of this project is to understand basic Python concepts such as functions, lists, loops, conditional statements, and user interaction through a menu-driven interface.

---

 Features
- Add new tasks with title, priority, and due date  
- View all existing tasks  
- Mark tasks as completed  
- Delete tasks from the list  
- Sort tasks by priority (High → Medium → Low)  
- Simple and clean menu-based interface  
- Stores tasks temporarily in memory 

---

Technologies / Tools Used
- Python 3.x
- Terminal / Command Prompt
- Basic Python libraries (no external packages)

---

 Steps to Install & Run the Project




---

 Instructions for Testing

1. Run the program
2. From the menu, test each feature:
   - Press 1 → Add a few tasks  
   - Press 2 → View tasks  
   - Press 3 → Mark a task as completed  
   - Press 4 → Delete a task  
   - Press 5 → Sort tasks by priority  
   - Press 6 → Exit  
3. Enter both valid and invalid inputs to test error handling.
4. Try adding tasks with different priority levels (High, Medium, Low) to test sorting.
5. Check how the program displays completed vs pending tasks.

---
# Source Code
tasks = []   # each task will be a list: [title, priority, due_date, status]

# -----------------------------
# Add a new task
# -----------------------------
def add_task():
    print("\n--- Add New Task ---")
    title = input("Enter task title: ")
    priority = input("Enter priority (High/Medium/Low): ")
    due_date = input("Enter due date: ")   
    
    task = [title, priority, due_date, "Pending"]
    tasks.append(task)
    
    print("Task added successfully!\n")


# View all tasks
def view_tasks():
    if len(tasks) == 0:
        print("\nNo tasks available.\n")
        return

    print("\n--- All Tasks ---")
    for i in range(len(tasks)):
        print("\nTask", i+1)
        print("Title    :", tasks[i][0])
        print("Priority :", tasks[i][1])
        print("Due Date :", tasks[i][2])
        print("Status   :", tasks[i][3])
    print()

# -----------------------------
# Mark task as completed
# -
def mark_completed():
    view_tasks()
    if len(tasks) == 0:
        return
    
    t = int(input("Enter task number to mark completed: "))
    if 1 <= t <= len(tasks):
        tasks[t-1][3] = "Completed"
        print("Task marked as completed!\n")
    else:
        print("Invalid task number!\n")

# Delete a task
def delete_task():
    view_tasks()
    if len(tasks) == 0:
        return
    
    t = int(input("Enter task number to delete: "))
    if 1 <= t <= len(tasks):
        tasks.pop(t-1)
        print("Task deleted successfully!\n")
    else:
        print("Invalid task number!\n")

# Sort tasks by priorit
def sort_by_priority():
    high = []
    medium = []
    low = []

 # separate tasks into three lists
    for task in tasks:
        if task[1].lower() == "high":
            high.append(task)
        elif task[1].lower() == "medium":
            medium.append(task)
        else:
            low.append(task)
    
  # clear original list
   tasks.clear()

   # add in order: High → Medium → Low
   for t in high:
        tasks.append(t)
   for t in medium:
        tasks.append(t)
   for t in low:
        tasks.append(t)

    print("Tasks sorted by priority!\n")
# Main Program Menu
def main():
    while True:
        print("===== SIMPLE TASK SCHEDULER =====")
        print("1. Add Task")
        print("2. View Tasks")
        print("3. Mark Task as Completed")
        print("4. Delete Task")
        print("5. Sort by Priority")
        print("6. Exit")
        
        choice = input("Enter your choice: ")
        
        if choice == "1":
            add_task()
        elif choice == "2":
            view_tasks()
        elif choice == "3":
            mark_completed()
        elif choice == "4":
            delete_task()
        elif choice == "5":
            sort_by_priority()
        elif choice == "6":
            print("Goodbye!")
            break
        else:
            print("Invalid choice. Try again.\n")


main()














