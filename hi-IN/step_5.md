## OTP से पत्र लोड करना

अब जब ओटीपी उत्पन्न हो गया है, तो आपको एक शीट (पत्र) को लोड करने और उसके सभी नंबरों को एक सूची में संग्रहीत करने का एक तरीका चाहिए।

- सबसे पहले, आप फ़ाइल खोलने के लिए एक फंक्शन बना सकते हैं:

   ```python
   def load_sheet(filename):
       with open(filename, "r") as f:
   ```

- तब आप फ़ाइल की सामग्री को एक सूची में डाल सकते हैं। `splitlines()` भाग सूची में प्रत्येक पंक्ति को किसी एक पद में तोड़ता है और `\n` वर्ण (नई पंक्ति) को भी हटाता है:

    ```python
    def load_sheet(filename):
        with open(filename, "r") as f:
            contents = f.read().splitlines()
        return contents
    ```

- अपने कोड को फिर से सहेजकर और चलाकर इस फ़ंक्शन का परीक्षण करें। अब आप **shell** में निम्नलिखित टाइप कर सकते हैं:

```python
sheet = load_sheet('otp0.txt')
print(sheet)
```

![output of load_sheet](images/screen2.png)


