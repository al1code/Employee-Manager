// Ali Kemal Dilek
// 1306230043
// 13.01.2024
// Assignment #1

#include <iostream>
#include <string>
using namespace std;

struct employeeManager {

  int id = 0;
  string name;
  string surname;
  string departmentName;
  double salary = 0;

} emp1, emp2, emp3, emp4, emp5, emp6, emp7, emp8, emp9, emp10;

void menu();
bool checkID(employeeManager employees[], int id);
void addnewEmployee(employeeManager employees[], int a);
void showEmplpyeebyID(employeeManager employees[], int id);
void showAllEmployees(employeeManager employees[]);
void updateEmployeeByID(employeeManager employees[], int id);
void deleteEmployeeByID(employeeManager employees[], int id);
void deleteAllEmployees(employeeManager employees[]);
double maximumSalaryy(employeeManager employees[]);
double minimumSalaryy(employeeManager employees[]);
double averageSalaryy(employeeManager employees[]);
void exit();

int main() {

  employeeManager employees[10] = {emp1, emp2, emp3, emp4, emp5,
                                   emp6, emp7, emp8, emp9, emp10};

  int userchoice;

  int id, employeeNumber;

  do {
    menu();

    cout << "Please enter a number from the menu : ";
    cin >> userchoice;
    cout << endl << "xxxxxxxxxxxxxxxxxxxxxxxxx" << endl << endl;

    if (userchoice >= 1 && userchoice <= 10) {
      switch (userchoice) {
      case 1:
        cout << "Which employee do you want to add (1-10) ? : ";
        cin >> employeeNumber;
        if (employeeNumber <= 10 && employeeNumber >= 1) {
          employeeNumber -= 1;
          addnewEmployee(employees, employeeNumber);
        } else {
          cout << "Please enter a number between 1-10" << endl;
        }
        break;

      case 2:

        cout << "Please enter the ID of the employee you want to display :  ";
        cin >> id;
        cout << endl;
        if (checkID(employees, id)) {
          showEmplpyeebyID(employees, id);
          break;
        } else {
          cout << "Please enter a valid ID" << endl;
        }
        break;

      case 3:
        showAllEmployees(employees);
        break;

      case 4:
        cout << "Which employee do you want to update ?" << endl;
        cin >> id;
        if (checkID(employees, id)) {
          updateEmployeeByID(employees, id);
          break;
        } else {
          cout << "Please enter a valid ID" << endl;
        }
        break;

      case 5:
        int id;
        cout << "Please enter the ID of the employee you want to delete :";
        cin >> id;
        if (checkID(employees, id)) {
          deleteEmployeeByID(employees, id);
          break;
        } else {
          cout << "Please enter a valid ID" << endl;
        }
        break;

      case 6:
        deleteAllEmployees(employees);
        break;

      case 7:
        cout << maximumSalaryy(employees) << endl;
        break;

      case 8:
        cout << minimumSalaryy(employees) << endl;
        break;

      case 9:
        cout << "The average salary of employees is : "
             << averageSalaryy(employees) << endl;
        break;

      case 10:
        exit();
        break;

      default:
        cout << "Please enter valid number !" << endl;
      }
    } else {
      cout << "The number that you have chosen is not in the menu ! Please "
              "enter valid number !"
           << endl;
    }
  } while (userchoice != 10);
}

void menu() {

  cout << "************MENU************" << endl;
  cout << "1. Add new employee: " << endl;
  cout << "2. Display employee by ID: " << endl;
  cout << "3. Display all employees: " << endl;
  cout << "4. Update an employee by ID: " << endl;
  cout << "5. Delete an employee by ID: " << endl;
  cout << "6. Delete all employees: " << endl;
  cout << "7. Display the employee with the highest salary:  " << endl;
  cout << "8. Display the employee with the lowest salary: " << endl;
  cout << "9. Display the average salary: " << endl;
  cout << "10.EXIT" << endl;

} // This program assigns the data of employees to the array .

// This program checks the IDs of the employees , so if user entered wrong ID
// system will warn him/her .
bool checkID(employeeManager employees[], int id) {
  bool isIdhere = false;
  for (int i = 0; i < id; i++) {
    if (employees[i].id == id) {
      isIdhere = true;
      cout << "ID has been found !" << endl;
      return isIdhere;
      break;
    }
  }
  return isIdhere;
}

void addnewEmployee(employeeManager employees[], int a) {

  cout << "Please enter the ID of the new employee  : ";
  cin >> employees[a].id;

  cout << "Please enter the name of the new employee  : ";
  cin.ignore();
  getline(cin, employees[a].name);

  cout << "Please enter the surname of the new employee  : ";
  cin.ignore();
  getline(cin, employees[a].surname);

  cout << "Please enter the department name of the new employee :";
  cin.ignore();
  getline(cin, employees[a].departmentName);

  cout << "Please enter the salary of the new employee : ";
  cin >> employees[a].salary;
}

// This program is wandering in array and display the employee with the ID that
// user entered .
void showEmplpyeebyID(employeeManager employees[], int id) {
  cout << "*************** Welcome to the employee displaying system "
          "***************";

  for (int i = 0; i < 10; i++) {
    if (employees[i].id == id) {

      cout << "Informations of " << i + 1 << ".Employee :" << endl;
      cout << "The employee ID : " << employees[i].id << endl;
      cout << "The employee name : " << employees[i].name << endl;
      cout << "The employee surname : " << employees[i].surname << endl;
      cout << "The employee department name : " << employees[i].departmentName
           << endl;
      cout << "The employee salary : " << employees[i].salary << endl;
      cout << endl << endl;
      break;
    }
    cout << endl;
  }
}

// This program is wandering in array and display all employees .
void showAllEmployees(employeeManager employees[]) {
  cout << "*************** HERE ALL EMPLOYEES ***************" << endl << endl;

  for (int j = 0; j < 10; j++) {
    cout << " Informations of " << j + 1 << ".Employee :" << endl;
    cout << "The employee ID : " << employees[j].id << endl;
    cout << "The employee name : " << employees[j].name << endl;
    cout << "The employee surname : " << employees[j].surname << endl;
    cout << "The employee department name : " << employees[j].departmentName
         << endl;
    cout << "The employee salary : " << employees[j].salary << endl;
  }
}

// This program is wandering in array and update the employee with the ID that
// user entered by rewriting the data .
void updateEmployeeByID(employeeManager employees[], int id) {
  cout << "*************** Welcome to the employee updating system "
          "***************"
       << endl
       << endl;

  for (int i = 0; i < 10; i++) {
    if (employees[i].id == id) {
      cout << "Please enter the new ID of the employee  : ";
      cin >> employees[i].id;
      cout << "Please enter the new name of the employee  : ";
      cin.ignore();
      getline(cin, employees[i].name);
      cout << "Please enter the new surname of the employee  : ";
      getline(cin, employees[i].surname);
      cout << "Please enter the new department name of the employee :";
      getline(cin, employees[i].departmentName);
      cout << "Please enter the new salary of the employee : ";
      cin >> employees[i].salary;
      break;
    }
  }
}

// This program assigns the data of employees of their inital values which means
// 0 or empty according to their ID .
void deleteEmployeeByID(employeeManager employees[], int id) {

  for (int i = 0; i < 10; ++i) {
    if (employees[i].id == id) {
      employees[i].id = 0;
      employees[i].name = "";
      employees[i].surname = "";
      employees[i].departmentName = "";
      employees[i].salary = 0;

      cout << "Employee with ID " << id << " has been deleted." << endl;
      break;
    }
  }
}

// This program assigns the data of employees of their inital values which means
// 0 or empty .
void deleteAllEmployees(employeeManager employees[]) {
  for (int i = 0; i < 10; ++i) {
    employees[i].id = 0;
    employees[i].name = "";
    employees[i].surname = "";
    employees[i].departmentName = "";
    employees[i].salary = 0;
  }
  cout << "All employees have been deleted." << endl
       << endl
       << "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx" << endl;
}

// This program is wandering in array and making some comparing controls then
// displays who has the maximum salary .
double maximumSalaryy(employeeManager employees[]) {
  double maximumsalary = employees[0].salary;
  int a = 0;
  for (int i = 0; i < 10; i++) {
    if (employees[i].salary > maximumsalary) {
      maximumsalary = employees[i].salary;
      a = i;
    }
  }
  cout << endl << endl;
  cout << "Name-Surname/Salary informations of the Employee with the maximum "
          "salary : "
       << employees[a].name << " - " << employees[a].surname << " / " << endl;
  return maximumsalary;
}

// This program is wandering in array and making some comparing controls then
// displays who has the minimum salary .
double minimumSalaryy(employeeManager employees[]) {
  double minimumsalary = employees[0].salary;
  int b = 0;
  for (int j = 0; j < 10; j++) {
    if (employees[j].salary < minimumsalary) {
      minimumsalary = employees[j].salary;
      b = j;
    }
  }
  cout << endl << endl;
  cout << "Name-Surname/Salary informations of the Employee with the minimum "
          "salary : "
       << employees[b].name << " - " << employees[b].surname << " / " << endl;
  return minimumsalary;
}

// This program is summing of salariess of all employees and then dividing by 10
// to get the average salary .
double averageSalaryy(employeeManager employees[]) {
  double sum = 0;
  double result;

  for (int a = 0; a < 10; a++) {
    sum += employees[a].salary;
  }
  cout << endl << endl;
  return result = sum / 10;
}

// This is the exit program .
void exit() {
  cout << "*************** Thank you for using this system ***************"
       << endl;
}
