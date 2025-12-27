#include <iostream>
#include <algorithm> 

int findPivot(const std::string& permutation){ // right most index of number where less than its right value
    int index = permutation.size() - 2;
    while(index >= 0){
        if(permutation[index] < permutation[index+1]) return index;
        index--;
    }
    return -1;
} 

int findSwapIndex(const std::string& permutation, const int &pivotIndex){
    int minIndex = pivotIndex + 1;
    int index = permutation.size() - 1;
    while(index > pivotIndex + 1){
        if(permutation[index] > permutation[pivotIndex]){
            minIndex = (permutation[index] < permutation[minIndex]) ? index : minIndex; 
        }
        index--;
    } 
    return minIndex;
} 

void reversePermutationTail(std::string &permutation, const int& pivotIndex){ // want to reverse substring from pivotIndex + 1 to end
    std::reverse(permutation.begin() + pivotIndex + 1, permutation.end());
}

int main(){

    std::string permutation = "0123456789";

    for(int i = 2; i <= 1000000; i++){
        int pivot = findPivot(permutation);
        if(pivot == -1) break;
        std::swap(permutation[pivot], permutation[findSwapIndex(permutation, pivot)]);
        reversePermutationTail(permutation, pivot);
    }
    
    std::cout << permutation;

    return 0;

}
