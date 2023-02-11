#include<iostream>
#include<conio.h>
#include"Drone.h"
using namespace std;
int Drone::id = 0;
Drone::Drone()
{
id++;
capacity = 0.0;
current_load = 0.0;
}
Drone::Drone(double capacity, double current_load)
{
id++;
this->capacity = capacity;
this->current_load = current_load;
}
Drone::~Drone()
{
capacity = 0.0;
current_load = 0.0;
}
Drone Drone:: operator + (Drone obj)
{
Drone res;
//res.id = id + obj.id;
res.capacity = capacity + obj.capacity;
res.current_load = current_load + obj.current_load;
return res;
}
//https://stackoverflow.com/questions/12802536/c-multiple-definitions-of-operator
ostream& operator<<(ostream& out, const Drone& d) {
return out << "Drone member data: " << d.id << ", " << d.capacity << ", " <<
d.current_load << endl;
}
int Package::id = 0;
Package::Package()
{
id++;
weight = 0.0;
}
Package::Package(double weight)
{
id++;
this->weight = weight;
}
Package::~Package()
{
weight = 0.0;
}
void Package::getdata()
{
cin >> weight;
}
double Package::putdata()
{
return weight;
}
Package Package:: operator + (Package obj)
{
Package res;
res.weight = weight + obj.weight;
return res;
}
ostream& operator<<(ostream& out, const Package& p) {
return out << p.id << " " << p.weight << endl;
}
int Route::id = 0;
Route::Route(Package p1, char R[])
{
id++;
pag = p1;
for (int i = 0; i < 20; i++)
Rutway[i] = R[i];
}
Route::~Route()
{
id = 0;
}
ostream& operator<<(ostream& out, const Route& p) {
return out << "Route member data: " << p.pag << endl;
}
int main()
{
double capacity, current_load;
do
{
do
{
cout << "Enter The capacity of a drone should be a positive number : ";
cin >> capacity;
} while (capacity <= 0);
cout << "Enter current_load less than capacity: ";
cin >> current_load;
} while (current_load > capacity);
Drone ob1(capacity, current_load);
cout << ob1 << endl;
//https://www.geeksforgeeks.org/array-of-objects-in-c-with-examples/
Package p1;
Package p2;
Package p3;
Package p4;
Package p5;
bool weighterror = false;
do
{
Package total;
cout << "Enter Package1 weight : ";
p1.getdata();
cout << "Enter Package2 weight : ";
p2.getdata();
total = total + p1;
if ((total.putdata() + current_load) > capacity)
{
cout << "Error drone current load plus the weight of the package exceeds
its capacity. " << endl;
cout << "current load plus the weight: " << total.putdata() +
current_load << endl;
cout << "capacity : " << capacity << endl;
weighterror = true;
}
} while (weighterror);
char Rut1[] = { 'A','B','C','D' };
char Rut2[] = { 'X','Y','Z' };
Route R1(p1, Rut1);
for (int i = 0; i < 4; i++)
{
cout << " p1 in station : " << Rut1[i];
cin.get();
}
cout <<"\np1 delivery "<< endl;
Route R2(p2, Rut2);
for (int i = 0; i < 3; i++)
{
cout << " p2 in station : " << Rut2[i];
cin.get();
}
cout << "\np2 delivery " << endl;
return 0;
}