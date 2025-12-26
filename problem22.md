#include <iostream> 
#include <fstream>
#include <sstream>
#include <vector> 
#include <algorithm>

int calculateWordValue(const std::string& word){
    int total = 0;
    for(char c : word){
        total += (c - 64);
    }
    return total;
} 

int main(){

    int total = 0;

    std::string line = "";
    std::ifstream inputFile("0022_names.txt");
    std::string token = "";
    std::vector<std::string> words;

    if(inputFile.is_open()){
        std::getline(inputFile, line);
    }

    std::istringstream iss(line);
    
    while(std::getline(iss, token, ',')){
        token = token.substr(1, token.size() - 2);
        words.push_back(token);
    }

    std::sort(words.begin(), words.end());

    for(int i = 0; i < words.size(); i++){
        total += calculateWordValue(words[i]) * (i + 1);
    }

    std::cout << total; 

    return 0;

}
