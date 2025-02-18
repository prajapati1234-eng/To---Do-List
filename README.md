import os

class TodoList:
    def __init__(self):
        self.tasks = []

    def add_task(self, task):
        self.tasks.append({"task": task, "done": False})
        print(f"Task '{task}' added successfully!")

    def remove_task(self, task_index):
        try:
            task = self.tasks.pop(task_index)
            print(f"Task '{task['task']}' removed successfully!")
        except IndexError:
            print("Invalid task index. Please try again.")

    def mark_task_done(self, task_index):
        try:
            self.tasks[task_index]['done'] = True
            print(f"Task '{self.tasks[task_index]['task']}' marked as done.")
        except IndexError:
            print("Invalid task index. Please try again.")

    def display_tasks(self):
        if not self.tasks:
            print("No tasks in the list.")
        else:
            for i, task in enumerate(self.tasks):
                status = "Done" if task["done"] else "Not done"
                print(f"{i}. {task['task']} - {status}")

# Function to interact with the user
def main():
    todo_list = TodoList()

    while True:
        os.system('cls' if os.name == 'nt' else 'clear')  # Clear the console screen for better UI

        print("=== To-Do List ===")
        todo_list.display_tasks()
        print("\nOptions:")
        print("1. Add Task")
        print("2. Remove Task")
        print("3. Mark Task as Done")
        print("4. Exit")
        
        choice = input("Enter your choice: ")
        
        if choice == "1":
            task = input("Enter the task: ")
            todo_list.add_task(task)
        elif choice == "2":
            task_index = int(input("Enter task index to remove: "))
            todo_list.remove_task(task_index)
        elif choice == "3":
            task_index = int(input("Enter task index to mark as done: "))
            todo_list.mark_task_done(task_index)
        elif choice == "4":
            print("Exiting To-Do List. Goodbye!")
            break
        else:
            print("Invalid choice. Please try again.")
        input("\nPress Enter to continue...")

if __name__ == "__main__":
    main()
