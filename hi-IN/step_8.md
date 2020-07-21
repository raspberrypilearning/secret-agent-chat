## संदेश एन्क्रिप्ट करना

अब मजेदार हिस्सा आता है: आप वन-टाइम पैड से शीट का उपयोग करके एक संदेश को एन्क्रिप्ट करने जा रहे हैं। इस फ़ंक्शन के दो पैरामीटर होंगे। पहला `string` के लिए होगा जिसमें प्लेनटेक्स्ट संदेश शामिल है; दूसरा वन-टाइम पैड शीट के लिए होगा, जिसका उपयोग किया जाएगा।

- आरंभ करने के लिए, आप फ़ंक्शन को परिभाषित (define) कर सकते हैं:

    ```python
    def encrypt(plaintext, sheet):
    ```

- एक बार जब आप प्लेनटेक्स्ट को एन्क्रिप्ट करना शुरू कर देते हैं, तो आपको सिफरटेक्स्ट(ciphertext) को स्टोर करना होगा। आप ऐसा करने के लिए एक खाली स्ट्रिंग का उपयोग कर सकते हैं:

    ```python
    def encrypt(plaintext, sheet):
        ciphertext = ''
    ```

- अब चतुर भाग आता है। यह फंक्शन प्लेनटेक्स्ट में हर अक्षर पर काम करने वाला है, एक प्रक्रिया जिसे 'इटरेशन' कहा जाता है। जब वह ऐसा कर रहा हो, तो उसे ट्रैक करने की जरूरत है कि वह किस अक्षर पर काम कर रहा है और उस अक्षर को प्लेनटेक्स्ट में किस स्थान पे रखा गया है। ऐसा करने के लिए, आप पहले से बनाया हुआ फ़ंक्शन `enumerate()` का उपयोग कर सकते हैं:

    ```python
    def encrypt(plaintext, sheet):
        ciphertext = ''
        for position, character in enumerate(plaintext):
    ```

- आगे यह जांचना है की प्लेनटेक्स्ट का अक्षर वर्णमाला में है या नहीं। इस प्रोग्राम में आपको खाली जगह या विराम चिह्नों को एन्क्रिप्ट करने के बारे में परेशान नहीं होना हैं, इसलिए यदि वर्ण कोई अक्षर नहीं है, तो इसे सिफरटेक्स्ट(ciphertext) स्ट्रिंग में जोड़ा जा सकता है। यह वह जगह है जहाँ हम उस `ALPHABET` कॉन्स्टन्ट (constant) का उपयोग करते हैं, जो आपने पहले लिखा था:

    ```python
    def encrypt(plaintext, sheet):
        ciphertext = ''
        for position, character in enumerate(plaintext):
            if character not in ALPHABET:
                ciphertext += character
    ```

- अगला हिस्सा समझने में थोड़ा मुश्किल है।

    - सबसे पहले, आपको वर्णमाला में प्लेनटेक्स्ट वर्ण की स्थिति को खोजना होगा - `ALPHABET.index(character)`।
    - फिर आपको इस नंबर को OTP से शीट पर समकक्ष स्थिति से मूल्य में जोड़ना होगा - `int(sheet[position])` ।
    - इस नई संख्या को वापस एक अक्षर में परिवर्तित करना होगा। यदि नई संख्या `0` थी, तो वह `a` बन जाएगी, यदि वह `5` थी, तो `f` बन जाएगी। क्या होगा यदि संख्या 25 से अधिक है? यदि संख्या `26` है, तो इसे `0` में बदलना होगा, और यदि `30` है, तो इसे `4` में बदलना होगा। ऐसा करने के लिए हम **modulo** ऑपरेटर (`%`) का उपयोग कर सकते हैं, जो विभाजन के बाद शेष का पता लगाता है।
    - अंत में, संख्या को एक अक्षर में बदल दिया जाता है।

- सभी को एक साथ आपके फ़ंक्शन में रखकर, यह इस तरह दिखाई देगा:

    ```python
    def encrypt(plaintext, sheet):
        ciphertext = ''
        for position, character in enumerate(plaintext):
            if character not in ALPHABET:
                ciphertext += character
            else:
                encrypted = (ALPHABET.index(character) + int(sheet[position])) % 26
                ciphertext += ALPHABET[encrypted]
    ```

- आप सिफरटेक्स्ट(ciphertext) को वापस करके समाप्त कर सकते हैं:

    ```python
    def encrypt(plaintext, sheet):
        ciphertext = ''
        for position, character in enumerate(plaintext):
            if character not in ALPHABET:
                ciphertext += character
            else:
                encrypted = (ALPHABET.index(character) + int(sheet[position])) % 26
                ciphertext += ALPHABET[encrypted]
        return ciphertext
    ```


- आपके फ़ंक्शन का परीक्षण करने के लिए आप अपना कोड सहेजें और चलाएं, और फिर **shell** में निम्नलिखित टाइप करें।

```python
sheet = load_sheet('otp0.txt')
encrypt('This is a secret message.', sheet)
```

![एन्क्रिप्ट आउटपुट(encrypt output)](images/screen3.png)

