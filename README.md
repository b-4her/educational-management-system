<a id="readme-top"></a>

# Educational Management System (CLI)
#### Video Demo:  <URL [HERE](https://youtu.be/GC_tZgSSwwM)>

## Overview
The **Educational Management System (EMS)** is a Python console app that lets students and professors manage courses, assignments, and profiles through a simple command-line interface. Students can enroll in courses and submit assignments, while professors can create courses and grade work. The system uses object-oriented programming and stores data with Python’s `pickle` module for easy saving and loading. EMS is designed to be straightforward, efficient, and a practical way to learn core programming concepts.

<!-- TABLE OF CONTENTS -->
<details>
<summary><strong>Table of Contents</strong></summary>

- [Key Features](#key-features)
  - [For Students](#for-students)
  - [For Professors](#for-professors)
  - [Account Management](#account-management)
- [Project Structure](#project-structure)
- [Data Storage & OOP Design](#data-storage--oop-design)
  - [Example Data Structures](#example-data-structures)
  - [OOP Structure](#oop-structure)
- [Challenges and Solutions](#challenges-and-solutions)
- [Lessons Learned](#lessons-learned)
- [Installation](#installation)
- [Usage](#usage)
- [Contact Information](#contact-information)

</details>

---

## Key Features

### For Students
- **Enroll in Courses:** Browse available courses and enroll with a single command.
- **View Enrolled Courses:** List all courses you are currently enrolled in.
- **Submit Assignments:** Upload assignment solutions directly through the CLI.
- **View Grades:** Check grades and feedback for submitted assignments.
- **Withdraw from Courses:** Unenroll from courses you no longer wish to attend.
- **Profile Management:** Update your name, email, password, or security question/answer.

### For Professors
- **Create Courses:** Set up new courses with custom titles, codes, and descriptions.
- **Manage Courses:** Edit course details or remove courses you created.
- **View Enrolled Students:** See a list of students enrolled in each course.
- **Create Assignments:** Add assignments to your courses for students to complete.
- **Grade Submissions:** Review and grade student assignment submissions.
- **View Assignment Status:** Track which students have submitted or are missing assignments.
- **Profile Management:** Update your name, email, password, or security question/answer.

### Account Management
- **Account Creation:** Register as a student or professor with email validation.
- **Login/Logout:** Secure login and logout functionality for all users.
- **Password Recovery:** Reset your password using a security question and answer.
- **Profile Editing:** Change personal information and account credentials at any time.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

---

## Project Structure

```
educational-management-system/
│
├── courses_data/
│   └── courses_list.txt         # Tracks all course objects saved (one per line)
│
├── fake_data/                   # Contains sample data for testing/demo
│
├── users_data/
│   └── usernames_list.txt       # Tracks all user objects saved (one per line)
│
├── courses.py                   # Handles course-related logic and data structures
├── users.py                     # Handles user-related logic and data structures
│
├── main_menu.py                 # Main menu logic and navigation
├── prof_portal.py               # Professor portal (inherits from main menu)
├── student_portal.py            # Student portal (inherits from professor portal)
│
├── project_art.py               # ASCII art or UI enhancements for the CLI
├── project.py                   # Entry point for running the application
│
├── LICENSE                      # Project License
└── README.md                    # Project documentation
```

- **courses_data/**: Stores pickled course objects and a text file listing all course names.
- **users/**: Stores pickled user objects and a text file listing all usernames.
- **fake_data/**: Contains sample users and courses for testing/demo purposes.
- **courses.py**: Defines the `Course` class and course management logic.
- **users.py**: Defines the `User` class and user management logic.
- **main_menu.py**: Implements the main menu and navigation logic.
- **prof_portal.py**: Professor-specific features; inherits from main menu.
- **student_portal.py**: Student-specific features; inherits from professor portal.
- **project_art.py**: Contains ASCII art or UI enhancements for the CLI.
- **project.py**: Main entry point to run the application.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

---

## Data Storage & OOP Design

The system uses two main classes for data storage:

- **User**: Stores user information (name, username, account type, email, password, security question/answer, and ID). Used for both students and professors.
- **Course**: Stores course information (title, code, professor, description, enrolled students, and assignments).

Each user and course is saved as a pickled object in its respective directory (`users/` or `courses_data/`). The text files (`usernames_list.txt` and `courses_list.txt`) keep track of all saved objects for easy loading and management.

### Example Data Structures

- **Enrolled Students** in a course:
    ```python
    enrolled_students = [
        {"name": "David", "id": "09876542"},
        {"name": "Joseph", "id": "76540987"},
    ]
    ```

- **Course Assignments**:
    ```python
    course_assignments = [{
        "name": "assignment1",
        "description": "This is a test assignment",
        "students": [
            {"name": "David", "id": "09876542", "grade": "NA / 100", "solution": "..."},
            {"name": "Joseph", "id": "76540987", "grade": "NA / 100", "solution": "..."},
        ]
    }]
    ```

### OOP Structure

- The **Main Menu** class provides the base navigation and logic.
- The **Professor Portal** inherits from Main Menu and adds professor-specific features.
- The **Student Portal** inherits from Professor Portal and adds student-specific features.

This inheritance structure allows for shared functionality and easy extension of features for different user types.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

---

## Challenges and Solutions  
As a beginner project, I faced several challenges that required creative problem-solving:

1. **Data Storage Design**  
   One of the main challenges was figuring out how to store complex, interrelated data (users, courses, assignments) efficiently. Rather than using multiple CSV files—which quickly became cumbersome—I decided to use Python’s `pickle` module to serialize and save user and course objects. This made it much easier to handle nested data structures and retrieve information as needed. The use of text files as indexes (listing all users and courses) helped mimic basic database functionality and kept data management organized.

2. **Logout Mechanism**  
   Initially, logging out would sometimes redirect users to unintended pages or leave the application in an inconsistent state. I resolved this by updating the logout logic to cleanly exit the application, ensuring a predictable and user-friendly flow.

3. **Keyboard Interrupts (Ctrl+C) Navigation**  
   I tried to implement Ctrl+C as a shortcut for navigating back to previous menus. However, this approach was inconsistent and sometimes caused the program to exit or behave unexpectedly. While I couldn’t fully resolve this, it was a valuable lesson in handling keyboard interrupts and user input gracefully.

Overall, these challenges helped me learn about error handling, data management, and the importance of planning for edge cases in software development.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

---

## Lessons Learned  

Completing this project in about 40 hours over five days gave me valuable hands-on experience with Python and software development. Here are some key lessons I learned:

- **Practical OOP:** Building the EMS helped me understand how to structure code using classes and inheritance for real-world applications.
- **Error Handling:** I learned the importance of anticipating and handling errors gracefully to improve user experience and program stability.
- **Data Persistence:** Working with file-based storage and the `pickle` module taught me how to manage persistent data without a database.
- **User Experience:** Designing clear CLI menus and navigation made me appreciate the importance of usability, even in console apps.
- **Planning & Testing:** Careful planning and regular testing helped me avoid structural issues and made debugging much easier.
- **Iterative Improvement:** Facing unexpected challenges (like input errors and navigation bugs) showed me the value of iterating and refining my code.
- **Documentation:** Writing clear documentation and comments made the project easier to maintain and share with others.

Overall, this project strengthened my programming fundamentals and gave me confidence to tackle more complex software challenges in the future.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

---

## Installation
To install the Educational Management System, follow these steps:

1. **Clone the repository:**
   ```
   git clone https://github.com/b-4her/educational-management-system.git
   ```

2. **Navigate to the project directory:**
   ```
   cd educational-management-system
   ```

3. **Install the required dependencies:**
   ```
   pip install -r requirements.txt
   ```

4. **Run the program:**
   ```
   python3 project.py
   ```

5. *(Optional)* If you want to use the fake users data provided,replace the empty `users_data` and `courses_data` folders with the ones inside the folder named `fake_data`. You'll find the users' information inside a CSV file called `fake_users`. You can use this information to login and try the program.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

---

## Usage

Simply run the program and follow the on-screen instructions to sign up, log in, and use the system as a student or professor. All interactions take place through the command-line interface.

**Note:** In some cases, the Control+C shortcut (to go back to the previous page) may not work reliably and could require multiple attempts. If you encounter this issue, try pressing it several times until it works.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

---

## Contact Information
- LinkedIn: [b-4her](https://www.linkedin.com/in/b-4her)
- GitHub: [b-4her](https://github.com/b-4her)
- YouTube: [b-4her](https://www.youtube.com/@b-4her)
- Email: baher.alabbar@gmail.com

<p align="right">(<a href="#readme-top">back to top</a>)</p>

---
