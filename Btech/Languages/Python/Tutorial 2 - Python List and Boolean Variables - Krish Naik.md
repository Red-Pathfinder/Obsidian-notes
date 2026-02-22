
---
# 🐍 Python Essentials for Data Work

---

## 1️⃣ Boolean Variables & Logical Operators

Boolean values represent truth using:

```python
True
False
```

In numeric contexts:

```python
True  == 1
False == 0
```

### Common String Validation Methods

> [!TIP] Use these to clean or validate data before processing (very useful in ML preprocessing)

|Method|Description|
|---|---|
|`.isalnum()`|All characters are letters or numbers|
|`.isalpha()`|Only letters|
|`.isdigit()`|Only digits|
|`.istitle()`|Title case format|

```python
my_str = "Krish123"

print(my_str.isalnum())      # True
print(my_str.startswith('K'))  # True
```

---

## 2️⃣ Lists

A **list** is an ordered, mutable collection.

```python
lst = ['Mathematics', 'Chemistry', 100, 200, 300, 204]

print(len(lst))      # 6
print(lst[0])        # First element
print(lst[1:4])      # Slicing (index 1 to 3)
```

> ⚠️ Accessing `lst[6]` would cause **IndexError**

---

### Adding Elements

> [!TIP] Append vs Extend

- `.append()` → adds **one object**
    
- `.extend()` → adds multiple items (keeps list flat)
    

```python
lst = [1, 2, 3]
lst.append([4, 5])
# Result: [1, 2, 3, [4, 5]]

lst = [1, 2, 3]
lst.extend([4, 5])
# Result: [1, 2, 3, 4, 5]
```

---

## 3️⃣ Sets

A **set** is unordered, mutable, and contains **unique elements only**.

```python
set1 = {"Avengers", "IronMan", "Hitman"}
set2 = {"Avengers", "IronMan", "Hitman", "Hulk"}
```

### Operations

```python
# Keep only common elements
set2.intersection_update(set1)

# Remove common elements
set2.difference_update(set1)
```

Useful for:

- Removing duplicates
    
- Finding overlaps in datasets
    

---

## 4️⃣ Dictionaries

A dictionary stores **key–value pairs**.

```python
my_dict = {
    "Car1": "Audi",
    "Car2": "BMW"
}
```

---

### Iteration Techniques

#### Loop through Keys

```python
for key in my_dict:
    print(key)
```

#### Loop through Values

```python
for value in my_dict.values():
    print(value)
```

#### Loop through Both

```python
for key, value in my_dict.items():
    print(key, value)
```

---

### Nested Dictionaries

```python
car_type = {
    'car1': {'Mercedes': 1960},
    'car2': {'Audi': 1970}
}

print(car_type['car1']['Mercedes'])   # 1960
```

Nested structures appear frequently in:

- JSON data
    
- API responses
    
- ML configurations
    

---

## 5️⃣ Tuples

A **tuple** is ordered but **immutable**.

```python
my_tuple = ("Krish", "Ankur", "John")

print(my_tuple.count("Krish"))   # 1
print(my_tuple.index("Ankur"))   # 1
```

Use tuples when:

- Data should not change
    
- Representing fixed records
    

---

## 🔎 When This Matters for ML

|Structure|Common Use|
|---|---|
|List|Raw data, feature collections|
|Set|Removing duplicates|
|Dictionary|Feature mapping, JSON data|
|Tuple|Fixed records, model outputs|
|Boolean|Filtering conditions|

---

## 🧠 Mental Model

> Lists = sequences  
> Sets = uniqueness  
> Dictionaries = meaning  
> Tuples = stability  
> Booleans = decisions