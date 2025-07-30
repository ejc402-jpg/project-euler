#include <iostream> 

bool isPythagorean(const int &a, const int &b, const int &c){
    return ((a*a) + (b*b)) == (c*c);
}

int main(){

    for(int a = 1; a < 1000; a++){
        for(int b = 1; b < 1000; b++){
            int c = 1000 - a - b; 
            if(isPythagorean(a, b, c)) {
                std::cout << (a*b*c);
                return 0;
            }
        }
    }

    return 0;

}
