#include <iostream> 
#include <vector>

int sumOfDigits(const std::vector<int> &number){
    int sum = 0;
    for(int num : number) sum += num;
    return sum;
}

int main(){

    int carry = 0;
    int product = 0;
    std::vector<int> digits = {1};

    for(int i = 2; i <= 100; i++){
        carry = 0;
        for(int j = 0; j < digits.size(); j++){
            product = digits[j] * i + carry;
            digits[j] = product % 10;
            carry = product/10;
        }
        while(carry > 0){
            digits.push_back(carry % 10);
            carry /= 10;
        }
    }

    std::cout << sumOfDigits(digits);

    return 0;

}
