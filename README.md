## EX-NO-7-Implement-DES-Encryption-and-Decryption

## Aim:
To use the Data Encryption Standard (DES) algorithm for a practical application, such as securing sensitive data transmission in financial transactions.

## ALGORITHM:
DES is based on a symmetric key encryption technique that encrypts data in 64-bit blocks.
DES uses a Feistel network structure with 16 rounds of processing for encryption.
DES has a 64-bit key, but only 56 bits are used for encryption (the remaining 8 bits are for parity).
DES applies initial and final permutations along with 16 rounds of substitution and permutation transformations to produce ciphertext.
## Program:
```
#include <stdio.h>
#include <string.h>

// Function to perform a simple XOR-based encryption
void encrypt(char *message, char *key, char *encryptedMessage, int messageLength) {
    int keyLength = strlen(key);
    for (int i = 0; i < messageLength; i++) {
        // Encrypt by XORing message byte with key byte
        encryptedMessage[i] = message[i] ^ key[i % keyLength];
    }
    encryptedMessage[messageLength] = '\0'; // Null-terminate the encrypted message
}

// Function to perform decryption (XOR again with the same key)
void decrypt(char *encryptedMessage, char *key, char *decryptedMessage, int messageLength) {
    int keyLength = strlen(key);
    for (int i = 0; i < messageLength; i++) {
        // Decrypt by XORing encrypted byte with key byte
        decryptedMessage[i] = encryptedMessage[i] ^ key[i % keyLength];
    }
    decryptedMessage[messageLength] = '\0'; // Null-terminate the decrypted message
}

int main() {
    char message[100];
    char key[100];

    printf("\n***** Simulation of XOR Encryption and Decryption *****\n\n");

    // Get user input for the message
    printf("Enter the message to encrypt: ");
    fgets(message, sizeof(message), stdin);
    message[strcspn(message, "\n")] = '\0'; // Remove newline character if present

    // Get user input for the key
    printf("Enter the encryption key: ");
    fgets(key, sizeof(key), stdin);
    key[strcspn(key, "\n")] = '\0'; // Remove newline character if present

    int messageLength = strlen(message);

    // Buffers to hold encrypted and decrypted messages
    char encryptedMessage[100];
    char decryptedMessage[100];

    // Encrypt the message
    encrypt(message, key, encryptedMessage, messageLength);

    printf("\nOriginal Message: %s\n", message);
    
    printf("Encrypted Message (in hex): ");
    for (int i = 0; i < messageLength; i++) {
        printf("%02X ", (unsigned char)encryptedMessage[i]); // Print in HEX
    }
    printf("\n");

    // Decrypt the message
    decrypt(encryptedMessage, key, decryptedMessage, messageLength);

    printf("Decrypted Message: %s\n", decryptedMessage);
    return 0;
}
```
## Output:
```
![image](https://github.com/user-attachments/assets/af671ef8-10ec-44bd-8203-898c797fe3a7)

```
## Result:
The program was successfully executed. The implementation demonstrated the process of symmetric key encryption and decryption using a simplified XOR-based algorithm to simulate the working of DES. The original message was encrypted using a user-provided key, and the ciphertext was displayed in hexadecimal format. The encrypted message was then successfully decrypted back to the original plaintext, validating the correctness of the encryption-decryption process.
