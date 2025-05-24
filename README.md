## EX : 5 IMPLEMENTATION OF RAIL FENCE CIPHER

## AIM:

To develop a simple C program to implement Rail Fence Cipher.


## ALGORITHM:
#### 1.	To perform the Encryption Process
#### •	Input the plaintext string from the user.
#### •	Calculate the length of the plaintext.
#### •	Create the ciphertext using two rails:
#### a.	First, collect characters at even indices (i.e., 0, 2, 4, …).
#### b.	Then, collect characters at odd indices (i.e., 1, 3, 5, …).
#### c.	Combine both parts to form the ciphertext.
#### •	Display the encrypted ciphertext.

#### 2.	To perform the Decryption Process:
#### •	Calculate the length of the ciphertext.
#### •	Find the midpoint:
#### ◦	a. If the length is even, midpoint = length / 2.
#### ◦	b. If the length is odd, midpoint = (length / 2) + 1.
#### •	Reconstruct the original message:
#### a.	Take the first half as characters from even positions.
#### b.	Take the second half as characters from odd positions.
#### c.	Merge both using alternating positions.

#### 3.	Display the decrypted plaintext.



## PROGRAM:
```
def encrypt_rail_fence(text, rails):
    if rails <= 1:
        return text
    fence = [''] * rails
    rail = 0
    direction = 1
    for char in text:
        fence[rail] += char
        rail += direction
        if rail == 0 or rail == rails - 1:
            direction *= -1
    return ''.join(fence)
def decrypt_rail_fence(ciphertext, rails):
    if rails <= 1:
        return ciphertext
    rail_pattern = [0] * len(ciphertext)
    rail = 0
    direction = 1
    for i in range(len(ciphertext)):
        rail_pattern[i] = rail
        rail += direction
        if rail == 0 or rail == rails - 1:
            direction *= -1
    rail_lengths = [0] * rails
    for r in rail_pattern:
        rail_lengths[r] += 1
    rail_chars = []
    index = 0
    for length in rail_lengths:
        rail_chars.append(list(ciphertext[index:index + length]))
        index += length
    decrypted_text = []
    for r in rail_pattern:
        decrypted_text.append(rail_chars[r].pop(0))
    return ''.join(decrypted_text)
if __name__ == "__main__":
    text = input("Enter a Secret Message: ")
    rails = int(input("Enter number of rails: "))
    encrypted_text = encrypt_rail_fence(text, rails)
    print("Encrypted Message:", encrypted_text)
    decrypted_text = decrypt_rail_fence(encrypted_text, rails)
    print("Decrypted Message:", decrypted_text)
```
## OUTPUT:
![image](https://github.com/user-attachments/assets/61302032-d07c-40f1-b3a8-0caf37ff29df)

## RESULT:
The program implementing the Rail Fence cipher for encryption and decryption has been successfully	executed,	and	the	results	have	been	verified.
