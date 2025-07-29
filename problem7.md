#include <iostream> 

bool isPrime(int number){
    if(number % 2 == 0) return false;
    for(int i = 3; i * i <= number; i += 2){
        if(number % i == 0) return false;
    }
    return true;
}

int main(){

    int number = 3;
    int primeNumbers = 1;

    while(primeNumbers != 10001){
        if(isPrime(number)) primeNumbers++;
        number += 2;
    }

    std::cout << number - 2;

    return 0;

}
