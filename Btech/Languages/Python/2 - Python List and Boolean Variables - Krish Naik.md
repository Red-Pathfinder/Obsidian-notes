
**Tags:** #python #programming #data-structures

**Related Notes:** [[Python-Functions]], [[Time-Complexity-Big-O]], [[Object-Oriented-Programming]]

---

## 1. Boolean Variables & Logical Operators

Boolean values represent truth values using `True` and `False`. In numeric contexts, they behave like $1$ and $0$.

### String Boolean Methods

Use these to validate data before processing:

- `.isalnum()`: `True` if all characters are alphanumeric.
    
- `.isalpha()`: `True` if all characters are alphabetic.
    
- `.isdigit()`: `True` if string contains only digits.
    
- `.istitle()`: `True` if string follows title case.

```python
my_str = 'Krish123'
print(my_str.isalnum())       # True
print(my_str.startswith('K'))  # True
```

---

## 2. Lists

**Properties:** #mutable, ordered sequence. Defined by `[]`.

### Basic Operations

> [!WARNING]
> 
> In your example `print(lst[6])`, Python will throw an `IndexError`. Since the length is 6, the highest index is **5**.

```python
lst = ['Mathematics', 'chemistry', 100, 200, 300, 204]
print(len(lst))    # Returns 6
print(lst[5])      # Access last element (204)
print(lst[1:4])    # Slicing: ['chemistry', 100, 200]
```

### Adding and Merging: Append vs. Extend

- **`.append()`**: Adds the input as **one single object** (creates a nested list if input is a list).
    
- **`.extend()`**: Unpacks the input and adds elements individually (**flattens** the result).


---

## 3. Sets

**Properties:** #unordered, #iterable, no duplicate elements.
- Uses Hash Maps $\rightarrow$ Faster 
- Doesn't support Indexing.

```python
set1 = {"Avengers", "IronMan", "Hitman"}
set2 = {"Avengers", "IronMan", "Hitman", "Hulk2"}

# Intersection: Keeps only common items
set2.intersection_update(set1) # changes the original set1

# Finds common tuples but doesn't change the original set1
set2.intersection(set1) 

# Difference: Removes items found in the other set
set2.difference_update(set1) 
```

---

## 4. Dictionaries

An unordered, changeable, and indexed collection of **Key-Value** pairs. Often compared to [[JSON]] format.
- Indexing possible but with a catch
		$\rightarrow$ We do not pass 0, 1, 2, 3,... but instead we pass **key names**.
### Iteration Techniques

```python
my_dict = {
			"Car1": "Audi", 
			"Car2": "BMW"
			}

# Loop through KEYS
for x in my_dict:
    print(x)

# Loop through VALUES
for x in my_dict.values():
    print(x)

# Loop through BOTH (Items)
for k, v in my_dict.items():
    print(f"Key: {k}, Value: {v}")
```

### Nested Dictionaries

```python
car_type = {
    'car1': {'Mercedes': 1960}, 
    'car2': {'Audi': 1970}
}
print(car_type['car1']['Mercedes']) # 1960
```

---

## 5. Tuples

**Properties:** #immutable (cannot be changed after creation). Use these for data that should remain a "constant" throughout your program.

```python
my_tuple = ("Krish", "Ankur", "John")
print(my_tuple.count('Krish')) # 1
print(my_tuple.index('Ankur')) # 1
```

---
