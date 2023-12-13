# Codesoft

TASK 1: CALCULATOR:
def add(x, y):
    return x + y

def subtract(x, y):
    return x - y

def multiply(x, y):
    return x * y

def divide(x, y):
    if y != 0:
        return x / y
    else:
        return "Cannot divide by zero."

def calculator():
    print("Simple Calculator")

    num1 = float(input("Enter the first number: "))
    num2 = float(input("Enter the second number: "))

    print("\nSelect operation:")
    print("1. Addition")
    print("2. Subtraction")
    print("3. Multiplication")
    print("4. Division")

    choice = input("Enter choice (1/2/3/4): ")

    if choice == '1':
        result = add(num1, num2)
    elif choice == '2':
        result = subtract(num1, num2)
    elif choice == '3':
        result = multiply(num1, num2)
    elif choice == '4':
        result = divide(num1, num2)
    else:
        result = "Invalid input. Please enter a valid operation choice (1/2/3/4)."

    print("\nResult:", result)

calculator()


TASK 2: CONTACT BOOK

class ContactManager:
    def __init__(self):
        self.contacts = {}

    def add_contact(self, name, phone_number, email, address):
        self.contacts[name] = {
            'phone_number': phone_number,
            'email': email,
            'address': address
        }
        print(f"Contact '{name}' added successfully!")

    def view_contact_list(self):
        if not self.contacts:
            print("Contact list is empty.")
        else:
            print("\n===== Contact List =====")
            for name, contact_info in self.contacts.items():
                print(f"Name: {name}")
                print(f"Phone Number: {contact_info['phone_number']}")
                print(f"Email: {contact_info['email']}")
                print(f"Address: {contact_info['address']}")
                print("-------------------------")

    def search_contact(self, keyword):
        matches = []
        for name, contact_info in self.contacts.items():
            if (
                keyword.lower() in name.lower() or
                keyword in contact_info['phone_number']
            ):
                matches.append((name, contact_info))
        return matches

    def update_contact(self, name, new_phone_number, new_email, new_address):
        if name in self.contacts:
            self.contacts[name]['phone_number'] = new_phone_number
            self.contacts[name]['email'] = new_email
            self.contacts[name]['address'] = new_address
            print(f"Contact '{name}' updated successfully!")
        else:
            print(f"Contact '{name}' not found.")

    def delete_contact(self, name):
        if name in self.contacts:
            del self.contacts[name]
            print(f"Contact '{name}' deleted successfully!")
        else:
            print(f"Contact '{name}' not found.")

def main():
    contact_manager = ContactManager()

    while True:
        print("\n===== Contact Management System =====")
        print("1. Add Contact")
        print("2. View Contact List")
        print("3. Search Contact")
        print("4. Update Contact")
        print("5. Delete Contact")
        print("6. Exit")

        choice = input("Enter your choice (1-6): ")

        if choice == "1":
            name = input("Enter contact name: ")
            phone_number = input("Enter phone number: ")
            email = input("Enter email: ")
            address = input("Enter address: ")
            contact_manager.add_contact(name, phone_number, email, address)

        elif choice == "2":
            contact_manager.view_contact_list()

        elif choice == "3":
            keyword = input("Enter name or phone number to search: ")
            matches = contact_manager.search_contact(keyword)
            if matches:
                print("\n===== Search Results =====")
                for name, contact_info in matches:
                    print(f"Name: {name}")
                    print(f"Phone Number: {contact_info['phone_number']}")
                    print(f"Email: {contact_info['email']}")
                    print(f"Address: {contact_info['address']}")
                    print("-------------------------")
            else:
                print("No matching contacts found.")

        elif choice == "4":
            name = input("Enter the name of the contact to update: ")
            new_phone_number = input("Enter new phone number: ")
            new_email = input("Enter new email: ")
            new_address = input("Enter new address: ")
            contact_manager.update_contact(name, new_phone_number, new_email, new_address)

        elif choice == "5":
            name = input("Enter the name of the contact to delete: ")
            contact_manager.delete_contact(name)

        elif choice == "6":
            print("\nExiting the Contact Management System. Goodbye!")
            break

        else:
            print("Invalid choice. Please enter a number between 1 and 6.")

if __name__ == "__main__":
    main()


TASK 3: PASSWORD GENERATOR:
import random
import string
def generate_password(length):
    characters = string.ascii_letters + string.digits + string.punctuation
    password = ''.join(random.choice(characters) for _ in range(length))
    return password
def main():
    print("Password Generator")
    try:
        password_length = int(input("Enter the desired length of the password: "))
        if password_length <= 0:
            print("Please enter a positive password length.")
            return
        password = generate_password(password_length)
        print("Generated Password:", password)

    except ValueError:
        print("Invalid input. Please enter a valid positive integer for the password length.")

if __name__ == "__main__":
    main()
