#include <iostream> 

int main(){

    int maxSteps = 0;
    int maxNumber = 0;
    int steps = 0;
    int* previousSteps = new int[1000001]();
    long long i = 0;

    for(int startingNumber = 1; startingNumber < 1000000; startingNumber++){
        steps = 0;
        i = startingNumber;
        while(i != 1){
            if(i < startingNumber){
                steps += previousSteps[i];
                break;
            }
            else{
                if(i % 2 == 0) i /= 2;
                else i = (3 * i) + 1;
                steps++;
            }
        }
        if(steps > maxSteps){
            maxSteps = steps;
            maxNumber = startingNumber;
        }
        previousSteps[startingNumber] = steps;
    }

    std::cout << maxNumber;

    return 0;

}
