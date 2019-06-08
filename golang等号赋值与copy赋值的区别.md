---
name: "golang等号赋值与copy赋值的区别"
createdat: 2019-06-08
tags:
    - golang
    - slice
---

## golang等号赋值与copy赋值的区别

### 结论:
`copy(des, src)`

copy赋值复制的是src引用的数组的元素的值

`desc = src`

等号赋值复制的是src的切片三要素(长度,容量, 指针),
也就意味着src与desc会引用同一个数组.

这样copy赋值必定比等号赋值慢,但因为没有引用相同的数组,所以更安全.

### 示例:
**copy赋值**

```go
s1 := []int{1, 2, 3}
s2 = make([]int, len(s1))

// copy赋值
copy(s2, s1)
s2[1] = 100
fmt.Printf("s1: %v, s2: %v\n"s1, s2) // 输出 s1:[1 2 3], s2:[100, 2, 3]
```

**等号赋值**

```go
s1 := []int{1, 2, 3}
s2 = make([]int, len(s1))

// 等号赋值
s2 = s1
s2[1] = 100
fmt.Printf("s1: %v, s2: %v\n"s1, s2) // 输出 s1:[100 2 3], s2:[100, 2, 3]
```
