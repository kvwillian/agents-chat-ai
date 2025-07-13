# Agents Server

This is the backend server for the Agents project. It provides a RESTful API for managing rooms, uploading audio, transcribing audio, generating embeddings, and answering questions using Google Gemini AI. The server is built with Fastify, Drizzle ORM, and PostgreSQL with pgvector extension for vector search.

## Features

- Room and question management
- Audio upload and transcription (Portuguese, using Google Gemini)
- Embedding generation and semantic search with pgvector
- AI-powered answers based on audio context
- REST API with validation and OpenAPI schema

## Technologies Used

- **Node.js** (TypeScript)
- **Fastify** – Web framework
- **Drizzle ORM** – Type-safe database ORM
- **PostgreSQL** – Database
- **pgvector** – Vector search extension for PostgreSQL
- **Google Gemini AI** – Audio transcription, embeddings, and answer generation
- **Zod** – Schema validation
- **drizzle-kit** – Database migrations and schema generation
- **drizzle-seed** – Database seeding
- **@fastify/multipart** – File uploads

## Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) (v22+ recommended)
- [Docker](https://www.docker.com/) (for PostgreSQL with pgvector)
- [pnpm](https://pnpm.io/) or [npm](https://www.npmjs.com/) (for dependency management)

### Installation

1. **Clone the repository:**

   ```sh
   git clone https://github.com/kvwillian/agents-chat-ai
   cd agents-chat-ai
   ```

2. **Install dependencies:**

   ```sh
   npm install
   # or
   pnpm install
   ```

3. **Set up environment variables:**

   Copy `.env.example` to `.env` and fill in the required values:

   ```sh
   cp .env.example .env
   ```

   - Set your `DATABASE_URL` (see below)
   - Set your `GEMINI_API_KEY` (Google Gemini API key)

4. **Start PostgreSQL with pgvector using Docker:**

   ```sh
   docker-compose up -d
   ```

5. **Run database migrations:**

   ```sh
   npm run db:migrate
   ```

6. **(Optional) Seed the database:**

   ```sh
   npm run db:seed
   ```

### Running the Server

Start the development server:

```sh
npm run dev
```

The server will run on the port specified in `.env` (default: `3333`).

### API Usage

You can use the included [`client.http`](client.http) file with [REST Client](https://marketplace.visualstudio.com/items?itemName=humao.rest-client) extension for VS Code to test the API endpoints.

#### Example Endpoints

- `GET /health` – Health check
- `GET /rooms` – List rooms
- `POST /rooms` – Create a room
- `GET /rooms/:roomId/questions` – List questions for a room
- `POST /rooms/:roomId/questions` – Ask a question (AI-powered answer)
- `POST /rooms/:roomId/audio` – Upload audio for transcription and embedding

### Environment Variables

See `.env.example` for all required variables:

- `PORT` – Server port
- `DATABASE_URL` – PostgreSQL connection string (e.g., `postgresql://docker:docker@localhost:5432/agents`)
- `GEMINI_API_KEY` – Google Gemini API key

### Database

- Uses PostgreSQL with the [pgvector](https://github.com/pgvector/pgvector) extension for vector similarity search.
- Database schema and migrations are managed with Drizzle ORM and drizzle-kit. 

Made with ❤️ using Fastify, Drizzle ORM, and Google Gemini