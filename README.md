#include <iostream>
#include <fstream>
#include <string>

using namespace std;

void signUp() {
    string username, password;

    cout << "=== Sign Up ===" << endl;
    cout << "Enter username: ";
    cin >> username;
    cout << "Enter password: ";
    cin >> password;

    // Check if username already exists
    ifstream infile("users.txt");
    string fileUsername, filePassword;
    while (infile >> fileUsername >> filePassword) {
        if (fileUsername == username) {
            cout << "Username already exists. Please choose another one." << endl;
            infile.close();
            return;
        }
    }
    infile.close();

    // Append new user to file
    ofstream outfile("users.txt", ios::app);
    outfile << username << " " << password << endl;
    outfile.close();

    cout << "Sign up successful!" << endl;
}

int main() {
    signUp();
    return 0;
}
