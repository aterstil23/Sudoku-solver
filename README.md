# Sudoku-solver
Usually the brute force way to solve sudoku that comes in mind would be to try every possible number from 1 to 9 starting from row 1 column 1 
(if the position is not occupied) and to use a function that verifies if after entering the number the sudoku puzzle is still valid, then for each possible number added 
to the puzzle grid you call recursively the function that adds a number and checks if it valid for the next position.
What i tried to do to restrain the amount of trials needed was to create an array for each position (possibilies[row][column][possible number-1] where column 
and row range from 0 to 8, and possible number range from 1 to 9) that has all the possibilities of number that could be in that position
so that the puzzle is still valid. Then the function remove_possibilities first takes in the numbers that are already in place and removes those numbers from 
the possibilities of all the other positions from the same row column or 9 by 9 square region it corresponds. This would reduce the possibilities of 
number that can occupy each free position.
Then there's a function initial fill that checks the positions that has only one possible number that could be in that position and fills the position in the 
puzzle with that number.
Remove_possibilities is called again to remove the new numbers from the possibilities of the other positions.
Another function which mimicks human solving soduku (remove_possibilities2) checks if for a possible number at a position A(row x, column y) if the other positions 
in the same row or column or 9 by 0 square region doesn't have that possibility, if it is the case, then it narrows down the possible numbers to 1 for the
position A(row x, column y) since the other positions in the same row or column or 9 by 9 square don't have that possibility.
Initial_fill and remove_possibilties are called again in loop until there's no new number to fill.
Remove_possibilities that checks if new numbers are added or were already there fills out an array is_occupied[row][column] for each position that is 1 if
it's occupied or 0 if not so that when it is called again to remove the possibilities it skips the old already occupied number that have been taken care of.
Finally the last function (generate_possibilities) tries every possibilities left recursively until the puzzle is solved.
Do not mind the error flag at the end just see the console and if the numbers entered line by line are correct it should be solved.
So to solve a sudoku puzzle, in the console it receives user input for each line at a time where you type and enter the numbers one line at a time without space and with
0 for the empty positions.
Then you enter 1 to solve the sudoku puzzle.
