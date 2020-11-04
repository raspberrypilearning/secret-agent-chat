## Writing a secret message

The next function is a really simple one: it asks the user to type in the message that will be encrypted. The only small addition is to convert all the letters to *lowercase*, as this will make it easier to encrypt without losing any meaning:

```python
def get_plaintext():
    plaintext = input('Please type your message ')
    return plaintext.lower()
```

