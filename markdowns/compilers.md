# Calling a compiler from Bash

We can also use a `bash` script to generate our source code, save it to a file, compile it, and run the compiled program.

* The same approach works also for interpreters, although it might be simpler to send the input source directly to the interpreter as a command line parameter (as we did earlier), instead of saving it to an interim file.
* For a few languages I still don't know the proper command line for CG. So `C#`, `F#`, `Java`, `Kotlin`, `Objective-C` and `VB.NET` are currently not working,
    * _give me a PM or PR if you know it..._
* Syntax highlighting is not working for the embedded language.
* I will exclude the embedded code in some of the examples, focusing only on the 'running the compiler' part.

## C

```sh
# ===== to C from Bash
# also works without the include line (with warnings)
cat > sol.c << EOF
#include <stdio.h>
int main(){int n;scanf("%d",&n);printf("%d\n",(n>1?6*n*(n-2)+8:1));}
EOF
gcc -o sol sol.c
./sol
```

This is still our sample puzzle solution, now in C.

## C\#

```sh
# ===== to C# from Bash
# not working. Also I could not suppress the dotnet welcome message...
cat > sol.cs << EOF
using System;class Solution{static void Main(string[] args){
int n=int.Parse(Console.ReadLine());Console.WriteLine(n>1?6*n*(n-2)+8:1);}}
EOF
cat > sol.csproj << EOF
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
    <OutputPath>.</OutputPath>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
    <PublishTrimmed>true</PublishTrimmed>
    <PublishReadyToRun>true</PublishReadyToRun>
    <PublishSingleFile>true</PublishSingleFile>
    <RuntimeIdentifier>linux-x64</RuntimeIdentifier>
  </PropertyGroup>
</Project>
EOF
export DOTNET_NOLOGO=true
/opt/coderunner/dotnetcore/sdk/dotnet publish sol.csproj --nologo --runtimeconfig /opt/coderunner/dotnetcore/cg/bin/Answer.runtimeconfig.json >&2
./sol
```

## C++

```sh
# ===== to C++ from Bash
cat > sol.cpp << EOF
#include <iostream>
int main(){int n;std::cin>>n;std::cout<<(n>1?6*n*(n-2)+8:1)<<"\n";}
EOF
g++ -o sol -x c++ sol.cpp
./sol
```

## Clojure

```sh
# ===== to Clojure from Bash
# not working...
cat > sol.clj << EOF
(ns Solution (:gen-class))
(defn -main [& args]
(let [N (read)]
(println (if (> N 1) (+ (* (* 6 N) (- N 2)) 8) 1))))
EOF
java -cp /opt/coderunner/clojure/clojure.jar:/opt/coderunner/clojure/spec.alpha.jar:/opt/coderunner/clojure/core.specs.alpha.jar:/tmp/ clojure.main sol.clj
```

## D

```sh
# ===== to D from Bash
cat > sol.d << EOF
import std.stdio;void main(){int n;readf!"%d"(n);writeln(n>1?6*n*(n-2)+8:1);}
EOF
/opt/coderunner/dlang/dmd/linux/bin64/dmd -defaultlib=libphobos2.so -L-rpath=/opt/coderunner/dlang/dmd/linux/lib64/ sol.d
./sol
```

## Dart

```sh
# ===== to Dart from Bash
cat > sol.dart << EOF
import 'dart:io';
String readLineSync(){String? s=stdin.readLineSync();return s==null?'':s;}
void main(){int n=int.parse(readLineSync());print(n>1?6*n*(n-2)+8:1);}
EOF
/usr/local/dart-sdk/bin/dart sol.dart
```

## F\#

```sh
# ===== to F# from Bash
#   NOT WORKING!
cat > sol.fs << EOF
open System
let N = int(Console.In.ReadLine())
let mutable ans = 0
if (N = 1) then
    ans <- 1
else
    ans <- 6 * N * (N - 2) + 8
printfn "%i" ans
EOF
/opt/coderunner/dotnetcore/sdk/dotnet fsi sol.fs
```

## Go

```sh
# ===== to Go from Bash
cat > sol.go << EOF
package main;import"fmt";
func main(){var n int;fmt.Scan(&n);var a int=1;if(n>1){ans=6*n*(n-2)+8};fmt.Println(a)}
EOF
/opt/coderunner/go/bin/go run sol.go
```

## Groovy

```sh
# ===== to Groovy from Bash
cat > sol.groovy << EOF
n=new Scanner(System.in).nextInt();println(n>1?6*n*(n-2)+8:1)
EOF
groovy /tmp/sol.groovy
```

## Haskell

```sh
# ===== to Haskell from Bash
cat > sol.hs << EOF
import System.IO
main=do
  inp <- getLine
  let n = read inp
  print (if (n>1) then 6*n*(n-2)+8 else 1)
EOF
ghc sol.hs -v0
./sol
```

## Java

```sh
# ===== to Java from Bash
cat > sol.java << EOF
import java.util.*;
class Solution {
    public static void main(String args[]) {
        int n = (new Scanner(System.in)).nextInt();
        System.out.println(n>1?6*n*(n-2)+8:1);
    }
}
EOF
java sol.java
```

## JavaScript

```sh
# ===== to JavaScript from Bash
cat > sol.js << EOF
const n=parseInt(readline());console.log(n>1?6*n*(n-2)+8:1)
EOF
/opt/coderunner/nodejs/bin/node -r /codemachine/lib/javascript/internal/polyfill.js /tmp/sol.js
```

## Kotlin

```sh
# ===== to Kotlin from Bash
#   NOT WORKING!
cat > sol.kt << EOF
import java.util.*
fun main() {
    val n = Scanner(System.in).nextInt()
    var ans = 1
    if (n > 1) {
        ans = 6 * n * (n - 2) + 8
    }
    println(ans)
}
EOF
/opt/coderunner/kotlin/kotlinc/bin/kotlinc -include-runtime -d sol.jar sol.kt 
java -jar sol.jar
```

## Lua

```sh
# ===== to Lua from Bash
cat > sol.lua << EOF
n = tonumber(io.read())
if (n > 1) then
    a=6*n*(n-2)+8
else
    a=1
end
print(a)
EOF
lua sol.lua
```

## Objective-C

```sh
# ===== to Objective-C from Bash
#   NOT WORKING!
cat > sol.m << EOF
#include <Foundation/Foundation.h>
int main(){int n;scanf("%d",&n);
printf([@"%d\n" UTF8String],(n>1?6*n*(n-2)+8:1));}
EOF
clang `gnustep-config --objc-flags` `gnustep-config --objc-libs` -Wno-everything sol.m -o sol
./sol
```

## OCaml

```sh
# ===== to OCaml from Bash
cat > sol.ml << EOF
let n = int_of_string (input_line stdin) in
let ans = if (n == 1) then 1 else (6 * n * (n - 2) + 8) in
print_endline (string_of_int ans);
EOF
/usr/local/bin/ocamlopt sol.ml -o sol
./sol
```

## Pascal

```sh
# ===== to Pascal from Bash
cat > sol.pas << EOF
// ...
EOF
fpc -v0 sol.pas >a.txt
./sol
```

## Rust

```sh
# ===== to Rust from Bash
cat > sol.rs << EOF
// ...
EOF
/usr/local/bin/rustc sol.rs
./sol
```

## Scala

```sh
# ===== to Scala from Bash
cat > sol.scala << EOF
import scala.util._
import scala.io.StdIn._

object Solution extends App {
    val N = readInt
    var ans = 0
    if (N > 1) {
        ans = 6 * N * (N - 2) + 8;
    } else {
        ans = 1;
    }
    println(ans)
}
EOF
/usr/local/share/scala/bin/scala -cp . sol.scala
```

## Swift

```sh
# ===== to Swift from Bash
cat > sol.swift << EOF
// ...
EOF
/opt/coderunner/swift/usr/bin/swift sol.swift

```

## TypeScript

```sh
# ===== to TypeScript from Bash
cat > sol.ts << EOF
// ...
EOF
/opt/coderunner/nodejs/bin/node -r /codemachine/lib/javascript/internal/polyfill.js -r /opt/coderunner/nodejs/lib/node_modules/source-map-support/register /tmp/sol.ts
```

## VB .NET

```sh
# ===== to VB.NET from Bash
#   NOT WORKING!
cat > sol.vb << EOF
// ...
EOF
# ???
```

## +1 bonus: COBOL

```sh
# ===== to COBOLfrom Bash
# code not ready...
cat > ./sol.cob << EOF
000100 IDENTIFICATION DIVISION.
000200 PROGRAM-ID. sol.
       ENVIRONMENT DIVISION.
       DATA DIVISION.
       WORKING-STORAGE SECTION.
           01 n PIC 9(5) VALUE 0.
           01 a PIC 9(5) VALUE 1.
000300 PROCEDURE DIVISION.
000400     ACCEPT n
000500 IF n > 1
000600     a = 6 * n *(n - 2) + 8
000700 ELSE
000800     a = 1
000900 END-IF.
001000 DISPLAY "Hello, World!".
001100 STOP RUN.
EOF
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/opt/coderunner/cobol/lib/
/opt/coderunner/cobol/bin/cobc -L opt/coderunner/cobol/lib/ -x sol.cob
./sol
```

While `Cobol` is officially not supported on CG, the compiler is still available on the virtual machine...

## +2 bonus: FORTRAN

```sh
# ===== to FORTRAN from Bash
cat > ./sol.f90 << EOF
program sol
  INTEGER :: n, a
  READ (*,*) n
  IF (n > 1) THEN
    a = 6*n*(n-2)+8
  ELSE
    a = 1
  END IF
  WRITE(*, '(I0)') a
end program sol
EOF
gfortran sol.f90 -o sol
./sol
```

While `Fortran` is officially not supported on CG, the compiler is still available on the virtual machine...

## +2 extra: Bash

It does not make any sense, but for the sake of completeness:

Another `bash` script can also be created and executed from the source script.

```sh
# ===== to Bash from Bash
cat > ./sol.sh << EOF
# ...
EOF
chmod +x sol.sh
./sol.sh
```

## Coming next...

Let's wrap up this playground by invoking all the compilers / runtimes to get their version numbers.
