#include #include #include #include using namespace std;

int main() {

string name;

cout << "Enter your name: ";
getline(cin, name);

vector<string> roasts = {

    "{name} writes code so slowly that even turtles feel fast.",
    "{name} debugs code by staring at the screen dramatically.",
    "If laziness had a CEO, it would be {name}.",
    "{name}'s code has more bugs than a jungle.",
    "{name} treats deadlines like suggestions.",
    "{name} can turn a simple print statement into a research project.",
    "{name}'s keyboard deserves compensation for overwork.",
    "Even AI gets confused reading {name}'s code.",
    "{name} writes comments nobody understands.",
    "{name}'s coding speed depends on Wi-Fi motivation."
};

srand(time(0));

int randomIndex = rand() % roasts.size();

string roast = roasts[randomIndex];

size_t pos = roast.find("{name}");

while (pos != string::npos) {

    roast.replace(pos, 6, name);
    pos = roast.find("{name}");
}

cout << roast << endl;

return 0;
}
