This repository will be used as the website for Functional Programming CS-210. It will be updated weekly throughout the semester. This README contains general information about the class.

- [previous-exams](previous-exams) contains PDFs for the previous exams.
- [exercises](exercises) contains markdown documents for the exercise sessions and solutions.
- [slides](slides) contains the slides presented in class (also attached or respective videos).
- [labs](labs) contains markdown documents for the labs.

We will use GitLab's issue tracker as a discussion forum. Feel free to [open an issue](https://gitlab.epfl.ch/lamp/cs210/issues/new) if you have any comments or questions

# First-week tasks

1. [Join the Discord](https://discord.gg/8ud6UpE)
2. Log into gitlab: https://gitlab.epfl.ch/users/sign_in
3. [Register in a group](exercises/Group workspaces.md) for the exercise sessions
4. Follow the [Tools Setup](labs/tools-setup.md) page.
5. Do the [example lab](labs/example-lab.md).
6. Do the [first graded lab](labs/lab-1.md).

## Grading

The grading of the course is divided between labs (25%), exercises (5%) and a final exam (70%). There will be no midterm exam this year.

## Staff

| Role        | People |
| :---        | :--- |
| Professors  | [Martin Odersky](https://people.epfl.ch/martin.odersky), [Viktor Kunčak](https://people.epfl.ch/viktor.kuncak) |
| TAs         | [Adrien Ghosn](https://people.epfl.ch/adrien.ghosn), [Dragana Milovancevic](https://people.epfl.ch/dragana.milovancevic), [Guillaume Martres](https://people.epfl.ch/guillaume.martres), [Nicolas Stucki](https://people.epfl.ch/nicolas.stucki), [Olivier Blanvillain](https://people.epfl.ch/olivier.blanvillain) |
| Student TAs | [Arthur Vignon](https://people.epfl.ch/arthur.vignon), [Emilien Ordonneau](https://people.epfl.ch/emilien.ordonneau), [Lucas Giordano](https://people.epfl.ch/lucas.giordano), [Mohamed Dhraief](https://people.epfl.ch/mohamed.dhraief), [Sara Djambazovska](https://people.epfl.ch/sara.djambazovska) |

## Rooms

Lectures are prerecorded and published on this page.
Exercise sessions take place on Wednesdays from 13:15 to 15:00 on [Discord](https://discord.gg/8ud6UpE).
Lab sessions take place on Fridays from 10:15 to 12:00, also on [Discord](https://discord.gg/8ud6UpE).
In the first 2 weeks of the semester, in-person office hours will be held on Wednesdays from 13:15 to 15:00 in CO 2, and on Fridays from 10:15 to 12:00 in ELA1.
These office hours are there to help you setting up Git and Java our your machines and answer any other question you might have about the class. We will be happy to arrange further in-person or virtual (Discord, Zoom, etc.) office hours--just contact one of us with a list of all your available time slots.

## Lecture Schedule

<!-- date -d "30/09/2019 364 days" +"%d.%m.%Y" -->

**Note**: In some lectures, worksheets are used to present code. To learn how to
use worksheets yourselves, please follow the [Tools
Setup](labs/tools-setup.md) and [example lab](labs/example-lab.md). To create a
new empty project to experiment with worksheets, you can clone the following
repository and run `code . ` inside as usual: [`git clone https://gitlab.epfl.ch/lamp/cs210-worksheets`](https://gitlab.epfl.ch/lamp/cs210-worksheets)

| Week | Date        | Topic                       | Video              |
| :--  | :--         | :--                         | :--                |
| 1    | 16.09.2020  | Intro class                 | [Introduction][Video 1.1.1], [Elements of programming][Video 1.1.2], [Evaluation strategies and termination][Video 1.1.3], [Value Definitions and Conditionals][Video 1.1.4], [Square Roots with Newtons Methods][Video 1.1.5], [Blocks and lexical scopes][Video 1.1.6], [Tail Recursion][Video 1.1.7] |
| 2    | 23.09.2020  | Recursion / Function values | [Higher-Order Functions][Video 1.2.1], [Currying][Video 1.2.2], [Finding FixedPoints][Video 1.2.3], [Scala Syntax Summary][Video 1.2.4], [Functions and Data][Video 1.2.5], [Data Abstraction][Video 1.2.6], [Evaluation and Operators][Video 1.2.7] |
| 3    | 30.09.2020  | Classes                     | [Class Hierarchies][Video 1.3.1], [How Classes are Organized][Video 1.3.2], [Polymorphism][Video 1.3.3], [Objects Everywhere][Video 1.3.4], [Functions as Objects][Video 1.3.5] |
| 4    | 07.10.2020  | Classes                     | [Decomposition][Video 1.4.1], [Pattern Matching][Video 1.4.2], [Lists][Video 1.4.3], [Enums][Video 1.4.4], [Subtyping and Generics][Video 1.4.5], [Variance][Video 1.4.6]                   |
| 5    | 14.10.2020  | List                        | [A closer look at lists][Video 1.5.1], [Tuples and generic methods][Video 1.5.2], [Higher order list functions][Video 1.5.3], [Reduction of lists][Video 1.5.4], [Reasoning about lists][Video 1.5.5]                   |
| 6    | 21.10.2020  | Collection                  | [Other Collections][Video 1.6.1], [Combinatorial Search and For-Expressions][Video 1.6.2], [Combinatorial Search Example][Video 1.6.3], [Maps][Video 1.6.4], [Putting the Pieces Together][Video 1.6.5] |
| 7    | 28.10.2020  | Monads                      | [Recap][Video 2.1.1], [Queries with for][Video 2.1.2], [Translation of for][Video 2.1.3], [Functional Random Generators][Video 2.1.4], [Monads][Video 2.1.5], [Exceptional Monads][Video 2.1.6]                   |
| 8    | 04.11.2020  | Lazy evaluation             | [Structural Induction on Trees][Video 2.2.1], [Lazy Lists][Video 2.2.2], [Lazy Evaluation][Video 2.2.3], [Infinite Sequences][Video 2.2.4], [Case Study][Video 2.2.5]                   |
| 9    | 11.11.2020  | Type-directed computation   | [Contextual abstraction][Video 2.3.1], [Using clauses and given instances][Video 2.3.2], [Type classes][Video 2.3.3], [Abstract algebra and type classes][Video 2.3.4], [Context passing][Video 2.3.5], [Implicit function types][Video 2.3.6]                   |
| 10   | 18.11.2020  | State                       |  [Functions and state][Video 2.4.1], [Identity and change][Video 2.4.2], [Loops][Video 2.4.3], [Discrete Event Simulation][Video 2.4.4]                  |
| 11   | 25.11.2020  | Functional Reactive Programming and Constraint Propagation / Symbolic computation |  [Observer Pattern][Video 2.5.1], [Functional Reactive Programming][Video 2.5.2], [A Simple FRP Implementation][Video 2.5.3]                  |
| 12   | 02.12.2020  | Interpreter I                | [Interpreter for Arithmetic][Video 3.1.1], [Substitution Interpreter for Recursive Functions][Video 3.1.2], [Environment Instead of Substitutions][Video 3.1.3], [Higher-Order Functions Using Naive Substitutions][Video 3.1.4], [Avoiding Variable Capture][Video 3.1.5], [Higher-Order Functions Using Environments][Video 3.1.6], [Nested Recursive Definitions][Video 3.1.7]   |
| 13   | 09.12.2020  | Parsing. Lambda Calculus  |                    |
| 14   | 16.12.2020  | Review for the exam         |                    |

## Lab Schedule

| Title                             | Start Date | Discord Session (Fridays 10:15 to 12:00) | Due Date ([AoE](https://en.wikipedia.org/wiki/Anywhere_on_Earth)) |
| :--                               | :--        | :--                     | :--        |
| Recursion                         | 16.09.2020 | 18.09.2020              | 27.09.2020 |
| Functional Sets                   | 23.09.2020 | 25.09.2020              | 01.10.2020 |
| Object-Oriented Sets              | 30.09.2020 | 02.10.2020              | **11.10.2020** (updated after GitLab outage) |
| Huffman Coding                    | 07.10.2020 | 09.10.2020 & 16.10.2020 | 22.10.2020 |
| Anagrams                          | 21.10.2020 | 23.10.2020              | 05.11.2020 |
| Quickcheck                        | 28.10.2020 | 30.10.2020              | 12.11.2020 |
| Bloxorz                           | 04.11.2020 | 06.11.2020 & 13.11.2020 | 19.11.2020 |
| Codecs                            | 18.11.2020 | 20.11.2020 & 27.11.2020 | 03.12.2020 |
| Interpreter                       | 02.12.2020 | 04.12.2020 & 11.12.2020 | 17.12.2020 |

Labs are individual assignments where you get to write Scala programs using the concepts learned during lectures.
Labs are submitted by pushing your code on GitLab, see details in the [grading and submission](labs/grading-and-submission.md) page.

## Exercise Schedule

| Title                                          | Handout Released | Discord Session (Wednesdays 13:15 to 15:00) | Due Date ([AoE](https://en.wikipedia.org/wiki/Anywhere_on_Earth)) | Solution Released |
| :--                                            | :--              | :--             | :--              | :--              |
|  First week tasks                              | -                | 16.09.2020      | -                | -                |
| Exercise Session 1                             | -                | 23.09.2020      | 27.09.2020       | 28.09.2020       |
| Exercise Session 2                             | 28.09.2020       | 30.09.2020      | 04.10.2020       | 05.10.2020       |
| Exercise Session 3                             | 05.10.2020       | 07.10.2020      | 11.10.2020       | 12.10.2020       |
| Exercise Session 4                             | 12.10.2020       | 14.10.2020      | 19.10.2020       | 20.10.2020       |
| Exercise Session 5                             | 20.10.2020       | 21.10.2020      | 25.10.2020       | 26.10.2020       |
| Exercise Session 6                             | 26.10.2020       | 28.10.2020      | 01.11.2020       | 02.11.2020       |
| Exercise Session 7                             | 09.11.2020       | 11.11.2020      | 15.11.2020       | 16.11.2020       |
| Exercise Session 8                             | 16.11.2020       | 18.11.2020      | 22.11.2020       | 23.11.2020       |
| Exercise Session 9                             | 23.11.2020       | 25.11.2020 & 02.12.2020     | **06.12.2020** (updated after late videos)       | 07.12.2020       |
| Exercise Session 10                            | 30.11.2020       | 02.12.2020 & 09.12.2020      | 13.12.2020       | 14.12.2020       |

Exercises are pen and paper style questions that will prepare you for the final exam.
Exercises should be done in groups and submitted via Google Drive, see details in the [Group workspaces](exercises/Group workspaces.md) page.

## Exam Schedule

The final exam date will be during the exam session in January 2021. The final exam will cover all material seen during the semester.

Information about exam organization will be communicated by email a few days before the exam.


[Video 1.1.1]: https://tube.switch.ch/videos/7ed71e65
[Video 1.1.2]: https://tube.switch.ch/videos/eefaaa33
[Video 1.1.3]: https://tube.switch.ch/videos/7ec55c9c
[Video 1.1.4]: https://tube.switch.ch/videos/f8abe6bf
[Video 1.1.5]: https://tube.switch.ch/videos/1f8d3205
[Video 1.1.6]: https://tube.switch.ch/videos/9274e0f4
[Video 1.1.7]: https://tube.switch.ch/videos/1843caa3

[Video 1.2.1]: https://tube.switch.ch/videos/646cfe4f
[Video 1.2.2]: https://tube.switch.ch/videos/9e573d2f
[Video 1.2.3]: https://tube.switch.ch/videos/0e2be793
[Video 1.2.4]: https://tube.switch.ch/videos/ddcbb43f
[Video 1.2.5]: https://tube.switch.ch/videos/dec623bc
[Video 1.2.6]: https://tube.switch.ch/videos/6e8643cf
[Video 1.2.7]: https://tube.switch.ch/videos/dc82606b

[Video 1.3.1]: https://tube.switch.ch/videos/56c88e00
[Video 1.3.2]: https://tube.switch.ch/videos/1c969056
[Video 1.3.3]: https://tube.switch.ch/videos/d3a7aff4
[Video 1.3.4]: https://tube.switch.ch/videos/03486c5a
[Video 1.3.5]: https://tube.switch.ch/videos/82b0e104

[Video 1.4.1]: https://tube.switch.ch/videos/f5879da4
[Video 1.4.2]: https://tube.switch.ch/videos/e7df77e5
[Video 1.4.3]: https://tube.switch.ch/videos/978832a8
[Video 1.4.4]: https://tube.switch.ch/videos/ea910999
[Video 1.4.5]: https://tube.switch.ch/videos/9a844297
[Video 1.4.6]: https://tube.switch.ch/videos/35c4e417

[Video 1.5.1]: https://tube.switch.ch/videos/8e9cf6a5
[Video 1.5.2]: https://tube.switch.ch/videos/40edd184
[Video 1.5.3]: https://tube.switch.ch/videos/af626839
[Video 1.5.4]: https://tube.switch.ch/videos/e0e380fe
[Video 1.5.5]: https://tube.switch.ch/videos/9ebad679

[Video 1.6.1]: https://tube.switch.ch/videos/58a6fe2a
[Video 1.6.2]: https://tube.switch.ch/videos/a09a7679
[Video 1.6.3]: https://tube.switch.ch/videos/7f2fcf99
[Video 1.6.4]: https://tube.switch.ch/videos/a4519732
[Video 1.6.5]: https://tube.switch.ch/videos/30005570

[Video 2.1.1]: https://tube.switch.ch/videos/680a1d2a
[Video 2.1.2]: https://tube.switch.ch/videos/935b0da5
[Video 2.1.3]: https://tube.switch.ch/videos/2ac4c232
[Video 2.1.4]: https://tube.switch.ch/videos/f9c5677b
[Video 2.1.5]: https://tube.switch.ch/videos/16b5d240
[Video 2.1.6]: https://tube.switch.ch/videos/fdfb0609

[Video 2.2.1]: https://tube.switch.ch/videos/0accfa13
[Video 2.2.2]: https://tube.switch.ch/videos/fbd7e361
[Video 2.2.3]: https://tube.switch.ch/videos/8506774b
[Video 2.2.4]: https://tube.switch.ch/videos/7064a6b1
[Video 2.2.5]: https://tube.switch.ch/videos/889a5305

[Video 2.3.1]: https://tube.switch.ch/videos/d5df9a21
[Video 2.3.2]: https://tube.switch.ch/videos/cef63f8a
[Video 2.3.3]: https://tube.switch.ch/videos/8c7b6f4e
[Video 2.3.4]: https://tube.switch.ch/videos/a65a3022
[Video 2.3.5]: https://tube.switch.ch/videos/ee6fdc37
[Video 2.3.6]: https://tube.switch.ch/videos/cab2248b

[Video 2.4.1]: https://tube.switch.ch/videos/f32bc013
[Video 2.4.2]: https://tube.switch.ch/videos/7bf009ce
[Video 2.4.3]: https://tube.switch.ch/videos/a2a7b6fb
[Video 2.4.4]: https://tube.switch.ch/videos/95c82b17

[Video 2.5.1]: https://tube.switch.ch/videos/5ca69d05
[Video 2.5.2]: https://tube.switch.ch/videos/700fc8b5
[Video 2.5.3]: https://tube.switch.ch/videos/d93a3d12

[Video 3.1.1]: https://tube.switch.ch/videos/b053ad9d
[Video 3.1.2]: https://tube.switch.ch/videos/59b7ae00
[Video 3.1.3]: https://tube.switch.ch/videos/0ccb68d7
[Video 3.1.4]: https://tube.switch.ch/videos/0de70fa1
[Video 3.1.5]: https://tube.switch.ch/videos/94bc1565
[Video 3.1.6]: https://tube.switch.ch/videos/6d332501
[Video 3.1.7]: https://tube.switch.ch/videos/18ba7117
