#include <iostream> 
#include <algorithm> 

// January - 31
// February - 28, February - 29 (leap year)
// March - 31
// April - 30
// May - 31
// June - 30
// July - 31
// August - 31
// September - 30
// October - 31
// November - 30
// December - 31

// 0 - Monday
// 1 - Tuesday
// 2 - Wednesday
// 3 - Thursday
// 4 - Friday
// 5 - Saturday
// 6 - Sunday

// 36,524 days is our range

int firstDaysNonLeap[] = {1, 32, 60, 91, 121, 152, 182, 213, 244, 274, 305, 335};
int firstDaysLeap[] = {1, 32, 61, 92, 122, 153, 183, 214, 245, 275, 306, 336};

bool isSunday(int day){
    return day % 7 == 6;
}
bool isLeapYear(int year){
    return(year % 4 == 0 && (year % 400 == 0 || year % 100 != 0));
}
bool isFirstDayOfMonth(int day, int year){
    if(isLeapYear(year)){
        auto it = std::find(std::begin(firstDaysLeap), std::end(firstDaysLeap), day);
        return (it == std::end(firstDaysLeap)) ? false : true; 
    }
    else{
        auto it = std::find(std::begin(firstDaysNonLeap), std::end(firstDaysNonLeap), day);
        return (it == std::end(firstDaysNonLeap)) ? false : true;
    }
}

int main(){
    int year = 1901;
    int days = 0;
    int sundays = 0;
    for(; year <= 2000; year++){ // 100 years
        if(!isLeapYear(year)){
            for(int i = 1; i <= 365; i++){
                if(isSunday(i + days) && isFirstDayOfMonth(i, year)) sundays++;
            }
            days += 365;
        }
        else{
            for(int i = 1; i <= 366; i++){
                if(isSunday(i + days) && isFirstDayOfMonth(i, year)) sundays++;
            }
            days += 366;
        }
    } 
    
    std::cout << sundays;

    return 0;

}
