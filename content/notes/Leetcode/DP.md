- 413
- 300 (LIS)
- 1671 (LIS + LDS)
- 1048 (hashmap)
- 2070 
```python
class Solution:
	def maximumBeauty(self, items: List[List[int]], queries: List[int]) -> List[int]:
		items.sort()
		# how to sort array with index
		queries = sorted([(q, i) for i,q in enumerate(queries)])
		ret = [0]*len(queries)
		j = 0
		cur_max = 0
		
		for q,i in queries:
			while j<len(items) and items[j][0]<=q:
				cur_max = max(cur_max, items[j][1])
				j+=1
			ret[i] = cur_max
	return ret
```