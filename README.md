# Cryptography---19CS412-classical-techqniques
## Caeser Cipher
Caeser Cipher using with different key values
### AIM:
To develop a simple C program to implement Caeser Cipher.
### DESIGN STEPS:
Step 1:
Design of Caeser Cipher algorithnm
Step 2:
Implementation using C or pyhton code
Step 3:
Testing algorithm with different key values.
### PROGRAM:
```
#include <stdio.h> #include <string.h> #include <ctype.h>
int main() { char plain[10], cipher[10]; int key, i, length;
printf("\n Enter the plain text:");
scanf("%s", plain);
printf("\n Enter the key value:");
scanf("%d", &key);
printf("\n \n \t PLAIN TEXT: %s", plain);
printf("\n \n \t ENCRYPTED TEXT: ");
length = strlen(plain);
for (i = 0; i < length; i++) {
    cipher[i] = plain[i] + key;
    if (isupper(plain[i]) && (cipher[i] > 'Z'))
        cipher[i] = cipher[i] - 26;
    if (islower(plain[i]) && (cipher[i] > 'z'))
        cipher[i] = cipher[i] - 26;
    printf("%c", cipher[i]);
}
printf("\n \n \t AFTER DECRYPTION : ");
for (i = 0; i < length; i++) {
    plain[i] = cipher[i] - key;
    if (isupper(cipher[i]) && (plain[i] < 'A'))
        plain[i] = plain[i] + 26;
    if (islower(cipher[i]) && (plain[i] < 'a'))
        plain[i] = plain[i] + 26;
    printf("%c", plain[i]);
}
return 0;
}
```
## OUTPUT:
![image](https://github.com/user-attachments/assets/b7fbf459-39b2-4cb9-ac8e-bb2f4fd5dead)
## RESULT:
The program is executed successfully
