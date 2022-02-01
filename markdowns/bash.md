# Calling an interpreter from Bash

We can call different interpreters with a one-liner solution passed as a command-line parameter directly from `bash`.

Unfortunatelly, we need to escape any dollar signs `$`, double quotes `"` and backslashes `\` in our source code (by adding a backslash `\` before them). This hurts especially in `Perl` and `PHP`, where all variable names start with a `$` sign... At least, in some languages single quotes `'` can be used instead of double quotes `"` (although in `PHP` with slightly different meaning).

_Note: All the examples provided would try to read the test cases as input. That would not work on `Tech.io`, therefore these coding examples are not runnable here. You can try them out in the CG IDE for the [Rubik puzzle](https://www.codingame.com/training/medium/rubik%C2%AE)._

## Base solution

My base solution for the sample puzzle is 34 characters long in Bash.

```sh
# ===== Bash
#   length = base [34] = 34 chars
read n;echo $((n>1?6*n*(n-2)+8:1))
```

## Perl

```sh
# ===== to Perl from Bash
#   length = 9 + base [38] + #vars [4] = 51 chars
#   $ in variable names must be escaped...
perl -e"my\$n=<STDIN>;print\$n>1?6*\$n*(\$n-2)+8:1"
```

My Perl solution is 38 chars. Calling the interpreter adds 9 chars, escaping adds another 4 extra chars in this tiny example.

## PHP

```sh
# ===== to PHP from Bash
#   length = 8 + base [41] + #vars [4] = 53 chars
#   $ in variable names must be escaped...
php -r"\$n=fgets(STDIN);echo\$n>1?6*\$n*(\$n-2)+8:1;"
```

My PHP solution is 41 chars. Calling the interpreter adds 8 chars, escaping adds 4.

## Python

```sh
# ===== to Python from Bash
#   length = 12 + base [47] = 59 chars
#   use python instead of python3 to invoke Python 2.x
python3 -c"n=int(input());print(6*n*(n-2)+8 if n>1 else 1)"
```

My Python solution is 47 chars. Calling the interpreter adds 12 chars. Here I did not need any escaping.

_Note: using `python` instead of `python3` saves 1 char, but it still invokes Python 2.x on CG, so your code might not be backwards compatible._

## Ruby

```sh
# ===== to Ruby from Bash
#   length = 24 + base [34] = 58 chars
#   calling ruby without the full path no longer works...
/usr/local/bin/ruby -e"n=gets.to_i;puts n>1?6*n*(n-2)+8:1"
```

My Ruby solution is 34 chars.
Currently `ruby` seems to be not in the `$PATH` on CG, so we need to add full path which costs 24 chars for invoking the interpreter.

## Coming next...

Starting from `bash` is not always what we need. How to do similar system calls from other languages?
