#include #include <unordered_map> #include <unordered_set> using namespace std;

class MovieTicket { private: unordered_map<int, unordered_set> bookings; unordered_map<int, int> bookedCount;

public:

bool BOOK(int userId, int movieId) {

    if (bookings[movieId].count(userId))
        return false;

    if (bookedCount[movieId] >= 100)
        return false;

    bookings[movieId].insert(userId);
    bookedCount[movieId]++;

    return true;
}

bool CANCEL(int userId, int movieId) {

    if (!bookings[movieId].count(userId))
        return false;

    bookings[movieId].erase(userId);
    bookedCount[movieId]--;

    return true;
}

bool IS_BOOKED(int userId, int movieId) {

    return bookings[movieId].count(userId);
}

int AVAILABLE_TICKETS(int movieId) {

    return 100 - bookedCount[movieId];
}

};

int main() {

int Q;
cin >> Q;

MovieTicket mt;

while (Q--) {

    string query;
    cin >> query;

    if (query == "BOOK") {

        int X, Y;
        cin >> X >> Y;

        cout << (mt.BOOK(X, Y) ? "true" : "false") << endl;
    }

    else if (query == "CANCEL") {

        int X, Y;
        cin >> X >> Y;

        cout << (mt.CANCEL(X, Y) ? "true" : "false") << endl;
    }

    else if (query == "IS_BOOKED") {

        int X, Y;
        cin >> X >> Y;

        cout << (mt.IS_BOOKED(X, Y) ? "true" : "false") << endl;
    }

    else if (query == "AVAILABLE_TICKETS") {

        int Y;
        cin >> Y;

        cout << mt.AVAILABLE_TICKETS(Y) << endl;
    }
}

return 0;

}
