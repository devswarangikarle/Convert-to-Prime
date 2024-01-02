# Convert-to-Prime

#include <iostream>
#include <vector>

using namespace std;

bool is_prime(int num) {
    if (num < 2) {
        return false;
    }
    for (int i = 2; i * i <= num; ++i) {
        if (num % i == 0) {
            return false;
        }
    }
    return true;
}

int find_prime_insertion(const vector<int>& arr) {
    int total_sum = 0;
    for (int num : arr) {
        total_sum += num;
    }

    if (is_prime(total_sum)) {
        return 0;
    }

    // Find the smallest non-negative number to be added
    for (int i = 1; i < total_sum; ++i) {
        if (is_prime(total_sum + i)) {
            return i;
        }
    }

    // This line should not be reached in a valid scenario, but added for completeness.
    return -1;
}

int main() {
    int n;
    cin >> n;

    vector<int> arr(n);
    for (int i = 0; i < n; ++i) {
        cin >> arr[i];
    }

    // Output
    int result = find_prime_insertion(arr);
    cout << result << endl;

    return 0;
}
