# Caesar-Cipher-in-Python
letters = 'abcdefghijklmnopqrstuvwxyz'
num_letters = len(letters)

def encrypt(plaintext, key):
    ciphertext = ''
    for letter in plaintext:
        letter = letter.lower()
        if letter in letters:
            index = letters.find(letter)
            new_index = (index + key) % num_letters
            ciphertext += letters[new_index]
        else:
            ciphertext += letter  
    return ciphertext

def decrypt(ciphertext, key):
    plaintext = ''
    for letter in ciphertext:
        letter = letter.lower()
        if letter in letters:
            index = letters.find(letter)
            new_index = (index - key) % num_letters
            plaintext += letters[new_index]
        else:
            plaintext += letter  
    return plaintext

print('* CAESAR CIPHER PROGRAM *')
print()

user_input = input('Do you want to encrypt or decrypt? (e/d): ').lower()
print()

if user_input == 'e':
    print('ENCRYPTION MODE SELECTED')
    print()
    key = int(input('Enter the key (1 through 26): '))
    text = input('Enter the text to encrypt: ')
    ciphertext = encrypt(text, key)
    print(f'CIPHERTEXT: {ciphertext}')

elif user_input == 'd':
    print('DECRYPTION MODE SELECTED')
    print()
    key = int(input('Enter the key (1 through 26): '))
    text = input('Enter the text to decrypt: ')
    plaintext = decrypt(text, key)
    print(f'PLAINTEXT: {plaintext}')

def encrypt_decrypt(text, mode, key):
    letters = 'abcdefghijklmnopqrstuvwxyz'
    num_letters = len(letters)
    result = ''

    if mode == 'd':
        key = -key  

    for letter in text:
        letter = letter.lower()
        index = letters.find(letter)

        if index == -1:
            result += letter  

            new_index = (index + key) % num_letters

            if new_index < 0:
                new_index += num_letters  

            result += letters[new_index]  

    return result
