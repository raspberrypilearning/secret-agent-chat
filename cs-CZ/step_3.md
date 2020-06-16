## Secret agent chat

In this resource you will learn how to send secret messages using a technique called the one-time pad.

![One-time pad](https://upload.wikimedia.org/wikipedia/commons/thumb/1/19/NSA_DIANA_one_time_pad.tiff/lossless-page1-677px-NSA_DIANA_one_time_pad.tiff.png)

When you're a secret agent, sending messages to your friends can be a tricky business. If the message is seen by your enemies they'll know what you're up to, and you could be in trouble.

Cryptography is a way of disguising the contents of your message, to make it harder for your enemies to read. One of the first forms of cryptography was used by the Roman emperor Julius Caesar, and is now called the *Caesar Cipher*.

Imagine Alice wants to send a secret message to Bob, without Eve knowing what the message says. Alice first picks a **key**, which will be a number such as `3`. Alice then tells Bob the key.

Whenever Alice wants to write a message, all she needs to do is shift each of the letters in her message forward in the alphabet by 3 places:

```
abcdefghijklmnopqrstuvwxyz
defghijklmnopqrstuvwxyzabc
```

So the **plaintext**...

```
Meet me at the park at three
```

becomes the **ciphertext**...

```
Phhw ph dw wkh sdun dw wkuhh
```

The problem with this is that Eve can easily decrypt the message. She just needs to try using every number between 1 and 26 as the key, and see which one makes sense. She could also look for words with 2 or 3 letters in them that occur a lot, like 'to', 'at', 'the' or 'and', then use these to find out what the key is.

During World War II the German military thought they had developed a perfect method of encrypting messages, using something called an [Enigma machine](https://simple.wikipedia.org/wiki/Enigma_%28machine%29).

![Engima](https://upload.wikimedia.org/wikipedia/commons/thumb/3/3e/EnigmaMachineLabeled.jpg/576px-EnigmaMachineLabeled.jpg)

The German military were wrong though. Thanks to some clever Polish mathematicians and a British mathematician called Alan Turing, the Enigma messages were decrypted, and this helped the Allies win the war.

A one-time pad (OTP) is a different method of encryption. When using an OTP, a string of random numbers are generated and shared between Alice and Bob. Each letter of the message is then shifted by the corresponding number in the OTP, so each letter has its own individual key! As long as Eve doesn't have the OTP, the message is **impossible** to decrypt.


