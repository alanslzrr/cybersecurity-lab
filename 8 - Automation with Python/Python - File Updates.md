# Python Automation: Updating an IP Allow List

## 🎯 Project Overview

As a security professional at a healthcare company, you are tasked with maintaining a file that controls access to restricted content based on IP addresses. This guide walks you through the process of creating a Python script to update this access control list.

### 🔑 Key Objectives:
1. Read the current allow list from a file
2. Remove specific IP addresses from the list
3. Update the file with the revised list.

### 📋 IP Addresses to Remove:
- `192.168.97.225`
- `192.168.158.170`
- `192.168.201.40`
- `192.168.58.57`

> Note: The Python code for this project is available in the Jupyter Notebook file `Python - Automation.ipynb`.

## 💻 Implementation

### Step 1: Import and Read File Contents

```python
import_file = "allow_list.txt"

with open(import_file, "r") as file:
    ip_addresses = file.read()

print(ip_addresses)
```

**Explanation:**
- We use the `import` module to access the `allow_list.txt` file.
- The `open()` function with `"r"` mode is used to read the file.
- The `with` statement ensures proper file handling.
- `file.read()` returns the entire file content as a string, which is assigned to `ip_addresses`.
- There are initially 17 IP addresses in `allow_list.txt`.

**Output:**
![File Content](https://raw.githubusercontent.com/alanslzrr/cybersecurity-lab/main/assets/8.1A.png)

### Step 2: Convert String to List

```python
ip_addresses = ip_addresses.split()
print(ip_addresses)
```

**Explanation:**
- `split()` converts the string into a list, separating elements by whitespace.
- This conversion is necessary to remove individual IP addresses from the allow list.

**Output:**
```python
['ip_address', '192.168.25.60', '192.168.205.12', '192.168.97.225', '192.168.6.9', '192.168.52.90', '192.168.158.170', '192.168.90.124', '192.168.186.176', '192.168.133.188', '192.168.203.198', '192.168.201.40', '192.168.218.219', '192.168.52.37', '192.168.156.224', '192.168.60.153', '192.168.58.57', '192.168.69.116']
```

### Step 3: Remove Specified IP Addresses

```python
remove_list = ["192.168.97.225", "192.168.158.170", "192.168.201.40", "192.168.58.57"]

for element in ip_addresses:
    if element in remove_list:
        ip_addresses.remove(element)

print(ip_addresses)
```

**Explanation:**
- We define `remove_list` containing IP addresses to be removed.
- A `for` loop iterates through `ip_addresses`.
- The `if` statement checks if each element is in `remove_list`.
- `remove()` method removes the matching elements.
- The `in` keyword is used to iterate through the sequence and assign each value to the loop variable `element`.

**Output:**
```python
['ip_address', '192.168.25.60', '192.168.205.12', '192.168.6.9', '192.168.52.90', '192.168.90.124', '192.168.186.176', '192.168.133.188', '192.168.203.198', '192.168.218.219', '192.168.52.37', '192.168.156.224', '192.168.60.153', '192.168.69.116']
```

### Step 4: Update the File

```python
ip_addresses = " ".join(ip_addresses)

with open(import_file, "w") as file:
    file.write(ip_addresses)

with open(import_file, "r") as file:
    text = file.read()

print(text)
```

**Explanation:**
- `join()` converts the list back to a string, which is necessary for writing to the file.
- We open the file in `"w"` (write) mode to overwrite its contents.
- `file.write()` updates the file with the new IP list.
- We then read and print the updated file to confirm changes.
- The `"\n".join(ip_addresses)` would place each element on a new line, but we're using space-separation here.

**Output:**
![Updated File Content](https://raw.githubusercontent.com/alanslzrr/cybersecurity-lab/main/assets/8.1B.png)

## 🔍 Summary

This Python script efficiently updates an IP address allow list by:
1. Opening the file and identifying the `remove_list` variable from `allow_list.txt`.
2. Converting the string into a list for easier manipulation.
3. Removing specified IP addresses from the list.
4. Converting the list back into a string format and revising the `allow_list.txt`.

This automation ensures quick and accurate updates to access control lists, enhancing security management in the healthcare environment.

## 📌 Notes
- The `allow_list.txt` file attached in this directory contains the initial list of 17 IP addresses.
- Run the code to observe the content being revised, or check `allow_list_revised.txt` to see the differences.
- After running the script, the `allow_list.txt` will contain 13 IP addresses, with the specified IPs removed.
