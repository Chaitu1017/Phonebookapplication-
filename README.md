# Phonebookapplication-
#include <iostream>
#include <string>
#include <map>

using namespace std;

// PhoneBook class
class PhoneBook {
private:
    map<string, string> contacts;

public:
    void addContact(const string& name, const string& phoneNumber) {
        contacts[name] = phoneNumber;
    }

    void displayContact(const string& name) {
        if (contacts.count(name) == 0)
            cout << "Contact not found." << endl;
        else
            cout << "Name: " << name << ", Phone number: " << contacts[name] << endl;
    }

    void displayAllContacts() {
        if (contacts.empty()) {
            cout << "Phone book is empty." << endl;
        } else {
            cout << "Phone Book Contacts:" << endl;
            for (const auto& contact : contacts) {
                cout << "Name: " << contact.first << ", Phone number: " << contact.second << endl;
            }
        }
    }

    void deleteContact(const string& name) {
        if (contacts.erase(name) == 0)
            cout << "Contact not found." << endl;
        else
            cout << "Contact deleted." << endl;
    }
};

// Main function
int main() {
    PhoneBook phoneBook;
    int choice;
    string name, phoneNumber;

    while (true) {
        cout << "Phone Book Application" << endl;
        cout << "1. Add contact" << endl;
        cout << "2. Display contact" << endl;
        cout << "3. Display all contacts" << endl;
        cout << "4. Delete contact" << endl;
        cout << "5. Quit" << endl;
        cout << "Enter your choice: ";
        cin >> choice;
   switch (choice) {
            case 1:
                cout << "Enter name: ";
                cin.ignore();
                getline(cin, name);
                cout << "Enter phone number: ";
                getline(cin, phoneNumber);
                phoneBook.addContact(name, phoneNumber);
                break;
            case 2:
                cout << "Enter name: ";
                cin.ignore();
                getline(cin, name);
                phoneBook.displayContact(name);
                break;
            case 3:
                phoneBook.displayAllContacts();
                break;
            case 4:
                cout << "Enter name: ";
                cin.ignore();
                getline(cin, name);
                phoneBook.deleteContact(name);
                break;
            case 5:
                cout << "Exiting program. Goodbye!" << endl;
                return 0;
            default:
                cout << "Invalid choice. Try again." << endl;
        }
        cout << endl;
    }

    return 0;
}
