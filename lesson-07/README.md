# This directory contains solution to the lesson-07
#include <iostream>
#include <cmath>
#include <stdexcept>
#include <string>
using namespace std;

class InvalidBaseException : public runtime_error {
public:
	explicit InvalidBaseException(const string& mess)
		:runtime_error(mess) {}
};

class InvalidNumberException : public runtime_error {
public:
	explicit InvalidNumberException(const string& mess)
		:runtime_error(mess) {}
};


class Logarithm {
public:
	Logarithm(double base, double number) {
		base_ = base;
		number_ = number;
	}

	double Calculate() const {

		 
		if ((base_<= 0) || (base_== 1))
		{
			throw InvalidBaseException(" logarithm base must be greater than 0 and not equal to 1");
		}
		
		if (number_ <=0)
		{
			throw InvalidNumberException(" logarithm number must be greater than 0");
		}
		return log(number_) / log(base_);

	}

private:
	double base_;
	double number_;
};

int main() {
	double base, number;
	cout << "Enter the base: ";
	cin >> base;
	cout << "Enter the number: ";
	cin >> number;

	try {
		Logarithm log(base, number);
		double result = log.Calculate();
		cout << "log_" << base << "(" << number << ") = " << result << endl;
	}
	catch (const InvalidBaseException& e) {
		cerr << "Invalid base: " << e.what() << endl;
	}
	catch (const InvalidNumberException& e) {
		cerr << "Invalid number: " << e.what() << endl;
	}
	catch (const exception& e) {
		cerr << "Error: " << e.what() << endl;
	}
	return 0;
}
