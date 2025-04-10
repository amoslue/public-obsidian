#python
list use "[]" tuple use "()"
![[Pasted image 20250121001739.png]]
![[Pasted image 20250121001824.png]]
## Lambda

- Using `lambda` with `sorted()`
```python
# List of tuples (name, age)
people = [("Alice", 30), ("Bob", 25), ("Charlie", 35)]
# Sort by age (second element of each tuple)
sorted_people = sorted(people, key=lambda person: person[1])
print(sorted_people)
# Output: [('Bob', 25), ('Alice', 30), ('Charlie', 35)]
```


- Using `lambda` with `filter()`
```python
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
# Filter out even numbers (keep only odd numbers)
odd_numbers = list(filter(lambda x: x % 2 != 0, numbers))
print(odd_numbers)
# Output: [1, 3, 5, 7, 9]
```


- Using lambda with map()
```python
numbers = [1, 2, 3, 4, 5]
# Multiply each number by 2
doubled_numbers = list(map(lambda x: x * 2, numbers))
print(doubled_numbers)
# Output: [2, 4, 6, 8, 10]

```