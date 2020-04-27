## Visual Studio Boost Configuration
* Build boost library running `bootstrap.bat` file
* After Successful build
```sh
...updated 2976 targets...

The Boost C++ Libraries were successfully built!

The following directory should be added to compiler include paths:

    D:\lib\boost

The following directory should be added to linker library paths:

    D:\lib\boost\stage\lib
```
* Configure a visual c++ project
* `Debug` -> `Project Properties` -> `C/C++` -> `General` -> `Additional Include Directories` add
```sh
D:\lib\boost
```
* Again `Debug` -> `Project Properties` -> `Linker` -> `General` -> `Additional Library Directories` add
```
D:\lib\boost\stage\lib
```

* Run a demo code
```c++
#include <boost/thread.hpp>
#include <boost/chrono.hpp>
#include <iostream>

void wait(int seconds)
{
    boost::this_thread::sleep_for(boost::chrono::seconds{ seconds });
}

void thread()
{
    for (int i = 0; i < 5; ++i)
    {
        wait(1);
        std::cout << i << '\n';
    }
}

int main()
{
    boost::thread t{ thread };
    t.join();
}
```
