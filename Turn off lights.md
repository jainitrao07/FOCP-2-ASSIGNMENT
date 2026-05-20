#include <iostream>
#include <string>
#include <vector>

using namespace std;

bool canTurnOffAll(const string& bulbs, int N, int K, int l) {
    int operations = 0;
    int i = 0;
    
    while (i < N) {
        if (bulbs[i] == '1') {
            operations++;
            i += l; 
        } else {
            i++;
        }
    }
  
    return operations <= K;
}

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    
    int N, K;
    if (!(cin >> N >> K)) return 0;
    
    string bulbs;
    cin >> bulbs;
    '
    int low = 1;
    int high = N;
    int ans = N;
    
    while (low <= high) {
        int mid = low + (high - low) / 2;
        
        if (canTurnOffAll(bulbs, N, K, mid)) {
            ans = mid;         
            high = mid - 1;    
        } else {
            low = mid + 1;     
        }
    }
    
    cout << ans << "\n";
    
    return 0;
}
