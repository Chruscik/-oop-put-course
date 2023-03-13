# This directory contains solution to the lesson-02
#include <iostream>

using namespace std;

    class Student{
        public:
        string name;
        int index;
        int term;

    };

    class Table{
        public:
        string material;
        int lenght;
    };

int main(int argc, const char * argv[])
{
   Student MyStudent;
   MyStudent.name='Agata';
   MyStudent.term=3;
   cout<< Mystudent.name <<endl;
   cout<< MyStudent.term <<endl;
   Table MyTable;
   MyTable.material = 'wood';
   MyTable.lenght = 4;
   cout<< MyTable.material <<endl;
   cout<< MyTable.lenght <<endl;
   return 0;

}
