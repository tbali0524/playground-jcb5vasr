# Calling an interpreter from other languages

In most (if not all) languages there is a built-in function or language construct which allows to execute an external program directly from our code. It works by sending a command line (with any arguments) to the operating system - which is in case of the CG runtime Linux. That means we can do anything as if we were in a `bash` script.

Let's see some examples by calling our sample solution in Python from different languages.
As the command line is given as a string, usually we need to escape the double quotes `"` in the embedded source code.

## C\#

```cs
// ===== to Python from C#
//   length = 97 + 12 (if python) + base + #quotes = 106 chars
//   double quotes must be escaped
using System.Diagnostics;class S{static void Main(){Process.Start(new ProcessStartInfo(
@"python3","-c\"n=int(input());print(6*n*(n-2)+8 if n>1 else 1)\""));}}
```

## Lua

```lua
# ===== to Python from Lua
#   length = 12 + 12 (if python) + base = 75 chars
os.execute("python3 -c\"n=int(input());print(6*n*(n-2)+8 if n>1 else 1)\"")
```

## Perl

```perl
# ===== to Python from Perl
#   length = 11 + 12 (if python) + base = 70 chars
system('python3 -c"n=int(input());print(6*n*(n-2)+8 if n>1 else 1)"');
```

## PHP

```php
# ===== to Python from PHP
#   length = 11 + 12 (if python) + base = 70 chars
system('python3 -c"n=int(input());print(6*n*(n-2)+8 if n>1 else 1)"');
```

A slightly shorter alternative is to use the backtick operator:

```sh
echo`python3 -c"n=int(input());print(6*n*(n-2)+8 if n>1 else 1)"`;
```

## Python

Here the example is for calling `ruby`:

```python
# ===== to Ruby from Python
#   length = 23 + 24 (if ruby) + base = 81 chars
import os;os.system('/usr/local/bin/ruby -e"n=gets.to_i;puts n>1?6*n*(n-2)+8:1"')
```

## Ruby

```ruby
# ===== to Python from Ruby
#   length = 10 + 12 (if python) + base = 69 chars
system('python3 -c"n=int(input());print(6*n*(n-2)+8 if n>1 else 1)"')
```

---

## Under construction (not working yet)

Below are system calling code for some other languages, however they are currently not working.

* _Give me a PM or PR if you know how to make them work..._

## C

```c
// ===== to Python from C
//   length = 19 + 12 (if python) + base + #quotes = 80 chars
//   double quotes must be escaped
//   currently BROKEN because of an extra GDB output: [Detaching after vfork from child process X]
main(){system("python3 -c\"n=int(input());print(6*n*(n-2)+8 if n>1 else 1)\"");}
```

This used to work before the latest CG update, but currently breaks any puzzle solution on CG, because the C debugger sends an extra message to the output, ruining the expected puzzle output.

## C++

```c++
// ===== to Python from C++
//   see C section, however below line must be added (+20 chars)
//   currently BROKEN because of an extra GDB output: [Detaching after vfork from child process X]
#include<stdlib.h>
```

The C solution would work (if it weren't broken) also in C++ but we need to add an include file.

## D

```d
// ===== to Python from D
//   NOT WORKING!
//   Error: variable `impl` cannot be modified at compile time
import std;auto p=execute(["python3", "-c\"n=int(input());print(6*n*(n-2)+8 if n>1 else 1)\""]);
```

## Go

```go
// ===== to Python from Go
//   NOT WORKING!
package main
import "os/exec"
func main() {
    cmd := exec.Command("python3", "-c\"n=int(input());print(6*n*(n-2)+8 if n>1 else 1)\"")
    cmd.Run()
}
```

## Java

```java
// ===== to Python from Java
//   NOT WORKING!
class Solution {
    public static void main(String args[]) {
        try {
            ProcessBuilder pb = new ProcessBuilder("python3", "-c", "\"n=int(input());print(6*n*(n-2)+8 if n>1 else 1)\"");
            Process p = pb.start();
            //Runtime.getRuntime().exec("python3 -c\"n=int(input());print(6*n*(n-2)+8 if n>1 else 1)\"");
        } catch (Exception e) {}
    }
}
```

## Objective-C

```c
// ===== to Python from Objective-C
//   length = 72 + 12 (if python) + base + #quotes = 133 chars
//   double quotes must be escaped
//   currently BROKEN because of an extra GDB output: [Detaching after vfork from child process X]
#include <Foundation/Foundation.h>
int main(){system([@"python3 -c\"n=int(input());print(6*n*(n-2)+8 if n>1 else 1)\"" UTF8String]);}
```

## Pascal

```pascal
// ===== to Python from Pascal
//   NOT WORKING!
program A;
{$mode objfpc}{$H+}
uses Process;
var s : ansistring;
begin
    RunCommand('python',['-c"n=int(input());print(6*n*(n-2)+8 if n>1 else 1)"'],s);
end.
```

## Rust

```rust
// ===== to Python from Rust
//   NOT WORKING!
use std::process::Command;
fn main() {
    let p = Command::new("python3")
        .arg("-c\"n=int(input());print(6*n*(n-2)+8 if n>1 else 1)\"")
        .output()
        .expect("");
}
```

## Coming next...

What to do if our code is much longer then a one-liner?
