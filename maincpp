#include <iostream>
#include <string>
using namespace std;

class Person {
protected:
    string name = "null";
public:
    void setName(string n) { name = n; }
    string getName() { return name; }
};

class Student : public Person {
    int id = 0, midterm = 0, final = 0;
    double average = 0;
    string letter = "null";
    void calculateLetter() {
        average = midterm * 0.4 + final * 0.6;
        if (average >= 90 && average <= 100) { letter = "A"; }
        else if (average >= 80 && average < 90) { letter = "B"; }
        else if (average >= 70 && average < 80) { letter = "C"; }
        else if (average >= 60 && average < 70) { letter = "D"; }
        else if (average < 60) { letter = "F"; }
    }
public:
    void setID(int i) { id = i; }
    void setMidterm(int m) { 
        midterm = m; 
        calculateLetter();
    }
    void setFinal(int f) { 
        final = f; 
        calculateLetter();
    }
    int getID() { return id; }
    int getMidterm() { return midterm; }
    int getFinal() { return final; }
    double getAverage() { return average; }
    string getLetter() { return letter; }
};

Student students[10];
int s = 0;

void AddStudent() {
    if (s >= 10) {
        cout << "\nClass capacity is full.\n";
        return;
    }
    string n;
    int id, m, f;
    cout << "\nPlease enter information.\n";
    cout << "Student name: ";
    cin >> n;
    cout << "Student id: ";
    cin >> id;

    for (int i = 0; i < s; i++) {
        if (students[i].getID() == id) {
            cout << "\nThis student already exists.\n";
            return;
        }
    }

    while (1) {
        cout << "Midterm score: ";
        cin >> m;
        if (0 <= m && m <= 100) { break; }
        else {
            cout << "\nYou entered an invalid score. Please enter between 0-100.\n";
        }
    }

    while (1) {
        cout << "Final score: ";
        cin >> f;
        if (0 <= f && f <= 100) { break; }
        else {
            cout << "\nYou entered an invalid score. Please enter between 0-100.\n";
        }
    }
    students[s].setName(n);
    students[s].setID(id);
    students[s].setMidterm(m);
    students[s].setFinal(f);
    cout << "\nStudent added successfully.\n";
    s++;
}

void ShowAllStudents() {
    if (s == 0) {
        cout << "\nThis class is empty, please add at least one student.\n";
        return;
    }

    for (int i = 0; i < s; i++) {
        cout << "\nStudent " << i + 1 << ":\n";
        cout << "Name: " << students[i].getName() << endl;
        cout << "ID: " << students[i].getID() << endl;
        cout << "Midterm score: " << students[i].getMidterm() << endl;
        cout << "Final score: " << students[i].getFinal() << endl;
        cout << "Average score: " << students[i].getAverage() << endl;
        cout << "Letter grade: " << students[i].getLetter() << endl << endl;
    }
}

void SearchStudent() {
    if (s == 0) {
        cout << "\nThis class is empty, please add at least one student.\n";
        return;
    }
    int se;
    cout << "\nEnter an ID to search: ";
    cin >> se;
    for (int i = 0; i < s; i++) {
        if (students[i].getID() == se) {
            cout << "\nStudent found successfully.\n";
            cout << "\nName: " << students[i].getName() << endl;
            cout << "ID: " << students[i].getID() << endl;
            cout << "Midterm score: " << students[i].getMidterm() << endl;
            cout << "Final score: " << students[i].getFinal() << endl;
            cout << "Average score: " << students[i].getAverage() << endl;
            cout << "Letter grade: " << students[i].getLetter() << endl << endl;
            return;
        }
    }
    cout << "\nID not found.\n";
}

void ShowClassStatistics() {
    if (s == 0) {
        cout << "\nThis class is empty, please add at least one student.\n";
        return;
    }
    double classTotal = 0;
    int failed = 0, passed = 0;
    Student highest = students[0];
    Student lowest = students[0];
    for (int i = 0; i < s; i++) {
        classTotal += students[i].getAverage();
        if (students[i].getAverage() > highest.getAverage()) {
            highest = students[i];
        }
        if (students[i].getAverage() < lowest.getAverage()) {
            lowest = students[i];
        }

        if (students[i].getLetter() != "F") {
            passed++;
        }
        else { failed++; }
    }
    double classAverage = classTotal / s;
    cout << "\nClass average: " << classAverage << endl;
    cout << "Highest - scoring student: " << highest.getName() << endl;
    cout << "Lowest - scoring student: " << lowest.getName() << endl;
    cout << "Number of passed students: " << passed << endl;
    cout << "Number of failed students: " << failed << endl;
}

int main() {
    int a;
    do {
        cout << "\n1. Add Student\n2. Show All Students\n3. Search Student\n4. Show Class Statistics\n5. Exit\n\nPlease select an option (1, 2, 3, 4 or 5): ";
        cin >> a;
        switch (a) {
        case 1:
            AddStudent();
            break;
        case 2:
            ShowAllStudents();
            break;
        case 3:
            SearchStudent();
            break;
        case 4:
            ShowClassStatistics();
            break;
        case 5:
            cout << "\nYou exited.\n";
            break;
        default:
            cout << "\nInvalid choice.\n";
        }
    } while (a!=5);
    return 0;
}
