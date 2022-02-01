# Calling a compiler from Bash

We can also use a `bash` script to generate our source code, save it to a file, compile it, and run the compiled program.

* The same approach works also for interpreters, although it might be simpler to send the input source directly to the interpreter as a command line parameter (as we did earlier), instead of saving it to an interim file.
* For a few languages I still don't know the proper command line for CG. So `C#`, `Clojure`, `F#`, `Groovy`, `Java`, `Kotlin`, `Objective-C` and `VB.NET` are currently not working,
    * _give me a PM or PR if you know it..._
* Notes: the sample code on this page is not minified. Syntax highlighting is not working for the embedded language.

## C

```sh
# ===== to C from Bash
cat > sol.c << EOF
int main(){int n;scanf("%d",&n);printf("%d\n",(n>1?6*n*(n-2)+8:1));}
EOF
gcc -o sol sol.c
./sol
```

This is still our sample puzzle solution, now in C. I will exclude the embedded code in the remaining examples, focusing on the 'running the compiler' part only.

## C\#

```sh
# ===== to C# from Bash
#   NOT WORKING!
cat > sol.cs << EOF
// ...
EOF
# this worked only before CG moved to .NET Core...
mcs -nologo -out:sol ./sol.cs
mono sol
```

## C++

```sh
# ===== to C++ from Bash
cat > sol.cpp << EOF
// ...
EOF
g++ -o sol -x c++ sol.cpp
./sol
```

## Clojure

```sh
# ===== to Clojure from Bash
#   NOT WORKING!
cat > sol.clj << EOF
; ...
EOF
java -cp /opt/coderunner/clojure/clojure.jar:/opt/coderunner/clojure/spec.alpha.jar:/opt/coderunner/clojure/core.specs.alpha.jar:/tmp/ clojure.main sol.clj
```

## D

```sh
# ===== to D from Bash
cat > sol.d << EOF
// ...
EOF
/opt/coderunner/dlang/dmd/linux/bin64/dmd -defaultlib=libphobos2.so -L-rpath=/opt/coderunner/dlang/dmd/linux/lib64/ sol.d
./sol
```

## Dart

```sh
# ===== to Dart from Bash
cat > sol.dart << EOF
// ...
EOF
/usr/local/dart-sdk/bin/dart sol.dart
```

## F\#

```sh
# ===== to F# from Bash
#   NOT WORKING!
cat > sol.fs << EOF
// ...
EOF
# ???
```

## Go

```sh
# ===== to Go from Bash
cat > sol.go << EOF
// ...
EOF
/usr/local/go/bin/go run sol.go
```

## Groovy

```sh
# ===== to Groovy from Bash
#   NOT WORKING!
cat > sol.groovy << EOF
// ...
EOF
groovy /tmp/sol.groovy
```

## Haskell

```sh
# ===== to Haskell from Bash
cat > sol.hs << EOF
-- ...
EOF
ghc sol.hs -v0
./sol
```

## Java

```sh
# ===== to Java from Bash
#   NOT WORKING!
 > sol.java << EOF
// ...
EOF
java /tmp/sol.java
```

## JavaScript

```sh
# ===== to JavaScript from Bash
cat > sol.js << EOF
// ...
EOF
/opt/coderunner/nodejs/bin/node -r /codemachine/lib/javascript/internal/polyfill.js /tmp/sol.js
```

## Kotlin

```sh
# ===== to Kotlin from Bash
#   NOT WORKING!
cat > sol.kt << EOF
// ...
EOF
/opt/coderunner/kotlin/kotlinc/bin/kotlinc sol.kt -include-runtime -d sol.jar
java -jar sol.jar
```

## Lua

```sh
# ===== to Lua from Bash
cat > sol.lua << EOF
-- ...
EOF
lua sol.lua
```

## Objective-C

```sh
# ===== to Objective-C from Bash
#   NOT WORKING!
cat > sol.m << EOF
// ...
EOF
clang `gnustep-config --objc-flags` `gnustep-config --objc-libs` sol.m -o sol
./sol
```

## OCaml

```sh
# ===== to OCaml from Bash
cat > sol.ml << EOF
(* ... *)
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
#   NOT WORKING!
cat > sol.scala << EOF
// ...
EOF
/usr/local/share/scala/bin/scala -cp /tmp sol.scala
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

## +1 bonus: FORTRAN

```sh
# ===== to FORTRAN from Bash
cat > ./sol.f90 << EOF
! ...
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
