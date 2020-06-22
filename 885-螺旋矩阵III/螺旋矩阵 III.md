# 螺旋矩阵 III


golang
```go
func spiralMatrixIII(R int, C int, r0 int, c0 int) [][]int {
    moves := R * C

    res := make([][]int, 1, moves)
    res[0] = []int{r0, c0}
    moves--
    
    dx, dy := 0, 1
    round := 2
    
    for moves > 0 {
        for m := round / 2; m > 0; m-- {
            r0 += dx
            c0 += dy
            if 0 <= r0 && r0 < R && 0 <= c0 && c0 < C {
                res = append(res, []int{r0, c0})
                moves--
            }
        }
        round++
        
        dx, dy = dy, -dx
    }

    return res
}
```

注意 dx, dy 的变化 以及 round 的计算