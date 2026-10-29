# n_queen_problem
#The N-Queen Problem is a classic problem in computer science and combinatorial optimization.
def solve_n_queen(n):
    cols,diag1,diag2 = set(), set(), set()
    placement = [-1] * n
    solutions = []

    def backtrack(row):
        if row == n:
            solutions.append(placement.copy())
            return
        for col in range(n):
            if col in cols or row-col in diag1 or row+col in diag2:
                continue
            placement[row] = col
            cols.add(col); diag1.add(row-col);diag2.add(row+col)
            backtrack(row+1)
            cols.remove(col); diag1.remove(row-col); diag2.remove(row+col)
            placement[row] = -1
    if n>0:
        backtrack(0)
    return solutions


