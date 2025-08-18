#include <iostream> 
#include <vector> 

std::vector<int> storedValues(10000, -1);

int d(const int &num){
    int sum = 1;
    if(num < 2) return 0;
    if(storedValues[num] != -1) return storedValues[num];
    for(int i = 2; i * i <= num; i++){
        if(num % i == 0){
            sum += i + (num/i);
            if(i * i == num) sum -= i;
        }
    }
    storedValues[num] = sum;
    return sum;
}

int main(){

    int sum = 0;

    for(int i = 1; i < 10000; i++){
        int result = d(i);
        if(result >= 10000) continue;
        int secondResult = d(result);
        if(secondResult >= 10000) continue; 
        if(i == secondResult && i != result){
            sum += i;
        }
    }

    std::cout << sum;

    return 0;

}

// int d(const int &num){
//     int sum = 0;
//     for(int i = 1; i <= num / 2; i++){
//         if(num % i == 0) sum += i;
//     }
//     return sum;
// }

// int main(){

//     int sum = 0;

//     for(int i = 1; i < 10000; i++){
//         int result = d(i);
//         int secondResult = d(result);
//         if(secondResult >= 10000 || result >= 10000 || secondResult <= 0 || result <= 0) continue;
//         if(i == secondResult && i != result){
//             sum += i;
//         }
//     }

//     std::cout << sum;

//     return 0;

// }
