# Why Go in Science?

Raul Mera A.


_Please don’t see this as me wanting to start a debate. For starters, I don’t claim to be even close to an expert (I’m a Chemist!). I merely aim for people to understand my choice, and see that it is at least somewhat justified and not just me being contrarian._


Python is ‘the’ science language nowadays. This wasn’t always the case. When I first started writing programs in Python, around 2004, there were a few visionaries like Konrad Hinsen and the late (and missed) Warren DeLano, who pushed for it. I believe Perl was the top dog in Bioinformatics, while several important (Bio)Chemistry software used TCL and a lot of scientific programming was also done in Matlab. “Bigger” things were mostly written in Fortran, with some C/C++ going around. Numpy existed already, but its documentation was not free. Nowadays, things are a lot better. I do believe, however, that the pendulum has swung a bit too far, and one has to practically apologize for not using Python in some projects. I suppose this is my apology.

Before asking the question in the title one should answer “When Go?”. My answer to that one is, as a personal rule of thumb: if the program is expected to exceed ~500 LOC and I don’t need a Python library (if I do, I might divide the programs in 2). For completeness, AWK is my language of choice if I expect to complete the task in 1 line (which might be somewhat longer than a regular LOC).

Python is a great language that doesn’t get in your way. After the shebang (I’m a Linux user) and the “imports”, you are ready to work on your problem. Common things, like reading a file, not at all verbose (compared to Go, anyway).   

I don’t think Python was ever well suited for large projects, though (perhaps for the very reasons stated above). I doubt it was even meant to. If your project is large-ish, dynamic typing already makes things pretty difficult and causes almost all errors to be runtime errors. To be honest, already using invisible characters to separate scopes is a deal breaker for me. Not to talk about the overuse of inheritance (‘treasure hunts’ to find what a method actually does) and the inevitable C libraries which you can’t really understand (more on that lated). And this was back when “There should be one-- and preferably only one --obvious way to do it” Was in PEP 20, “The Zen of Python”. It still is, but there are, for instance, about 3 ways to read a file (they couldn’t stay out of the RAII train) and 2 ways of formatting text (!). I’m not saying you can’t write a large program in Python. But you can do so in Perl, also. 

I wouldn’t claim Go is the perfect language (if such a thing exists), but it is fast enough, safe enough, well adapted for large projects, while focusing on engineering, rather than some sort of Platonic purity. I wouldn’t write MD or QM code in it (then again, I wouldn’t write MD or QM code, in general) and I wouldn’t write short programs in it either (too much boilerplate), but it’s perfectly suited for the kind of work goChem and Bartender do.

* Go is easy to learn. If you already know Python, I'd say it's a few days to understand what most Go code does, and even start writting. If you have somebody teach you, it can be just a few days even if you haven't programmed before.

* Go is very readable. Related to the previous. I don’t think you need much experience in Go to know what code does. It’s, generally, not as readable as Python (see below for qualifiers to this) but it’s much more readable than C.

* Go is fast enough that you can write almost anything in it. Combined with the previous point, this means that you can actually read and understand the numerical libraries you use. I’m just a regular user and have read code from [Gonum](https://gonum.org), the numerical library for Go, many times. I'd say this is generally not the case for numerical Python libraries (though Cython is a big help, when it’s used). I prefer to have as little 'magic' as possible involved in my project.

* While not as fast as C, Go lets you -with relative ease- use all your CPU cores. Whoever you are, I don’t wish on you having to do that in C (I kid, but, yeah, it’s a lot harder). Data races are possible in Go, but not too hard to avoid them, especially with the included detector. Thus, unless you are willing to put a fair bit of extra effort to parallelize C code, Go code is often faster.

* Python is a very simple and readable language until you change something and something else changes unexpectedly because you never learned about pointers, and they are not clearly indicated (I have personally seen seasoned programmers misunderstand this kind of unexpected behavior). Pointers are a thing in Go (though not pointer arithmetic). Being garbage-collected, you don’t really deal with handling memory, but the whole thing isn’t hidden from you, either. Joel Spolsky’s law of leaky abstractions comes to mind. This is also why I don’t think Python is a good language to teach programming, although it is a great language to know if you already understand the basics of how memory works.

* When you compile a program in Go, you get a single executable that you are ready to deploy whenever. Thus, installing Go code is very easy for the final user. I do admit that cross-compilation, while very easy, is not as effortless as the equivalent Python process, as you do have to test things.

* I get that this is contentious, and a matter of personal taste, but I can’t stand exceptions. I just never could. Raymond Chen explains it much better than I could in [“The old new thing”](https://devblogs.microsoft.com/oldnewthing/20050114-00/?p=36693).

Incidentally, when not some other language? Rust is very strongly pushed by its community, for instance. I suppose I would consider it if I wanted to write quantum-mechanics or molecular-mechanics code, though, really, I’d probably just go with C or, perhaps, Zig. Rust seems like a pretty big language, and I personally favor small ones that fit in my head (I have a somewhat big head, but it doesn’t fit much). Both Go and Rust are memory-safe. While Go uses garbage collection, Rust uses a more efficient, but a lot more complex system, which also creates long compilation times (Go compiles so fast it feels like running a script). If people have issues learning Go, Rust has a way steeper learning curve. 

Please don’t take this as an attack on Python (or Rust, with which I have zero experience). While there are things about Python that irritate me, that’s also the case with Go. Python is a fantastic language and I wish it and Go could interact better (I know there are efforts in that direction). I merely think Go is better for a particular kind of problem.




