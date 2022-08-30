# Checking the compiler / runtime versions

The [CG FAQ](https://www.codingame.com/playgrounds/40701/help-center/languages-versions) lists all the language / compiler / interpeter versions provided by CG.
But we can also check them easily directly. By copying the script below to the CG IDE for any puzzle (with `Bash` as selected language) it will print out the version numbers to the error log. This is not particularly useful, I put it here only because the script is a nice summary of where all the compilers are located (if not in the `$PATH`) on the CG virtual machine.

* CG and `Tech.io` are using different virtual machines. So below script works only in the CG IDE and not runnable here.

## Bash script

```bash
# ===== run from Bash
echo "=== BASH ===" >&2
bash --version  | head -1 >&2
echo "=== C ===" >&2
gcc --version | head -1 >&2
echo "=== C# ===" >&2
printf ".NET Core " >&2 ; /opt/coderunner/dotnetcore/sdk/dotnet --version | head -1 >&2
echo "=== C++ ===" >&2
g++ --version | head -1 >&2
echo "=== CLOJURE ===" >&2
java -cp /opt/coderunner/clojure/clojure.jar:/opt/coderunner/clojure/spec.alpha.jar:/opt/coderunner/clojure/core.specs.alpha.jar:/tmp/ clojure.main | head -1 >&2
echo "=== D ===" >&2
/opt/coderunner/dlang/dmd/linux/bin64/dmd --version | head -1 >&2
echo "=== DART ===" >&2
/usr/local/dart-sdk/bin/dart --version | head -1 >&2
echo "=== F# ===" >&2
printf ".NET Core " >&2 ; /opt/coderunner/dotnetcore/sdk/dotnet --version | head -1 >&2
echo "=== GO ===" >&2
/opt/coderunner/go/bin/go version | head -1 >&2
echo "=== GROOVY ===" >&2
groovy --version >&2
echo "=== HASKELL ===" >&2
ghc --version >&2
echo "=== JAVA ===" >&2
java --version | head -1 >&2
echo "=== JAVASCRIPT ===" >&2
printf "Node.js " >&2 ; /opt/coderunner/nodejs/bin/node --version >&2
echo "=== KOTLIN ===" >&2
/opt/coderunner/kotlin/kotlinc/bin/kotlinc -version >&2
echo "=== LUA ===" >&2
lua -v >&2
echo "=== OBJECTIVE-C ===" >&2
clang --version | head -1 >&2
echo "=== OCAML ===" >&2
/usr/local/bin/ocamlopt -v | head -1 >&2
echo "=== PASCAL ===" >&2
printf "Free Pascal Compiler " >&2 ; fpc -iW >&2
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
printf "Node.js " >&2 ; /opt/coderunner/nodejs/bin/node --version >&2
printf "Typescript Compiler " >&2 ; /opt/coderunner/nodejs/bin/node /opt/coderunner/typescript/tsc/node_modules/typescript/bin/tsc --version | head -2 | tail -1 >&2
echo "=== VB.NET ===" >&2
printf ".NET Core " >&2 ; /opt/coderunner/dotnetcore/sdk/dotnet --version | head -1 >&2
echo "=== EXTRA: COBOL ===" >&2
/opt/coderunner/cobol/bin/cobc --version | head -1 >&2
echo "=== EXTRA: FORTRAN ===" >&2
gfortran --version | head -1 >&2
echo "=== EXTRA: R ===" >&2
/opt/coderunner/R/bin/R --version | head -1 >&2
```

## Sample output (on CG)

(as of _April 2022_)

```txt
=== BASH ===
GNU bash, version 5.1.16(1)-release (x86_64-pc-linux-gnu)
=== C ===
gcc (Debian 11.2.0-20) 11.2.0
=== C# ===
.NET Core 3.1.201
=== C++ ===
g++ (Debian 11.2.0-20) 11.2.0
=== CLOJURE ===
Clojure 1.11.1
=== D ===
DMD64 D Compiler v2.099.1
=== DART ===
Dart SDK version: 2.16.2 (stable) (Tue Mar 22 13:15:13 2022 +0100) on "linux_x64"
=== F# ===
.NET Core 3.1.201
=== GO ===
go version go1.18.1 linux/amd64
=== GROOVY ===
Groovy Version: 3.0.8 JVM: 11.0.2 Vendor: Oracle Corporation OS: Linux
=== HASKELL ===
The Glorious Glasgow Haskell Compilation System, version 8.4.3
=== JAVA ===
openjdk 11.0.2 2019-01-15
=== JAVASCRIPT ===
Node.js v16.14.2
=== KOTLIN ===
info: kotlinc-jvm 1.5.0 (JRE 11.0.2+9)
=== LUA ===
Lua 5.4.4  Copyright (C) 1994-2022 Lua.org, PUC-Rio
=== OBJECTIVE-C ===
Debian clang version 13.0.1-3+b2
=== OCAML ===
The OCaml native-code compiler, version 4.12.0
=== PASCAL ===
Free Pascal Compiler 3.2.2
=== PERL ===
This is perl 5, version 34, subversion 0 (v5.34.0) built for x86_64-linux-gnu-thread-multi
=== PHP ===
PHP 7.3.9 (cli) (built: Nov 25 2019 15:05:20) ( NTS )
=== PYTHON ===
Python 3.9.12
=== RUBY ===
ruby 3.1.2p20 (2022-04-12 revision 4491bb740a) [x86_64-linux]
=== RUST ===
rustc 1.60.0 (7737e0b5c 2022-04-04)
=== SCALA ===
Scala code runner version 2.13.5 -- Copyright 2002-2020, LAMP/EPFL and Lightbend, Inc.
=== SWIFT ===
Swift version 5.3.3 (swift-5.3.3-RELEASE)
=== TYPESCRIPT ===
Node.js v16.14.2
Typescript Compiler Version 4.6.3
=== VB.NET ===
.NET Core 3.1.201
=== EXTRA: COBOL ===
cobc (GnuCOBOL) 3.1.2.0
=== EXTRA: FORTRAN ===
GNU Fortran (Debian 11.2.0-20) 11.2.0
=== EXTRA: R ===
R version 3.6.3 (2020-02-29) -- "Holding the Windsock"
```

## That's all folks!

Thanks for your time!

PS: Check out my other playgrounds on `Tech.io`:

* [A Babel of Languages on CodinGame](https://www.codingame.com/playgrounds/56997/a-babel-of-languages-on-codingame/intro)
* [PHP Dev Tools (for CodinGame or elsewhere)](https://www.codingame.com/playgrounds/77580/php-dev-tools-for-codingame-or-elsewhere/intro)
