def encrypt(text, shift):
    result = ""
    for char in text:
        if char.isalpha():
            base = ord('A') if char.isupper() else ord('a')
            result += chr((ord(char) - base + shift) % 26 + base)
        else:
            result += char
    return result

def decrypt(text, shift):
    return encrypt(text, -shift)

from encrypt_decrypt import encrypt, decrypt

def main():
    print("Text Encryption System")
    choice = input("Do you want to (E)ncrypt or (D)ecrypt? ").lower()

    if choice in ['e', 'encrypt']:
        text = input("Enter text to encrypt: ")
        shift = int(input("Enter shift value: "))
        print("Encrypted text:", encrypt(text, shift))
    elif choice in ['d', 'decrypt']:
        text = input("Enter text to decrypt: ")
        shift = int(input("Enter shift value used during encryption: "))
        print("Decrypted text:", decrypt(text, shift))
    else:
        print("Invalid choice!")

if __name__ == "__main__":
    main()
