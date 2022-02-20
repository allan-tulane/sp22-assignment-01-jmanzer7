

# CMPS 2200 Assignment 1

**Name:** James Manzer


In this assignment, you will learn more about asymptotic notation, parallelism, functional languages, and algorithmic cost models. As in the recitation, some of your answer will go here and some will go in `main.py`. You are welcome to edit this `assignment-01.md` file directly, or print and fill in by hand. If you do the latter, please scan to a file `assignment-01.pdf` and push to your github repository. 
  
  

1. (2 pts ea) **Asymptotic notation** (12 pts)

  - 1a. Is $2^{n+1} \in O(2^n)$? Why or why not? 

.  There exists two constants. Let c ∈ R+ and n0 ∈ N. For 
.  n ≥ n0, f(n) <= c * g(n). With c = 2 and n0 = 1,
.  2 * 2^n >= 2^n+1 for all n >= 1. Therefore, 
.  2^n+1 is O(2^n)

  - 1b. Is $2^{2^n} \in O(2^n)$? Why or why not?  

.  No, because there doesn't exist two constants c ∈ R+ 
.  and n0 ∈ N s.t. c * 2^n >= 2^2^n.

  ln2 * 2^n <= lnc + ln2 * n
  2^n <= lnc + n
.  n <= lnc
.  There is no c s.t. lnc <= n for all n >= n0, therefore 2^2^n is not O(2^n).
.  
  - 1c. Is $n^{1.01} \in O(\mathrm{log}^2 n)$?    
.  
There exists two constants. Let c ∈ R+ and n0 ∈ N. For 
.  n ≥ n0, n^1.01 <= c * (logn)^2.
.  n^1.01 = c*logn*logn. Using L/Hospital's rule,
  1.01n^.01 = (c * 2logn)/n
  lim n -> infinity of 1.01n^.01 = (c * 2logn)/n is infinity
.  Therefore, n^1.01 is not in O(\mathrm{log}^2 n)$, because it is in Ω.
.  

  - 1d. Is $n^{1.01} \in \Omega(\mathrm{log}^2 n)$?  
.  
.  Taking the derivative of f(n) and g(n), and using L'hospital's rule, f(n) does not asymptotitacly dominate g(n). * using the same work from above (1c)*, f(n) is in Ω
.  
.  
  - 1e. Is $\sqrt{n} \in O((\mathrm{log} n)^3)$?  
.  
.  There exists two constants. Let c ∈ R+ and n0 ∈ N. For 
.  n ≥ n0, f(n) <= c * g(n). 

   sqrt(n) = (log(n)^3)*c. Using l'hospital's rule,
   (n^-1/2)/2 = c * 3log^2(n)/n

   lim n -> infinity = 0, therefore f(n) is in O g(n)
  
.  
  - 1f. Is $\sqrt{n} \in \Omega((\mathrm{log} n)^3)$?  
.  
There exists two constants. Let c ∈ R+ and n0 ∈ N. For 
.  n ≥ n0, f(n) <= c * g(n).

Using the same work from 1e, because the lim n -> infinity is 0, f(n) is in O g(n), not Omega.

The functions cross at approximately 3.675, and therefore f(n) is in O g(n) after no of 3.675


2. **SPARC to Python** (12 pts)

Consider the following SPARC code of the Fibonacci sequence, which is the series of numbers where each number is the sum of the two preceding numbers. For example, 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, 377, 610 ... 
$$
\begin{array}{l}
\mathit{foo}~x =   \\
~~~~\texttt{if}{}~~x \le 1~~\texttt{then}{}\\
~~~~~~~~x\\   
~~~~\texttt{else}\\
~~~~~~~~\texttt{let}{}~~(ra, rb) = (\mathit{foo}~(x-1))~~,~~(\mathit{foo}~(x-2))~~\texttt{in}{}\\  
~~~~~~~~~~~~ra + rb\\  
~~~~~~~~\texttt{end}{}.\\
\end{array}
$$ 

  - 2a. (6 pts) Translate this to Python code -- fill in the `def foo` method in `main.py`  

  - 2b. (6 pts) What does this function do, in your own words?  

.  This function simulates a Fibonacci sequence. First, it checks if x is less than or equal to one, and returns x if this is the case. Otherwise, it creates two variables, ra and rb, and sets them equal to the recursive call of the foo function, with the input being x-1 and x-2 respectively. It then returns the sum of ra and rb, whose sum is the next number in the Fibonacci sequence.
.  
.  
.  
.  
.  
.  
.  
  

3. **Parallelism and recursion** (26 pts)

Consider the following function:  

```python
def longest_run(myarray, key)
   """
    Input:
      `myarray`: a list of ints
      `key`: an int
    Return:
      the longest continuous sequence of `key` in `myarray`
   """
```
E.g., `longest_run([2,12,12,8,12,12,12,0,12,1], 12) == 3`  
 
  - 3a. (7 pts) First, implement an iterative, sequential version of `longest_run` in `main.py`.  

  - 3b. (4 pts) What is the Work and Span of this implementation?  
    Work and span are both O(n). This is because this implementation is sequential and iterates through the array only once.
.  
.  
.  
.  


  - 3c. (7 pts) Next, implement a `longest_run_recursive`, a recursive, divide and conquer implementation. This is analogous to our implementation of `sum_list_recursive`. To do so, you will need to think about how to combine partial solutions from each recursive call. Make use of the provided class `Result`.   

  - 3d. (4 pts) What is the Work and Span of this sequential algorithm?  
.  
.  
.  Work and span for this sequential algorithm is O(n) and O(log(n))
.  
.  
.  
.  
.  
.  
.  
.  


  - 3e. (4 pts) Assume that we parallelize in a similar way we did with `sum_list_recursive`. That is, each recursive call spawns a new thread. What is the Work and Span of this algorithm?  

.  
.  
.   Work and span for this sequential algorithm is O(n) and O(n)
.  
.  
.  
.  
.  

