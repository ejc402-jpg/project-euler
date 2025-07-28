#include <iostream>

int main(){

    int number = 2520; 
    bool foundNumber = false;

    while(!foundNumber){
        foundNumber = true;
        for(int i = 11; i <= 20; i++){
            if(number % i != 0){
                foundNumber = false;
                number += 2520;
                break;
            }
        }
    
    }

    std::cout << number;
 
    return 0;

}
