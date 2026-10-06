# Python Day 10 — Function Arguments, Return Values & Scope

## 📌 Topics Covered

Today we will learn:

1. Function Arguments
2. Positional Arguments
3. Keyword Arguments
4. Default Arguments
5. Variable-Length Arguments
6. `*args`
7. `**kwargs`
8. Return Values
9. Returning Multiple Values
10. Local Scope
11. Global Scope
12. `global` Keyword
13. Practical Cloud/DevOps Examples
14. Practice Questions

---

# 1. Function Arguments

Arguments are the values that we pass to a function when calling it.

### Example

```python
def greet(name):
    print("Hello", name)

greet("Adi")
```

Output:

```text
Hello Adi
```

Here:

- `name` → parameter
- `"Adi"` → argument

### Simple Difference

**Parameter:** Variable written inside the function definition.

**Argument:** Actual value passed when calling the function.

---

# 2. Positional Arguments

Arguments can be passed according to their position.

```python
def student(name, age):
    print("Name:", name)
    print("Age:", age)

student("Adi", 21)
```

Output:

```text
Name: Adi
Age: 21
```

The first value goes to `name`.

The second value goes to `age`.

---

# 3. Order Matters in Positional Arguments

```python
def student(name, age):
    print(name)
    print(age)

student("Adi", 21)
```

Correct.

But:

```python
student(21, "Adi")
```

The values will be assigned differently:

```text
Name: 21
Age: Adi
```

So positional arguments depend on order.

---

# 4. Keyword Arguments

With keyword arguments, we explicitly specify the parameter name.

```python
def student(name, age):
    print("Name:", name)
    print("Age:", age)

student(age=21, name="Adi")
```

Output:

```text
Name: Adi
Age: 21
```

Here the order doesn't matter because we specify the parameter names.

---

# 5. Positional vs Keyword Arguments

### Positional

```python
student("Adi", 21)
```

### Keyword

```python
student(name="Adi", age=21)
```

Keyword arguments are often easier to understand when a function has many parameters.

---

# 6. Default Arguments

A default argument has a value that is automatically used if the user doesn't provide one.

```python
def greet(name="User"):
    print("Hello", name)

greet()
```

Output:

```text
Hello User
```

If we provide a value:

```python
greet("Adi")
```

Output:

```text
Hello Adi
```

The provided value replaces the default value.

---

# 7. Practical Example — Server Status

```python
def server_status(server="EC2"):
    print(server, "is running")

server_status()
```

Output:

```text
EC2 is running
```

We can also provide another server:

```python
server_status("Web Server")
```

Output:

```text
Web Server is running
```

---

# 8. Multiple Parameters

A function can have multiple parameters.

```python
def server_info(name, region, status):
    print("Server:", name)
    print("Region:", region)
    print("Status:", status)

server_info("EC2-1", "ap-south-1", "Running")
```

Output:

```text
Server: EC2-1
Region: ap-south-1
Status: Running
```

---

# 9. Return Values

`return` sends a value back from a function.

```python
def add(a, b):
    return a + b

result = add(10, 20)

print(result)
```

Output:

```text
30
```

The function calculates:

```text
10 + 20 = 30
```

Then `return` sends `30` back.

---

# 10. `print()` vs `return`

This is very important.

### Using `print()`

```python
def add(a, b):
    print(a + b)

result = add(10, 20)

print(result)
```

Output:

```text
30
None
```

Why?

Because `print()` only displays the result.

It does not send the result back to the caller.

---

### Using `return`

```python
def add(a, b):
    return a + b

result = add(10, 20)

print(result)
```

Output:

```text
30
```

`return` allows us to store and use the result.

---

# 11. Using Returned Values

```python
def square(number):
    return number * number

result = square(5)

print(result)
```

Output:

```text
25
```

We can also directly use it:

```python
print(square(5))
```

Output:

```text
25
```

---

# 12. Returning Strings

```python
def get_region():
    return "ap-south-1"

region = get_region()

print(region)
```

Output:

```text
ap-south-1
```

---

# 13. Returning Boolean Values

A function can return `True` or `False`.

```python
def is_running(status):
    return status == "Running"

result = is_running("Running")

print(result)
```

Output:

```text
True
```

This is useful for checking conditions.

---

# 14. Practical Cloud Example

```python
def check_server(status):
    if status == "Running":
        return True
    else:
        return False

server_running = check_server("Running")

if server_running:
    print("Server is available")
else:
    print("Server is stopped")
```

Output:

```text
Server is available
```

---

# 15. Returning Multiple Values

Python allows a function to return multiple values.

```python
def server_info():
    return "EC2-1", "ap-south-1", "Running"

name, region, status = server_info()

print(name)
print(region)
print(status)
```

Output:

```text
EC2-1
ap-south-1
Running
```

Python internally returns these values as a tuple.

---

# 16. Function with a List

Functions can accept lists as arguments.

```python
def show_servers(servers):
    for server in servers:
        print(server)

servers = ["EC2-1", "EC2-2", "EC2-3"]

show_servers(servers)
```

Output:

```text
EC2-1
EC2-2
EC2-3
```

---

# 17. Function with a Dictionary

```python
def show_server(server):
    print("Name:", server["name"])
    print("Region:", server["region"])
    print("Status:", server["status"])

server = {
    "name": "EC2-1",
    "region": "ap-south-1",
    "status": "Running"
}

show_server(server)
```

Output:

```text
Name: EC2-1
Region: ap-south-1
Status: Running
```

---

# 18. Variable-Length Arguments

Sometimes we don't know how many arguments the user will provide.

Python provides:

```text
*args
```

and

```text
**kwargs
```

---

# 19. `*args`

`*args` allows a function to accept multiple positional arguments.

```python
def numbers(*args):
    print(args)

numbers(10, 20, 30, 40)
```

Output:

```text
(10, 20, 30, 40)
```

The values are stored inside a tuple.

---

# 20. Using `*args` with a Loop

```python
def show_servers(*servers):
    for server in servers:
        print(server)

show_servers("EC2-1", "EC2-2", "EC2-3")
```

Output:

```text
EC2-1
EC2-2
EC2-3
```

This is useful when the number of arguments can change.

---

# 21. `**kwargs`

`**kwargs` allows a function to accept multiple keyword arguments.

```python
def server_info(**details):
    print(details)

server_info(
    name="EC2-1",
    region="ap-south-1",
    status="Running"
)
```

Output:

```text
{'name': 'EC2-1', 'region': 'ap-south-1', 'status': 'Running'}
```

`kwargs` is stored as a dictionary.

---

# 22. Looping Through `**kwargs`

```python
def server_info(**details):
    for key, value in details.items():
        print(key, ":", value)

server_info(
    name="EC2-1",
    region="ap-south-1",
    status="Running"
)
```

Output:

```text
name : EC2-1
region : ap-south-1
status : Running
```

---

# 23. Scope

Scope means **where a variable can be accessed in a program**.

The two important scopes for beginners are:

- Local scope
- Global scope

---

# 24. Local Scope

A variable created inside a function is usually a local variable.

```python
def my_function():
    name = "Adi"
    print(name)

my_function()
```

Output:

```text
Adi
```

But this will cause an error:

```python
def my_function():
    name = "Adi"

my_function()

print(name)
```

Why?

Because `name` exists only inside the function.

---

# 25. Global Scope

A variable created outside a function is a global variable.

```python
name = "Adi"

def greet():
    print(name)

greet()
```

Output:

```text
Adi
```

The function can read the global variable.

---

# 26. Local and Global Variables with Same Name

```python
name = "Global Adi"

def test():
    name = "Local Adi"
    print(name)

test()

print(name)
```

Output:

```text
Local Adi
Global Adi
```

The function uses the local variable.

Outside the function, the global variable is used.

---

# 27. `global` Keyword

If we want to modify a global variable from inside a function, we can use `global`.

```python
count = 0

def increase():
    global count
    count = count + 1

increase()

print(count)
```

Output:

```text
1
```

Without `global`, Python would treat `count` inside the function as a local variable when assigning to it.

---

# 28. Practical Example — Server Count

```python
server_count = 0

def add_server():
    global server_count
    server_count += 1

add_server()
add_server()
add_server()

print("Total servers:", server_count)
```

Output:

```text
Total servers: 3
```

For beginner programs this demonstrates `global`, although in larger applications it is usually better to avoid unnecessary global state.

---

# 29. Function Arguments + Return

We can combine arguments and return values.

```python
def calculate_cost(hours, price):
    return hours * price

cost = calculate_cost(5, 10)

print("Cost:", cost)
```

Output:

```text
Cost: 50
```

Flow:

```text
Arguments
    ↓
Function
    ↓
Calculation
    ↓
return
    ↓
Result
```

---

# 30. Practical Cloud/DevOps Example

Suppose we want to check whether an EC2 instance is running.

```python
def check_ec2(status):
    if status == "running":
        return "EC2 instance is running"
    else:
        return "EC2 instance is stopped"

result = check_ec2("running")

print(result)
```

Output:

```text
EC2 instance is running
```

---

# 31. AWS Region Function

```python
def check_region(region):
    if region == "ap-south-1":
        return "Mumbai region"
    else:
        return "Different region"

result = check_region("ap-south-1")

print(result)
```

Output:

```text
Mumbai region
```

---

# 32. Complete Example

```python
def server_check(name, region, status="Running"):
    if status == "Running":
        return f"{name} is running in {region}"
    else:
        return f"{name} is stopped"

result = server_check(
    "EC2-1",
    "ap-south-1"
)

print(result)
```

Output:

```text
EC2-1 is running in ap-south-1
```

This example combines:

- Parameters
- Arguments
- Default arguments
- Conditions
- Return values
- f-strings

---

# 33. Important Difference

### Parameter

```python
def greet(name):
```

`name` is a parameter.

### Argument

```python
greet("Adi")
```

`"Adi"` is an argument.

### Return

```python
return name
```

Sends a value back.

### Scope

Determines where variables can be accessed.

---

# 34. Common Beginner Mistakes

### Mistake 1 — Forgetting parentheses

Wrong:

```python
greet
```

Correct:

```python
greet()
```

---

### Mistake 2 — Forgetting `return`

```python
def add(a, b):
    a + b
```

This doesn't return the result.

Correct:

```python
def add(a, b):
    return a + b
```

---

### Mistake 3 — Confusing `print()` and `return`

```python
print()
```

displays something.

```python
return
```

sends something back from the function.

---

### Mistake 4 — Using a local variable outside its function

```python
def test():
    x = 10

test()

print(x)
```

This causes a `NameError`.

---

# 35. Practice Questions

### Practice 1

Create a function that accepts two numbers and returns their sum.

```python
def add(a, b):
    return a + b
```

---

### Practice 2

Create a function that accepts a server name and returns:

```text
Server <name> is running
```

---

### Practice 3

Create a function that accepts an AWS region and checks whether it is:

```text
ap-south-1
```

---

### Practice 4

Create a function using a default parameter:

```text
cloud = "AWS"
```

---

### Practice 5

Create a function using `*args` to print multiple server names.

---

### Practice 6

Create a function using `**kwargs` to display server information.

---

# 36. Day 10 Summary

Today you learned how to make functions more powerful and reusable.

### Function Arguments

```python
def greet(name):
```

### Positional Arguments

```python
greet("Adi")
```

### Keyword Arguments

```python
greet(name="Adi")
```

### Default Arguments

```python
def greet(name="User"):
```

### Variable Arguments

```python
*args
```

### Keyword Variable Arguments

```python
**kwargs
```

### Return Values

```python
return value
```

### Local Scope

Variables created inside a function.

### Global Scope

Variables created outside a function.

### Global Keyword

```python
global variable
```

---

# ✅ Day 10 Checklist

- [ ] Understand function parameters
- [ ] Understand arguments
- [ ] Use positional arguments
- [ ] Use keyword arguments
- [ ] Use default arguments
- [ ] Understand `*args`
- [ ] Understand `**kwargs`
- [ ] Use `return`
- [ ] Return multiple values
- [ ] Understand local scope
- [ ] Understand global scope
- [ ] Understand the `global` keyword
- [ ] Practice Cloud/DevOps examples

---

## 🚀 What You Learned

By the end of Day 10, you can create functions that accept different types of inputs, process those inputs, return useful results, and control how variables are accessed within your program.

These concepts are especially important for Cloud and DevOps automation because functions are commonly used to organize tasks such as checking server status, processing AWS resource information, handling configuration data, and automating repetitive operations.

## 📅 Day 11 Preview

**Modules and Imports**

You will learn how to:

- Create Python modules
- Import modules
- Use built-in modules
- Use `import`
- Use `from ... import`
- Create your own modules
- Organize Python programs
- Use modules in automation projects
