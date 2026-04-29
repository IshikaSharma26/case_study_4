import os

FILE_NAME = "tasks.txt"

# Ensure file exists
if not os.path.exists(FILE_NAME):
    open(FILE_NAME, "w").close()


# -------- Add Task --------
def add_task():
    task_id = input("Enter Task ID: ")
    desc = input("Enter Description: ")
    status = "Pending"

    with open(FILE_NAME, "a") as f:
        f.write(f"{task_id}|{desc}|{status}\n")

    print("Task added successfully!\n")


# -------- View Tasks --------
def view_tasks():
    with open(FILE_NAME, "r") as f:
        tasks = f.readlines()

    if not tasks:
        print("No tasks found.\n")
        return

    print("\n--- Task List ---")
    for t in tasks:
        tid, desc, status = t.strip().split("|")
        print(f"ID: {tid} | Task: {desc} | Status: {status}")
    print()


# -------- Update Task --------
def update_task():
    task_id = input("Enter Task ID to update: ")

    with open(FILE_NAME, "r") as f:
        tasks = f.readlines()

    found = False
    with open(FILE_NAME, "w") as f:
        for t in tasks:
            tid, desc, status = t.strip().split("|")

            if tid == task_id:
                found = True
                print("1. Update Description")
                print("2. Mark as Completed")
                choice = input("Enter choice: ")

                if choice == "1":
                    desc = input("Enter new description: ")
                elif choice == "2":
                    status = "Completed"

            f.write(f"{tid}|{desc}|{status}\n")

    if found:
        print("Task updated!\n")
    else:
        print("Task not found.\n")


# -------- Delete Task --------
def delete_task():
    task_id = input("Enter Task ID to delete: ")

    with open(FILE_NAME, "r") as f:
        tasks = f.readlines()

    found = False
    with open(FILE_NAME, "w") as f:
        for t in tasks:
            tid, desc, status = t.strip().split("|")

            if tid != task_id:
                f.write(t)
            else:
                found = True

    if found:
        print("Task deleted!\n")
    else:
        print("Task not found.\n")


# -------- Search Task --------
def search_task():
    keyword = input("Enter ID or keyword: ")

    with open(FILE_NAME, "r") as f:
        tasks = f.readlines()

    found = False
    for t in tasks:
        tid, desc, status = t.strip().split("|")

        if keyword in tid or keyword.lower() in desc.lower():
            print(f"ID: {tid} | Task: {desc} | Status: {status}")
            found = True

    if not found:
        print("No matching task found.\n")


# -------- Menu --------
def menu():
    while True:
        print("------ TO-DO MENU ------")
        print("1. Add Task")
        print("2. View Tasks")
        print("3. Update Task")
        print("4. Delete Task")
        print("5. Search Task")
        print("6. Exit")

        choice = input("Enter choice: ")

        if choice == "1":
            add_task()
        elif choice == "2":
            view_tasks()
        elif choice == "3":
            update_task()
        elif choice == "4":
            delete_task()
        elif choice == "5":
            search_task()
        elif choice == "6":
            print("Exiting...")
            break
        else:
            print("Invalid choice!\n")


# Run program
menu()
