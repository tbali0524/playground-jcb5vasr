# Swapping languages in CodinGame

___... a.k.a. 'how to use system() calls?'___

This `Tech.io` playground explores how to use a coding language within another language in the context of [CodinGame](https://www.codingame.com/) puzzles.
Topics we will cover:

* Calling an interpreter from `bash`
* Calling an interpreter from other languages
* Calling a compiler from `bash`
* Checking the compiler / runtime versions

## Motivation and usage

CodinGame is about improving coding skills by solving puzzles (and by participating in contests). This playground is really just a sidetrack, a kind of 'hacking passtime'. Some ideas might come in handy, although using `system()` calls is rarely a best practice in real projects.

__It is not meant to encourage you to circumvent the CG language selector__ and to submit a solution in another language than you labeled it.

I personally don't like the usage of `system()` calls at all, especially in _codegolf_, where it made the per language leaderboards rather pointless.
I still have some (<10) older non-bash solo puzzle submissions in `bash`, but I try to replace them with a proper script as I improve my (rather basic) skills in bash.

## Sample puzzle

In many examples I will use my solutions in different languages for a CG community solo puzzle called [Rubik](https://www.codingame.com/training/medium/rubik%C2%AE).
This is one of the simplest and shortest puzzle on CG. It is more an elementary school math question than a coding puzzle. Still, if you don't like spoilers, go and solve it on your own __before__ going to the next page on this playground.

## Contributions welcome

As you will see, this playground is far from complete. For some languages I couldn't figure out the proper syntax yet for the system() call or how to invoke the compiler within the CG runtime.
If you have suggestions for improvements, please:

* send me ([TBali](https://www.codingame.com/profile/08e6e13d9f7cad047d86ec4d10c777500155033)) a __private message__ on CodinGame;
* or give a __pull request__ directly to the [github repo](https://github.com/tbali0524/playground-jcb5vasr) of this playground;
* or just leave a comment here on `Tech.io`.

Regarding __attributions__:

* Some of the ideas here I found in a bunch CG forum posts or chat messages.
* Many command line arguments were taken from a published code by _Westicles_ (a.k.a. _Mrs.GloriaZindlebocker_).
* _abt8601_ contributed many additions and corrections.

## Let's get started!

How to call an interpreter from `bash` with a one-liner code?
