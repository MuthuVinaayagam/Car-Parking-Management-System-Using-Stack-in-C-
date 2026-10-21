# Car-Parking-Management-System-Using-Stack-in-C-
A Car Parking Management System implemented in C++ using a stack data structure. It allows users to park cars, remove the most recently parked car, and display parked cars. Demonstrates stack operations, push, pop, arrays, and Last In, First Out (LIFO) principles.

#include <iostream>
#include <limits>
using namespace std;

class Stack {
    int car[10];
    int top;

public:
    Stack() {
        top = -1;
    }

    bool push(int value) {
        if (top == 9) {
            cout << "Parking is full.\n";
            return false;
        }

        car[++top] = value;
        cout << "Car entered successfully.\n";
        return true;
    }

    bool pop(int &value) {
        if (top == -1) {
            cout << "Parking is empty.\n";
            return false;
        }

        value = car[top--];
        return true;
    }

    void display() {
        if (top == -1) {
            cout << "Parking is empty.\n";
            return;
        }

        cout << "Cars in parking (top to bottom): ";

        for (int i = top; i >= 0; i--) {
            cout << car[i] << " ";
        }

        cout << '\n';
    }
};

int main() {
    Stack s;
    int ch, num;

    do {
        cout << "\n=== Car Parking Management System ===\n";
        cout << "1. Car enters\n";
        cout << "2. Car leaves\n";
        cout << "3. Display cars\n";
        cout << "4. Exit\n";
        cout << "Enter your choice: ";

        if (!(cin >> ch)) {
            cout << "Invalid input. Enter a number.\n";
            cin.clear();
            cin.ignore(numeric_limits<streamsize>::max(), '\n');
            continue;
        }

        switch (ch) {
        case 1:
            cout << "Enter the car number: ";

            if (!(cin >> num)) {
                cout << "Invalid car number.\n";
                cin.clear();
                cin.ignore(numeric_limits<streamsize>::max(), '\n');
                break;
            }

            s.push(num);
            break;

        case 2:
            if (s.pop(num)) {
                cout << "The car leaving the parking: " << num << '\n';
            }
            break;

        case 3:
            s.display();
            break;

        case 4:
            cout << "Exiting Car Parking Management System.\n";
            break;

        default:
            cout << "Invalid choice. Select 1 to 4.\n";
        }

    } while (ch != 4);

    return 0;
}
