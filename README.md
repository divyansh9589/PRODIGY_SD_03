# PRODIGY_SD_03
Implement a Simple Contact Management System

class Contact:
    def __init__(self, name, phone, email):
        self.name = name
        self.phone = phone
        self.email = email

    def __str__(self):
        return f"Name: {self.name}, Phone: {self.phone}, Email: {self.email}"
class ContactManager:
    def __init__(self):
        self.contacts = []

    def add_contact(self, name, phone, email):
        self.contacts.append(Contact(name, phone, email))

    def view_contacts(self):
        if not self.contacts:
            print("No contacts available.")
        for i, contact in enumerate(self.contacts, 1):
            print(f"{i}. {contact}")

    def edit_contact(self, index, name=None, phone=None, email=None):
        if 0 <= index < len(self.contacts):
            if name:
                self.contacts[index].name = name
            if phone:
                self.contacts[index].phone = phone
            if email:
                self.contacts[index].email = email

    def delete_contact(self, index):
        if 0 <= index < len(self.contacts):
            del self.contacts[index]
def display_menu():
    print("\nContact Manager")
    print("1. Add Contact")
    print("2. View Contacts")
    print("3. Edit Contact")
    print("4. Delete Contact")
    print("5. Exit")

def add_contact(manager):
    name = input("Enter name: ")
    phone = input("Enter phone: ")
    email = input("Enter email: ")
    manager.add_contact(name, phone, email)
    print("Contact added successfully!")

def view_contacts(manager):
    print("\nContact List:")
    manager.view_contacts()

def edit_contact(manager):
    manager.view_contacts()
    index = int(input("Enter the contact number to edit: ")) - 1
    name = input("Enter new name (leave blank to keep current): ")
    phone = input("Enter new phone (leave blank to keep current): ")
    email = input("Enter new email (leave blank to keep current): ")
    manager.edit_contact(index, name or None, phone or None, email or None)
    print("Contact updated successfully!")

def delete_contact(manager):
    manager.view_contacts()
    index = int(input("Enter the contact number to delete: ")) - 1
    manager.delete_contact(index)
    print("Contact deleted successfully!")
def main():
    manager = ContactManager()
    
    while True:
        display_menu()
        choice = input("Enter your choice: ")
        
        if choice == '1':
            add_contact(manager)
        elif choice == '2':
            view_contacts(manager)
        elif choice == '3':
            edit_contact(manager)
        elif choice == '4':
            delete_contact(manager)
        elif choice == '5':
            print("Exiting Contact Manager.")
            break
        else:
            print("Invalid choice. Please try again.")

# Run the main program loop
main()
