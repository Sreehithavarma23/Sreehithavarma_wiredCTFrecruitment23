#Crypto Layers

-From the data given in the description and in the hint box
- I figured out that the given data is in encrypted form i should decrypt that to find flag
- from the hint box I should use 3 kinds of decypters to decode that
- First one i should use a binary decoder as mention in the hint box
- With using binary decoder i got a decrypted value of the code given in description
- after that i used caesar cipher decoder to decrypt that value we got in binary decoder and the key is (-5)
- Then with the value we got using cipher decoder then i decrypt that value using vigenere cipher decoder and found the flag
- I used 3 layers(binary decoder,caesar cipher decoder,vigenere decoder) to decrypt and find the flag

Binary decoder i used (https://cryptii.com/pipes/binary-decoder)

Ceasar cipher decoder with key -5 (https://www.dcode.fr/caesar-cipher)

vigenere decoder (https://www.dcode.fr/vigenere-cipher)
