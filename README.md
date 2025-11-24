# Student-grade-management
# Initialising dictionary
student_grade = {}

# Add a new student
def add_student(name, grade):
    
    student_grade[name] = grade 
    print(f"Added {name} with a grade of {grade}")

# Update a student
def update_student(name, grade):
    
    if name in student_grade:
        
        student_grade[name] = grade
        
        print(f"The grade for {name} has been updated to {grade}")
    else:
        print(f"{name} is not found!")

# Delete a student
def delete_student(name):
    
    if name in student_grade:
        del student_grade[name]
        print(f"{name} has been successfully deleted")
    else:
        print(f"{name} is not found!")

# View all students
def display_all_students():
    if student_grade:
        print("\n--- Current Student Grades ---")
        for name, grade in student_grade.items():
            print(f"{name}: {grade}")
        print("------------------------------")
    else:
        print("No students found/added.")

def main():
    while True:
        print('\n--- Student Grade Management System ---')
        print("1. Add Student")
        print("2. Update Student Grade")
        print("3. Delete Student")
        print("4. View All Students")
        print("5. Exit")

        try:
            choice = input("Enter your choice (1-5): ")
            if not choice.isdigit():
                raise ValueError
            choice = int(choice)
        except ValueError:
            print("Invalid input. Please enter a number from 1 to 5.")
            continue

        if choice == 1:
            name = input("Enter student name: ")
            
            try:
                grade = int(input("Enter student grade: "))
                add_student(name, grade)
            except ValueError:
                print("Invalid grade. Please enter a whole number.")
        
        elif choice == 2:
            name = input("Enter student name to update: ")
            try:
                grade = int(input("Enter new student grade: "))
                update_student(name, grade)
            except ValueError:
                print("Invalid grade. Please enter a whole number.")

        elif choice == 3:
            name = input("Enter student name to delete: ")
            delete_student(name)

        elif choice == 4:
            display_all_students()

        elif choice == 5:
            print("Closing the program...")
            break

        else:
            print("Invalid choice. Please enter a number between 1 and 5.")

if __name__ == "__main__":
    main()
