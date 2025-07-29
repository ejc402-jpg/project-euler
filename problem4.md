#include <iostream> 
#include <string> 
#include <algorithm>

bool isPalindrome(int num){
    std::string number = std::to_string(num);
    std::string numberReversed = number;
    std::reverse(numberReversed.begin(), numberReversed.end());
    return (number == numberReversed);
}

int main(){

    int highestPalindrome = 0;

    for(int i = 999; i >= 100; i--){
        for(int j = i; j >= 100; j--){
            if(isPalindrome(i*j) && i*j > highestPalindrome) highestPalindrome = i*j;
        }
    }

    std::cout << highestPalindrome;

    return 0;

}
