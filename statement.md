# description: 
 BOX is printed.  The return type of an overriding virtual function must have either the same type as the function it is overriding or both functions must return a pointer or reference with the same cv-qualifications whereby the class pointed or reffered to in the overridden function is an unambiguous and accessible direct or indirect base class of the class pointed or referred to in the overriding function.

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
