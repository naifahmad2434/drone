#pragma once
#ifndef Drone_h
#define Drone_h
#include <iostream>
using namespace std;
class Drone
{
private:
static int id;
double capacity;
double current_load;
public:
Drone();
Drone(double capacity, double current_load);
~Drone();
friend ostream& operator<<(ostream& out, const Drone& d);
Drone operator + (Drone obj);
};
class Package
{
private:
static int id;
double weight;
friend ostream& operator<<(ostream& out, const Package& d);
friend class Route;
public:
Package();
Package(double weight);
~Package();
void getdata();
double putdata();
Package operator + (Package obj);
};
class Route
{
private:
static int id;
Package pag;
char Rutway[20];
public:
Route();
Route(Package p1, char R[]);
~Route();
friend ostream& operator<<(ostream& out, const Route& d);
};
class CargoDrone : public Drone
{
private:
string cargo;
public:
CargoDrone();
CargoDrone(string cargo);
};
#endif