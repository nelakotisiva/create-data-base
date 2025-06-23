# create-data-base

CREATE DATABASE LibraryDB;
USE LibraryDB;
-- Table: Members
CREATE TABLE Members (
    member_id INT  PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100) UNIQUE,
    phone VARCHAR(15)
);

-- Table: Books
CREATE TABLE Books (
    book_id INT PRIMARY KEY,
    title VARCHAR(255),
    author VARCHAR(100),
    isbn VARCHAR(20) UNIQUE,
    category VARCHAR(50)
);

-- Table: Staff
CREATE TABLE Staff (
    staff_id INT  PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100) UNIQUE,
    role VARCHAR(50)
);

-- Table: Borrowings (Many-to-Many relationship between Members and Books)
CREATE TABLE Borrowings (
    borrow_id INT PRIMARY KEY,
    member_id INT,
    book_id INT,
    borrow_date DATE,
    return_date DATE,
    FOREIGN KEY (member_id) REFERENCES Members(member_id) ON DELETE CASCADE,
    FOREIGN KEY (book_id) REFERENCES Books(book_id) ON DELETE CASCADE
);

INSERT INTO Members (member_id, name, email, phone)
VALUES 
  (1, 'Ravi Kumar', 'ravi.kumar@example.com', '9876543210'),
  (2, 'Anjali Mehta', 'anjali.mehta@example.com', '8765432109'),
  (3, 'Rahul Sharma', 'rahul.sharma@example.com', '7654321098'),
  (4, 'Sneha Reddy', 'sneha.reddy@example.com', '6543210987'),
  (5, 'Amit Verma', 'amit.verma@example.com', '9432109876');
SELECT * FROM Members;

INSERT INTO Books (book_id, title, author, isbn, category)
VALUES 
  (12354, 'To Kill a Mockingbird', 'Harper Lee', '9780061120084', 'Fiction'),
  (12355, '1984', 'George Orwell', '9780451524935', 'Dystopian'),
  (12356, 'The Great Gatsby', 'F. Scott Fitzgerald', '9780743273565', 'Classic'),
  (12357, 'Pride and Prejudice', 'Jane Austen', '9781503290563', 'Romance'),
  (12358, 'The Hobbit', 'J.R.R. Tolkien', '9780547928227', 'Fantasy'),
  (12359, 'Sapiens: A Brief History of Humankind', 'Yuval Noah Harari', '9780062316097', 'Non-Fiction');

SELECT * FROM Books;

INSERT INTO Staff (staff_id, name, email, role)
VALUES
  (1, 'Priya Das', 'priya.das@example.com', 'Manager'),
  (2, 'Arjun Nair', 'arjun.nair@example.com', 'Assistant'),
  (3, 'Kavita Joshi', 'kavita.joshi@example.com', 'Librarian'),
  (4, 'Rohan Malik', 'rohan.malik@example.com', 'Clerk'),
  (5, 'Sneha Iyer', 'sneha.iyer@example.com', 'Technician');
SELECT * FROM staff;
INSERT INTO Borrowings (borrow_id, member_id, book_id, borrow_date, return_date)
VALUES
  (1, 1, 12354, '2025-06-01', '2025-06-15'),
  (2, 2, 12355, '2025-06-03', '2025-06-18'),
  (3, 3, 12356, '2025-06-05', '2025-06-20'),
  (4, 4, 12357, '2025-06-07', '2025-06-22'),
  (5, 5, 12358, '2025-06-09', NULL);  -- NULL = not returned yet
SELECT * FROM Borrowings;
