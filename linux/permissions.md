# permissions

directory - execute - to walk inside but it doesnt allow user to modify

Binary Notation:                4 2 1  |  4 2 1  |  4 2 1
----------------------------------------------------------
Binary Representation:          1 1 1  |  1 0 1  |  1 0 0
----------------------------------------------------------
Octal Value:                      7    |    5    |    4
----------------------------------------------------------
Permission Representation:      r w x  |  r - x  |  r - -


suid, sgid - temporary access pass. s in place of x
program runs with permissions of owner, group instead of that of the user

Sticky Bit

shared folders

t - 
T - all other users do not have permissions
