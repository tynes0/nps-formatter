# nps::formatter — A Tiny and Simple C++ String Formatter
nps::formatter is a lightweight and header-only string formatting utility for C++, inspired by Python’s str.format(). It brings clean formatting syntax without the overhead of external dependencies or modern C++ baggage.

## Features
- Positional placeholders like {0}, {1}, etc.
- Alignment support: {0,10} (right-aligned) or {1,-15} (left-aligned)
- Basic formatting field support (e.g., {0:.2f}) — easily extendable
- Escaped braces with {{ and }}
- Compile-time type safety using templates
- Works with C++11 and above
- No external dependencies

##  Setup
Simply include the header file. No linking, no nonsense.
```cpp
#include "formatter.h"
```

## Usage

```cpp
#include <iostream>
#include "formatter.h"

int main() {
    std::string result = nps::formatter::format("Hello {0}, your score is {1}", "Alice", 95);
    std::cout << result << std::endl;
    // Output: Hello Alice, your score is 95

    // Or use the functor style:
    nps::formatter fmt;
    std::cout << fmt("Value: {0,6}, Name: {1,-10}", 42, "Bob") << std::endl;
    // Output: Value:     42, Name: Bob       
}

```

## Format Syntax
| Syntax | Description |
| :--------: | :------- |
| {0} | Inserts the first argument |
| {1,10} | Inserts the second argument, right-aligned in 10 chars |
| {2,-15} | Inserts the third argument, left-aligned in 15 chars |
| {{ and }} | Escapes braces |

## Why?
Because std::format isn’t fully supported across all compilers yet, and not everyone wants to pull in Boost just to format a string. Sometimes you just want a clean, minimal solution that just works.

### Note
The number of placeholders {} should match the arguments passed. Extra placeholders are ignored gracefully.

Arguments must be streamable via std::ostream (operator<< must be defined).

## License 
MIT — Use it, break it, extend it, embed it in a toaster — just don't blame me if it sets your house on fire.

-------------------

Let me know if you'd like badges, CI examples, or an extended test suite included. Also happy to help you implement advanced format specifiers if you want to level this up a bit.
