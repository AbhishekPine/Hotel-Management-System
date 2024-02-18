# Hotel-Management-System
## Introduction
This code is an implementation of a Hotel Management System in C++. It allows users to book rooms, display customer records, view allotted rooms, edit records, and delete records. The system provides a user-friendly interface for managing hotel operations efficiently.

## Key Concepts
### Classes: 
The code uses a class called hotel to encapsulate the data and functions related to hotel management.
### File Handling: 
The code uses file handling to store and retrieve customer records. It uses the fstream library to read and write data to a file.
### User Input: 
The code prompts the user for input to perform various operations such as booking a room, displaying records, editing records, etc.
### Control Flow: 
The code uses control flow statements such as if, switch, and while to control the execution of different parts of the program based on user input.

## Code Structure
The code is structured into several functions and a main function. Here is an overview of the functions:

* intro(): Displays the introduction and credits for the hotel management system.
* head(): Displays the header of the hotel management system.
* time(): Simulates a loading screen by displaying a message while syncing data.
* class hotel: Defines the hotel class and its member functions.
* main_menu(): Displays the main menu options and handles user input to perform different operations.
* add(): Allows the user to add a customer record by entering details such as room number, name, address, phone number, and number of days to checkout.
* display(): Displays the details of a customer record based on the entered room number.
* rooms(): Displays a list of all rooms that have been allotted to customers.
* edit(): Allows the user to edit or delete a customer record by entering the room number and choosing the desired operation.
* check(): Checks if a room is already booked by searching for the room number in the record file.
* modify(): Modifies the details of a customer record based on the entered room number.
* delete_rec(): Deletes a customer record based on the entered room number.
* main(): The main function that initializes the hotel object, displays the login screen, and calls the main_menu() function.
## Code Examples
Here are a few code examples to illustrate the usage of functions in the code:

Adding a customer record:
```cpp
void hotel::add() {
	clrscr();
	head();
	int r,flag;
	ofstream fout("Record.dat",ios::app);
	cout<<"\n Enter Customer Details";
	cout<<"\n ----------------------";
	cout<<"\n\n Room no: ";
	cin>>r;
	flag=check(r);
	if(flag)
		cout<<"\n Sorry..!!!Room is already booked";
	else {
		room_no=r;
		cout<<" Name: ";
		gets(name);
		cout<<" Address: ";
		gets(address);
		cout<<" Phone No: ";
		gets(phone);
		cout<<" No of Days to Checkout: ";
		cin>>days;
		fare=days*900;						

		fout.write((char*)this,sizeof(hotel));
		cout<<"\n Room is booked...!!!";
	}

	cout<<"\n Press any key to continue.....!!";
	getch();
	fout.close();
}
```
Displaying a customer record:
```cpp
void hotel::display() {
	clrscr();
	head();
	ifstream fin("Record.dat",ios::in);
	int r,flag;
	cout<<"\n Enter room no: ";
	cin>>r;
	while(!fin.eof()) {
		fin.read((char*)this,sizeof(hotel));
		if(room_no==r) {
			clrscr();
			head();
			cout<<"\n Customer Details";
			cout<<"\n ----------------";
			cout<<"\n\n Room no: "<<room_no;
			cout<<"\n Name: "<<name;
			cout<<"\n Address: "<<address;
			cout<<"\n Phone no: "<<phone;
			cout<<"\n Days: "<<days;
			cout<<"\n Total Fare: "<<fare;
			flag=1;
		}
	}
	if(flag==0)
		cout<<"\n Sorry Room no. not found or vacant....!!";
	cout<<"\n\n Press any key to continue....!!";
	getch();
	fin.close();
}
Editing a customer record:
language-cpp
 Copy code
void hotel::edit() {
	clrscr();
	head();
	int choice,r;
	cout<<"\n EDIT MENU";
	cout<<"\n ---------";
	cout<<"\n\n 1.Modify Customer Record";
	cout<<"\n 2.Delete Customer Record";
	cout<<"\n Enter your choice: ";
	cin>>choice;

	clrscr();
	head();
	cout<<"\n Enter room no: " ;
	cin>>r;
	switch(choice) {
		case 1:	modify(r);
				break;
		case 2:	delete_rec(r);
				break;
		default: cout<<"\n Wrong Choice.....!!";
	}
	cout<<"\n Press any key to continue....!!!";
	getch();
}
```
## Conclusion
The Hotel Management System implemented in C++ provides a convenient way to manage hotel operations such as booking rooms, displaying customer records, and editing or deleting records. The code demonstrates the use of classes, file handling, and control flow statements to create a functional and user-friendly system. By understanding the code structure and examples provided, you can further customize and enhance the system to meet specific requirements.
