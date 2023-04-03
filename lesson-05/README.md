# This directory contains solution to the lesson-05
#include <iostream>

using namespace std;

class Shape {
public:

    virtual double Surface() = 0;
    virtual double Circuit() = 0;
};

class Rectangle : public Shape {
public:
    Rectangle(double width, double height) { this->width = width; this->height = height; };
    double Surface() {
        return (width * height);
    
    }
    double Circuit() {
        return (2 * width + 2 * height);
    }
private:
    double width;
    double height;
};

class Triangle : public Shape {
public:
    Triangle(double base, double height, double lenght) { this->base = base; this->height = height; this->lenght = lenght; };
    double Surface() {
        return (base * height) / 2;
    }
    double Circuit() {
        return (base + 2 * lenght);
    };
private:
    double base;
    double height;
    double lenght;
};

class Square : public Shape {
public:
    Square(double width) { this->width = width; };
    double Surface() {
        return (width * width);
    }
    double Circuit() {
        return (4*width);
    }
private:
    double width;
};

int main() {
    Rectangle rectangle(4.0, 5.0);
    cout << "Rectangle surface: " << rectangle.Surface() << endl;
    cout << "Rectangle circuit: " << rectangle.Circuit() << endl;


    Triangle triangle(2.0, 2.0, 2.0);
    cout << "Triangle surface: " << triangle.Surface() << endl;
    cout << "Triangle circuit: " << triangle.Circuit() << endl;

    Square square(2.0);
    cout << "Square surface: " << square.Surface() << endl;
    cout << "Square circuit: " << square.Circuit() << endl;
    return 0;
}
