# Books Marketplace API - Prisma

## The Purpose

Enhance your skills in handling relational databases with Prisma and Node.js by building a comprehensive API for a book-selling platform.

This lab provides detailed guidance, so make sure to read through the entire document thoroughly.

## The Lab

Your task is to develop an Express API for managing data related to books, authors, and buyers in a database using Prisma. This involves defining models in Prisma, seeding data, and creating an API for data management.

Manual testing is recommended; tools like Postman can be used for this purpose.

### The models and their data

Define the following models in your Prisma schema:

* `Author` - Represents book authors.
  * Fields:
    * `id` - unique identifier (auto-incremented)
    * `name` - author's name
    * `bio` - short biography
    * `books` - Relation to Books (many-to-many with `BookAuthors` join-table)

* `Book` - Contains details about books.
  * Fields:
    * `id` - unique identifier (auto-incremented)
    * `title` - book title
    * `description` - brief description
    * `price` - selling price
    * `authors` - Relation to Authors (many-to-many with `BookAuthors` join-table)

* `BookAuthors` - join-table for many-to-many relationship between books and authors.
  * Fields:
    * `bookId` - Connects to the Book model
    * `authorId` - Connects to the Author model

* `Buyer` - Stores information about buyers.
  * Fields:
    * `id` - unique identifier (auto-incremented)
    * `name` - buyer's name
    * `email` - buyer's email (unique)

* `Purchase` - A junction model for the many-to-many relationship between buyers and books (represents purchases).
  * Fields:
    * `buyerId` - Connects to the Buyer model
    * `bookId` - Connects to the Book model
    * `purchaseDate` - date of purchase

### The API endpoints for you to implement

Implement the following endpoints using Prisma:

* `GET` `/api/books` - list all books, including details of authors
* `GET` `/api/books/:id` - get details of a single book, including authors
* `POST` `/api/books` - add a new book (exclude `id`, include author details)
* `PUT` `/api/books/:id` - update a book's details (including authors)
* `DELETE` `/api/books/:id` - delete a book
* `GET` `/api/authors` - list all authors with their books
* `POST` `/api/authors` - add a new author
* `GET` `/api/purchases` - list all purchases, including buyer and book details
* `POST` `/api/purchases` - record a new purchase (include `buyerId` and `bookId`)

### Additional Guidance

* Use Prisma Studio and VSCode Extension for Prisma for schema management.
* Seed your database using Prisma's seed script.
* Create separate files for different aspects of your API, e.g., `models.ts` for Prisma model definitions, `db.ts` for database access code.
* Utilize the `@prisma/client` package for database interactions.
* Explore automated testing with tools like `supertest` if desired.
