import os
import subprocess
from typing import List, Tuple

# Define constants for employees and directories
EMPLOYEES: List[Tuple[str, str]] = [
    ("Andrew", "System_Administrator"),
    ("Julius", "Legal"),
    ("Chizi", "Human_Resource_Manager"),
    ("Jeniffer", "Sales_Manager"),
    ("Adeola", "Business_Strategist"),
    ("Bach", "CEO"),
    ("Gozie", "IT_intern"),
    ("Ogochukwu", "Finance_Manager")
]

COMPANY_DIRECTORIES: List[str] = [
    "Finance Budgets",
    "Contract Documents",
    "Business Projections",
    "Business Models",
    "Employee Data",
    "Company Vision and Mission Statement",
    "Server Configuration Script"
]

def run_subprocess(command: List[str]):
    """Run a subprocess command and handle errors."""
    try:
        subprocess.run(command, check=True)
    except subprocess.CalledProcessError as e:
        print(f"Command '{' '.join(command)}' failed with error: {e}")

def create_group(group: str):
    """Create a group if it does not exist."""
    run_subprocess(['sudo', 'groupadd', group])

def create_user(username: str, group: str):
    """Create a user and add to the specified group."""
    run_subprocess(['sudo', 'useradd', '-m', '-G', group, username])

def setup_users_and_groups(employees: List[Tuple[str, str]]):
    """Create users and their respective groups."""
    for username, group in employees:
        create_group(group)
        create_user(username, group)
        print(f"User {username} created and added to group {group}.")

def create_directory(directory_name: str):
    """Create a directory if it does not exist."""
    os.makedirs(directory_name, exist_ok=True)
    print(f"Directory {directory_name} created.")

def setup_directories(directories: List[str]):
    """Create the specified directories."""
    for directory in directories:
        create_directory(directory)

def create_file_in_directory(file_name: str, directory_name: str, directories: List[str]):
    """Create a file in the specified directory if it exists."""
    if directory_name in directories:
        file_path = os.path.join(directory_name, file_name)
        with open(file_path, 'w') as file:
            file.write("")  # Create an empty file
        print(f"File {file_name} created in directory {directory_name}.")
    else:
        print(f"Directory {directory_name} does not exist among the company directories.")

def main():
    """Main function to set up users, groups, and directories."""
    setup_users_and_groups(EMPLOYEES)
    setup_directories(COMPANY_DIRECTORIES)
    
    # Take user input for file creation
    file_name = input("Enter the name of the file to create: ")
    directory_name = input("Enter the directory to create the file in: ")
    
    create_file_in_directory(file_name, directory_name, COMPANY_DIRECTORIES)

if __name__ == "__main__":
    main()
