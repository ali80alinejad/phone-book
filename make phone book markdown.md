# **make phone book with python**
for make phone book we make some function:
* load
* write
* add user
* read 
* update 
* delete
---


<span style="color:green">***step 1*** </span>:first we import two modules for save item in system
```python

import json
import os
```

<span style="color:green">***step 2***</span> :we make empty list for keep input item
```python
phonebook = []
```


<span style="color:green">***step 3***</span> :function to load telephoon with os and json
```python

def load():
    if os.path.exists('telephon.json'):
        with open('telephon.json', 'r') as f:
            return json.load(f)
    return []
```


<span style="color:green">***step 4***</span> :we write item in phonebook list with json

```python
def write():
    with open('telephon.json', 'w') as f:
        json.dump(phonebook, f)
```

<span style="color:green">***step 5***</span> :now add user with four input and add id for search with id 
and append to phonebook
```python
def add_user():
    name = input('Enter the new name: ')
    number = input('Enter the new number: ')
    email = input('Enter the new email: ')
    address = input('Enter the new address: ')
    
    user = {
        "name": name,
        "number": number,
        "email": email,
        "address": address
    }
    
    if not phonebook:
        user['id'] = 1
    else:
        user['id'] = max(entry['id'] for entry in phonebook) + 1
        
    phonebook.append(user)
    write()
    print(f'User saved with id {user["id"]}')

```


<span style="color:green">***step 6*** </span>:how we can read user? with read function

```python
def read():
    for entry in phonebook:
        print(f"ID: {entry['id']}, Name: {entry['name']}, Number: {entry['number']}, Email: {entry['email']}, Address: {entry['address']}")
```

<span style="color:green">***step 7*** </span>:when we want change information , use update function

```python
def update():
    id = int(input('Enter the user ID to update: '))
    for user in phonebook:
        if user['id'] == id:
            order = int(input('Choose what to update: 1=name, 2=number, 3=email, 4=address: '))
            if order == 1:
                user['name'] = input('Enter updated name: ')
            elif order == 2:
                user['number'] = input('Enter updated number: ')
            elif order == 3:
                user['email'] = input('Enter updated email: ')
            elif order == 4:
                user['address'] = input('Enter updated address: ')
            else:
                print('Invalid choice')
            write()
            return
    print('User not found')
```

<span style="color:green">***step 8***</span> :delete function 

```python
def delete():
    id = int(input('Enter the user ID to delete: '))
    for i in range(len(phonebook)):
        if phonebook[i]['id'] == id:
            del phonebook[i]
            print('User deleted')
            write()
            return
    print('User not found')
```

<span style="color:green">***step 9***</span> :Load phonebook data if file exists

```python
phonebook = load()
```

<span style="color:green">***step 10*** </span>: now We need a loop to repeat the functions and access the user permanently
 ```python
while True:
    print('\nEnter your option:\n1=add user\n2=read phone book\n3=update user\n4=delete user\n5=exit')
    choice = input('Enter your choice: ')
    if choice == '1':
        add_user()
    elif choice == '2':
        read()
    elif choice == '3':
        update()
    elif choice == '4':
        delete()
    elif choice == '5':
        break
    else:
        print('Invalid option. Please try again.')
```

 
 finished you make a phone book with python :sunglasses:
 
 
 
