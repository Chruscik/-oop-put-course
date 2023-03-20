# This directory contains solution to the lesson-03
#include <string>
#include <iostream>
#include <optional>
#include <utility>
#include <vector>

using namespace std;

class Mouse {
private:
	string color;
public:
	
	Mouse Paint(string newColor) {
		this -> color = std::move(newColor);
		return *this;
	}
string CurentColor() {
	return this->color;
 }
};
class Cat {
private:
	string name;
	std::optional< vector <Mouse>> catsMouse;
public:
	void NameCat(string catsNewName) {
		this->name = std::move(catsNewName);
	}
	void GiveMouse(const Mouse &mouse) {
		this->catsMouse->push_back(mouse);
	}
	Mouse TakeMouse() {
		Mouse takenFromCat = this->catsMouse->back();
		this->catsMouse->pop_back();
		return takenFromCat;
	}
};

int main()
{
	Cat Guapa;
	Guapa.NameCat("Kitty");
	Mouse mouse;
	Mouse newMouse = mouse.Paint("Grey");
	Guapa.GiveMouse(newMouse);
	Mouse deadMouse = Guapa.TakeMouse();
	cout << deadMouse.CurentColor();
	return 0;
}


