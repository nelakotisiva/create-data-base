This database system is designed to manage the operations of a library, including storing details about members, books, staff, and book borrowings.

1. Members Table (Members)
Stores details of library users who borrow books.

Each member has a unique ID, name, email, and phone number.

Ensures that no two members share the same email.

2. Books Table (Books)
Stores all the books available in the library.

Each book has a unique ID, title, author name, ISBN number, and category.

ISBN is a unique code assigned to each book for global identification.

Helps track and categorize books easily (e.g., Fiction, Non-Fiction, etc.).

3. Staff Table (Staff)
Contains information about employees working in the library.

Each staff member has a unique ID, name, email, and role (like Manager, Librarian, etc.).

Email must be unique to avoid duplication and maintain proper communication records.

4. Borrowings Table (Borrowings)
This table records the borrowing activity.

Represents the relationship between members and books (many-to-many).

Tracks which member borrowed which book and on what date.

Also includes the return date. If the book is not yet returned, the return date remains empty.

Maintains foreign key references to both the Members and Books tables.

If a member or book is deleted, the related borrowing records are also automatically removed (this is called a cascading delete).

🔗 Relationships Between Tables
Members and Books: Connected through the Borrowings table (many-to-many relationship).

Staff: Independent from other tables (does not directly relate to borrowings or books in this design).

This structure helps efficiently manage and retrieve library data, such as:

Listing all borrowed books

Finding which member borrowed a specific book

Managing book returns

Keeping track of staff roles and responsibilities

