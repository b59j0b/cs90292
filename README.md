java c
CSCI   4041   Algorithms   and   Data   Structures   -   Spring   2025 
Homework   2   -   Correctness   and   Sorting 
Due Date: Friday,   February   21,   2025   by   11:59pm.Instructions: This   is   an   individual   homework   assignment.   You   may work together to   discuss   con-   cepts,   but   the   solutions   must   be   your   own   work.    Submit   your   answers   on   Canvas,   which   is   linked to   Gradescope   (be   sure   to   correctly   map   the   page   for   each   problem).    We   will   not   grade   *Practice Problems*,   however,   you   are   responsible   for   knowing   how   to   solve   them   in   order   to   prepare   for quizzes   and   exams.    This   homework   is   divided   into   two   parts.    Part      A   focuses   on   written   problems involving   correctness.   Part   B   involves   programming   solutions   to   real   world   sorting   problems.
Part A - Correctness (Written Problems) 
Problem H2.1: Proving Correctness Consider   the   MERGE(   .   .   .)      function   in   Section   2.3,   p.      31   of   the   textbook,   which   takes   two   sorted arrays   and   merges   them   into   one   sorted   array.    The   python   function   below,   merge3(A,B,C),   takes three   sorted   arrays,   A,B,   and   C   ,   and   merges   the   values   from   each   into   a   single   sorted   array,   D.    Let n   =   ∣A∣   +   ∣B∣   +   ∣C∣ .
merge3(A,      B,      C):
D    =      []
...
...
return      D
Answer   the   following   questions:
(a)   Write   the   algorithm   for   merge3(A,B,C).   You   may   write   the   algorithm   using   python,   pseu-   docode,   or   another   language.    Regardless   of   which   of   these   you   use,   you   may   assume   there   is an   append   function   to   add   an   element   to   the   end   of D.   (b)      Analyze   the   runtime   for   your   algorithm. 
(c)      Describe   a loop invariant or loop invariants that   will   help   you   prove   correctness   of   merge3(A,B,C).
(d) Prove that   your   algorithm   is correct by   showing   that   your   loop   invariant(s)   remains   true   during   initialization,   maintenance,   and   termination.
(e)    Create   a   merge sort3(   .   .   .)    algorithm   that   uses   merge3(A,B,C)   to   recursively   sort   the   solu-   tions   of   three   sub   problems.    (*Practice   Problem*)
(f)      Use the Master Theorem to   analyze   the   runtime   of   merge   sort3(   .   .   .).    (*Practice   Problem*)
(g)   Which   algorithm   has   a   slower   growing   asymptotic   runtime,   MERGE-SORT(   .   .   .)   in   Section   2.3,   p.   34   of   the   textbook   or   merge   sort3(   .   .   .)?    (*Practice   Problem*)
Problem H2.2: Loop Invariants Describe   specific   loop   invariant(s)   for   proving   correctness   for   each   of the   following   algorithms.   You   do   not   have   to   prove   that   the   algorithms   are   correct.      Remember   if   there   are   multiple   loops,   you   need   an   separate   invariant   for   each   loop:
(a)    (*Practice   Problem*)
find_min(A)
min         =      A[1]
for         i      =         1      to      A .   length
if    min         >    A[i]
min         =      A[i]
return         min
(b)    (*Practice   Problem*)
all_less_than_test_value(A,    testVal)
allLess         =      True
for         j      =         1      to      A .   length
if      A[j]         >=    testVal
allLess         =         False
return         allLess
(c)      divisible_by(A,      k)
D    =      []
for      i      =    1      to      A   .length
if      A[i]      %      k      ==      0
D.append(A[i])
return      D
(d)    scaled_sum(A)
sum      =      0
for      i      =    1      to A   .length  
sum      =    sum      +    A[i]*i 
return    sum
(e)      euclidean_norm(Matrix,      n)
sum      =      0
for      i      =    1      to      n
for      j      =      1      to      n
sum      =      sum      +      Matrix[i,      j]*Matrix[i,      j]
return      sqrt(sum)
Problem H2.3: Recursion Invariants 
For   each   algorithm   below   and recursion invariant,   use induction to   prove   the   invariant   is   true   for the   algorithm   (initialization,   maintenance, termination).
(a) Recursion Invariant: power(a,n)   calculates   an−1 for   any   a   ∈ R   and   for   all   n   ∈ Z,   n   ≥   1:
power(a, n) 
if (n == 1): 
return 1 


if 代 写CSCI 4041 Algorithms and Data Structures - Spring 2025 Homework 2 - Correctness and SortingPython
代做程序编程语言(n % 2) == 0 
// n is even 
x = power(a, n / 2) return a * x * x 


else 
// n is 
odd 
x = power(a, (n + 1) / 2) 
return x * x (b) (*Practice Problem*) 


textbfRecursion   Invariant:      deep sum(A)   sums   all   the   numbers   in   an   array,   including   num-   bers   that   are   recursively   stored   in   sublists.
For   example,   deep sum([[1,2],3,[4,5,[6]]])      =    1      +      2      +      3      +      4      +      5      +      6.
deep_sum(A)
if      A         is         Number   return         A
if      A .   length         ==         0   return         0
return    deep   _sum(A[1])         +         deep   _sum(A[2:A .   length])
(c)    (*Practice   Problem*)
Recursion Invariant: reverse(A)   reverses   the   elements   in   array   A.
def         reverse(A):   n      =         len(A)         if      n         <= 1:
return         A   q      =      n//2
return    reverse(A[q:n])    +    reverse(A[0:q])
Part B - Sorting (Programming Problems) 
Submission: Submit   the   following   file   to   “Homework   2B”   submission   on   Gradescope.
•   H2 4.py   (Problem   H2.4)
Problem H2.4: Video Frame Ordering Instructions: You   have   received   a   set   of video   frames   sent   over   a   network.   Due   to   network   traffic, the   video   frames   are   received   in   a   different   order   than   they   are   sent.    The   frames   are   buffered   into   an   array   in   the   order   that   they   are   received.   You   are   tasked   with   reordering   the   video   frame   array   as   quickly   as   possible.   You   will   need   to   consider   the   following   details   to   accomplish   this   task:
1.    Comparison   is   cheap   since   we   know   the   frame   number   for   each   image.
2.    Swapping   memory,   however,   is   expensive   since   we   are   moving   images   around.
3.   Video   frame   numbers   may   be   reused.       Fortunately,    duplicate      frame      numbers      will      ordered correctly   within   the   buffer.    For   example,   you   may   get   1   1   2   3   1   1   2   1   3   3   1   2.    If   two   frames   have   the   same   number,   you   should   maintain   the   order   in   which   they   are   stored   in   the   array. (In   other   words,   your   sort   should   be   stable).
4.    The   frame   array   is   twice   as   large   as   the   size   of   the   video,   which   is   stored   in   the   first   half   of the   buffer.   The   remaining   slots   are   empty   frames   that   can   be   swapped.
5.      Use   the   assignment   operator   for   swapping   (e.g.    A[i]   =   A[k])   and   the   comparison   operators (e.g.   A[i] < A[k]) for sorting.
6.   You   should   use   or   modify   sorting   algorithms   from   class   or   the   textbook.    Do   not   use   python   system   sorting   algorithms.
7.   You   can   change   the   start   index   of the   video   in   the   array   by   returning   start index.Task: Program   the   following   algorithm   in   H2 4.py   to   correctly   sort   the   video   frames   using   as   few   swaps   as   possible.    When   writing   your   algorithm,   consider   using   or   modifying   multiple   algorithms.   The   sort   may   depend   on   best,   worst,   and   average   situations   when   writing   your   algorithm:
def    order   _video   _frames(frames ,         start   _index   ,         length):   #         Sort         video         frames         in         the         frame         array
#    The         video         is         of         size      n=length         and         the         array         is         of         size         2*n
#         Example       (comparison         and         swap):   #    if         (frames[i]    < frames[j]):
#                              temp         =         frames[i]
#                   frames[i]    =         frames[j]   #                              frames[j]      =      temp
return         start   _index
Testing: You   can test your   program   by   ordering   the   provided   video   file   (unordered.gif).
First   you   will   need   to   install   dependencies:   pip3         install         imageio
Then,   run   your   program   with   the   following   command:
python3         H2   _   4 .   py    unordered   .   gif       ordered .   gif
Open   ordered.gif   and   you   should   see   an   ordered   video   sequence

         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
