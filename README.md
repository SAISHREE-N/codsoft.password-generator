import string
import secrets
def generate_password(length):
    """
    Generate a strong and random password of a given length.
    Args:
        length (int): The length of the password to generate.
    Returns:
        str: A strong and random password.
    """
    characters = string.ascii_letters + string.digits + string.punctuation
    while True:
        password = ''.join(secrets.choice(characters) for _ in range(length))
        if (any(c.islower() for c in password) 
                and any(c.isupper() for c in password) 
                and any(c.isdigit() for c in password) 
                and any(c in string.punctuation for c in password)):
            return password
def main():
    print("Password Generator")
    print("------------------")
    while True:
        try:
            length = int(input("Enter the desired length of the password: "))
            if length < 5:
                print("Password length should be at least 5 characters.")
                continue
            break
        except ValueError:
            print("Invalid input. Please enter a number.")
    password = generate_password(length)
    print(f"Generated Password : {password}")
if __name__ == "__main__":
    main()
