You are given a string s and an array of strings words. All the strings of words are of the same length.  

A concatenated string is a string that exactly contains all the strings of any permutation of words concatenated.  

For example, if words = ["ab","cd","ef"], then "abcdef", "abefcd", "cdabef", "cdefab", "efabcd", and "efcdab" are all concatenated strings. "acdbef" is not a concatenated string because it is not the concatenation of any permutation of words.  
Return an array of the starting indices of all the concatenated substrings in s. You can return the answer in any order.  

 

Example 1:  

Input: s = "barfoothefoobarman", words = ["foo","bar"]  

Output: [0,9]  

Explanation:  

The substring starting at 0 is "barfoo". It is the concatenation of ["bar","foo"] which is a permutation of words.  
The substring starting at 9 is "foobar". It is the concatenation of ["foo","bar"] which is a permutation of words.  


```
class Solution(object):
    def findSubstring(self, s, words):
        """
        :type s: str
        :type words: List[str]
        :rtype: List[int]
        """
        n = len(words[0])
        m = len(words)
        res = []
        count = collections.Counter(words)

        for i in range(len(s) - m * n + 1):
            seen = collections.defaultdict(int)
            j = 0
            while j < m:
                word = s[i + j * n : i + j * n + n]
                seen[word] += 1
                if seen[word] > count[word]:
                    break
                j += 1
                if j == m:
                    res.append(i)
        
        return res

```
**collections.Counter()**  
**A counter is a container that stores elements as dictionary keys, and their counts are stored as dictionary values.**  

**collections.defaultdict(int)**  
**Define a defaultdict with default value as int(0)**  




