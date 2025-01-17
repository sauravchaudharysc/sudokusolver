# Sudoku Solver
![](sudoku.png)
## Hi Everyone.
In this project the sudoku solver is designed.
Algorithm to solve the sudoku. (9*9)<br/>
1.Brute Force Approach<br/>
We will try to place a number at any cell. We will put a number if and only if
it isn't repeating in the row or the column or in the sub-grid. So lets put that a number in index (0,0)
Then make a recursive call . And we have solved the one part of sudoku . Let other be solved by recursion.
Recursion ja aur baki ka solve tu karke aa :D :D .
But doing this way at certain point we will realize it cant be done further because it doesnt satisfy the
condition so we need to backtrack it. So a better approach is backtracking.<br/>
2.Backtracking<br/>
Here also we use recursion but here we create a helper function that return true or false. If the number to
be placed is the right number then return true no return false. In this case the recursive call is done and
it will return a true value if the problem is solved . If it return false we will update the value. And
each time we will try to keep a safe number.
To check if number is already filled traverse the board col row and sub-grid if present return false.
Try For another value.<br/>

### Pseudo Code For Sudoku helper

    Base Case
    Row==9
    To Display Change on the board:- changeBoard(board);

    To Shift to next row:-
    if(column==9)
     {return solveSudokuHelper(board,r+1,0)};

    To check prefilled cell
    if(board[r][c]!=0)
    {return solveSudokuHelper(board,r,c+1)};

    So after coming so far it is assured that current index isnt prefilled.
    So we will try to put all values.And to put values we will take the help of a
    isSafe helper function to assure there is no similar element present in the row
    column or grid.

    for(var i=1;i<=9;i++){
      if(isSafe(board,r,c,i)){
          board[r][c]=i; //Try to put a value
          var sucess= solveSudokuHelper(board,r,c+1); //Check for rest sub-grid
          //If stuck return false then Backtracking take place or true is returned
          if(sucess==ture){
          return true;
          }
          board[r][c]=0; //Backtracking
      }
    }
    return false; //if true is not returned from sucess.

### To check Is Number Valid Or Not
        
        isPossible
        Here we check if the number is present in column and row or not.
        The number in column can be done simply by using a iterator and traverse 
        the row and column .If present return false.
        To check in a grid:-
        Assume we are at (4,5)
        X=4 , Y=5
        So to get the starting point of sub-grid:-
        Do integer division
        SX=(X/3)*3
        SY=(Y/3)*3

