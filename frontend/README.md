# Social Circle – Frontend

The frontend for **Social Circle**, a full-stack social networking application designed to help people stay connected with their closest friends.

Built with React and Vite, the frontend provides the user interface for authentication, profiles, social connections and interactions.

## Overview

The Social Circle frontend is a React single-page application responsible for rendering the user interface and communicating with the backend REST API.

### Features

- User registration and login.

- JWT-based authentication.

- User profile viewing and editing.

- Browse registered users.

- Follow and unfollow users.

- Social feed.

- Create posts.

- Like and unlike posts.

- Comment on posts.

- Individual post views.

- Client-side routing using React Router.

## Tech Stack

| Technology     | Purpose                           |
| -------------- | --------------------------------- |
| React 19       | UI framework                      |
| Vite 6         | Development server and build tool |
| JavaScript     | Application programming language  |
| React Router 7 | Client-side routing               |
| HTML5          | Markup                            |
| CSS3           | Styling                           |
| REST API       | Backend communication             |

## Getting Started

### Prerequisites

- Node.js

- pnpm (preferred)

- Git

### Installation

Clone the repository:

```
git clone https://github.com/amalk-au/social-circle-app.git

cd social-circle-app/frontend
```

Install dependencies:

```
pnpm install
```

### Environment Variables

Create a `.env` file in the `frontend/` directory:

```
VITE_API_URL=http://localhost:4000
```

| Variable       | Description                  |
| -------------- | ---------------------------- |
| `VITE_API_URL` | Base URL of the backend API. |

### Start the Development Server

```
pnpm run dev
```

Vite will display the local development URL in the terminal.

Open the displayed URL in your browser.

## Available Scripts

| Command            | Description                                          |
| ------------------ | ---------------------------------------------------- |
| `pnpm run dev`     | Start the Vite development server.                   |
| `pnpm run build`   | Build the application for production.                |
| `pnpm run preview` | Preview the production build locally.                |
| `pnpm run lint`    | Run ESLint.                                          |
| `pnpm run deploy`  | Build and deploy the application using GitHub Pages. |

## Project Structure

```
frontend/
├── public/
├── src/
│   ├── components/
│   ├── ApiQueries.js
│   ├── App.jsx
│   ├── App.css
│   ├── ErrorPage.jsx
│   ├── index.css
│   ├── main.jsx
│   └── routes.jsx
├── index.html
├── package.json
├── vite.config.js
└── .env
```

## Deployment

The frontend is deployed using GitHub Pages.

The application is configured to run under the following base path:

```
/social-circle-app
```

The deployment script builds the application and publishes the production build.

### Production Configuration

Configure the following environment variable:

```
VITE_API_URL=https://social-circle-app.onrender.com
```

### Deployment Command

```
pnpm run deploy
```

**Live Application:**

[Social Circle](https://amalk.au/social-circle-app/)

> The application uses React Router and a configured deployment base path. Direct navigation to nested routes may return a 404 depending on the hosting configuration.

## Testing

Automated tests are not currently configured.

The following checks are available:

```
pnpm run lint
```

```
pnpm run build
```

## Related Links

- [Main Project README](../README.md)

- [Backend README](../backend/README.md)

- [GitHub Repository](https://github.com/amalk-au/social-circle-app)

- [Live Application](https://amalk.au/social-circle-app/)

- [Portfolio](https://amalk.au)

---

Developed by [amalk-au](https://github.com/amalk-au)
