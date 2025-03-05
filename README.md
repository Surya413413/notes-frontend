# Notes Application - Frontend

This is a frontend application for a Notes management system built using React.js. The application allows users to register, log in, create, view, update, and delete notes. It also supports features like pinning, archiving, and searching notes. The frontend interacts with a backend API to perform CRUD operations on notes and user authentication.

---

## Features

1. **User Authentication**:
   - Users can register and log in using their email and password.
   - JWT (JSON Web Token) is used for authentication and session management.
   - Protected routes ensure that only authenticated users can access certain pages.

2. **Notes Management**:
   - Users can create, view, update, and delete notes.
   - Notes can be pinned or archived.
   - Notes are categorized and displayed in separate sections (Pinned, Unpinned, Archived).

3. **Search Functionality**:
   - Users can search for notes by title.

4. **Responsive Design**:
   - The application is designed to be responsive and works well on both desktop and mobile devices.

5. **Protected Routes**:
   - Certain routes (e.g., `/notes`, `/notes/create`) are protected and can only be accessed by authenticated users.

---

## Technologies Used

- **Frontend**:
  - React.js
  - React Router for routing
  - JavaScript (ES6+)
  - CSS for styling
  - Axios (or Fetch API) for making HTTP requests

- **Backend**:
  - Node.js with Express.js (assumed based on the API endpoints)
  - SQLite (or any relational database) for storing user and note data
  - JWT for authentication

- **Other Tools**:
  - `js-cookie` for managing cookies in the browser
  - `react-icons` for icons (e.g., search icon)

---

## Folder Structure

```
src/
|-- components/
|   |-- Home.js
|   |-- LoginForm.js
|   |-- Register.js
|   |-- ProtectedRoute.js
|   |-- HomePage.js
|   |-- Notedetailsitems.js
|   |-- NotFound.js
|   |-- CreateNotes.js
|   |-- Header.js
|   |-- NoteItems.js
|-- App.js
|-- App.css
|-- index.js
|-- index.css
```

---

## Components Overview

1. **App.js**:
   - The main component that sets up routing using `react-router-dom`.
   - Defines routes for login, register, home, notes, and other pages.
   - Uses `ProtectedRoute` to protect certain routes.

2. **LoginForm.js**:
   - Handles user login.
   - Validates user credentials and stores the JWT token in cookies upon successful login.
   - Redirects to the notes page after login.

3. **Register.js**:
   - Handles user registration.
   - Validates input fields and sends registration data to the backend.
   - Redirects to the login page after successful registration.

4. **ProtectedRoute.js**:
   - A higher-order component that checks for the presence of a JWT token.
   - Redirects unauthenticated users to the login page.

5. **HomePage.js**:
   - Displays the list of notes.
   - Supports searching, pinning, archiving, and deleting notes.
   - Separates notes into Pinned, Unpinned, and Archived sections.

6. **CreateNotes.js**:
   - Allows users to create new notes.
   - Validates input fields and sends the note data to the backend.

7. **Header.js**:
   - Displays the navigation bar with options to log out, go to the home page, or view notes.

8. **NoteItems.js**:
   - Displays individual note items with options to pin, archive, or delete them.

9. **NotFound.js**:
   - Displays a 404 error page when a user tries to access an invalid route.

---

## API Endpoints

The frontend interacts with the following backend API endpoints:

1. **User Authentication**:
   - `POST /users/login` - User login.
   - `POST /users/register` - User registration.

2. **Notes Management**:
   - `GET /notes` - Fetch all notes for the logged-in user.
   - `POST /notes/create` - Create a new note.
   - `DELETE /notes/:id` - Delete a note by ID.
   - `PATCH /notes/:id/pin` - Toggle pin status of a note.
   - `PATCH /notes/:id/archive` - Toggle archive status of a note.

---

## Setup Instructions

1. **Clone the Repository**:
   ```bash
  git clone https://github.com/Surya413413/notes-frontend.git
  
   ```

2. **Install Dependencies**:
   ```bash
   npm install
   ```

3. **Run the Application**:
   ```bash
   npm start
   ```

4. **Access the Application**:
   - Open your browser and navigate to `http://localhost:3000`.

---

## Environment Variables

Ensure the following environment variables are set for the backend API:

- `REACT_APP_API_URL`: The base URL for the backend API (e.g., `http://localhost:3000`).

---

## Database Schema

The backend uses the following database schema:

1. **Users Table**:
   ```sql
   CREATE TABLE users (
     id INTEGER PRIMARY KEY AUTOINCREMENT,
     name TEXT NOT NULL,
     email TEXT UNIQUE NOT NULL,
     password TEXT NOT NULL,
     created_at DATETIME DEFAULT CURRENT_TIMESTAMP
   );
   ```

2. **Notes Table**:
   ```sql
   CREATE TABLE notes (
     id INTEGER PRIMARY KEY AUTOINCREMENT,
     title TEXT NOT NULL,
     content TEXT NOT NULL,
     category TEXT NOT NULL,
     created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
     updated_at DATETIME DEFAULT CURRENT_TIMESTAMP,
     pinned BOOLEAN DEFAULT 0,
     archived BOOLEAN DEFAULT 0,
     user_id INTEGER,
     FOREIGN KEY (user_id) REFERENCES users(id)
   );
   ```

---

## Future Enhancements

1. **Note Editing**:
   - Allow users to edit existing notes.

2. **User Profile**:
   - Add a user profile page where users can update their information.

3. **Rich Text Editor**:
   - Integrate a rich text editor for creating and editing notes.

4. **Dark Mode**:
   - Add a dark mode option for better user experience.

5. **Pagination**:
   - Implement pagination for the notes list to handle large numbers of notes.

---

## Contributing

Contributions are welcome! Please fork the repository and submit a pull request with your changes.

---




Thank you for using the Notes Application!


