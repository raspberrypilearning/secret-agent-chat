## मेनू जोड़ना

हालांकि अब आपके पास मौजूदा OTP जनरेशन, एन्क्रिप्शन और डिक्रिप्शन है, लेकिन आपको उपयोगकर्ता के लिए प्रोग्राम को थोड़ा आसान बनाना चाहिए। इसमें एन्क्रिप्ट किए गए टेक्स्ट को सहेजना शामिल होना चाहिए, ताकि इसे आपके मित्र को ईमेल किया जा सके।

- आप मेनू के लिए एक नया फ़ंक्शन निर्धारित करके शुरू कर सकते हैं:

    ```python
    def menu():
    ```

- आप मेनू में उपयोगकर्ता को 4 विकल्प देने जा रहे हैं। अगर उनकी पसंद 1, 2, 3 या 4 नहीं है, तो वापस से पसंद पूछनी चाहिए:

    ```python
    def menu():
        choices = ['1', '2', '3', '4']
        choice = '0'
        while True:
            while choice not in choices:
    ```

- आगे, आप मेनू के लिए विकल्प जोड़ सकते हैं, और उनकी `choice` को एक वेरिएबल के रूप में सहेज सकते हैं:

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

- यदि विकल्प 1 चुना जाता है, तो उपयोगकर्ता को यह पूछना चाहिए कि वे कितनी शीट उत्पन्न करना चाहते हैं और शीट कितनी लंबी होनी चाहिए। फिर इन मूल्य(values) को `generate_otp` फ़ंक्शन में जोड़ा जा सकता है:

    ```python
    if choice == '1':
        sheets = int(input('How many one-time pads would you like to generate? '))
        length = int(input('What will be your maximum message length? '))
        generate_otp(sheets, length)
    ```

- यदि वे विकल्प 2 चुनते हैं, तो आपको उस शीट का नाम प्राप्त करने की आवश्यकता होगी जिसे वे उपयोग करना चाहते हैं और वह संदेश जो वे लिखना चाहते हैं। फिर संदेश को उनके चयन के नाम के साथ एन्क्रिप्ट और सहेजा जा सकता है:

    ```python
    elif choice == '2':
        filename = input('Type in the filename of the OTP you want to use ')
        sheet = load_sheet(filename)
        plaintext = get_plaintext()
        ciphertext = encrypt(plaintext, sheet)
        filename = input('What will be the name of the encrypted file? ')
        save_file(filename, ciphertext)
    ```

- यदि वे विकल्प 3 चुनते हैं, तो आपको फ़ाइल को एन्क्रिप्ट करने के लिए उपयोग की जाने वाली शीट का नाम और फ़ाइल को डिक्रिप्ट किए जाने वाले नाम की आवश्यकता होगी। तब फ़ाइल खोली जा सकती है, डिक्रिप्ट की जा सकती है और फ़ाइल की सामग्री प्रिंट की जा सकती है:

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

- यदि वे 4 चुनते हैं तो प्रोग्राम से बाहर निकल जाना चाहिए:

    ```python
    elif choice == '4':
        exit()
    ```

- आपको फ़ंक्शन के अंत में `choice` वेरिएबल को रीसेट करने की आवश्यकता होगी, ताकि फिर से लूप जारी रहे। अब आपका पूरा फंक्शन इस तरह दिखना चाहिए:

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

- कोड समाप्त करने के लिए, आपको केवल `menu()` फ़ंक्शन में कॉल (call) जोड़ना होगा:

```python
menu()
```

