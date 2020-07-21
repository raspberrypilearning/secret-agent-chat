## संदेशों को लोड करना और सहेजना

इसके बाद, आपको लिखे गए संदेशों को खोलने और एन्क्रिप्ट किए गए संदेशों को सहेजने की एक विधि की आवश्यकता होगी। फिर से, आपको कुछ काफी सरल फ़ंक्शन की आवश्यकता होगी - एक फ़ाइल को खोलने और पढ़ने के लिए, दूसरा किसी फ़ाइल को खोलने और लिखने के लिए:

```python
def load_file(filename):
    with open(filename, "r") as f:
        contents = f.read()
    return contents

def save_file(filename, data):
    with open(filename, 'w') as f:
        f.write(data)
```

