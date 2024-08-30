# Cryptography---19CS412-classical-techqniques
## PlayFair Cipher
Playfair Cipher using with different key values
### AIM:
To develop a simple C program to implement PlayFair Cipher
### DESIGN STEPS:
Step 1:
Design of PlayFair Cipher algorithnm
Step 2:
Implementation using C or pyhton code
Step 3:
Testing algorithm with different key values.
### PROGRAM:
```
#include <stdio.h> #include <string.h> #include <ctype.h>
#define MX 5
void playfair(char ch1, char ch2, char key[MX][MX]) { int i, j, w, x, y, z; 
FILE *out;
if ((out = fopen("cipher.txt", "a+")) == NULL) {
 printf("Error: Unable to open file.\n");
 return;
}
for (i = 0; i < MX; i++) {
 for (j = 0; j < MX; j++) {
 if (ch1 == key[i][j]) {
 w = i;
 x = j;
 } else if (ch2 == key[i][j]) {
 y = i;
 z = j;
 }
 }
}
if (w == y) {
 x = (x + 1) % MX;
 z = (z + 1) % MX;
 printf("%c%c ", key[w][x], key[y][z]);
 fprintf(out, "%c%c ", key[w][x], key[y][z]);
} else if (x == z) {
 w = (w + 1) % MX;
 y = (y + 1) % MX;
 printf("%c%c ", key[w][x], key[y][z]);
 fprintf(out, "%c%c ", key[w][x], key[y][z]);
} else {
 printf("%c%c ", key[w][z], key[y][x]);
 fprintf(out, "%c%c ", key[w][z], key[y][x]);
}
fclose(out);
}
int main() { int i, j, k = 0, l, m = 0, n; char key[MX][MX], keyminus[25], 
keystr[10], str[25] = {0}; char alpa[26] = "ABCDEFGHIKLMNOPQRSTUVWXYZ"; // 'J' 
is omitted as per Playfair cipher printf("\nEnter key: "); fgets(keystr, 
sizeof(keystr), stdin); keystr[strcspn(keystr, "\n")] = '\0'; // Removing 
newline character printf("\nEnter the plain text: "); fgets(str, sizeof(str), 
stdin); str[strcspn(str, "\n")] = '\0'; // Removing newline character n =
strlen(keystr);
for (i = 0; i < n; i++) {
 if (keystr[i] == 'j' || keystr[i] == 'J') {
 keystr[i] = 'I';
 }
 keystr[i] = toupper(keystr[i]);
}
for (i = 0; i < strlen(str); i++) {
 if (str[i] == 'j' || str[i] == 'J') {
 str[i] = 'I';
 }
 str[i] = toupper(str[i]);
}
j = 0;
for (i = 0; i < 26; i++) {
 for (k = 0; k < n; k++) {
 if (keystr[k] == alpa[i]) {
 break;
 } else if (alpa[i] == 'J') {
 break;
 }
 }
 if (k == n) {
 keyminus[j] = alpa[i];
 j++;
 }
}
k = 0;
for (i = 0; i < MX; i++) {
 for (j = 0; j < MX; j++) {
 if (k < n) {
 key[i][j] = keystr[k];
 k++;
 } else {
 key[i][j] = keyminus[m];
 m++;
 }
 printf("%c ", key[i][j]);
 }
 printf("\n");
}
printf("\n\nEntered text: %s\nCipher Text: ", str);
for (i = 0; i < strlen(str); i++) {
 if (str[i + 1] == '\0') {
 playfair(str[i], 'X', key);
 } else {
 if (str[i] == str[i + 1]) {
 playfair(str[i], 'X', key);
 i++;
 } else {
 playfair(str[i], str[i + 1], key);
 i++;
 }
 }
}
return 0;
}
```
### OUTPUT:
![image](https://github.com/user-attachments/assets/11fbfbed-f448-4c39-aec7-57d464a9b2cc)
### RESULT:
The program is executed successfully
