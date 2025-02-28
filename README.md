# project1
Random Username Generator

import random
import string

# Pre-defined lists of adjectives and nouns
adjectives = ["Cool", "Happy", "Fast", "Strong", "Mighty", "Brave"]
nouns = ["Tiger", "Dragon", "Wolf", "Lion", "Eagle", "Panther"]

def generate_username(include_number=False, include_special_char=False):
    # Randomly choose an adjective and a noun
    adjective = random.choice(adjectives)
    noun = random.choice(nouns)
    
    # Base username
    username = adjective + noun
    
    # Add number if selected
    if include_number:
        username += str(random.randint(10, 99))
    
    # Add special character if selected
    if include_special_char:
        username += random.choice(string.punctuation)
    
    return username

def save_usernames_to_file(usernames, filename="usernames.txt"):
    with open(filename, "w") as file:
        for username in usernames:
            file.write(username + "\n")
    print(f"User names saved to {filename}")

def main():
    usernames = []
    print("Welcome to the Random Username Generator!")

    num_usernames = int(input("How many usernames would you like to generate? "))

    include_number = input("Include numbers? (y/n): ").strip().lower() == 'y'
    include_special_char = input("Include special characters? (y/n): ").strip().lower() == 'y'

    for _ in range(num_usernames):
        username = generate_username(include_number, include_special_char)
        usernames.append(username)
        print("Generated Username:", username)

    save_choice = input("Do you want to save the usernames to a file? (y/n): ").strip().lower()
    if save_choice == 'y':
        save_usernames_to_file(usernames)

if __name__ == "__main__":
    main()
