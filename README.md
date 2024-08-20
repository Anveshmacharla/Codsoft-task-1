# Codsoft-task-1
import string
import random

def generate_password(length, complexity):
    # Define character sets based on complexity level
    character_sets = {
        1: string.ascii_lowercase,
        2: string.ascii_lowercase + string.ascii_uppercase,
        3: string.ascii_lowercase + string.ascii_uppercase + string.digits,
        4: string.ascii_lowercase + string.ascii_uppercase + string.digits + string.punctuation
    }
    
    # Choose the appropriate character set
    characters = character_sets[complexity]
    
    # Generate the password using random choices from the characters
    password = ''.join(random.choice(characters) for _ in range(length))
    return password

def main():
    # Prompt the user to specify the desired length of the password
    while True:
        try:
            length = int(input("Enter the desired length of the password: "))
            if length <= 0:
                raise ValueError("The length should be a positive integer.")
            break
        except ValueError as e:
            print(e)
    
    # Prompt the user to specify the desired complexity level of the password
    while True:
        try:
            complexity = int(input("Enter the complexity level (1: lowercase, 2: lowercase + uppercase, 3: lowercase + uppercase + digits, 4: lowercase + uppercase + digits + punctuation): "))
            if complexity not in [1, 2, 3, 4]:
                raise ValueError("Please choose a complexity level between 1 and 4.")
            break
        except ValueError as e:
            print(e)

    # Generate the password
    password = generate_password(length, complexity)
    
    # Display the generated password
    print("Generated Password:", password)

if _name_ == "_main_":
    main()
