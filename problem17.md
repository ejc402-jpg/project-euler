#include <iostream> 
#include <vector> 

int main(){

    int letters = 11; // one thousand
    int i = 0;
    int lengthsOnes[] = {0, 3, 3, 5, 4, 4, 3, 5, 5, 4, 3, 6, 6, 8, 8, 7, 7, 9, 8, 8};
    int lengthsTens[] = {0, 0, 6, 6, 5, 5, 5, 7, 6, 6};
    for(int original = 1; original < 1000; original++){
        i = original;
        if(i <= 19){
            letters += lengthsOnes[i];
        }
        else{ // 20 - 99, 101 - 999, deal with #10 - #19
            if(i >= 20 && i <= 99){
                letters += lengthsOnes[i % 10];
                i /= 10;
                letters += lengthsTens[i];
            }
            else{
                if(i % 100 == 0) letters -= 3;
                letters += 10;
                if(i % 100 >= 10 && i % 100 <= 19){
                    letters += lengthsOnes[i % 100];
                    letters += lengthsOnes[i / 100];
                }
                else{
                    letters += lengthsOnes[i % 10];
                    i /= 10;
                    letters += lengthsTens[i % 10];
                    i /= 10;
                    letters += lengthsOnes[i];
                }
            }
        }
    }

    std::cout << letters;

    return 0;

}
