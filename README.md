# Ex-4 Rail-Fence-Program

# IMPLEMENTATION OF RAIL FENCE – ROW & COLUMN TRANSFORMATION TECHNIQUE

# AIM:

# To write a C program to implement the rail fence transposition technique.

# DESCRIPTION:

In the rail fence cipher, the plain text is written downwards and diagonally on successive "rails" of an imaginary fence, then moving up when we reach the bottom rail. When we reach the top rail, the message is written downwards again until the whole plaintext is written out. The message is then read off in rows.

# ALGORITHM:

STEP-1: Read the Plain text.
STEP-2: Arrange the plain text in row columnar matrix format.
STEP-3: Now read the keyword depending on the number of columns of the plain text.
STEP-4: Arrange the characters of the keyword in sorted order and the corresponding columns of the plain text.
STEP-5: Read the characters row wise or column wise in the former order to get the cipher text.

# PROGRAM
```
Name: K Hasini
Reg No: 212224240074
```

```
def rail_fence_encrypt(text, rails):
    fence = [[] for _ in range(rails)]
    rail = 0
    direction = 1
    
    for char in text:
        fence[rail].append(char)
        rail += direction
        if rail == 0 or rail == rails - 1:
            direction *= -1
    
    return "".join("".join(row) for row in fence)

def rail_fence_decrypt(ciphertext, rails):
    fence = [['' for _ in range(len(ciphertext))] for _ in range(rails)]
    rail = 0
    direction = 1
    
    for i in range(len(ciphertext)):
        fence[rail][i] = '*'
        rail += direction
        if rail == 0 or rail == rails - 1:
            direction *= -1
    
    index = 0
    for row in range(rails):
        for col in range(len(ciphertext)):
            if fence[row][col] == '*' and index < len(ciphertext):
                fence[row][col] = ciphertext[index]
                index += 1
    
    result = []
    rail = 0
    direction = 1
    for i in range(len(ciphertext)):
        result.append(fence[rail][i])
        rail += direction
        if rail == 0 or rail == rails - 1:
            direction *= -1
    
    return "".join(result)

# Get user input
message = input("Enter the message: ").replace(" ", "")
rails = int(input("Enter the number of rails: "))

encrypted_text = rail_fence_encrypt(message, rails)
decrypted_text = rail_fence_decrypt(encrypted_text, rails)

print("Encrypted:", encrypted_text)
print("Decrypted:", decrypted_text)

```
# OUTPUT
![image](https://github.com/user-attachments/assets/207257be-af2b-42f9-b806-afca8ecd1363)

# RESULT
The Program is implemented successfullly.
