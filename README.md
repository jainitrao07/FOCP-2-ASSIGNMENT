#include<iostreeam>
using namespace std;

int main() {

int T;
cin >> T;

while (T--) {

    long long N;
    cin >> N;

    if (N % 2 == 0)
        cout << "Even" << endl;
    else
        cout << "Odd" << endl;
}

return 0;
}
