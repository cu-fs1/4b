# 4b-me

## What this project builds
This is a small Express API for a card collection. It uses an in-memory array as a mock database, follows a simple controller/service/model structure, and exposes CRUD routes with pagination.

## Features
- Express server with CORS and JSON middleware
- CRUD endpoints for cards
- Pagination via `page` and `limit` query params
- In-memory data store for quick iteration

## Folder structure
```
4b-me/
├─ index.js
├─ package.json
├─ controllers/
│  └─ card.controller.js
├─ models/
│  └─ card.model.js
├─ routes/
│  └─ card.routes.js
└─ services/
   └─ card.service.js
```

## Scripts
- start: node index.js
- dev: nodemon index.js

## How it works (high level)
### Server entry
- Creates the Express app and registers middleware.
- Defines a base `/` route for a welcome message.
- Mounts the cards router at `/cards`.

### Router
- Defines the REST routes and delegates to the controller.

### Controller
- Handles request/response logic and basic validation.

### Service
- Encapsulates pagination and business logic.

### Model
- Manages the in-memory card array.

## API
Base URL: http://localhost:3000

### Endpoints
- GET /cards
  - Query params: page (default 1), limit (default 10)
  - Response shape:
    ```json
    {
      "totalCards": 1,
      "totalPages": 1,
      "currentPage": 1,
      "limit": 10,
      "cards": [
        { "id": 171836785992, "suit": "diamonds", "value": "queen", "collection": "royal" }
      ],
      "next": { "page": 2, "limit": 10 },
      "previous": { "page": 1, "limit": 10 }
    }
    ```
- GET /cards/:id
- POST /cards
  - Body: { "suit": "hearts", "value": "ace", "collection": "classic" }
- PUT /cards/:id
  - Body: any fields to update
- DELETE /cards/:id

## Example requests (describe, don’t paste files)
- List cards: send a GET request to /cards.
- Paginate: add ?page=2&limit=5 to /cards.
- Fetch one card: GET /cards/:id.
- Create a card: POST /cards with JSON body { "suit": "hearts", "value": "ace", "collection": "classic" }.
- Update a card: PUT /cards/:id with any fields you want to change.
- Delete a card: DELETE /cards/:id.
