#include <iostream>
#include <vector>
using namespace std;

// Student class
class Student {
public:
    string name;
    string indexNumber;
    string programme;

    void input() {
        cout << "Enter student name: ";
        getline(cin, name);

        cout << "Enter index number: ";
        getline(cin, indexNumber);

        cout << "Enter programme: ";
        getline(cin, programme);
    }

    void display(int number) {
        cout << number << ". "
             << "Name: " << name
             << ", Index: " << indexNumber
             << ", Programme: " << programme << endl;
    }
};

// Function prototypes
void addStudent(vector<Student>& students);
void viewStudents(const vector<Student>& students);
void showMenu();

int main() {
    vector<Student> students;
    int choice;

    do {
        showMenu();
        cout << "Enter choice: ";
        cin >> choice;
        cin.ignore(); // clear input buffer

        switch (choice) {
            case 1:
                addStudent(students);
                break;
            case 2:
                viewStudents(students);
                break;
            case 0:
                cout << "Exiting program..." << endl;
                break;
            default:
                cout << "Invalid choice. Try again." << endl;
        }
    } while (choice != 0);

    return 0;
}

void showMenu() {
    cout << "\n===== DIGITAL ATTENDANCE SYSTEM =====\n";
    cout << "1. Register Student\n";
    cout << "2. View All Students\n";
    cout << "0. Exit\n";
}

void addStudent(vector<Student>& students) {
    Student s;
    cin.ignore();
    s.input();
    students.push_back(s);
    cout << "Student registered successfully.\n";
}

void viewStudents(const vector<Student>& students) {
    if (students.empty()) {
        cout << "No students registered yet.\n";
        return;
    }

    cout << "\n--- Registered Students ---\n";
    for (size_t i = 0; i < students.size(); i++) {
        students[i].display(i + 1);
    }
}
