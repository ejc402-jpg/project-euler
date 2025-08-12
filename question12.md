#include <iostream> 
#include <cmath>

int factors(int number){
    int factors = 0;
    int root = static_cast<int>(std::sqrt(number));
    for(int i = 1; i <= root; i++){
        if(number % i == 0) factors += 2;
        if(root * root == number) factors--;
    }
    return factors;
}

int main(){

    int add = 2;
    int number = 1;

    while(true){
        if(factors(number) > 500){
            std::cout << number;
            break;
        };
        number += add;
        add++;
    }

    return 0;

}
