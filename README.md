#include <iostream>
#include <fstream>
#include <string>
#include <iomanip>

using namespace std;

int main()
{
    cout << setprecision(2) << fixed; 
    string filename;
    cout << "** Welcome to UIC Bank v1.0 **" << endl;
    cout << "Enter bank filename>" << filename << endl;
    cin >> filename;

    cout << "** Inputting account data..." << endl;
    ifstream infile;
    infile.open(filename); // open infile
    if (!infile.good())
    {
        cout << "**Error: unable to open input file '" << filename << "'" << endl;
        return 0;
    }
    
    //input 5 bank accounts
    int  account1, account2, account3, account4, account5;
    double balance1,balance2, balance3, balance4, balance5;
    infile >> account1;
    infile >> balance1;
    infile >> account2;
    infile >> balance2;
    infile >> account3;
    infile >> balance3;
    infile >> account4;
    infile >> balance4;
    infile >> account5;
    infile >> balance5;
    
    //output account data
    cout << "** Outputting account data..." << endl;
    cout << "Account " << account1 << ": " << "balance $" << balance1 << endl;
    cout << "Account " << account2 << ": " << "balance $" << balance2 << endl;
    cout << "Account " << account3 << ": " << "balance $" << balance3 << endl;
    cout << "Account " << account4 << ": " << "balance $" << balance4 << endl;
    cout << "Account " << account5 << ": " << "balance $" << balance5 << endl;
      
    cout << "** Processing user commands..." << endl;
      
    string command = "";
    int account;
    double amount;
    
    //when the command unequal to the x, into the while loop
    while (command != "x"){
        cout << "Enter command (+, -, ?, ^, *, x):" << endl;
        cin >> command;
        //deposit: +
        if (command == "+"){
            cin >> account;
            cin >> amount;
            if (account == account1){
               balance1 += amount;
                cout << "Account " << account1 << ": balance $" << balance1 << endl;
            }
            else if (account == account2){
                balance2 += amount;
                cout << "Account " << account2 << ": balance $" << balance2 << endl;
            }
            else if (account == account3){
                balance3 += amount;
                cout << "Account " << account3 << ": balance $" << balance3 << endl;
            }
            else if (account == account4){
                balance4 += amount;
                cout << "Account " << account4 << ": balance $" << balance4 << endl;
            }
            else if (account == account5){
                balance5 += amount;
                cout << "Account " << account5 << ": balance $" << balance5 << endl;
            }
            else {
                cout << "** Invalid account, transaction ignored" << endl;
            }
    
        }
        //withdrawal: -
        else if (command == "-"){
            cin >> account;
            cin >> amount;
            if (account == account1){
                balance1 -= amount;
                cout << "Account " << account1 << ": balance $" << balance1 << endl;   
            }
            else if (account == account2){
                balance2 -= amount;
                cout << "Account " << account2 << ": balance $" << balance2 << endl;
            }
            else if (account == account3){
                balance3 -= amount;
                cout << "Account " << account3 << ": balance $" << balance3 << endl;
            }
            else if (account == account4){
                balance4 -= amount;
                cout << "Account " << account4 << ": balance $" << balance4 << endl;
            }
            else if (account == account5){
                balance5 -= amount;
                cout << "Account " << account5 << ": balance $" << balance5 << endl;
            }
            else{
                cout << "** Invalid account, transaction ignored" << endl;
            }
         
        }
        //check balcance: ?
        else if (command == "?"){
            cin >> account;
            if (account == account1){
                cout << "Account " << account1 << ": balance $" << balance1 << endl; 
            }
            else if (account == account2){
                cout << "Account " << account2 << ": balance $" << balance2 << endl;
            }
            else if (account == account3){
                cout << "Account " << account3 << ": balance $" << balance3 << endl;
            }
            else if (account == account4){
                cout << "Account " << account4 << ": balance $" << balance4 << endl;
            }
            else if (account == account5){
                cout << "Account " << account5 << ": balance $" << balance5 << endl;
            }
            else{
                cout << "** Invalid account, transaction ignored" << endl;   
            }

        }
        // find the account with the largest balance: ^
        else if (command == "^"){
            int maxAccount = account1;
            double maxBalance = balance1;
            if (maxBalance < balance2){
               maxAccount = account2;
               maxBalance = balance2;
            }
            if (maxBalance < balance3){
               maxAccount = account3;
               maxBalance = balance3;
            }
            if (maxBalance < balance4){
               maxAccount = account4;
               maxBalance = balance4;
            }
            if (maxBalance < balance5){
               maxAccount = account5;
               maxBalance = balance5;
            }
            cout << "Account " << maxAccount << ": balance $" << maxBalance << endl;
          
        }
        //list all accounts and balances: *
        else if (command == "*"){
            cout << "Account " << account1 << ": " << "balance $" << balance1 << endl;
            cout << "Account " << account2 << ": " << "balance $" << balance2 << endl;
            cout << "Account " << account3 << ": " << "balance $" << balance3 << endl;
            cout << "Account " << account4 << ": " << "balance $" << balance4 << endl;
            cout << "Account " << account5 << ": " << "balance $" << balance5 << endl;
        }
        else if (command != "x"){
             cout << "** Invalid command, try again..." << endl;
        }
        
    }
    
    cout << "** Saving account data..." << endl;
    
    ofstream outfile;
    outfile.open(filename);//open outfile
    if (!outfile.good())
    {
        cout << "**Error: unable to open input file '" << filename << "'" << endl;
    }
    //output the accounts and balances to same banking file
    outfile << account1 << " " << balance1 << endl;
    outfile << account2 << " " << balance2 << endl;
    outfile << account3 << " " << balance3 << endl;
    outfile << account4 << " " << balance4 << endl;
    outfile << account5 << " " << balance5 << endl;
    
    cout << "** Done **" << endl;
    infile.close();
    outfile.close();
    return 0;
}
