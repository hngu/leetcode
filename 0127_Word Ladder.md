### 127. Word Ladder
Hard

A transformation sequence from word beginWord to word endWord using a dictionary wordList is a sequence of words beginWord -> s1 -> s2 -> ... -> sk such that:

Every adjacent pair of words differs by a single letter.
Every si for 1 <= i <= k is in wordList. Note that beginWord does not need to be in wordList.
sk == endWord
Given two words, beginWord and endWord, and a dictionary wordList, return the number of words in the shortest transformation sequence from beginWord to endWord, or 0 if no such sequence exists.
 

**Example 1:**
```
Input: beginWord = "hit", endWord = "cog", wordList = ["hot","dot","dog","lot","log","cog"]
Output: 5
Explanation: One shortest transformation sequence is "hit" -> "hot" -> "dot" -> "dog" -> cog", which is 5 words long.
```

**Example 2:**
```
Input: beginWord = "hit", endWord = "cog", wordList = ["hot","dot","dog","lot","log"]
Output: 0
Explanation: The endWord "cog" is not in wordList, therefore there is no valid transformation sequence.
``` 

**Constraints:**
```
1 <= beginWord.length <= 10
endWord.length == beginWord.length
1 <= wordList.length <= 5000
wordList[i].length == beginWord.length
beginWord, endWord, and wordList[i] consist of lowercase English letters.
beginWord != endWord
All the words in wordList are unique.
```

**Tags**
- Revisit
- BFS
- Hashmap

### Solution
```
class Solution:
    def ladderLength(self, beginWord: str, endWord: str, wordList: List[str]) -> int:
        """
            If the end word is not in word list, then return False
            
            We have to create a graph using a hash map where:
            - the key is the pattern like "d*t"
            - and the value is the list of words that fit that pattern: [dot]
            
            After building this graph, use BFS to traverse the graph
            and see if you reach the endWord.
            
            To efficiently do this, have a count[word] -> # of words from beginWord to reach word
            Seed it with count[beginWord] = 1 which is 1 transformation to beginWord -> beginWord
            
            Pop the element from the queue
            Then generate patterns for that element and check if those patterns are in the 
            graph.
            
            Use the count map as a way to skip traversing already traversed steps 
            
            At the end of BFS, return count[endWord]
        """
        if endWord not in wordList:
            return 0
        
        # build the graph
        patterns = collections.defaultdict(list)
        for word in wordList:
            length = len(word)
            for i in range(length):
                pattern = word[:i] + '*' + word[i+1:]
                patterns[pattern].append(word)
        
        queue = collections.deque([beginWord])
        count = collections.defaultdict(int)
        
        # seed the beginWord
        count[beginWord] = 1
        
        while queue:
            word = queue.popleft()
            
            if word == endWord:
                break
                
            n = count[word]
            
            length = len(word)
            for i in range(length):
                pattern = word[:i] + '*' + word[i+1:]
                if pattern in patterns:
                    for candidate in patterns[pattern]:
                        if candidate not in count:
                            count[candidate] = n + 1
                            queue.append(candidate)
        
        return count[endWord]
        
        
```
