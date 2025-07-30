#include <iostream> 

bool isPrime(const int &number){
    for(int j = 3; j*j <= number; j += 2){
        if(number % j == 0) return false;
    }
    return true;
}

int main(){

    long long int sum = 2;

    for(int i = 3; i < 2000000; i += 2){
        if(isPrime(i)) sum += i;
    }

    std::cout << sum;

    return 0;

}
