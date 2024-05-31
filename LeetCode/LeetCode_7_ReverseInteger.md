# LeetCode 7: Reverse Integer

- [Link to Problem](https://leetcode.com/problems/reverse-integer/)

## Solution
```go
func reverse(x int) int {
	input := int32(x)
	base := int32(10)
	reversed := int32(0)

	for input != 0 {
		digit := input % base
		input = input / base
		current := reversed * base + digit
		if (current - digit)/base != reversed {
			return 0
		}
        reversed = current
	}
	return int(reversed)
}
```