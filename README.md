#include <iostream>
#include <fstream>
#include <vector>
#include <list>
// Функція для зчитування дійсних чисел з файлу у вектор
std::vector<double> readNumbersFromFile(const std::string& filename) {
    std::vector<double> numbers;
    std::ifstream file(filename);
    double number;
    while (file >> number) {
        numbers.push_back(number);
    }
    return numbers;
}
// Функція для видалення додатніх чисел з вектора та перенесення у список у зворотному порядку
std::list<double> processVector(const std::vector<double>& numbers) {
    std::list<double> result;
    for (auto it = numbers.rbegin(); it != numbers.rend(); ++it) {
        if (*it <= 0) {
            result.push_back(*it);
        }
    }
    return result;
}
// Функція для виведення списку на екран
void printList(const std::list<double>& lst) {
    for (double number : lst) {
        std::cout << number << " ";
    }
    std::cout << std::endl;
}
int main() {
    // Зчитування дійсних чисел з файлу у вектор
    std::string filename = "numbers.txt"; // Припустимо, що файл називається numbers.txt
    std::vector<double> numbers = readNumbersFromFile(filename);
    // Видалення додатніх чисел з вектора та перенесення у список у зворотному порядку
    std::list<double> resultList = processVector(numbers);
    // Виведення утвореного списку на екран
    std::cout << "Утворений список у зворотному порядку: ";
    printList(resultList);
    return 0;
}
