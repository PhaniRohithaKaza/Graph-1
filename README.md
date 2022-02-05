# Graph-1

## Problem1 Find Judge (https://leetcode.com/problems/find-the-town-judge/)

# Time COmplexity = O(n+len(trust))
# Space COmplexity = O(n)
class Solution:
    def findJudge(self, n: int, trust: List[List[int]]) -> int:
        degree=[0 for _ in range(n+1)]
        for i in trust:
            degree[i[0]]-=1
            degree[i[1]]+=1
        for i in range(1,n+1):
            if degree[i]==n-1:
                return i
        return -1

## Problem2 The Maze (https://leetcode.com/problems/the-maze/)


# Time COmplexity = O(mn)
# Space COmplexity = O(mn)

class Solution:
    def hasPath(self, maze: List[List[int]], start: List[int], destination: List[int]) -> bool:
        row=deque()
        col=deque() 
        maze[start[0]][start[1]]=2
        row.append(start[0])
        col.append(start[1])
        dirs=[[0,1],[0,-1],[1,0],[-1,0]]
        while row:
            curr=row.popleft()
            curc=col.popleft()
            for k in dirs:
                newi=curr+k[0]
                newj=curc+k[1]
                while(newi<len(maze) and newi>=0 and newj>=0 and newj<len(maze[0]) and maze[newi][newj]!=1):
                    newi+=k[0]
                    newj+=k[1]
                newi-=k[0]
                newj-=k[1]
                if newi==destination[0] and newj==destination[1]:
                    return True
                if maze[newi][newj]!=2:
                    maze[newi][newj]=2
                    row.append(newi)
                    col.append(newj)
        return False
                
            
            
        
        

