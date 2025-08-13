#include <iostream> 
#include <vector> 

std::vector<int> add(const std::vector<int> &first, const std::vector<int> &second){
    int index = 0;
    int sum = 0;
    int carry = 0;
    std::vector<int> result;
    while(index < first.size() && index < second.size()){
        sum = first[index] + second[index] + carry;
        carry = sum / 10;
        result.push_back(sum % 10);
        index++;
    }
    while(index < first.size()){
        sum = first[index] + carry;
        carry = sum / 10;
        result.push_back(sum % 10);
        index++;
    }
    while(index < second.size()){
        sum = second[index] + carry;
        carry = sum / 10;
        result.push_back(sum % 10);
        index++;
    }
    while(carry){
        result.push_back(carry % 10);
        carry /= 10;
    }
    return result;
}

int main(){

    std::vector<int> previous, current, newCurrent;
    previous.push_back(1);
    current.push_back(2);
    int index = 3;

    while(current.size() < 1000){
        index++;
        newCurrent = add(current, previous);
        previous = current;
        current = newCurrent;

    }

    std::cout << index;

    return 0;

}
