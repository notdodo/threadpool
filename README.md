# ThreadPool
A very fast and lightweight C++14 thread pool library (general purpose)

# Example
The library is very easy to use: just `#include` it to your project, create the object `ThreadPool pool(_numberofcores)` and add tasks to pool using `AddTask` functions.

```c++
#include "ThreadPool.h"
#include <iostream>

int main(int argc, char **argv) {
	// number of task to exec
	const int TASKS=100000;

	ThreadPool pool(std::thread::hardware_concurrency() + 1);
	for(int i = 0; i < TASKS; i++)
		pool.AddTask([i]{ std::cout << "I'm task # " << i << " doing some stuffs" << std::endl; });

	// wait for all tasks to finish, not necessary in this case: when `pool` goes out of scope it will automatically call `JoinAll`.
	pool.JoinAll();
	return 0;
}
```

### Development

	Add support for `future`
	Add support for multitemplate functions
