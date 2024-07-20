# Calling an interpreter from other languages

In most (if not all) languages there is a built-in function or language construct which allows to execute an external program directly from our code. It works by sending a command line (with any arguments) to the operating system - which is in case of the CG runtime Linux. That means we can do anything as if we were in a `bash` script.

Let's see some examples by calling our sample solution in Python from different languages.
As the command line is given as a string, usually we need to escape the double quotes `"` in the embedded source code.

## C

```c
// ===== to Python from C
//   length = 19 + 12 (if python) + base + #quotes = 80 chars
main(){system("python3 -c\"n=int(input());print(6*n*(n-2)+8 if n>1 else 1)\"");}
```

## C++

```c++
// ===== to Python from C++
//   length = 38 + 12 (if python) + base + #quotes = 99 chars
#include<stdlib.h>
main(){system("python3 -c\"n=int(input());print(6*n*(n-2)+8 if n>1 else 1)\"");}
```

The C solution works here also, ut an extra include line must be added (+19 chars).

## C\#

```cs
// ===== to Python from C#
//   length = 97 + 12 (if python) + base + #quotes = 106 chars
/sing System.Diagnostics;class S{static void Main(){Process.Start(new ProcessStartInfo(
@"python3","-c\"n=int(input());print(6*n*(n-2)+8 if n>1 else 1)\""));}}
```

## Go

```go
// ===== to Python from Go
package main
import (
    "os"
    "os/exec"
)
func main() {
    cmd := exec.Command("python3", "-c", "n=int(input());print(6*n*(n-2)+8 if n>1 else 1)")
    cmd.Stdin = os.Stdin
    cmd.Stdout = os.Stdout
    cmd.Run()
}
```

## Haskell

```haskell
-- ===== to Python from Go
import System.Process
main=callCommand"python3 -c\"n=int(input());print(6*n*(n-2)+8 if n>1 else 1)\""
```

## Java

```java
// ===== to Python from Java
class Solution{public static void main(String a[]){try{(new ProcessBuilder(
"python3", "-c", "n=int(input());print(6*n*(n-2)+8 if n>1 else 1)"
).inheritIO()).start();}catch(Exception e){}}}
```

## Lua

```lua
-- ===== to Python from Lua
--   length = 12 + 12 (if python) + base = 75 chars
os.execute("python3 -c\"n=int(input());print(6*n*(n-2)+8 if n>1 else 1)\"")
```

## Objective-C

```c
// ===== to Python from Objective-C
//   length = 72 + 12 (if python) + base + #quotes = 133 chars
#include <Foundation/Foundation.h>
int main(){system([@"python3 -c\"n=int(input());print(6*n*(n-2)+8 if n>1 else 1)\"" UTF8String]);}
```

## Pascal

```pascal
// ===== to Python from Pascal
program A;{$H+}uses Process;var s:ansistring;begin RunCommand(
'python',['-c','n=int(input());print(6*n*(n-2)+8 if n>1 else 1)']
,s,[poPassInput]);write(s);end.
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

## Rust

```rust
// ===== to Python from Rust
use std::process::Command;fn main(){Command::new("python3").args([
"-c","n=int(input());print(6*n*(n-2)+8 if n>1 else 1)"])
.spawn();}
```

---

## Under construction (not working yet)

Below are system calling code for some other languages, however they are currently not working.

* _Give me a PM or PR if you know how to make them work..._

## D

```d
// ===== to Python from D
//   NOT WORKING!
//   Error: variable `impl` cannot be modified at compile time
import std;auto p=execute(["python3", "-c\"n=int(input());print(6*n*(n-2)+8 if n>1 else 1)\""]);
```

## Coming next...

What to do if our code is much longer then a one-liner?
