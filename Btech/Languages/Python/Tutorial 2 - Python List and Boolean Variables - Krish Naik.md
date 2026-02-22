
---
# 🐍 Python Data Structures & Boolean Logic

---
## 1. Boolean Variables & Logical Operators

Boolean values represent truth values using `True` and `False`. In numeric contexts, they behave like `1` and `0`.

> [!TIP] String Boolean Methods
> 
> Use these to validate data before processing:
> 
> - `.isalnum()`: True if all characters are alphanumeric.
>     
> - `.isalpha()`: True if all characters are alphabetic.
>     
> - `.isdigit()`: True if string contains only digits.
>     
> - `.istitle()`: True if string follows title case (Initial letter upper case).
>     

```python
my_str = 'Krish123'
print(my_str.isalnum())       # True
print(my_str.startswith('K'))  # True
```
---
## 2. Lists

A **List** is a mutable (can be changed), ordered sequence of elements defined by square brackets `[]`.

#### Basic Operations :
```python
lst = ['Mathematics', 'chemistry', 100, 200, 300, 204]
print(len(lst))   # Returns 6
print(lst[6])     # Access element by index
print(lst[1:6])   # Slicing from index 1 to 5
```
### Adding and Merging

> [!TIP] Append vs. Extend
> 
> - Use `.append()` to add a **single item** (adds a list as one object).
>     
> - Use `.extend()` to merge multiple items while **keeping the list flat**.
>     

```python
lst = [1, 2, 3]
lst.append([4, 5]) 
# Result: [1, 2, 3, [4, 5]]

lst = [1, 2, 3, 4, 5, 6]
lst.extend([8, 9]) 
# Result: [1, 2, 3, 4, 5, 6, 8, 9]
```
---
## 3. Sets

A **Set** is an unordered collection that is iterable, mutable, and contains **no duplicate elements.**

```python
set1 = {"Avengers", "IronMan", "Hitman"}
set2 = {"Avengers", "IronMan", "Hitman", "Hulk2"}

# Intersection: Keeps only common items
set2.intersection_update(set1) 

# Difference: Removes items found in the other set
set2.difference_update(set1) 
```

---

## 4. Dictionaries

An unordered, changeable, and indexed collection of **key-value pairs**.

> [!IMPORTANT] Iteration Techniques
> 
> Python
> 
> ```
> my_dict = {"Car1": "Audi", "Car2": "BMW"}
> ```

# Dictionary Looping in Python

## Loop through KEYS
```python
for x in my_dict:
    print(x)
```
## Loop through VALUES
```python
for x in my_dict.values():
    print(x)
```
## Loop through BOTH (key and value)
```python
for key, value in my_dict.items():
    print(key, value)
```
### Nested Dictionaries

```
car_type = {
    'car1': {'Mercedes': 1960}, 
    'car2': {'Audi': 1970}
}
print(car_type['car1']['Mercedes']) # 1960
```

---

## 5. Tuples

Ordered sequences that are **immutable** (cannot be changed after creation).

Python

```
my_tuple = ("Krish", "Ankur", "John")
print(my_tuple.count('Krish')) # 1
print(my_tuple.index('Ankur')) # 1
```

---

### Why this works in Obsidian:

1. **Language Tagging:** I used ` ```python ` instead of just ` ``` `. This triggers Obsidian's internal Prism.js highlighter.
    
2. **Indentation:** I used 4 spaces for nested logic (like inside `for` loops).
    
3. **Callouts:** Used `> [!TIP]` syntax which Obsidian renders as beautiful colored blocks.
    

**Would you like me to convert any other specific code snippets or notebooks using this layout?**