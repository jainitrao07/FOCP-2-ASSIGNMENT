#include #include #include #include using namespace std;

int main() {

string name;

cout << "Enter student name: ";
getline(cin, name);

vector<string> excuses = {

    "{name} couldn't finish the assignment because the laptop updated for 5 hours.",
    "{name} was about to submit homework when the Wi-Fi disappeared.",
    "{name}'s keyboard stopped working during the assignment.",
    "{name} accidentally deleted the assignment file.",
    "{name} got trapped in a never-ending software update.",
    "{name}'s browser crashed before submission.",
    "{name} was fighting with compiler errors all night.",
    "{name}'s pet walked on the keyboard and ruined the code.",
    "{name} forgot to save the file before shutdown.",
    "{name}'s internet connection entered airplane mode emotionally."
};

srand(time(0));

int randomIndex = rand() % excuses.size();

string excuse = excuses[randomIndex];

size_t pos = excuse.find("{name}");

while (pos != string::npos) {

    excuse.replace(pos, 6, name);
    pos = excuse.find("{name}");
}

cout << excuse << endl;

return 0;

}
