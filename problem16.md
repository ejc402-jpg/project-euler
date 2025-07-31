#include <iostream> 
#include <cmath> 
#include <string> 
#include <vector>

int main(){

    std::vector<int> digits = {1};

    for(int i = 0; i < 1000; i++){
        int carry = 0;
        for(int j = 0; j < digits.size(); j++){
            int product = (digits[j] * 2) + carry;
            digits[j] = product % 10;
            carry = product / 10; 
        }
        while(carry > 0){
            digits.push_back(carry % 10);
            carry /= 10;
        }
    }

    int sum = 0;

    for(int num : digits){
        sum += num;
    }

    std::cout << sum;

    return 0;

}
