Wrapper for canutils to play nice with ros/rosmod
======================================================

Install Build Tools
-------------------------

```bash
sudo apt-get install python-catkin-tools
```

Build Library:
-------------

```bash
cd
mkdir catkin_ws #if a workspace does not already exist
cd catkin_ws
git clone https://github.com/rosmod/lib-can.git src/lib-can
catkin build lib-can
```

Update Library:
-----------------

```bash
cd ~/catkin_ws
catkin clean lib-can
cd src/lib-can
git pull
cd ..
catkin build lib-can
```


Rosmod Source Library Setup:
-------------------------------

1. In this github repo navigate to [releases](https://github.com/rosmod/lib-can/releases), right click on `can.zip` (not the source code zip!) and select `Copy link address'
2. In a rosmod project, drag in a new source library to the software model
3. Paste the link in the url attribute
4. Name the source library `can`
5. Drag the library into the `set editor` of any component that uses it
6. In the forwards section of the component add 

```c++
extern "C" {
    #include "lib-can/linux/can.h"
	#include "lib-can/linux/can/raw.h"
	#include "lib-can/lib-can.h"
}
```

