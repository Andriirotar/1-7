#include <iostream>
#include <vector>
#include <string>

using namespace std;

// Клас для представлення машини
class Car {
public:
    Car(const string& make, const string& model, int year, double price)
        : make(make), model(model), year(year), price(price) {}

    // Метод для відображення інформації про машину
    void display() const {
        cout << "Make: " << make << ", Model: " << model
             << ", Year: " << year << ", Price: $" << price << endl;
    }

private:
    string make;
    string model;
    int year;
    double price;
};

// Клас для обліку машин в автосалоні
class Showroom {
public:
    void addCar(const Car& car) {
        cars.push_back(car);
    }

    void listCars() const {
        if (cars.empty()) {
            cout << "No cars available." << endl;
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
        cout << "1. Add Car\n2. List Cars\n3. Exit\n";
        cout << "Enter your choice: ";
        cin >> choice;
        cin.ignore();  // Ігноруємо символ нового рядка, залишений у буфері

        if (choice == 1) {
            string make, model;
            int year;
            double price;

            cout << "Enter make: ";
            getline(cin, make);
            cout << "Enter model: ";
            getline(cin, model);
            cout << "Enter year: ";
            cin >> year;
            cout << "Enter price: ";
            cin >> price;
            cin.ignore();  // Ігноруємо символ нового рядка, залишений у буфері

            Car newCar(make, model, year, price);
            showroom.addCar(newCar);
        } else if (choice == 2) {
            showroom.listCars();
        } else if (choice == 3) {
            break;
        } else {
            cout << "Invalid choice. Please try again." << endl;
        }
    }

    return 0;
}
