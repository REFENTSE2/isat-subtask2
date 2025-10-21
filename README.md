#include <iostream>
#include <string>
#include <cstdlib>  // for rand()
#include <ctime>    // for time()
using namespace std;

// Function 1: Decimal to Binary
string decimalToBinary(int decimal) {
    if (decimal == 0) return "0";
    string binary = "";
    while (decimal > 0) {
        binary = char((decimal % 2) + '0') + binary;
        decimal /= 2;
    }
    return binary;
}

// Function 2: Binary to Decimal
int binaryToDecimal(string binary) {
    int decimal = 0;
    int power = 1;
    for (int i = binary.length() - 1; i >= 0; i--) {
        if (binary[i] == '1') {
            decimal += power;
        }
        power *= 2;
    }
    return decimal;
}

// Function 3: Decimal to Hexadecimal
string decimalToHex(int decimal) {
    if (decimal == 0) return "0";
    string hex = "";
    char hexDigits[] = "0123456789ABCDEF";
    while (decimal > 0) {
        int remainder = decimal % 16;
        hex = hexDigits[remainder] + hex;
        decimal /= 16;
    }
    return hex;
}

// Function 4: Hexadecimal to Decimal
int hexToDecimal(string hex) {
    int decimal = 0;
    int power = 1;
    for (int i = hex.length() - 1; i >= 0; i--) {
        char c = hex[i];
        int value;
        if (c >= '0' && c <= '9') value = c - '0';
        else if (c >= 'A' && c <= 'F') value = c - 'A' + 10;
        else if (c >= 'a' && c <= 'f') value = c - 'a' + 10;
        else value = 0;  // invalid character
        decimal += value * power;
        power *= 16;
    }
    return decimal;
}

// Menu
void menu() {
    int choice;
    srand(time(0)); // seed for random numbers

    do {
        cout << "\n--- Number Converter Menu ---\n";
        cout << "1. Convert Decimal to Binary\n";
        cout << "2. Convert Binary to Decimal\n";
        cout << "3. Convert Decimal to Hexadecimal\n";
        cout << "4. Convert Hexadecimal to Decimal\n";
        cout << "5. Demo (Random number to Binary)\n";
        cout << "6. Exit\n";
        cout << "Enter your choice (1-6): ";
        cin >> choice;

        if (choice == 1) {
            int num;
            cout << "Enter a decimal number: ";
            cin >> num;
            cout << "Binary: " << decimalToBinary(num) << endl;
        }
        else if (choice == 2) {
            string binaryStr;
            cout << "Enter a binary number: ";
            cin >> binaryStr;
            cout << "Decimal: " << binaryToDecimal(binaryStr) << endl;
        }
        else if (choice == 3) {
            int num;
            cout << "Enter a decimal number: ";
            cin >> num;
            cout << "Hexadecimal: " << decimalToHex(num) << endl;
        }
        else if (choice == 4) {
            string hexStr;
            cout << "Enter a hexadecimal number: ";
            cin >> hexStr;
            cout << "Decimal: " << hexToDecimal(hexStr) << endl;
        }
        else if (choice == 5) {
            int randomNum = rand() % 100; // random number between 0 and 99
            cout << "Random Number: " << randomNum << endl;
            cout << "Binary: " << decimalToBinary(randomNum) << endl;
        }
        else if (choice == 6) {
            cout << "Exiting program. Goodbye!" << endl;
        }
        else {
            cout << "Invalid choice. Please select a number between 1 and 6." << endl;
        }
    } while (choice != 6);
}

// Main function
int main() {
    menu();
    return 0;
}


