# LeetCode 5: Merge Two Sorted Lists

- [Link to Problem](https://leetcode.com/problems/longest-palindromic-substring/description/)

## Solution
### Approach 1: Two Pointers
- Iterate all elements in the loop and expand the range until it is not palindrome anymore.
- Time complexity: O(N)*O(N) = O(N^2)
```go
func longestPalindrome(s string) string {
    if len(s) == 1 {
		return s
	}
    maxLen := 0
    maxStr := ""
    for i:=0 ; i<len(s) ; i++ {
        for j:=i ; j<len(s) ; j++ {
            current := s[i:j+1]
            if len(current) > maxLen {
                if isPalindromic(current) {
                    maxLen = len(current)
                    maxStr = current
                }
            }
        }
    }
    return maxStr
}

func isPalindromic(s string) bool {
    size := len(s)
    mid := size / 2
    if size % 2 == 0 {
        for i:=0 ; i< size/2; i++ {
            if string(s[mid-1-i]) != string(s[mid+i]) {
                return false
            }
        }
        return true
    } else {
        for i:=1 ; i< size/2+1; i++ {
            if string(s[mid-i]) != string(s[mid+i]) {
                return false
            }
        }
        return true
    }
}
```

### Approach 2: Manachar's Algorithm
- [Blog Post](https://dev-ujin.github.io/computer-science/algorithm/manachars-algorithm/)
- Time complexity: O(N)+O(N) = O(N)
```go
func longestPalindrome(s string) string {
	if len(s) == 1 {
		return s
	}
	S := "#" + strings.Join(strings.Split(s, ""), "#") + "#"
	P := make([]int, len(S))
	C, R := 0, 0

	for i := 1; i < len(S); i++ {
		if i < R {
			P[i] = min(R-i, P[2*C-i])
		}
		for i+P[i] < len(S)-1 && i-P[i] >= 1 &&
        S[i+P[i]+1] == S[i-1-P[i]] {
		}
		if i+P[i] > R {
			C, R = i, i+P[i]
		}
	}

	max := 0
	maxIndex := 0
	for i, v := range P {
		if v > max {
			max = v
			maxIndex = i
		}
	}

	return s[(maxIndex-max)/2 : (maxIndex+max)/2]
}

func min(a int, b int) int {
    if a < b {
        return a
    } else {
        return b
    }
}
```