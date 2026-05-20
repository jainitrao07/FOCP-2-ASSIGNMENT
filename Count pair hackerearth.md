#include #include <unordered_map> using namespace std;

int main() {

int n;
cin >> n;

int arr[n];

for (int i = 0; i < n; i++) {
    cin >> arr[i];
}

unordered_map<int, int> frequency;

long long pairs = 0;

for (int i = 0; i < n; i++) {

    pairs += frequency[arr[i]];

    frequency[arr[i]]++;
}

cout << pairs << endl;

return 0;

}
