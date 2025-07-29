#include <iostream>

bool isPrime(int number){
    if(number <= 1) return false;
    if(number == 2) return true;
    if(number % 2 == 0) return false;
    for(int i = 3; i*i <= number; i += 2){
        if(number % i == 0) return false;
    }
    return true;
}

int main(){ // fundamental theorem of arithmetic implementation

    int recentFactor = 2;
    long long int number = 600851475143;

    while(number != 1){
        if(number % recentFactor == 0 && isPrime(recentFactor)){
            number /= recentFactor;
        }
        else{
            recentFactor++;
        }
    }

    std::cout << recentFactor;
 
    return 0;

}
