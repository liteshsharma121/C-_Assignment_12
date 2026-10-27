
#include <iostream>
using namespace std;

class Base {
public:
    virtual void display() {
        cout << "Base class" << endl;
    }
};

class Derived : public Base {
public:
    void display() override {
        cout << "Derived class" << endl;
    }
};

int main() {
    cout << "IMPLICIT TYPE CASTING" << endl;
    int a = 25;
    double b = a;
    cout << "Integer value: " << a << endl;
    cout << "Double value: " << b << endl;

    cout << "\nSTATIC_CAST" << endl;
    double x = 27.89;
    int y = static_cast<int>(x);
    cout << "Double value: " << x << endl;
    cout << "Integer value: " << y << endl;

    cout << "\nDYNAMIC_CAST" << endl;
    Base* ptr = new Derived();
    Derived* dptr = dynamic_cast<Derived*>(ptr);
    if (dptr != nullptr) {
        dptr->display();
    }
    delete ptr;

    cout << "\nCONST_CAST" << endl;
    const int value = 50;
    const int* cptr = &value;
    int* mptr = const_cast<int*>(cptr);
    cout << "Original value: " << *cptr << endl;
    cout << "Modified pointer value: " << *mptr << endl;

    cout << "\nREINTERPRET_CAST" << endl;
    int num = 65;
    int* iptr = &num;
    char* c = reinterpret_cast<char*>(iptr);
    cout << "Integer value: " << *iptr << endl;
    cout << "Pointer conversion completed." << endl;

    return 0;
}
