#include <iostream> //input-output
#include <string> //for string statments
#include <fstream> //for creating file
#include <vector> //for vectors
using namespace std;

int main() {
	vector<string> names = {"Envy", "Ilyas", "Damon", "Hamir", "Anthony", "Bode","George",
	                        "Jordan","Christopher", "Caleb", "Seth", "Ryan", "Tiahna", "Bailin", "Elija", "Connor"
	                       };
	vector<string> attendance = {}; //vector to hold attendance
	string name; //to take name
	string date; //to take date
	int loop = 0; //loop variable
	int fail; //for invalid inputs
	int i, attendances; //temporary variable and attendance

	cout << "enter date as month-day-year\n"; //asks for date
	cin >> date;
	ofstream MyFile (date + ".txt"); //creates file name

	do {
		i = 0;
		while (i < 16) {
			fail = 0;
			i++;
			cout << names.front() << " are they present, yes(1) no(2)\n"; //asks if student is present
			cin >> attendances;
			if (attendances == 1) {

				MyFile << names.size() <<  ", attendance: present\n"; //1 = yes
				attendance.push_back(", attendance: present\n");
			}
			else if (attendances == 2) {
				MyFile << names.front() <<  ", attendance: absent\n"; //2 = no
				attendance.push_back(", attendance: absent\n");
			} else {
				cout << "invalid input, try again\n"; //otherwise reloops
				fail++;
			}
		}
	} while (fail == 1); // resets on invalid input

	loop++;

	MyFile.close();

	return 0;
}
