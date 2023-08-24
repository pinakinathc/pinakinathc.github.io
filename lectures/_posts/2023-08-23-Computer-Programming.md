---
title: A Perspective on Computer Programming
layout: post
comments: false
mathjax: true
header: true
author: pinaki
date: August 23, 2023
permalink: /computer-programming/
---

<!--more-->

*The following is a combination of a lecture and also my view on Computer Programming. I am no expert so take this lecture with a grain of salt. If you find it useful, feel free to steal it and share (with or without attribution). I don't want any hindrance to knowledge just because someone forgot to cite the source.*

# Introduction

In this lecture, we shall revisit computer programming. This lecture is relevant for those who already has learned some basic programming language like C, C++, Python etc. Also, if you haven't learned any computer programming, then read it as a fun story, but don't believe everything I say. I am no expert, and these are just my view of computer programming. So let's dig in.

First, we should be clear, when to use a computer and when to simply use a mathematical formula. If you want to add two small numbers, maybe a computer is not required -- you can just do it in your head or on a piece of paper. A computer comes in when we have to add several (say 1000) large numbers. But we also need to ask -- can we add any number in a computer? How many numbers can I add using a computer? 10, 100, 1000 ... maybe $$10^{6}$$ (that is 1,000,000)? Yes, modern computer allow you to do that. But even modern computers would fail if you try to add $$1,000,000,000,000$$ numbers.

In my opinion, this perspective is important -- before we start thinking about writing computer programs, we should have a clear picture of:
- what is a computer, 
- what advantages does it give -- the reason why and when we should use it,
- what is not possible using a computer.

`What is a computer?`

[Wikipedia](https://en.wikipedia.org/wiki/Computer) (the repository of collective human knowledge) gives a nice description -- *A computer is a machine that can be programmed to carry out sequences of arithmetic or logical operations (computation) automatically.*

Now my ''hand-wavy'' version -- A computer can be an [imaginary or mathematical tool](https://en.wikipedia.org/wiki/Turing_machine), a [person](https://en.wikipedia.org/wiki/Computer_(occupation)), a wodden box with multiple columns and slidable beads (the [abacus](https://en.wikipedia.org/wiki/Abacus)), a [vaccum tube](https://en.wikipedia.org/wiki/Vacuum_tube) that can control the flow of electric current, a silicon+germanium based [transistor](https://en.wikipedia.org/wiki/Transistor) that can change the voltage of current flowing through a wire. As you see, we kept evolving computers and going from abacus, to humans, to transistors, and hopefully to [quantum physics](https://en.wikipedia.org/wiki/Quantum_computing) -- we get some added benefits/features and some limitations.

![abacus](https://upload.wikimedia.org/wikipedia/commons/thumb/a/af/Abacus_%28PSF%29.png/220px-Abacus_%28PSF%29.png){: width="17%" } ![finite state machines](https://upload.wikimedia.org/wikipedia/commons/thumb/4/4b/State_diagram_3_state_busy_beaver_2B.svg/500px-State_diagram_3_state_busy_beaver_2B.svg.png){: width="17%" } ![vaccum tubes](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e9/Elektronenroehren-auswahl.jpg/290px-Elektronenroehren-auswahl.jpg){: width="17%" } ![transistor](https://upload.wikimedia.org/wikipedia/commons/thumb/2/21/Transistorer_%28cropped%29.jpg/220px-Transistorer_%28cropped%29.jpg){: width="17%" } ![quantum computer](https://upload.wikimedia.org/wikipedia/commons/thumb/6/60/IBM_Q_system_%28Fraunhofer_2%29.jpg/260px-IBM_Q_system_%28Fraunhofer_2%29.jpg){: width="17%" }

Okay, so there are a lot of variation and each type of computer has some advantages and some disadvantages -- but then what is the common factor among all of them? From the wikipedia definition -- `can be programmed to carry out sequence of operations`.

In other words, 
1. you can rely on your `computer` -- be it a person or a box -- to do some operation reliably. E.g., you can rely on your friend to correctly add two numbers for you.
2. you can ask your `computer` to do some specific operation (say add two or multiply two numbers) whenever you feel like -- this is what we mean by `programmable`.

# The Rules

Given that you have a human friend (who is a `computer`) -- your first job is to identify -- what can your friend do `reliably` and `quickly`?

To understand the significance of capabilites and how it affect computer programming, we consider two friends -- **Dr. X** can only do additions whereas **Dr. Y** can do additions and multiplications.

Since, Dr. X can only do addition, we create Rules as:
- `ADD a + b` means Dr. X will add a + b
- `ASSIGN c = ...` means Dr. X will assign the value in `...` to `c`

Since Dr. Y can do both addition and multiplication, we create Rules as:
- `ADD a + b` means Dr. Y will add a + b
- `MULTIPLY a * b` means Dr. Y will multiply a * b
- `ASSIGN c = ...` means Dr. Y will assign the value in `...` to `c`

(ps: I skipped some things for simplicity, e.g., how I store the variables a, b, c; the fact that I used algebriac notation, etc. But let's keep things simple for now.)

```
Note: 
    First, identify the capabilities of your computer.
    
    Second, using those capabilities, define the best set of rules. Try to keep these rules short and simply so that everyone can use your computer.
```

# Use the Computer

Suppose, I want to use your computer for some problem that I want to solve. The first thing I should do is -- `Get the list of Rules from you`.

Now that I have your computer and the list of rules -- I will use it to solve a problem -- *track how much money I have in my bank, in particular, how much money I earn and how much money I spend*.

Here is the list of records:

```
Day-1:
    My bank balance is £0.
    I earned £100 as salary.
    I bought 1 potato price £7.

Day-2:
    I bought 10 potatoes each price £5.
    I earned £30 as salary.

Day-3:
    I bought 3 potatoes each price £6.

What is my final bank balance after 3 days?
```

If I had to track the record for one day, I would do it myself. But tracking money for 3 days is tedious and repetative -- so, I can teach or `program` my friend a computer (Dr. X or Dr. Y) how to do it.

Note, we already highlighted a `limitation of computer programming` -- since you teach your computer what to do -- first, you need to know how to keep track of money (i.e., addition when you get salary and substraction when you buy potatoes).

This is easy for buying potatoes or getting salary -- but there are problems where:
1. We can solve the problem ourselves, but we do not know how we do it. E.g., ''Draw a cat from your imagination''. Well, this task has two problems -- (a) you need to know what is a cat. (b) how to draw a cat -- should you just draw the face with whiskers, pointy ears, two eyes or the entire body of cat?
2. We know the problem, but we have no idea how to solve the problem. These problems are usually called `undecidable problems` ([click here for a list](https://en.wikipedia.org/wiki/List_of_undecidable_problems)) like the famous **Halting Problem**, **Hilbert's Entscheidungsproblem**, etc. I will later write a lecture/blog on these interesting undecidable problems, or better, you can learn about these problem from experts like [Erik D. Demaine](https://ocw.mit.edu/courses/6-890-algorithmic-lower-bounds-fun-with-hardness-proofs-fall-2014/).

**Anyways, back to our money tracking problem**

Given that **Dr. X** can only do addition and we know the **Rules** of how to ask **Dr. X** to do an addition for us, we can write a `program` as:
```
ASSIGN bank_balance = 0

// Day-1
ASSIGN bank_balance = ADD bank_balance + 100
ASSIGN bank_balance = ADD bank_balance - 7

// Day-2
ASSIGN bank_balance = ADD bank_balance -5
ASSIGN bank_balance = ADD bank_balance - 5
ASSIGN bank_balance = ADD bank_balance - 5
ASSIGN bank_balance = ADD bank_balance - 5
ASSIGN bank_balance = ADD bank_balance - 5
ASSIGN bank_balance = ADD bank_balance - 5
ASSIGN bank_balance = ADD bank_balance - 5
ASSIGN bank_balance = ADD bank_balance - 5
ASSIGN bank_balance = ADD bank_balance - 5
ASSIGN bank_balance = ADD bank_balance - 5

ASSIGN bank_balance = ADD bank_balance + 30

// Day-3
ASSIGN bank_balance = ADD bank_balance - 6
ASSIGN bank_balance = ADD bank_balance - 6
ASSIGN bank_balance = ADD bank_balance - 6

```

Now that was a lengthy program. At least, we know that our computer can do these additons reliably and all we had to say is a sequence of `ADD a + b` and `ASSIGN c = ...`.

Using a more powerful **Dr. Y** that allows addition and multiplication, we can write a smaller program (and hopefully less number of operation to make it fast) as:
```
ASSIGN bank_balance = 0

// Day-1
ASSIGN bank_balance = ADD bank_balance + 100
ASSIGN bank_balance = ADD bank_balance - 7

// Day-2
ASSIGN total_price = MULTIPLY 10 * 5
ASSIGN bank_balance = ADD bank_balance - total_price
ASSIGN bank_balance = ADD bank_balance + 30

// Day-3
ASSIGN total_price = MULTIPLY 3 * 6
ASSIGN bank_balance = ADD bank_balance - total_price
```

# Conclusion

The main takeaway from this lecture is -- before you write Computer Programs -- you need to be clear about the following two things:
1. What can this computer do and what it cannot. A modern CPU-like computer can add $$1,000,000,000$$ numbers, do mathematical operations like addition, multiplication and non-mathematical operation like `ASSIGN` and store information inside a magnetic tape. A modern GPU-like computer can add $$1,000,000,000,000$$ numbers and do mathematical operations (additions, multiplications) much much faster but is not good for non-mathematical operations like `ASSIGN`.
2. Once we have a computer -- it must have a set of `Rules` defined by the people who created that computer. If you know these rules properly, you will have an idea of all the problems that I can solve using this computer.

The objective of `Rules` are to be short and simply but allows maximum use of the computer's capabilities. If you feel that some rules are unnecessarily complicated, then you can ask the people who created the computer to modify the rules.

Programming languages like C, C++, and Python -- they are basically different `Rules` to use the same computer. 

Then, you should ask -- if everyone wants to utilise the same computer -- `why not have a common set of Rules because, at the end, we just want to use the modern computers and its capabilities?`

You see, our modern computers are very general -- that is -- using the same computer you can play video games whereas I can calculate the precise trajectory of a rocket. We have different needs but our computers are the same. Programming language like C, C++, Python basically provide these `customised set of Rules` instead of forcing everyone to use the same set of Rules.

If tomorrow, your needs change (say you want your computer to solve a problem that helps you go to Mars so you need more `MULTIPLY` and less `ADD`), you might come up with a `new set of Rules` to make you job easier and we shall call it a new programming language.

Hope this helps. The reason I wrote this lecture is -- I think we should teach some basics of ''what is a computer'' before teaching ''how to program a computer'' using C, C++, Python. We should also teach -- what is easy, what is hard, and what can never be solved using our current computers.