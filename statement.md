# description: 
 The code is ill-formed.  Virtual functions must have a unique "final overrider" that overrides all other instances of that function in its inheritance heirarchy.  In this case neither Box::print nor Sphere::print override each other, so the condition is not met and the GeoDisc class is ill-formed.
```C++ runnable
#include <iostream>

struct Shape
{
  virtual void print()
  {
    std::cout << "SHAPE" << std::endl;
  }
  virtual ~Shape() {}
};

struct Box : public virtual Shape
{
  void print()
  {
    std::cout << "BOX" << std::endl;
  }
};

struct Sphere : public virtual Shape
{
  void print()
  {
    std::cout << "SPHERE" << std::endl;
  }
};

struct GeoDisc : public Box, public Sphere
{
};

int main(int argc, char** argv)
{
  Shape* s = new GeoDisc;

  s->print();

  delete s;

  return 0;
}
```

