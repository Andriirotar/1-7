#include <iostream>
#include <vector>
#include <string>

using namespace std;

class Car {
public:
    Car(const string& make, const string& model, int year, double price)
        : make(make), model(model), year(year), price(price) {}

    void display() const {
        cout << "Зробити: " << make << ", Модель: " << model
             << ", Рік: " << year << ", Ціна: $" << price << endl;
    }

private:
    string make;
    string model;
    int year;
    double price;
};

class Showroom {
public:
    void addCar(const Car& car) {
        cars.push_back(car);
    }

    void listCars() const {
        if (cars.empty()) {
            cout << "Автомобілів немає». << endl;
            return;
        }

        for (const auto& car : cars) {
            car.display();
        }
    }

private:
    vector<Car> cars;
};

int main() {
    Showroom showroom;
    int choice;

    while (true) {
        cout << "1. Додати автомобіль\n2. Список автомобілів\n3. Вийти\n";
        cout << "Введіть ваш вибір: ";
        cin >> choice;
        cin.ignore();  
        if (choice == 1) {
            string make, model;
            int year;
            double price;

           cout << "Введіть make: ";
            getline(cin, make);
            cout << "Введіть модель: ";
            getline(cin, модель);
            cout << "Введіть рік: ";
            cin >> рік;
            cout << "Введіть ціну: ";
            cin >> price;
            cin.ignore();  
            Car newCar(make, model, year, price);
            showroom.addCar(newCar);
        } else if (choice == 2) {
            showroom.listCars();
        } else if (choice == 3) {
            break;
        } else {
            cout << "Неправильний вибір. Спробуйте ще раз." << endl;
        }
    }

    return 0;
}
