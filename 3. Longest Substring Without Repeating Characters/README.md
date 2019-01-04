# Longest Substring Without Repeating Characters

Medium

Given a string, find the length of the **longest substring** without repeating characters.

**Example 1:**

```
Input: "abcabcbb"
Output: 3 
Explanation: The answer is "abc", with the length of 3. 
```

**Example 2:**

```
Input: "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
```

**Example 3:**

```
Input: "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3. 
             Note that the answer must be a substring, "pwke" is a subsequence and not a substring.
```

# 思路：

这题做了两个小时也没能做出正确答案，去参考了discussion中最高的正确答案，

```python
class Solution:
    # @return an integer
    def lengthOfLongestSubstring(self, s):
    	used = {}
    	max_length = start = 0
    	for i, c in enumerate(s):
    	    if c in used and start <= used[c]:
    	        start = used[c] + 1
    	    else:
    	        max_length = max(max_length, i - start + 1)
    	        
    	    used[c] = i
	
    	
    	return max_length
```

used字典中存储了char的最新index，c in used 为在字典中进行查找，时间复杂度为$O(1)$。但是有很多人会问，为什么要有start <= used[c]这个判断。 我觉得有个解释特别好，After we do `start = usedChar[s[i]] + 1`, there could be characters whose last seen indexes stored in `usedChar` are from before `start`. We don't want to consider those characters as repeats because we are only considering the substring from `start` to `i` each iteration.



并且可以举出如下例子：

Here's an example: "tmmzuxta"

Two characters are repeated: t and m. Because of the repeated m, your `start` will be 2. Now, when you're at the second occurrence of t, this check ensures that you don't go into the `if` just because you've seen it before. In this case, you have seen it before BUT you saw it before you started the count.

If you remove that condition, your `maxlength` will be 5. Otherwise it will be 6 - which is the right answer。即在m重复之前，已经出现过t，而当再次出现t的时候，这并不能算作重复，因为这时候我们计算长度是从start开始到目前第二个t，即从index为3到index为6，而第一个t的index为0，在start index(3)之前，这并不在我们的计算长度范围内，所以我们认为第二个t目前不算重复。

# 解题：

参考如上解题方案。