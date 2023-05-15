# This directory contains solution to the lesson-08
#include <iostream>
#include <vector>

using namespace std;

class Product {
public:
    Product(string name, double price, int id)
        : name_(name), price_(price), id_(id) {}

    string name() const { return name_; }
    double price() const { return price_; }
    int id() const { return id_; }

private:
    string name_;
    double price_;
    int id_;
};

class Customer {
public:
    Customer(string name, string email, int id)
        : name_(name), email_(email), id_(id) {}

    string name() const { return name_; }
    string email() const { return email_; }
    int id() const { return id_; }

private:
    string name_;
    string email_;
    int id_;
};

class Order {
public:
    Order(Customer customer, int id)
        : customer_(customer), id_(id), total_cost_(0.0) {}

    void ProductItems(Product product) {
        products_.push_back(product);
        total_cost_ += product.price();
    }

    double total_cost() const { return total_cost_; }

private:
    Customer customer_;
    int id_;
    vector<Product> products_;
    double total_cost_;
};

int main() {
    
    string product_name;
    double product_price;
    int product_id;
    cout << "Product name: ";
    cin >> product_name;
    cout << "Product price: ";
    cin >> product_price;
    cout << "Product ID: ";
    cin >> product_id;

    Product product1(product_name, product_price, product_id);

    string customer_name;
    string customer_email;
    int customer_id;
    cout << "Customer name: ";
    cin >> customer_name;
    cout << "Customer email: ";
    cin >> customer_email;
    cout << "Customer ID: ";
    cin >> customer_id;

    Customer customer1(customer_name, customer_email, customer_id);

    Order order1(customer1, 1);
    order1.ProductItems(product1);

    cout << "Total cost of order 1: $" << order1.total_cost() << endl;

    return 0;
}
