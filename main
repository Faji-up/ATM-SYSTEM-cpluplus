#include <iostream>
#include <vector>
#include <ctime>
using namespace std;

void bankSystem();

void create_user();
bool check_age(int age);
bool check_acc_type(string type);
void login();

class User {
    public:
        string firstname;
        string lastname;
        string address;
        string birthday;
        string gender;
        string account_type;
        int balance;
        int pin;
        int user_id;

    User(string firstname,
         string lastname,
         string address,
         string birthday,
         string gender,
         string account_type,
         int balance,
         int pin,
         int user_id) : firstname(firstname), lastname(lastname), address(address), birthday(birthday), gender(gender), account_type(account_type), balance(balance), pin(pin), user_id(user_id) {}

    void show_balance() {
        cout << "********************\n";
        cout << "Your Balance is :" << balance << "\n";
        cout << "********************\n";
        bankSystem();
    }

    int get_pin() {
        return pin;
    }

    void deposit() {
        int dep;
        while (true) {
            cout << "Deposit Value :";
            cin >> dep;
            if (account_type == "SA") {
                if (dep >= 300) {
                    balance += dep;
                    cout << "Transaction Successful ";
                    bankSystem();
                    break;
                } else {
                    cout << "Amount is not Valid !";
                    continue;
                }
            } else if (account_type == "CA") {
                if (dep >= 500) {
                    balance += dep;
                    cout << "Transaction Successful ";
                    bankSystem();
                    break;
                } else {
                    cout << "Amount is not Valid !";
                    continue;
                }
            }
        }
    }

    void withdraw() {
        int wid;
        while (true) {
            cout << "Withdraw Value :";
            cin >> wid;
            if (account_type == "SA") {
                if (wid < balance) {
                    if (wid >= 300) {
                        balance -= wid;
                        cout << "Transaction Successful ";
                        bankSystem();
                        break;
                    } else {
                        cout << "Amount is not Valid !";
                        continue;
                    }
                } else {
                    int can;
                    cout << "Insufficient  Balance\n";
                    cout << "Want to cancel Transaction ? [0]NO [1]YES :";
                    cin >> can;
                    if (can == 0) {
                        continue;
                    } else if (can == 1) {
                        bankSystem();
                        break;
                    }
                }
            } else if (account_type == "CA") {
                if (wid < balance) {
                    if (wid >= 500) {
                        balance -= wid;
                        cout << "Transaction Successful ";
                        bankSystem();

                        break;
                    } else {
                        cout << "Amount is not Valid !";
                        continue;
                    }
                } else {
                    int can;
                    cout << "Insufficient  Balance\n";
                    cout << "Want to cancel Transaction ? [0]NO [1]YES :";
                    cin >> can;
                    if (can == 0) {
                        continue;
                    } else if (can == 1) {
                        bankSystem();
                        break;
                    }
                }
            }
        }
    }

    void view_info() {
        cout << "*****************************************\n";
        cout << "Firstname : " << firstname << "\n";
        cout << "Lastname : " << lastname << "\n";
        cout << "Address : " << address << "\n";
        cout << "Birthday : " << birthday << "\n";
        cout << "Gender : " << gender << "\n";
        cout << "Account Type : " << account_type << "\n";
        cout << "Current Balance : " << balance << "\n";
        cout << "*****************************************\n";
        bankSystem();

    }
};

int current_user = -1;
vector<User> users;
int main() {
    cout << "*******************************************\n";
    cout << "           VOYTICAS BANKING SYSTEM         \n";
    cout << "*******************************************\n";
    bankSystem();
    return 0;
}

void bankSystem() {
    int opt;

    cout << "\n[1] Open new Account\n[2] Balance Inquiry\n[3] Deposit\n[4] Withdraw\n[5] View Account information\n[6] Close Account\n[7] Exit Program\n";
    cout << ">> ";
    while (true) {
        cin >> opt;
        switch (opt) {
            case 1:
                login();
                break;
            case 2:
                if (current_user != -1) {
                    users[current_user].show_balance();
                } else {
                    cout << "No logged account yet please login\n";
                    login();
                }
                break;
            case 3:
                if (current_user != -1) {
                    int p;
                    cout << "Proceed ? [0]Yes [1]No :";
                    cin >> p;
                    if (p == 0) {
                        users[current_user].deposit();
                    }
                } else {
                    cout << "No logged account yet please login\n";
                    login();
                }
                break;
            case 4:
                if (current_user != -1) {
                    int p;
                    cout << "Proceed ? [0]Yes [1]No :";
                    cin >> p;
                    if (p == 0) {
                        users[current_user].withdraw();
                    }
                } else {
                    cout << "No logged account yet please login\n";
                    login();
                }
                break;
            case 5:
                if (current_user != -1) {
                    int p;
                    cout << "Proceed ? [0]Yes [1]No :";
                    cin >> p;
                    if (p == 0) {
                        users[current_user].view_info();
                    }
                } else {
                    cout << "No logged account yet please login\n";
                    login();
                }
                break;
            case 6:
                if (current_user != -1) {
                    int p;
                    cout << "Proceed ? [0]Yes [1]No :";
                    cin >> p;
                    if (p == 0) {
                        current_user = -1;
                        bankSystem();
                    }
                } else {
                    cout << "No logged account yet please login\n";
                    login();
                }
                break;
            case 7:
                cout << "Program closed\n";
                return;
            default:
                cout << "Invalid option, please try";

}}}
void create_user() {
    string firstname;
    string lastname;
    string address;
    string birthday;
    string gender;
    string account_type;
    int balance;
    int pin;
    srand(time(0));
    int user_id = rand();

    cout << "Enter Firstname: ";
    cin >> firstname;
    cout << "Enter Lastname: ";
    cin >> lastname;
    cout << "Enter Address: ";
    cin >> address;
    while (true) {
        cout << "Enter Birthday [yyyy/mm/dd]: ";
        cin >> birthday;
        if (check_age(stoi(birthday.substr(0, 4)))) {
            break;
        } else {
            cout << "You are too young to make an account\n";
            continue;
        }
    }
    while (true) {
        cout << "Enter Gender [M]MALE [F]FEMALE : ";
        cin >> gender;
        if (gender == "M") {
            gender = "MALE";
            break;
        } else if (gender == "F") {
            gender = "FEMALE";
            break;
        } else {
            cout << "Invalid Gender\n";
            continue;
        }
    }
    while (true) {
        cout << "Enter Account Type [SA]Saving Account [CA] Current Account: ";
        cin >> account_type;
        if (check_acc_type(account_type)) {
            break;
        } else {
            cout << "Invalid Type\n";
            continue;
        }
    }
    while (true) {
        cout << "Enter Balance: ";
        cin >> balance;
        if (account_type == "SA") {
            if (balance >= 5000) {

                break;
            } else {
                cout << "SA initial balance must be greater or equal to 5000\n";
                continue;
            }
        } else if (account_type == "CA") {
            if (balance >= 10000) {
                break;
            } else {
                cout << "CA initial balance must be greater or equal to 10000\n";
                continue;
            }
        }
    }
    while (true) {
        cout << "Enter 6 digits Pin: ";
        cin >> pin;
        if (pin >= 100000) {
            break;
        } else {
            cout << "Pin must be a 6-digit number!\n";
            continue;
        }
    }

    User user(firstname, lastname, address, birthday, gender, account_type, balance, pin, user_id);
    users.push_back(user);
    cout << "Account Successfully Created !\n";
    bankSystem();
}

bool check_age(int age){
    if(age > 2005){
        return false;
    }else{
        return true;
    }
}
bool check_acc_type(string type) {
    return (type == "SA" || type == "CA");
}

void login() {
    int pin;
    bool isExist = false;
    cout << "Enter Pin: ";
    cin >> pin;
    for (int i = 0; i < users.size(); i++) {
        if (users[i].get_pin() == pin) {
            current_user = i;
            isExist = true;
            bankSystem();
            return;
        }
    }
    if (!isExist) {
        cout << "There's no account yet\n";
        cout << "Create Account\n";
        create_user();
    }
}
