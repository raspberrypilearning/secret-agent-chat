## Loading and saving the messages

Next, you're going to need a method of opening messages written to you, and saving the messages that have been encrypted. Again, you're going to need a couple of fairly basic functions - one to open and read a file, the other to open and write a file:

```python
def load_file(filename):
    with open(filename, "r") as f:
        contents = f.read()
    return contents

def save_file(filename, data):
    with open(filename, 'w') as f:
        f.write(data)
```

