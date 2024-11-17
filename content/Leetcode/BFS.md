- [317] (https://www.youtube.com/watch?app=desktop&v=yjHXS2w_IvY):
```python
class Solution:
	def shortestDistance(self, grid: List[List[int]]) -> int:
	rows = len(grid)
	cols = len(grid)

	dist_matrix = [[0]*cols for row in range(rows)]
	directions = [(1,0), (0,1), (-1,0), (0,-1)]
	
	LAND = 0
	BUILDING = 1
	OBSTACLE = 2

	ret = float('inf')

	for row in range(rows):
		for col in range(cols):
			# count from the building perspective
			if grid[row][col] == BUILDING:
				local_min = float('inf)
				queue = collections.deque([row, col, 0])
				while queue:
					cur_row, cur_col, distant = queue.popleft()
					for row_inc, col_inc: directions
					new_row = cur_row+row_inc
					new_col = cur_col+col_inc
					
					# not out of bond && is empty land				
					if validate:
						# to avoid infinite loop
						grid[row][col] -=1
						dist_matrix[new_row][new_col]+=distant+1
						queue.append([new_row, new_col, distant+1])
						local_min = min(local_min, dist_matrix[new_row][new_col])
				# to update new land mark		
				LAND -= 1
				ret = local_min
				
	return ret if ret != float('inf') else -1
				
						
			
	

```