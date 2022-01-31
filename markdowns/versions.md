# Checking the compiler / runtime versions

The [FAQ](https://www.codingame.com/playgrounds/40701/help-center/languages-versions) lists all the language / compiler / interpeter versions provided by CG.
But we can also check them easily directly. By copying the script below to the CG IDE for any puzzle (with `Bash` as selected language) it will print out the version numbers to the error log. This is not particularly useful, I put it here only because the script is a nice summary of where all the compilers are located (if not in the PATH) on the CG runtime image.

* For a few languages I still don't have the proper command line to run on CG. So `C#`, `Clojure`, `F#`, `Groovy`, `Kotlin` and `VB.NET` are currently missing.
    * _give me a PM or PR if you know it..._

## Bash script

```sh
# ===== run from Bash
echo "=== BASH ===" >&2
bash --version  | head -1 >&2
echo "=== C ===" >&2
gcc --version | head -1 >&2
echo "=== C# ===" >&2
echo "****************  NOT WORKING! ****************" >&2
# /opt/coderunner/dotnet/bin/dotnet --version | head -1 >&2
echo "=== C++ ===" >&2
g++ --version | head -1 >&2
echo "=== CLOJURE ===" >&2
echo "****************  NOT WORKING! ****************" >&2
#
echo "=== D ===" >&2
/opt/coderunner/dlang/dmd/linux/bin64/dmd --version | head -1 >&2
echo "=== DART ===" >&2
/usr/local/dart-sdk/bin/dart --version | head -1 >&2
echo "=== F# ===" >&2
echo "****************  NOT WORKING! ****************" >&2
#
echo "=== GO ===" >&2
/opt/coderunner/go/bin/go version | head -1 >&2
echo "=== GROOVY ===" >&2
echo "****************  NOT WORKING! ****************" >&2
# /opt/coderunner/groovy/bin/groovy --help >&2
echo "=== HASKELL ===" >&2
ghc --version >&2
echo "=== JAVA ===" >&2
java --version | head -1 >&2
echo "=== JAVASCRIPT ===" >&2
echo "node " >&2 ; /opt/coderunner/nodejs/bin/node --version >&2
echo "=== KOTLIN ===" >&2
echo "****************  NOT WORKING! ****************" >&2
# /opt/coderunner/kotlin/kotlinc/bin/kotlinc -version >&2
echo "=== LUA ===" >&2
lua -v >&2
echo "=== OBJECTIVE-C ===" >&2
clang --version | head -1 >&2
echo "=== OCAML ===" >&2
/usr/local/bin/ocamlopt -v | head -1 >&2
echo "=== PASCAL ===" >&2
fpc -iW >&2
echo "=== PERL ===" >&2
perl --version | head -2 | tail -1 >&2
echo "=== PHP ===" >&2
php --version | head -1 >&2
echo "=== PYTHON ===" >&2
python3 --version >&2
echo "=== RUBY ===" >&2
/usr/local/bin/ruby -v >&2
echo "=== RUST ===" >&2
/usr/local/bin/rustc --version >&2
echo "=== SCALA ===" >&2
/usr/local/share/scala/bin/scala --version >&2
echo "=== SWIFT ===" >&2
/opt/coderunner/swift/usr/bin/swift --version | head -1 >&2
echo "=== TYPESCRIPT ===" >&2
echo "node " >&2 ; /opt/coderunner/nodejs/bin/node --version >&2
echo "=== VB.NET ===" >&2
echo "****************  NOT WORKING! ****************" >&2
#
echo "=== EXTRA: FORTRAN ===" >&2
gfortran --version |head -1 >&2
```

## Sample output

(as of February 2022)

```txt
=== BASH ===
GNU bash, version 5.1.4(1)-release (x86_64-pc-linux-gnu)
=== C ===
gcc (Debian 10.2.1-6) 10.2.1 20210110
=== C# ===
****************  NOT WORKING! ****************
=== C++ ===
g++ (Debian 10.2.1-6) 10.2.1 20210110
=== CLOJURE ===
****************  NOT WORKING! ****************
=== D ===
DMD64 D Compiler v2.096.1
=== DART ===
Dart SDK version: 2.12.4 (stable) (Thu Apr 15 12:26:53 2021 +0200) on "linux_x64"
=== F# ===
****************  NOT WORKING! ****************
=== GO ===
go version go1.17.1 linux/amd64
=== GROOVY ===
****************  NOT WORKING! ****************
=== HASKELL ===
The Glorious Glasgow Haskell Compilation System, version 8.4.3
=== JAVA ===
openjdk 11.0.2 2019-01-15
=== JAVASCRIPT ===
node
v14.16.1
=== KOTLIN ===
****************  NOT WORKING! ****************
=== LUA ===
Lua 5.4.3  Copyright (C) 1994-2021 Lua.org, PUC-Rio
=== OBJECTIVE-C ===
Debian clang version 11.0.1-2
=== OCAML ===
The OCaml native-code compiler, version 4.12.0
=== PASCAL ===
3.2.0
=== PERL ===
This is perl 5, version 32, subversion 1 (v5.32.1) built for x86_64-linux-gnu-thread-multi
=== PHP ===
PHP 7.3.9 (cli) (built: Nov 25 2019 15:05:20) ( NTS )
=== PYTHON ===
Python 3.9.9
=== RUBY ===
ruby 3.0.1p64 (2021-04-05 revision 0fb782ee38) [x86_64-linux]
=== RUST ===
rustc 1.51.0 (2fd73fabe 2021-03-23)
=== SCALA ===
Scala code runner version 2.13.5 -- Copyright 2002-2020, LAMP/EPFL and Lightbend, Inc.
=== SWIFT ===
Swift version 5.3.3 (swift-5.3.3-RELEASE)
=== TYPESCRIPT ===
node
v14.16.1
=== VB.NET ===
****************  NOT WORKING! ****************
=== EXTRA: FORTRAN ===
GNU Fortran (Debian 10.2.1-6) 10.2.1 20210110
```

## That's all folks

PS: Check out my other playground on `Tech.io`: [A Babel of Languages on CodinGame](https://www.codingame.com/playgrounds/56997/a-babel-of-languages-on-codingame/intro)
