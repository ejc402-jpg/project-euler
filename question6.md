#include <iostream>
#include <cmath>

int main(){

    int squareOfSum = 0;
    int sumOfSquare = 0;
    for(int i = 1; i <= 100; i++){
        squareOfSum += i;
        sumOfSquare += pow(i, 2);
    }

    squareOfSum = pow(squareOfSum, 2);

    std::cout << squareOfSum - sumOfSquare;
 
    return 0;

}
