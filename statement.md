# Welcome!

This C++ template lets you get started quickly with a simple one-page playground.

```C++ runnable
#include <iostream>

struct Shape
{
  virtual Shape* duplicate()
  {
    std::cout << "SHAPE" << std::endl;
    return new Shape;
  }
  virtual ~Shape() {}
};

struct Box : public Shape
{
  virtual Box* duplicate()
  {
    std::cout << "BOX" << std::endl;
    return new Box;
  }
};

int main(int argc, char** argv) 
{ 
  Shape* s1 = new Box;

  Shape* s2 = s1->duplicate();

  delete s1;
  delete s2;
  return 0; 
}
