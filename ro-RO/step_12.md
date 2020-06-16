## Using the program

While a one-time pad offers perfect secrecy, you still have to be careful if you want to remain really secure, and there are some issues with this program.

- To send encrypted messages to each other, you can use email, SMS or even social media such as Facebook or Twitter. It won't even matter if your posts are public, as the only person who could decrypt the message is your friend.
- Once you've generated your OTP, such as by generating 100 sheets, you need to transfer them to the person you want to communicate with. You can't send them electronically, such as by email, as this is insecure. Probably the most secure method is giving them to your friend on a storage device, such as an SD card or USB flash memory.
- The OTP method is only secure if you and your friend *keep the OTP secure*.
- You and your friend need to be sure which OTP you're using. The best way of doing this is by starting with `otp0.txt` and then deleting it when you've encrypted or decrypted a message. You can then progress to using `otp1.txt`.
- The OTP relies on the randomness of the random number generator. If the generator isn't truly random, then the OTP could be cracked. Python's `random` module is probably not the best way of generating random numbers.
- Your message can't be longer than the length of the sheet from the OTP. If you're not sure how long your messages will be, it's better to generate large sheets just in case.

