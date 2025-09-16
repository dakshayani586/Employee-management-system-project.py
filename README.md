# Employee-management-system-project.py
class Employee:
    def __init__(self, emp_id, name, age, department):
        self.emp_id = emp_id
        self.name = name
        self.age = age
        self.department = department

    def __str__(self):
        return f"ID: {self.emp_id}, Name: {self.name}, Age: {self.age}, Department: {self.department}"


class EmployeeManagementSystem:
    def __init__(self):
        self.employees = []

    def add_employee(self):
        emp_id = input("Enter employee ID: ")
        if self.find_employee(emp_id):
            print("Employee with this ID already exists!")
            return
        name = input("Enter employee name: ")
        age = input("Enter employee age: ")
        department = input("Enter employee department: ")
        emp = Employee(emp_id, name, age, department)
        self.employees.append(emp)
        print("Employee added successfully.")

    def view_employees(self):
        if not self.employees:
            print("No employees found.")
            return
        print("\nList of Employees:")
        for emp in self.employees:
            print(emp)

    def find_employee(self, emp_id):
        for emp in self.employees:
            if emp.emp_id == emp_id:
                return emp
        return None

    def update_employee(self):
        emp_id = input("Enter employee ID to update: ")
        emp = self.find_employee(emp_id)
        if emp:
            emp.name = input(f"Enter new name ({emp.name}): ") or emp.name
            emp.age = input(f"Enter new age ({emp.age}): ") or emp.age
            emp.department = input(f"Enter new department ({emp.department}): ") or emp.department
            print("Employee updated successfully.")
        else:
            print("Employee not found.")

    def delete_employee(self):
        emp_id = input("Enter employee ID to delete: ")
        emp = self.find_employee(emp_id)
        if emp:
            self.employees.remove(emp)
            print("Employee deleted successfully.")
        else:
            print("Employee not found.")

    def run(self):
        while True:
            print("\nEmployee Management System")
            print("1. Add Employee")
            print("2. View Employees")
            print("3. Update Employee")
            print("4. Delete Employee")
            print("5. Exit")
            choice = input("Enter your choice: ")
            if choice == '1':
                self.add_employee()
            elif choice == '2':
                self.view_employees()
            elif choice == '3':
                self.update_employee()
            elif choice == '4':
                self.delete_employee()
            elif choice == '5':
                print("Exiting system. Goodbye!")
                break
            else:
                print("Invalid choice. Try again.")


if __name__ == "__main__":
    system = EmployeeManagementSystem()
    system.run()
