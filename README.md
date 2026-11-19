# Social Circle

A full-stack social networking application designed to help people stay connected with their closest friends through profiles, follow relationships and social interactions.

## Table of Contents

- [Overview](#overview)

- [Features](#features)

- [Screenshots](#screenshots)

- [Live Demo](#live-demo)

- [Tech Stack](#tech-stack)

- [Architecture](#architecture)

- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)

  - [Installation](#installation)

  - [Environment Variables](#environment-variables)

- [Project Structure](#project-structure)

- [Available Scripts](#available-scripts)

- [Development](#development)

- [Testing](#testing)

- [API Reference](#api-reference)

- [Deployment](#deployment)

- [Troubleshooting](#troubleshooting)

- [Contributing](#contributing)

- [License](#license)

- [Acknowledgements](#acknowledgements)

- [Contact](#contact)

---

## Overview

Social Circle is a full-stack social networking application designed to help users connect and interact with their closest friends.

The application provides a platform where users can create profiles, establish connections, share posts and interact with content published by other users.

The project was developed to strengthen practical experience in full-stack web development, including REST API development, database management, authentication and frontend-backend integration.

The application follows a client-server architecture:

- **Frontend:** A React-based single-page application providing the user interface.

- **Backend:** A Node.js and Express REST API responsible for application logic and authentication.

- **Database:** PostgreSQL for persistent data storage, accessed through Prisma ORM.

## Features

### User Management

- User registration and login.

- JWT-based authentication.

- Secure password hashing using bcryptjs.

- User profiles with personal information and profile pictures.

- Profile editing.

### Social Connections

- Browse registered users.

- View other users' profiles.

- Send follow requests.

- Manage follow relationships and their statuses.

### Social Feed

- Create and publish posts.

- View posts from the current user and followed users.

- Like and unlike posts.

- Comment on posts.

- View individual posts and their associated information.

### Authentication and Security

- Protected API endpoints using JWT authentication.

- Bearer token authentication.

- Password hashing before database storage.

- Token expiration after 30 minutes.

## Screenshots

### Application Overview

### User Authentication

### Social Feed

### User Profiles

### User Connections

### Mobile View

> **Note:** These are placeholder image references. Add the corresponding screenshots to `docs/screenshots/` when available.

## Live Demo

**Frontend Application:**

[Social Circle – Live Application](https://amalk.au/social-circle-app/)

**Backend API:**

[Social Circle – API Status](https://social-circle-app.onrender.com/social-circle-api/v1/status)

**Portfolio:**

[https://amalk.au](https://amalk.au)

**Source Code:**

[GitHub Repository](https://github.com/amalk-au/social-circle-app)

> **Deployment notes:**
>
> - The frontend is hosted using GitHub Pages.
> - The backend API is hosted on Render.
> - The application uses a PostgreSQL database.
> - Free hosting tiers may introduce cold-start delays. Initial requests can take up to two minutes.
> - The frontend uses React Router with a deployment base path. Navigate through the application rather than directly accessing nested routes, which may return a 404 depending on the hosting configuration.

## Tech Stack

| Category                  | Technology              |
| ------------------------- | ----------------------- |
| Frontend Framework        | React 19                |
| Frontend Build Tool       | Vite 6                  |
| Language                  | JavaScript (ES Modules) |
| Markup                    | HTML5                   |
| Styling                   | CSS3                    |
| Routing                   | React Router 7          |
| Backend Runtime           | Node.js                 |
| Backend Framework         | Express 5               |
| Database                  | PostgreSQL              |
| ORM                       | Prisma 6                |
| Authentication            | JSON Web Tokens (JWT)   |
| Password Hashing          | bcryptjs                |
| Environment Configuration | dotenv                  |
| API Testing               | Postman                 |
| Frontend Hosting          | GitHub Pages            |
| Backend Hosting           | Render                  |
| Package Manager           | pnpm (preferred)        |

## Architecture

Social Circle follows a client-server architecture with three primary components.

### Frontend

The frontend is a React single-page application built with Vite.

It is responsible for:

- Rendering application pages and reusable components.

- Managing client-side navigation through React Router.

- Handling user registration and authentication.

- Communicating with the backend through HTTP requests.

- Managing JWT authentication tokens in browser local storage.

- Displaying user profiles, social connections and posts.

### Backend

The backend is a REST API developed using Node.js and Express.

It is responsible for:

- Processing frontend API requests.

- Authenticating users.

- Generating and validating JWT tokens.

- Hashing passwords using bcryptjs.

- Managing user profiles and follow relationships.

- Creating and retrieving posts.

- Processing likes and comments.

- Communicating with PostgreSQL through Prisma ORM.

### Database

PostgreSQL provides persistent application storage.

Prisma manages database access and defines the application's data models.

The database includes the following entities:

| Model    | Description                                      |
| -------- | ------------------------------------------------ |
| User     | Stores user accounts and profile information.    |
| Follow   | Stores follow relationships and their statuses.  |
| Post     | Stores posts created by users.                   |
| PostLike | Stores post likes and associated users.          |
| Comment  | Stores comments associated with posts and users. |

### Request Flow

1.  A user interacts with the React frontend.

2.  The frontend sends an HTTP request to the Express API.

3.  Protected requests include a JWT Bearer token.

4.  Authentication middleware validates the token.

5.  Express controllers process the request.

6.  Prisma communicates with PostgreSQL.

7.  The API returns a JSON response to the frontend.

## Getting Started

### Prerequisites

Ensure the following tools are installed:

| Requirement | Purpose                   |
| ----------- | ------------------------- |
| Node.js     | JavaScript runtime        |
| pnpm        | Preferred package manager |
| PostgreSQL  | Relational database       |
| Git         | Version control           |

The repository does not currently specify a required Node.js version. Use a Node.js version compatible with the installed dependencies.

### Installation

#### 1\. Clone the repository

```
git clone https://github.com/amalk-au/social-circle-app.git

cd social-circle-app
```

#### 2\. Install frontend dependencies

```
cd frontend

pnpm install
```

#### 3\. Install backend dependencies

Open another terminal or return to the repository root:

```
cd backend

pnpm install
```

#### 4\. Configure environment variables

Create the required environment files.

For the backend:

```
cd backend

touch .env
```

For the frontend:

```
cd frontend

touch .env
```

Configure the variables described in the [Environment Variables](#environment-variables) section.

#### 5\. Configure the database

Ensure PostgreSQL is running and create a database for the application.

From the backend directory, generate the Prisma client:

```
pnpm exec prisma generate --schema src/prisma/schema.prisma
```

Synchronise the database schema:

```
pnpm exec prisma db push --schema src/prisma/schema.prisma
```

#### 6\. Seed sample data (Optional)

The backend provides a seed script for generating sample application data.

```
cd backend

pnpm run seed
```

#### 7\. Start the backend

```
cd backend

pnpm run dev
```

The backend defaults to:

```
http://localhost:4000
```

#### 8\. Start the frontend

In another terminal:

```
cd frontend

pnpm run dev
```

Vite will display the local development URL in the terminal.

Open the displayed URL in your browser.

### Environment Variables

The application requires environment variables for database connectivity, authentication, cross-origin requests and frontend API communication.

#### Backend

Create `backend/.env`:

| Variable         | Description                                        | Required |
| ---------------- | -------------------------------------------------- | -------- |
| `DATABASE_URL`   | PostgreSQL connection string used by Prisma.       | Yes      |
| `JWT_SECRET_KEY` | Secret used to sign and verify JWT tokens.         | Yes      |
| `CORS_URL`       | Allowed frontend origin for cross-origin requests. | Yes      |
| `PORT`           | Backend server port. Defaults to `4000`.           | No       |

Example:

```
DATABASE_URL="postgresql://username:password@localhost:5432/social_circle"
JWT_SECRET_KEY="replace-with-a-secure-secret"
CORS_URL="http://localhost:5173"
PORT=4000
```

#### Frontend

Create `frontend/.env`:

| Variable       | Description                  | Required |
| -------------- | ---------------------------- | -------- |
| `VITE_API_URL` | Base URL of the backend API. | Yes      |

Example:

```
VITE_API_URL="http://localhost:4000"
```

The frontend appends the API endpoint paths to this base URL.

**Important:**

- Never commit `.env` files or production credentials.

- Use a strong, unique JWT secret in production.

- Configure `CORS_URL` to match the deployed frontend origin.

- Frontend environment variables prefixed with `VITE_` are exposed to the browser. Never store secrets in frontend environment variables.

## Project Structure

```
social-circle-app/
│
├── frontend/
│   ├── public/
│   ├── src/
│   │   ├── components/
│   │   ├── ApiQueries.js
│   │   ├── App.jsx
│   │   ├── App.css
│   │   ├── ErrorPage.jsx
│   │   ├── index.css
│   │   ├── main.jsx
│   │   └── routes.jsx
│   │
│   ├── index.html
│   ├── package.json
│   ├── vite.config.js
│   └── .env
│
├── backend/
│   ├── src/
│   │   ├── controllers/
│   │   ├── middleware/
│   │   ├── prisma/
│   │   │   ├── schema.prisma
│   │   │   ├── PrismaQueries.js
│   │   │   └── SeedSampleData.js
│   │   ├── routes/
│   │   │   └── mainRoutes.js
│   │   └── index.js
│   │
│   ├── package.json
│   └── .env
│
├── docs/
│   └── screenshots/
│
├── .gitignore
├── LICENSE
└── README.md
```

> The structure above highlights the main application files and directories. Generated files, installed dependencies and additional implementation files are omitted.

## Available Scripts

The frontend and backend maintain separate `package.json` files.

### Frontend

Run commands from the `frontend/` directory.

| Command            | Description                                       |
| ------------------ | ------------------------------------------------- |
| `pnpm run dev`     | Start the Vite development server.                |
| `pnpm run build`   | Build the frontend for production.                |
| `pnpm run preview` | Preview the production build locally.             |
| `pnpm run lint`    | Run ESLint.                                       |
| `pnpm run deploy`  | Build and deploy the frontend using GitHub Pages. |

### Backend

Run commands from the `backend/` directory.

| Command           | Description                                 |
| ----------------- | ------------------------------------------- |
| `pnpm run dev`    | Start the backend using Node.js watch mode. |
| `pnpm start`      | Start the backend server.                   |
| `pnpm run studio` | Open Prisma Studio.                         |
| `pnpm run seed`   | Run the sample data seeding script.         |

**Note:** pnpm is the preferred package manager for development. The repository currently does not enforce a specific package manager through its package configuration.

## Development

Follow these guidelines when contributing to the project.

1.  Create a feature branch before implementing changes.

2.  Follow the existing project structure and coding conventions.

3.  Keep frontend components and backend responsibilities separated.

4.  Use Prisma for database interactions.

5.  Protect authenticated API endpoints using the existing JWT middleware.

6.  Keep environment variables and credentials outside version control.

7.  Run the available linting and build commands before submitting changes.

8.  Update documentation when introducing new functionality or configuration requirements.

### Database Development

The Prisma schema is located at:

```
backend/src/prisma/schema.prisma
```

After modifying the schema, regenerate the Prisma client:

```
cd backend

pnpm exec prisma generate --schema src/prisma/schema.prisma
```

Synchronise database changes when appropriate:

```
pnpm exec prisma db push --schema src/prisma/schema.prisma
```

For production database changes, use an appropriate migration workflow rather than relying on development-only schema synchronisation.

## Testing

The project currently does not provide a configured automated test suite.

The backend `test` script is a placeholder and exits with an error. The frontend does not currently define a test script.

### Current Verification

The following checks are available:

**Frontend linting:**

```
cd frontend

pnpm run lint
```

**Frontend production build:**

```
cd frontend

pnpm run build
```

**Backend API verification:**

The backend provides a status endpoint:

```
GET /social-circle-api/v1/status
```

You can also use Postman to manually verify API endpoints and authentication behaviour.

Automated unit, integration and end-to-end tests are not currently configured.

## API Reference

### Base URL

Local development:

```
http://localhost:4000
```

Production:

```
https://social-circle-app.onrender.com
```

### Authentication

Protected endpoints require a valid JWT supplied through the HTTP Authorization header.

```
Authorization: Bearer <JWT_TOKEN>
```

### Endpoints

All API endpoints use the following prefix:

```
/social-circle-api/v1
```

#### Authentication

| Method | Endpoint    | Description                    | Authentication |
| ------ | ----------- | ------------------------------ | -------------- |
| GET    | `/status`   | Check backend status.          | No             |
| POST   | `/login`    | Authenticate an existing user. | No             |
| POST   | `/register` | Register a new user.           | No             |

#### User Profiles

| Method | Endpoint                                                            | Description                              | Authentication |
| ------ | ------------------------------------------------------------------- | ---------------------------------------- | -------------- |
| GET    | `/authorized/:authenticatedUserName/:selectedUserName/profile/view` | Retrieve a user's profile.               | Yes            |
| PUT    | `/authorized/:authenticatedUserName/profile/edit`                   | Update the authenticated user's profile. | Yes            |

#### Social Connections

| Method | Endpoint                                                                      | Description                   | Authentication |
| ------ | ----------------------------------------------------------------------------- | ----------------------------- | -------------- |
| GET    | `/authorized/:authenticatedUserName/all-users`                                | Retrieve registered users.    | Yes            |
| PUT    | `/authorized/:authenticatedUserName/all-users/:selectedUserName/followstatus` | Update a follow relationship. | Yes            |

#### Posts and Interactions

| Method | Endpoint                                                                   | Description               | Authentication |
| ------ | -------------------------------------------------------------------------- | ------------------------- | -------------- |
| GET    | `/authorized/:authenticatedUserName/all-users/:selectedUserName/home-feed` | Retrieve the social feed. | Yes            |
| POST   | `/authorized/:authenticatedUserName/new-post`                              | Create a new post.        | Yes            |
| GET    | `/authorized/:authenticatedUserName/posts/:postId`                         | Retrieve a post by ID.    | Yes            |
| PUT    | `/authorized/:authenticatedUserName/posts/:postId/like`                    | Like or unlike a post.    | Yes            |
| POST   | `/authorized/:authenticatedUserName/posts/:postId/comment`                 | Add a comment to a post.  | Yes            |

> All endpoints are relative to `/social-circle-api/v1`. The tables document the implemented routes, not every request payload or response structure.

## Deployment

The application uses separate hosting environments for the frontend and backend.

### Frontend Deployment

**Hosting:** GitHub Pages

The frontend is configured to run under the following base path:

```
/social-circle-app
```

This is configured in `frontend/vite.config.js`:

```
export default defineConfig({
  base: '/social-circle-app',
  plugins: [react()],
})
```

The frontend package provides a deployment script:

```
cd frontend

pnpm run deploy
```

The deployment script builds the application and publishes the `dist` directory using `gh-pages`.

Configure the following frontend environment variable for production:

```
VITE_API_URL=https://social-circle-app.onrender.com
```

**Live URL:**

[https://amalk.au/social-circle-app/](https://amalk.au/social-circle-app/)

### Backend Deployment

**Hosting:** Render

The backend starts using:

```
pnpm start
```

The application listens on the port supplied by the hosting environment, falling back to port `4000`.

Configure the backend environment variables in the hosting provider:

- `DATABASE_URL`

- `JWT_SECRET_KEY`

- `CORS_URL`

- `PORT` (when required by the hosting configuration)

Ensure the PostgreSQL database is accessible from the deployed backend.

**API Status:**

[https://social-circle-app.onrender.com/social-circle-api/v1/status](https://social-circle-app.onrender.com/social-circle-api/v1/status)

### Production Considerations

- Ensure the frontend API URL points to the deployed backend.

- Configure CORS to allow requests from the deployed frontend origin.

- Keep database credentials and JWT secrets secure.

- Ensure Prisma Client is generated during backend deployment.

- Verify database connectivity before starting the application.

- Account for cold starts when using free hosting tiers.

- Ensure the frontend hosting configuration supports the application's React Router routes.

## Troubleshooting

| Issue                                  | Possible Solution                                                                             |
| -------------------------------------- | --------------------------------------------------------------------------------------------- |
| Frontend cannot connect to the backend | Check `VITE_API_URL` and verify that the backend is running.                                  |
| CORS errors                            | Verify that `CORS_URL` matches the frontend origin.                                           |
| Database connection fails              | Check PostgreSQL availability and `DATABASE_URL`.                                             |
| Authentication fails                   | Verify `JWT_SECRET_KEY` and ensure the token has not expired.                                 |
| Prisma Client errors                   | Run `pnpm exec prisma generate --schema src/prisma/schema.prisma` from the backend directory. |
| Frontend routes return 404             | Check the GitHub Pages base path and navigate through the application.                        |
| Application takes a long time to load  | Free hosting tiers may introduce cold-start delays.                                           |
| Frontend build fails                   | Run `pnpm install` and inspect the Vite build output.                                         |
| Backend fails to start                 | Verify environment variables, dependencies and database connectivity.                         |

## Contributing

Contributions and suggestions are welcome.

To contribute:

1.  Fork the repository.

2.  Create a feature branch.

3.  Implement your changes following the existing conventions.

4.  Verify the changes using the available development commands.

5.  Submit a pull request describing your changes.

For significant changes, consider opening an issue before implementation.

## License

This project is licensed under the **GNU General Public License v3.0 (GPL-3.0)**.

You are free to use, modify and distribute this software under the terms of the licence.

See the [LICENSE](LICENSE) file for the complete licence terms.

## Contact

- **Author:** Amal K.

- **GitHub:** [@amalk-au](https://github.com/amalk-au)

- **Portfolio:** [https://amalk.au](https://amalk.au)

- **Repository:** [Social Circle](https://github.com/amalk-au/social-circle-app)

For bug reports, feature requests or questions, please use the repository's [GitHub Issues](https://github.com/amalk-au/social-circle-app/issues).

---

Developed by [amalk-au](https://github.com/amalk-au)
