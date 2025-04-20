# nps::formatter — A Tiny and Simple C++ String Formatter
nps::formatter is a lightweight and header-only string formatting utility for C++, inspired by Python’s str.format(). It brings clean formatting syntax without the overhead of external dependencies or modern C++ baggage.

## Features
- Positional placeholders like {0}, {1}, etc.
- Alignment support: {0,10} (right-aligned), {1,-15} (left-aligned)
- Advanced format specifiers:
    - Float precision: {0:.2f}
    - Boolean as true/false: {0:ba} or {0:boolalpha}
    - Scientific notation (lowercase e): {0:sci} or {0:e}
    - Scientific notation (uppercase E): {0:E}
    - Hexadecimal: {0:x} (lower), {0:X} (upper)
    - Octal: {0:o}
    - Binary: {0:b}
- Escaped braces with {{ and }}
- Type-safe, stream-based formatting
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

    // Functor style usage
    nps::formatter fmt;
    std::cout << fmt("Value: {0,6}, Name: {1,-10}", 42, "Bob") << std::endl;
    // Output: Value:     42, Name: Bob       

    // Float formatting
    std::cout << fmt("Pi: {0:.3f}", 3.14159) << std::endl;
    // Output: Pi: 3.142

    // Boolean formatting
    std::cout << fmt("Flag: {0:ba}", true) << std::endl;
    // Output: Flag: true

    // Scientific notation
    std::cout << fmt("Scientific: {0:sci}, Upper: {0:E}", 12345.678) << std::endl;
    // Output: Scientific: 1.234568e+04, Upper: 1.234568E+04

    // Binary, Octal, Hex
    std::cout << fmt("Binary: {0:b}, Octal: {0:o}, Hex: {0:X}", 255) << std::endl;
    // Output: Binary: 11111111, Octal: 377, Hex: FF
}

}

```

## Format Syntax
| Syntax | Description |
| :--------: | :------- |
| {0} | Inserts the first argument |
| {1,10} | Right-align in 10 characters |
| {2,-15} | Left-align in 15 characters |
| {0:.2f} | Fixed-point float with 2 decimals |
| {0:ba} | Boolean as "true" / "false" |
| {0:sci} | Scientific notation (lowercase e) |
| {0:E} | Scientific notation (uppercase E) |
| {0:x} / {0:X} | Hexadecimal (lower / upper) |
| {0:o} | Octal notation |
| {0:b} | Binary representation (with leading zeros) |
| {{, }} | Escaped literal { or } |

## Why?
Because std::format isn’t fully supported across all compilers yet, and not everyone wants to pull in Boost just to format a string. Sometimes you just want a clean, minimal solution that just works.

### Note
The number of placeholders {} should match the arguments passed. Extra placeholders are ignored gracefully.

Arguments must be streamable via std::ostream (operator<< must be defined).

## License 
MIT — Use it, break it, extend it, embed it in a toaster — just don't blame me if it sets your house on fire.

-------------------

Let me know if you'd like badges, CI examples, or an extended test suite included. Also happy to help you implement advanced format specifiers if you want to level this up a bit.
