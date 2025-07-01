+++
title= "Python Day 1 Learning Document"
date= '2025-07-01'
draft= 'false'
tags= ["learning", "python"]
categories= ["python"]
+++

# **📘 Python Day 1 Learning Document**

## ✅ **Topics Practiced**

* Variables & Data Types
* Basic Functions
* Lists
* Dictionaries
* Nested Data Access
* Control Flow (if-else)

---

## 🧠 **Session Summary and Corrections**

### 🔹 **Variables & Strings**

```python
name = "ajmal"      # ✅ Valid string assignment
age = 28            # ✅ Integer assignment
ajn = '2a'          # ✅ String with alphanumeric content
```

❌ **Mistakes:**

```python
name = "ajmal       # ❌ Missing closing quote — causes `SyntaxError: EOL while scanning string literal`
ajn = 2a            # ❌ Invalid syntax — 2a is not a valid variable assignment
```

---

### 🔹 **Printing and Types**

```python
print(name)            # ajmal
print(type(name))      # <type 'str'> (Python 2.x style)
```

❌ **Mistake:**

```python
print(type(name)       # ❌ Missing closing parenthesis
```

---

### 🔹 **Functions**

```python
def greet(name):
    return "Hello {}!".format(name)

print(greet("Ajmal"))  # ✅ Output: Hello Ajmal!
```

✅ Also tried:

```python
def myFunction(value):
    return "good job{}".format(value)
```

❌ **Common Mistakes:**

```python
def greet(name):
return "hello {name}"     # ❌ IndentationError: expected an indented block

return f"Hello {name}!"   # ❌ Python 2.7 doesn't support f-strings — upgrade to Python 3
```

---

### 🔹 **Nested Functions**

```python
def good(var1, var2):
    var3 = var1 + var2
    def food(var4):
        return var4 * 3
    return food(var3)

print(good(1, 2))  # ✅ Output: 9
```

❌ **Mistake:**

```python
print(good(2))  # ❌ Missing second argument — TypeError
```

---

### 🔹 **Lists**

```python
names = ["ajmal", good(1, 2), "Data"]
names.append(["aja", "aka"])  # ✅ Appending a sublist
print(names[2])               # Output: ['aja', 'aka']
print(names[2][1])            # Output: aka
```

❌ **Mistake:**

```python
print(names[3])        # ❌ IndexError — list index out of range
```

---

### 🔹 **Dictionaries**

```python
user = {
    "id": 101,
    "value": "aja",
    "status": "active"
}

user["email"] = "aja@mail.in"
print(user["status"])  # ✅ active
```

❌ **Mistakes:**

```python
print(user[status])            # ❌ status is not defined as a variable, use quotes
user = { ... )                # ❌ Incorrect closing bracket
user.get('status', default)   # ❌ default not defined
```

---

### 🔹 **Nested Dictionary Example**

```python
booking = {
    "booking_id": 1001,
    "user": {
        "id": 501,
        "name": "Ajmal"
    },
    "flight": "AI203",
    "status": "confirmed",
    "addons": {
        "meal": True,
        "baggage": "15kg"
    }
}

# ✅ Accessing nested values and modifying
booking["addons"]["baggage"] = "20Kg"
booking["addons"]["priority_boarding"] = True

print(booking["user"]["name"] + " your Flight number is : " + booking["flight"])
# Output: Ajmal your Flight number is : AI203
```

---

### 🔹 **Control Flow**

```python
if booking["addons"]["meal"] == True:
    print("works")
else:
    print("not works")
# ✅ Output: works
```

---

## 📌 **Tips & Learnings Recap**

| Mistake                                         | Correction                                 | Reason                                    |
| ----------------------------------------------- | ------------------------------------------ | ----------------------------------------- |
| Missing quotes in string                        | `"ajmal"` instead of `"ajmal`              | String must be enclosed in quotes         |
| Invalid syntax (`2a`)                           | `'2a'`                                     | Variable values must follow type rules    |
| Indentation                                     | Indent `return` under `def`                | Python enforces indentation               |
| Using f-strings in Python 2                     | Use `str.format()`                         | f-strings work only in Python 3.6+        |
| Accessing dict key without quotes               | Use `'status'` instead of `status`         | Dictionary keys must be strings           |
| `.get(..., default)` without defining `default` | Use a string like `.get('key', 'default')` | Default value must be defined or provided |

---
