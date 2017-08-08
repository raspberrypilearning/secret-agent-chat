## Decrypting messages

When communicating with your friends, you'll need a way to decrypt the message as well. The next function is very similar to the previous one, but instead of adding the value from the one-time pad's sheet, you just need to subtract the value:

```python
def decrypt(ciphertext, sheet):
    plaintext = ''
    for position, character in enumerate(ciphertext):
        if character not in ALPHABET:
            plaintext += character
        else:
            decrypted = (ALPHABET.index(character) - int(sheet[position])) % 26
            plaintext += ALPHABET[decrypted]
    return plaintext
```

- Let's test the decryption. Save and run your code, then type the following into the **shell**

	```python
	sheet = load_sheet('otp0.txt')
	ciphertext = encrypt('Nobody can read this - hehehe', sheet)
	ciphertext
	```

- You should see the encrypted text. To decrypt, just type the following line:

```python
decrypt(ciphertext, sheet)
```

![decrypt output](images/screen4.png)

