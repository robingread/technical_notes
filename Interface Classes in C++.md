tags: #cpp

# Pure Interfaces

This is an example of a pure interface class. The thing that makes it *pure* is that all the methods are `virtual` and have no implementation.

```cpp
class Interface
{
public:
    virtual ~Interface() default;
	virtual int get() = 0;
	virtual void run() = 0;
};
```

Some notes:
- Pure `virutal` functions probably shouldn't be `const` as it would imply that the `override` implementations will also be `const`, which can be hard to guarantee. For example, if you wanted to implement the `Interface::get()` method with a `std::mutex`  making the method  `const` is problematic.

# Interface Implementations

Header file.
```cpp
# pragma once

class Implementation : public Interface
{
public:
    Implementation();
    ~Implementation();
    int get() override;
    int run() override;

private:
    int m_count;
}
```

C++ file:
```cpp
#include "header.hpp"

Implementation::Implementation()
{
    m_count = 0;
}

Implementation::~Implementation()
{
}

int Implementation::get()
{
    return m_count;
}

void Implementation::run()
{
    for (std::size_t i=0; i < 100; ++i)
    {
        m_count++;
    }
}
```

# Using Interfaces

You can now instantiate an instance of an `Implementation` but present it to class and/or functions as an instance of an `Interface`. When doing this we can easily change the instance of the `Implementation` and ensuring that all code is written to run against the `Interface`.

```cpp
#include <memory>

std::shared_ptr<Interface> inter = std::make_shared<Interface>(new Implementation());
```