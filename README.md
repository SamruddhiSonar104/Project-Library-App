# Project-Library-App

# Library Management System

A comprehensive web-based library management system designed to enhance student and librarian interactions through advanced features like personalized book recommendations, QR code-based library cards, and intuitive book management.

## Features

### For Students
- Browse and search the library's book collection
- Reserve books that are currently unavailable
- Borrow and return books through a simple interface
- View borrowing history and current loans
- Get personalized book recommendations
- Generate and access a digital library card via QR code
- Track reservation status

### For Librarians/Admins
- Manage the book inventory (add, update, delete books)
- Process book check-outs and returns
- Approve or deny book reservations
- Scan student library cards via QR code
- View detailed borrowing statistics
- Manage user accounts
- Issue and renew library cards

## Tech Stack

- **Frontend**: React with TypeScript
- **Backend**: Node.js with Express
- **Database**: PostgreSQL with Drizzle ORM
- **Authentication**: Passport.js
- **UI Components**: Shadcn UI components with Tailwind CSS
- **Recommendations**: Perplexity AI for personalized book recommendations
- **QR/Barcode**: QR code generation and scanning functionality

## System Architecture

The application follows a client-server architecture:

1. **Client**: React SPA with role-based interfaces (student view vs. admin view)
2. **Server**: Express.js REST API
3. **Database**: PostgreSQL for data persistence
4. **External Services**: Perplexity API for AI-powered book recommendations

## API Endpoints

### Authentication
- `POST /api/auth/login` - User login
- `POST /api/auth/register` - User registration
- `GET /api/auth/session` - Get current session info
- `POST /api/auth/logout` - User logout

### Books
- `GET /api/books` - Get all books (with search and category filters)
- `GET /api/books/:id` - Get book by ID
- `GET /api/books/isbn/:isbn` - Get book by ISBN
- `POST /api/books` - Add a new book (admin only)
- `PUT /api/books/:id` - Update a book (admin only)
- `DELETE /api/books/:id` - Delete a book (admin only)

### Borrows
- `GET /api/borrows` - Get borrowing records (filtered by user role)
- `POST /api/borrows` - Borrow a book
- `POST /api/borrows/:id/return` - Return a borrowed book

### Reservations
- `GET /api/reservations` - Get reservation records (filtered by user role)
- `POST /api/reservations` - Reserve a book
- `PUT /api/reservations/:id` - Update reservation status (admin only)
- `DELETE /api/reservations/:id` - Cancel a reservation

### Library Cards
- `GET /api/library-cards` - Get library cards (all for admin, own for student)
- `GET /api/library-cards/my-card` - Get user's own library card
- `POST /api/library-cards` - Create a new library card
- `PUT /api/library-cards/:id` - Update a library card
- `POST /api/library-cards/:id/renew` - Renew a library card (admin only)
- `GET /api/library-cards/scan/:cardNumber` - Scan a library card by number (admin only)

### Recommendations
- `GET /api/recommendations` - Get general book recommendations
- `GET /api/recommendations/personal` - Get personalized recommendations (requires authentication)

## Database Schema

The system uses the following database tables:

1. **users** - User accounts with authentication info
2. **books** - Book information including availability
3. **borrows** - Records of book loans
4. **reservations** - Book reservation requests
5. **library_cards** - Library card information and status

## Offline Support

The application includes a robust offline sync system:
- Queues operations when offline
- Automatically syncs when connection is restored
- Provides status updates for pending operations

## Getting Started

### Prerequisites
- Node.js (v18 or later)
- PostgreSQL database
- Perplexity API key (for book recommendations)

### Installation

1. Clone the repository
2. Install dependencies:
   ```
   npm install
   ```
3. Set up environment variables in `.env`:
   ```
   DATABASE_URL=your_postgresql_connection_string
   PERPLEXITY_API_KEY=your_perplexity_api_key
   ```
4. Push schema to database:
   ```
   npm run db:push
   ```
5. Start the development server:
   ```
   npm run dev
   ```

## Usage

1. Register as a new user (student or admin)
2. Browse books, make reservations, and borrow items
3. Admins can access additional features through the admin dashboard

## License

This project is licensed under the MIT License - see the LICENSE file for details.
