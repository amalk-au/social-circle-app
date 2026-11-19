# Social Circle – Backend API

The backend REST API for **Social Circle**, a full-stack social networking application designed to help people connect through profiles, follow relationships and social interactions.

Built with Node.js, Express, PostgreSQL and Prisma ORM, the API handles authentication, user management, social connections, posts, likes and comments.

## Overview

The Social Circle backend provides the API and database functionality powering the Social Circle frontend.

### Features

- User registration and authentication.

- JWT-based authentication and protected routes.

- Password hashing using bcryptjs.

- User profile retrieval and editing.

- User discovery and follow relationships.

- Social feed retrieval.

- Post creation and retrieval.

- Post likes and comments.

- PostgreSQL database integration using Prisma ORM.

## Tech Stack

| Technology            | Purpose                       |
| --------------------- | ----------------------------- |
| Node.js               | JavaScript runtime            |
| Express 5             | REST API framework            |
| PostgreSQL            | Relational database           |
| Prisma 6              | ORM and database access       |
| JSON Web Tokens (JWT) | Authentication                |
| bcryptjs              | Password hashing              |
| dotenv                | Environment configuration     |
| CORS                  | Cross-origin request handling |

## Getting Started

### Prerequisites

- Node.js

- pnpm (preferred)

- PostgreSQL

- Git

### Installation

Clone the repository:

```
git clone https://github.com/amalk-au/social-circle-app.git

cd social-circle-app/backend
```

Install dependencies:

```
pnpm install
```

### Environment Variables

Create a `.env` file in the `backend/` directory:

```
DATABASE_URL="postgresql://username:password@localhost:5432/social_circle"
JWT_SECRET_KEY="replace-with-a-secure-secret"
CORS_URL="http://localhost:5173"
PORT=4000
```

| Variable         | Description                          |
| ---------------- | ------------------------------------ |
| `DATABASE_URL`   | PostgreSQL connection string.        |
| `JWT_SECRET_KEY` | Secret used to sign and verify JWTs. |
| `CORS_URL`       | Allowed frontend origin.             |
| `PORT`           | Server port. Defaults to `4000`.     |

### Database Setup

Generate the Prisma client:

```
pnpm exec prisma generate --schema src/prisma/schema.prisma
```

Synchronise the database schema:

```
pnpm exec prisma db push --schema src/prisma/schema.prisma
```

Optionally, populate the database with sample data:

```
pnpm run seed
```

### Start the Server

Development:

```
pnpm run dev
```

Production:

```
pnpm start
```

The server defaults to:

```
http://localhost:4000
```

## Available Scripts

| Command           | Description                                |
| ----------------- | ------------------------------------------ |
| `pnpm run dev`    | Start the server using Node.js watch mode. |
| `pnpm start`      | Start the server.                          |
| `pnpm run studio` | Open Prisma Studio.                        |
| `pnpm run seed`   | Populate the database with sample data.    |

## API

### Base URL

Local:

```
http://localhost:4000/social-circle-api/v1
```

Production:

```
https://social-circle-app.onrender.com/social-circle-api/v1
```

### Status Endpoint

Check whether the API is responding:

```
GET /social-circle-api/v1/status
```

[Production API Status](https://social-circle-app.onrender.com/social-circle-api/v1/status)

### Authentication

Protected endpoints require a valid JWT supplied through the Authorization header:

```
Authorization: Bearer <JWT_TOKEN>
```

Tokens expire after 30 minutes.

### API Endpoints

| Method | Endpoint                                                                      | Description                              |
| ------ | ----------------------------------------------------------------------------- | ---------------------------------------- |
| `POST` | `/register`                                                                   | Register a user.                         |
| `POST` | `/login`                                                                      | Authenticate a user.                     |
| `GET`  | `/authorized/:authenticatedUserName/all-users`                                | Retrieve registered users.               |
| `GET`  | `/authorized/:authenticatedUserName/:selectedUserName/profile/view`           | Retrieve a user profile.                 |
| `PUT`  | `/authorized/:authenticatedUserName/profile/edit`                             | Update the authenticated user's profile. |
| `PUT`  | `/authorized/:authenticatedUserName/all-users/:selectedUserName/followstatus` | Update a follow relationship.            |
| `GET`  | `/authorized/:authenticatedUserName/all-users/:selectedUserName/home-feed`    | Retrieve the social feed.                |
| `POST` | `/authorized/:authenticatedUserName/new-post`                                 | Create a post.                           |
| `GET`  | `/authorized/:authenticatedUserName/posts/:postId`                            | Retrieve an individual post.             |
| `PUT`  | `/authorized/:authenticatedUserName/posts/:postId/like`                       | Like or unlike a post.                   |
| `POST` | `/authorized/:authenticatedUserName/posts/:postId/comment`                    | Add a comment to a post.                 |

All endpoints are relative to the API base path.

## Project Structure

```
backend/
├── src/
│   ├── controllers/     # Request handlers
│   ├── middleware/      # Authentication middleware
│   ├── prisma/
│   │   ├── schema.prisma
│   │   ├── PrismaQueries.js
│   │   └── SeedSampleData.js
│   ├── routes/
│   │   └── mainRoutes.js
│   └── index.js
├── package.json
└── .env
```

## Testing

Automated tests are not currently configured.

The `test` script is a placeholder. API endpoints can be manually tested using Postman or other HTTP clients.

## Deployment

The backend is deployed on Render and uses PostgreSQL for persistent data storage.

Production environment variables must be configured in the hosting environment:

- `DATABASE_URL`

- `JWT_SECRET_KEY`

- `CORS_URL`

- `PORT` (when required by the hosting environment)

The backend is configured to use the hosting provider's assigned port, falling back to `4000`.

[Production API Status](https://social-circle-app.onrender.com/social-circle-api/v1/status)

> Free hosting tiers may introduce cold-start delays.

## License

This project is licensed under the **GNU General Public License v3.0 (GPL-3.0)**.

See the repository's [LICENSE](../LICENSE) file for details.

## Related Links

- [Main Project README](../README.md)

- [Social Circle Repository](https://github.com/amalk-au/social-circle-app)

- [Live Application](https://amalk.au/social-circle-app/)

- [Portfolio](https://amalk.au)

---

Developed by [amalk-au](https://github.com/amalk-au)
