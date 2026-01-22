# Paginated API

## What this project builds
This is a small Express API for a card collection. It uses an in-memory array as a mock database and exposes CRUD routes (create, read, update, delete) with simple pagination.

## Learning goals
- Set up an Express server with middleware.
- Create an Express router for a resource (cards).
- Implement CRUD endpoints.
- Add pagination with query parameters.

## Folder structure
Create this structure exactly:

```
4b-me/
├─ index.js
├─ package.json
└─ routes/
	 └─ cards.js
```

## Step-by-step build (no starter files)
1. Create a new project folder named `4b-me`.
2. Inside the folder, create a `routes` directory.
3. Create `package.json` and add `"type": "module"` to enable ES modules.
4. Add scripts to `package.json`: `"start": "node index.js"` and `"dev": "nodemon index.js"`.
5. Install dependencies: `pnpm add express cors` and `pnpm add -D nodemon`.
6. Create the files `index.js` and `routes/cards.js` following the implementation checklist.
7. Run `pnpm start` or `pnpm dev` to start the server.

## Code explanation (high level)
### Server entry (`index.js`)
- Imports Express, CORS, and the cards router.
- Creates the app and registers middleware.
- Defines a base `/` route for a friendly message.
- Mounts the cards router at `/cards`.
- Starts the server on port 3000.

### Cards router (`routes/cards.js`)
- Uses an in-memory `cards` array as a mock database.
- `GET /cards` returns a paginated list of cards.
- `GET /cards/:id` returns one card by `id`.
- `POST /cards` creates a new card (validates required fields).
- `PUT /cards/:id` updates an existing card.
- `DELETE /cards/:id` removes a card.

## Implementation checklist (no code provided)
Use this checklist to build each file yourself.

### package.json
- Set the project to ESM by adding `"type": "module"`.
- Add runtime dependencies: Express and CORS.
- Add a `scripts` section with:
  - `"start": "node index.js"` to run the server.
  - `"dev": "nodemon index.js"` for development with auto-restart.
- Add Nodemon as a dev dependency.

### index.js
- Import Express, CORS, and your cards router module.
- Create the Express app and choose a port (3000).
- Add middleware for CORS and JSON body parsing.
- Add a base route at `/` that returns a welcome message.
- Mount the cards router at `/cards`.
- Start the server and log the URL.

### routes/cards.js
- Create an Express router.
- Create an in-memory array named `cards` with one example card object.
- Add a `GET /` route that supports pagination with `page` and `limit` query params.
- Add `GET /:id` to fetch one card by `id`.
- Add `POST /` with basic validation for `suit`, `value`, and `collection`.
- Add `PUT /:id` to update a card (keep old fields if not provided).
- Add `DELETE /:id` to remove a card.
- Export the router as the default export.

## Example requests (describe, don’t paste files)
- List cards: send a GET request to `/cards`.
- Paginate: add `?page=2&limit=5` to `/cards`.
- Fetch one card: GET `/cards/:id`.
- Create a card: POST `/cards` with JSON body `{ "suit": "hearts", "value": "ace", "collection": "classic" }`.
- Update a card: PUT `/cards/:id` with any fields you want to change.
- Delete a card: DELETE `/cards/:id`.
