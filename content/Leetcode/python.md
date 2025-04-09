#python
list use "[]" tuple use "()"
![[Pasted image 20250121001739.png]]
![[Pasted image 20250121001824.png]]
## Lambda
```python
# List of tuples (name, age)
people = [("Alice", 30), ("Bob", 25), ("Charlie", 35)]

# Sort by age (second element of each tuple)
sorted_people = sorted(people, key=lambda person: person[1])

print(sorted_people)
# Output: [('Bob', 25), ('Alice', 30), ('Charlie', 35)]

```