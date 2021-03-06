
# Technical debt

**Technical debt** is a frequent problem in projects evolving over time. When existing code is hard to work with, this is called **technical debt**. It includes:

* lack of documentation
* lack of structure
* badly written code
* bugs
* .. and many more

## Reasons for technical debt

How does technical debt emerge? There are at least four reasons:

## 1. Time pressure
Generally, it is a good thing if someone wants to have a program working (because they need it). Generally, sooner is better than later. In scientific projects, this is often expressed by deadlines. A deadline could be a paper submission, the end of a funding period or the end of a PhD thesis. Although many deadlines in science are soft and negotiable, they create time pressure.

Pressure teases programmers to cut corners. Programmers under pressure try to get the code running, no matter what (*"I can clean this up later."*). Producing clean, transparent, well-tested code becomes a secondary issue. Small nodules of messy code will emerge, grow, accumulate, and if you rush from deadline to deadline, the program becomes a jungle.

Slowing down your pace of programming under pressure takes courage.


## 2. Lack of experience
A programmer might write code that is difficult to maintain because he doesn't know better. An unexperienced programmer thinks that programming means writing code. An experienced programmer - like anyone interested in a book on software engineering - knows that sometimes programming means writing code, and sometimes it doesn't.

Lack of experience often results in code that is unnecessary long or complicated. This can happen even to experienced programmers switching from another language. Once, we stumbled upon the following Python code fragment written by a C programmer:

    i = 0; s = []
    f = open(filename,'r')
    while 1:
	    z = f.seek(i)
    	if z==None:
    		break
    	ch = f.read(1)
    	s.append(ch)
    	i = i+1

This code fragment can be written as:

    s = list(open(filename).read())

Even though Python is considered easy to learn, writing good Python code is not trivial.

## 3. Overabundant experience

Experienced programmers can create problematic code, too. In the first place, an experienced programmer is very good to have: They write sophisticated programs incredibly quickly, master new technologies and make them work. Such programmers are rare and valuable.

The problem is that sometimes it takes another experienced programmer to understand their code. One example of such code is called **code golf**. In code golf, the programmer tries to implement a program with as few key strokes as possible:

    return max([(d.count(x),x) for x in set(d)])[1]

This line returns the most frequent element from a list. It is a moderate example, we have seen much worse.

The moment an experienced programmer departs and leaves a lot of functional code that is hard to read, the project can suddenly go into debt.

As long as great programmers are in short supply, you need to find alternatives.

## 4. Python

Pythons built-in method to check program code before execution gives you SyntaxErrors and the most crude exceptions. Unfortunately, Python does not provide you with anything more.

Even a simple bug resulting from a typo like the following will go unnoticed:

    def get_modification_name(id):
         return DATABASE.get(idx)

Strongly typed languages like Java and C are fundamentally different in this aspect. They enforce strict rules on variable types and method signatures that are checked automatically while compiling a program. Without additional tests, Java and C code that compiles is much more reliable than Python code.

Summarizing, Python is not very good at telling whether the code you took over is working. You need to add engineering tools to improve maintainability by yourself.

## Summary

Technical debt is a serious problem in your own projects over time and when taking over a project. It can slow down development or even lead to a standstill.
