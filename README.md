
# 8 Queens Problem in Prolog




## Overview
This repository contains an efficient Prolog solution to the classic 8 Queens Problem. The objective of the 8 Queens Problem is to place eight queens on an 8x8 chessboard such that no two queens threaten each other. This means no two queens can share the same row, column, or diagonal.

## Features
- **Efficiency:** The solution is designed to print all possible combinations that satisfy the conditions with every tab, ensuring an optimized and swift output.
- **Clarity:** The code is written in a clear and concise manner, making it easy to understand and modify.
- **Flexibility:** The solution can be adapted to similar problems or extended to larger chessboards with minimal changes.


## Usage
1. **Clone the repository:**
   ```bash
   git clone https://github.com/aditxa/8-queens-prolog.git
   cd 8-queens-prolog
2. **Run the Prolog script:**
    Use your favorite Prolog interpreter to load and run the    script.
    ```bash
    swipl -s 8queens.pl
3. **Get all Solutions**
    Simply run the main predicate in the Prolog console to print all possible solutions by pressing Tab until you reach the final solution.
    ```prolog
    ?- eight_queens(Queens).
## Code Explanation
The core of the solution revolves around using the Constraint Logic Programming over Finite Domains (CLP(FD)) library in Prolog to efficiently handle constraints and backtracking. Here's the provided code with a brief explanation:

      
        use_module(library(clpfd)).

        eight_queens(Queens) :-
            Queens = [Q1, Q2, Q3, Q4, Q5, Q6, Q7, Q8],
            Queens ins 1..8,
            Q1 #\= Q2, Q1 #\= Q3, Q1 #\= Q4, Q1 #\= Q5, Q1  #\=  Q6, Q1 #\= Q7, Q1 #\= Q8,
            Q2 #\= Q3, Q2 #\= Q4, Q2 #\= Q5, Q2 #\= Q6, Q2  #\=  Q7, Q2 #\= Q8,
            Q3 #\= Q4, Q3 #\= Q5, Q3 #\= Q6, Q3 #\= Q7, Q3  #\= Q8,
            Q4 #\= Q5, Q4 #\= Q6, Q4 #\= Q7, Q4 #\= Q8,
            Q5 #\= Q6, Q5 #\= Q7, Q5 #\= Q8,
            Q6 #\= Q7, Q6 #\= Q8,
            Q7 #\= Q8,
            safe(Queens),
            label(Queens).

        safe([]).
        safe([Q|Qs]) :-
            safe(Qs, Q, 1),
            safe(Qs).

        safe([], _, _).
        safe([Q|Qs], Q0, N) :-
            Q0 #\= Q,
            abs(Q0 - Q) #\= N,
            D1 #= N + 1,
            safe(Qs, Q0, D1).
        

    




- **eight_queens/1:** The main predicate that sets up the queens and their constraints.
- **safe/1 and safe/3:** Helper predicates that ensure no two queens threaten each other by checking rows, columns, and diagonals.

        

    



