## HILL CIPHER
Using Hill Cipher method with different key values.

## AIM:
To develop a simple C program to implement Hill Cipher.

## DESCRIPTION:

Each letter is represented by a number modulo 26. Often the simple scheme A = 0, B
= 1... Z = 25, is used, but this is not an essential feature of the cipher. To encrypt a message, each block of n letters is  multiplied by an invertible n × n matrix, against modulus 26. To
decrypt the message, each block is multiplied by the inverse of the m trix used for
 
encryption. The matrix used
 
for encryption is the cipher key, and it sho
 
ld be chosen
 
randomly from the set of invertible n × n matrices (modulo 26).


## ALGORITHM:

STEP-1: Read the plain text and key from the user. STEP-2: Split the plain text into groups of length three. STEP-3: Arrange the keyword in a 3*3 matrix.
STEP-4: Multiply the two matrices to obtain the cipher text of length three.
STEP-5: Combine all these groups to get the complete cipher text.

## PROGRAM 

```
NAME: LOGA MITHRA R
REGISTER NUMBER: 212223100027
#include <stdio.h>
#include <string.h>
#include <ctype.h>

int key[3][3]    = {{1, 2, 1}, {2, 3, 2}, {2, 2, 1}};
int inv[3][3]    = {{-1, 0, 1}, {2, -1, 0}, {-2, 2, -1}};

void applyMatrix(char a, char b, char c, char *out, int mat[3][3]) {
    int A = a - 'A', B = b - 'A', C = c - 'A';
    out[0] = 'A' + ( (A*mat[0][0] + B*mat[1][0] + C*mat[2][0] + 26*3) % 26 );
    out[1] = 'A' + ( (A*mat[0][1] + B*mat[1][1] + C*mat[2][1] + 26*3) % 26 );
    out[2] = 'A' + ( (A*mat[0][2] + B*mat[1][2] + C*mat[2][2] + 26*3) % 26 );
    out[3] = '\0';
}

int main() {
    char msg[100] = "logamithra", enc[100] = "", dec[100] = "";
    for (int i = 0; msg[i]; i++) msg[i] = toupper(msg[i]);
    while (strlen(msg) % 3 != 0) strcat(msg, "X");

    for (int i = 0; i < strlen(msg); i += 3) {
        char temp[4];
        applyMatrix(msg[i], msg[i+1], msg[i+2], temp, key);
        strcat(enc, temp);
    }

    for (int i = 0; i < strlen(enc); i += 3) {
        char temp[4];
        applyMatrix(enc[i], enc[i+1], enc[i+2], temp, inv);
        strcat(dec, temp);
    }

    printf("Original : %s\nEncoded  : %s\nDecoded  : %s\n", msg, enc, dec);
    return 0;
}


```
## OUTPUT

![image](https://github.com/user-attachments/assets/1a072622-e54e-4ebe-96da-1fdb08e0d61b)

## RESULT
The program is executed sucessfully
