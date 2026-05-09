#include #include <unordered_map> using namespace std;

class Bank {

private: unordered_map<int, int> accounts;

public:

bool CREATE(int userId, int amount) {

    if (accounts.find(userId) == accounts.end()) {

        accounts[userId] = amount;
        return true;
    }

    accounts[userId] += amount;
    return false;
}

bool DEBIT(int userId, int amount) {

    if (accounts.find(userId) == accounts.end())
        return false;

    if (accounts[userId] < amount)
        return false;

    accounts[userId] -= amount;

    return true;
}

bool CREDIT(int userId, int amount) {

    if (accounts.find(userId) == accounts.end())
        return false;

    accounts[userId] += amount;

    return true;
}

int BALANCE(int userId) {

    if (accounts.find(userId) == accounts.end())
        return -1;

    return accounts[userId];
}
};

int main() {

int Q;
cin >> Q;

Bank bank;

while (Q--) {

    string query;
    cin >> query;

    if (query == "CREATE") {

        int X, Y;
        cin >> X >> Y;

        cout << (bank.CREATE(X, Y) ? "true" : "false") << endl;
    }

    else if (query == "DEBIT") {

        int X, Y;
        cin >> X >> Y;

        cout << (bank.DEBIT(X, Y) ? "true" : "false") << endl;
    }

    else if (query == "CREDIT") {

        int X, Y;
        cin >> X >> Y;

        cout << (bank.CREDIT(X, Y) ? "true" : "false") << endl;
    }

    else if (query == "BALANCE") {

        int X;
        cin >> X;

        cout << bank.BALANCE(X) << endl;
    }
}

return 0;
}
