## Adding a menu

Although you now have working OTP generation, encryption and decryption, you should make the program a little easier for the user. This should include saving the encrypted text, so that it can be emailed to your friend.

- You can begin by defining a new function for the menu:

	```python
	def menu():
	```

- You're going to give the user 4 choices in the menu. It should just loop if their choice isn't 1, 2, 3 or 4:

	```python
	def menu():
		choices = ['1', '2', '3', '4']
		choice = '0'
		while True:
			while choice not in choices:
	```

- Next, you can add in the options for the menu, and save their `choice` as a variable:

	```python
	def menu():
		choices = ['1', '2', '3', '4']
		choice = '0'
		while True:
			while choice not in choices:
				print('What would you like to do?')
				print('1. Generate one-time pads')
				print('2. Encrypt a message')
				print('3. Decrypt a message')
				print('4. Quit the program')
				choice = input('Please type 1, 2, 3 or 4 and press Enter ')
	```

- If option 1 is chosen, then the user needs to be asked how many sheets they want to generate and how long the sheets should be. These values can then be fed into the `generate_otp` function:

	```python
	if choice == '1':
		sheets = int(input('How many one-time pads would you like to generate? '))
		length = int(input('What will be your maximum message length? '))
		generate_otp(sheets, length)
	```

- If they choose option 2, then you need to get the name of the sheet they wish to use and the message they want to write. Then the message can be encrypted and saved with a name of their choosing:

	```python
	elif choice == '2':
		filename = input('Type in the filename of the OTP you want to use ')
		sheet = load_sheet(filename)
		plaintext = get_plaintext()
		ciphertext = encrypt(plaintext, sheet)
		filename = input('What will be the name of the encrypted file? ')
		save_file(filename, ciphertext)
	```

- If they choose option 3, then you need to get the name of the sheet used to encrypt the file and the name for the file to be decrypted. The file can then be opened, decrypted, and the contents printed out:

	```python
	elif choice == '3':
		filename = input('Type in the filename of the OTP you want to use ')
		sheet = load_sheet(filename)
		filename = input('Type in the name of the file to be decrypted ')
		ciphertext = load_file(filename)
		plaintext = decrypt(ciphertext, sheet)
		print('The message reads:')
		print('')
		print(plaintext)
	```

- If they choose 4 then the program should exit:

	```python
	elif choice == '4':
		exit()
	```

- You need to reset the `choice` variable at the end of the function, so that the loop will continue around. Your entire function should now look like this:

	```python
	def menu():
		choices = ['1', '2', '3', '4']
		choice = '0'
		while True:
			while choice not in choices:
				print('What would you like to do?')
				print('1. Generate one-time pads')
				print('2. Encrypt a message')
				print('3. Decrypt a message')
				print('4. Quit the program')
				choice = input('Please type 1, 2, 3 or 4 and press Enter ')
				if choice == '1':
					sheets = int(input('How many one-time pads would you like to generate? '))
					length = int(input('What will be your maximum message length? '))
					generate_otp(sheets, length)
				elif choice == '2':
					filename = input('Type in the filename of the OTP you want to use ')
					sheet = load_sheet(filename)
					plaintext = get_plaintext()
					ciphertext = encrypt(plaintext, sheet)
					filename = input('What will be the name of the encrypted file? ')
					save_file(filename, ciphertext)
				elif choice == '3':
					filename = input('Type in the filename of the OTP you want to use ')
					sheet = load_sheet(filename)
					filename = input('Type in the name of the file to be decrypted ')
					ciphertext = load_file(filename)
					plaintext = decrypt(ciphertext, sheet)
					print('The message reads:')
					print('')
					print(plaintext)
				elif choice == '4':
					exit()
				choice = '0'
	```

- To finish off the code, you just need to add a call to the `menu()` function:

```python
menu()
```

