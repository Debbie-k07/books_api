# Books REST API

A simple REST API built with Flask that manages a list of books, storing data in memory (no database).

## Language/Framework
- Python 3.x
- Flask

## Setup Instructions

1. Clone this repository:  https://github.com/Debbie-k07/books_api.git
2. Create a virtual environment:
   python -m venv venv
3. Activate the virtual environment:
   - Windows: `venv\Scripts\activate`
   - Mac/Linux: `source venv/bin/activate`

4. Install dependencies:
   pip install flask
5. Run the app:
   python book_fetcher.py

6. The API will be available at `http://127.0.0.1:5000`

## Endpoints & Sample Requests/Responses

### GET /books
Returns all books.

**Request:** `GET /books`

**Response:** `200 OK`
```json
[
  {
    "id": 101,
    "title": "Deep Work",
    "author": "Cal Newport"
  }
]
```

### GET /books/:id
Returns a single book by ID.

**Request:** `GET /books/101`

**Response:** `200 OK`
```json
{
  "id": 101,
  "title": "Deep Work",
  "author": "Cal Newport"
}
```

**Error response (book not found):** `404 Not Found`
```json
{
  "error": "Book with id 999 not found"
}
```

### GET /books/count
Returns the total number of books.

**Request:** `GET /books/count`

**Response:** `200 OK`
```json
{
  "count": 1
}
```

### POST /books
Creates a new book.

**Request:** `POST /books`
```json
{
  "title": "Atomic Habits",
  "author": "James Clear"
}
```

**Response:** `201 Created`
```json
{
  "id": 102,
  "title": "Atomic Habits",
  "author": "James Clear"
}
```

**Error response (missing fields):** `400 Bad Request`
```json
{
  "error": "Both 'title' and 'author' are required"
}
```

### PUT /books/:id
Updates a book's title and/or author.

**Request:** `PUT /books/102`
```json
{
  "title": "Atomic Habits (revised version)"
}
```

**Response:** `200 OK`
```json
{
  "id": 102,
  "title": "Atomic Habits (Updated Edition)",
  "author": "James Clear"
}
```

### DELETE /books/:id
Deletes a book by ID.

**Request:** `DELETE /books/102`

**Response:** `200 OK`
```json
{
  "message": "Book with id 102 deleted"
}
```

## Notes
- No database is used; all data is stored in memory and resets when the server restarts.
- Built and tested using Thunder Client / browser for GET requests.
