When we download the cipher2.txt file, we get below

![image](https://github.com/nenowoDev/rentas2024/assets/38612806/2b4552a9-251b-46aa-a3aa-156bdd052a66)

Now we know the flag format is RWSC{, so 2126226{ probably correspond to RWSC{.
Since its just a bunch of numbers , we can assume they are using Letter Number cipher, in which A=1 , B=2 ... Z=26

If we put 2126226{19122929121712_6121911821_26422_842928} into [Letter Number Decrypter ](https://rumkin.com/tools/cipher/letter-numbers/), we get UZVF{SLBIBILQL_FLSKHU_ZDV_HDBIBH} as a result

![image](https://github.com/nenowoDev/rentas2024/assets/38612806/72b7d7e5-1ea4-44e5-ad13-18633cfded49)

RWSC{ and  UZVF{  have the same number of character .Now , maybe they are shifting the letter by some number ? Say maybe Caesar Cipher? Head over to [dcode](https://www.dcode.fr/caesar-cipher) and bruteforce it

![image](https://github.com/nenowoDev/rentas2024/assets/38612806/8d3dbfaf-040a-428f-95ed-4360bbb54c8f)

The Caesar Cipher key is 3, and we got RWSC{PIYFYFINI_CIPHER_WAS_EAYFYE},, well.. PIYFYFINI and EAYFYE doesnt make sense. What if , the did Caesar first and then Letter to number?
 
The two words that we need to fix are 19122929121712 and 842928. We will first divide it up so into x amount of group, in which each of the group is between 1 and 26 ( A to Z) and the group-3 != 0.
So the acceptable range is now 4 and 29.

we can split 19122929121712 into a lot of things but since 1 and 2 is not allowed, we only get

19 12 29 29 12 17 12

for 842928, same rules apply and we get

8 4 29 28

so now just shift all of those by 3

19 12 29 29 12 17 12  ->  16 9 26 26 9 14 9

8 4 29 28  -> 5 1 26 25

if we put the new values into letter to number, we get 

16 9 26 26 9 14 9-> P I Z Z I N I

5 1 26 25 -> EAZY

So the flag is RWSC{PIZZINI_CIPHER_WAS_EAZY}

After that, I check out what Pizzini Cipher is and its actually Caesar+Letter Number .

If we go to [Pizzini Decrypter](https://www.cachesleuth.com/pizzini.html) and put in our original 2126226{19122929121712_6121911821_26422_842928}, we instantly got it lmao

![image](https://github.com/nenowoDev/rentas2024/assets/38612806/d762e696-1b60-4b16-81be-54334700685b)




