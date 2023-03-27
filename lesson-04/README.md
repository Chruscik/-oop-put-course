# This directory contains solution to the lesson-04
#include<iostream>
#include<string>

using namespace std;

class Temperature {
private:
	double Celsius;
	double Farenheit;
public:
	double CelsiusValue() { return this->Celsius; };
	double FarenheitValue() { return this->Farenheit; };
	Temperature() { this->Celsius = 0.0; this->Farenheit = 32; };
	Temperature(double tem) { this->Celsius = tem; this->Farenheit = tem * 9 / 5 + 32; };
	Temperature(float tem) : Temperature(static_cast<double>(tem)) {};
	Temperature(int tem) : Temperature(static_cast<double>(tem)) {};
	Temperature(std::string tem) : Temperature(std::stod (tem)) {};

};

int main()
{
	Temperature defaultCelsius;
	Temperature doubleCelsius(23.45);
	Temperature floatCelsius(56.78);
	Temperature stringCelsius("78.89");
	Temperature intCelsius(10);
	std::cout << defaultCelsius.CelsiusValue() << std::endl;
	std::cout << doubleCelsius.CelsiusValue() << std::endl;
	std::cout << floatCelsius.CelsiusValue() << std::endl;
	std::cout << stringCelsius.CelsiusValue() << std::endl;
	std::cout << intCelsius.CelsiusValue() << std::endl;
	std::cout << doubleCelsius.FarenheitValue() << std::endl;
	

	return 0;
}
