# 10xCards

[![Project Status: In Progress](https://img.shields.io/badge/status-in--progress-yellow.svg)](https://github.com/your-username/10x-cards)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)

A web application designed to streamline the learning process by automating the creation of educational flashcards using Artificial Intelligence.

## Table of Contents

- [Project Description](#project-description)
- [Tech Stack](#tech-stack)
- [Getting Started Locally](#getting-started-locally)
- [Available Scripts](#available-scripts)
- [Project Scope](#project-scope)
- [Project Status](#project-status)
- [License](#license)

## Project Description

**10xCards** is a web application that allows users to quickly generate high-quality flashcards from any text, eliminating the time-consuming task of manual preparation. The application is targeted at a wide range of users, from students to professionals, who want to effectively use the spaced repetition technique to reinforce their knowledge. The MVP version focuses on key functionalities: AI-powered flashcard generation, flashcard management, and a simple learning system based on the SM-2 algorithm.

The problem this project aims to solve is the time-consuming and laborious nature of manual flashcard creation. By reducing the creation time from hours to minutes, 10xCards helps users adopt the effective spaced repetition learning method.

## Tech Stack

### Frontend

- **[Astro 5](https://astro.build/)**: For building fast, content-focused websites.
- **[React 19](https://react.dev/)**: For creating interactive UI components.
- **[TypeScript 5](https://www.typescriptlang.org/)**: For static typing and improved code quality.
- **[Tailwind 4](https://tailwindcss.com/)**: For utility-first CSS styling.
- **[Shadcn/ui](https://ui.shadcn.com/)**: For accessible and reusable UI components.

### Backend

- **[Supabase](https://supabase.io/)**: An open-source Firebase alternative providing a PostgreSQL database, authentication, and a Backend-as-a-Service SDK.

### AI

- **[OpenRouter.ai](https://openrouter.ai/)**: For accessing a wide range of AI models (OpenAI, Anthropic, Google) to ensure high efficiency and low costs.

### CI/CD and Hosting

- **[GitHub Actions](https://github.com/features/actions)**: For creating CI/CD pipelines.
- **[DigitalOcean](https://www.digitalocean.com/)**: For hosting the application via a Docker image.

## Getting Started Locally

To get a local copy up and running, follow these simple steps.

### Prerequisites

- Node.js version **24.11.0**. We recommend using [nvm](https://github.com/nvm-sh/nvm) (Node Version Manager) to manage Node.js versions.
    ```sh
    nvm install 24.11.0
    nvm use 24.11.0
    ```
- A package manager like `npm` or `yarn`.

### Installation

1.  **Clone the repo**
    ```sh
    git clone https://github.com/PatrykMlodawski/10x-cards.git
    ```
2.  **Navigate to the project directory**
    ```sh
    cd 10x-cards
    ```
3.  **Install NPM packages**
    ```sh
    npm install
    ```
4.  **Set up environment variables**
    Create a `.env` file in the root of the project and add the necessary environment variables (e.g., Supabase keys, OpenRouter API key). You can use `.env.example` as a template.

5.  **Run the development server**
    ```sh
    npm run dev
    ```
    The application will be available at `http://localhost:3000`.

## Available Scripts

In the project directory, you can run the following scripts:

- `npm run dev`: Runs the app in the development mode.
- `npm run build`: Builds the app for production to the `dist/` folder.
- `npm run preview`: Serves the production build locally for preview.
- `npm run lint`: Lints the codebase using ESLint.
- `npm run lint:fix`: Lints and automatically fixes issues in the codebase.
- `npm run format`: Formats the code using Prettier.

## Project Scope

The MVP of 10xCards focuses on the following core functionalities:

- **User Account System**: Users can register and log in using an email and password.
- **AI-Powered Flashcard Generation**: Generate 5 to 100 flashcards from a source text (1,000 to 10,000 characters).
- **Flashcard Review and Acceptance**: Users can accept, edit, or reject AI-generated flashcards. Unreviewed sessions are saved to `localStorage`.
- **Flashcard Collection Management**: A single list of all accepted flashcards, with options to manually create, edit, and delete cards. A client-side search is also available.
- **Spaced Repetition Learning System**: A learning mode based on a ready-made SM-2 algorithm implementation, presenting cards scheduled for review daily.

### Out of Scope for MVP

The following features are intentionally **not** included in the MVP:

- Advanced, custom repetition algorithms.
- Importing files (PDF, DOCX, etc.).
- Grouping flashcards into decks or folders.
- Sharing flashcard sets between users.
- Integrations with external educational platforms.
- Dedicated mobile applications.
- Social logins (Google, Facebook, etc.).

## Project Status

This project is currently **in progress**. The core functionalities are being actively developed.

## License

Distributed under the MIT License. See `LICENSE` for more information.
