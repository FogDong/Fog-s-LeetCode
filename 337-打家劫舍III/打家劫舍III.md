# 打家劫舍 III

```go
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
func rob(root *TreeNode) int {
    return dfs(root, true)
}

func dfs(t *TreeNode, state bool) int {
    if t == nil {
        return 0
    }
    if state {
        return max(t.Val+dfs(t.Left, false) + dfs(t.Right, false), dfs(t.Left, true) + dfs(t.Right, true))
    } else {
        return dfs(t.Left, true) + dfs(t.Right, true)
    }
}

func max(x, y int) int {
    if x > y {
        return x
    }
    return y
}
```
