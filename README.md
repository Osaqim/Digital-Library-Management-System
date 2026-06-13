# Digital Library Management System

An advanced relational database ecosystem built with MySQL to streamline digital library assets, user memberships, and automated loan transaction workflows.

## Database Architecture
The schema is engineered around four core entities structured to maintain strict contextual relationships:
* **Authors (`authors`):** Manages writer profiles and biographical data.
* **Books Catalog (`books`):** Tracks literary assets, publishing details, classifications, and dynamic availability statuses.
* **Members (`members`):** Manages user registration profiles and institutional membership timelines.
* **Borrowing Transactions (`borrows`):** A transactional bridge mapping member-to-book interactions including rental and return timelines.

## Advanced Database Automation (Triggers)
The core strength of this project lies in its server-side automation, eliminating manual status updates through built-in event listeners:
* **`After_Book_Borrowed` (AFTER INSERT):** Automatically updates a book's status to `'Borrowed'` instantly upon a new loan creation.
* **`After_Book_Returned` (AFTER UPDATE):** Monitors transaction records and reverts a book's status back to `'Available'` the exact moment a valid `return_date` is logged.

## Performance Optimization
* **Structured Indexing:** Implemented targeted composite/single indexes (`idx_book_title`, `idx_book_category`, and `idx_borrow_member`) to optimize query execution plans and drastically cut search latencies during mass data filtration.
