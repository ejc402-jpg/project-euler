#include <iostream>

int main(){

    int first = 1;
    int second = 2;
    int third = 3;

    int sum = 2;

    while(third <= 4000000){
        if(third % 2 == 0){
            sum += third;
        }
        first = second; 
        second = third;
        third = first + second;
    }

    std::cout << sum;
 
    return 0;
    
}
