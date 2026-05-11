# Products API — Node + Express + MongoDB

This project uses the same development-container style and product data structure from the `mongodb-activities-s26` repo:

```js
{ name: "Laptop", price: 899.99, quantity: 10, warehouse: "A" }
```

The database connection is configured through `.env`:

```bash
MONGODB_URI=mongodb://db:27017
DB_NAME=storeDB
COLLECTION_NAME=products
PORT=3000
```

## Run in VS Code Dev Containers

1. Open this folder in VS Code.
2. Choose **Reopen in Container**.
3. After the container finishes building, run:

```bash
npm run seed
npm run dev
```

Open:

```text
http://localhost:3000
```

## API Routes

| Method | Route | Description |
|---|---|---|
| GET | `/api/health` | Check API and database connection |
| GET | `/api/products` | List all products |
| GET | `/api/products?warehouse=A` | Filter by warehouse |
| GET | `/api/products?minPrice=50&maxPrice=200` | Filter by price range |
| GET | `/api/products/:id` | Get one product |
| POST | `/api/products` | Create a product |
| PUT | `/api/products/:id` | Replace a product |
| PATCH | `/api/products/:id` | Partially update a product |
| DELETE | `/api/products/:id` | Delete a product |

## Example POST

```bash
curl -X POST http://localhost:3000/api/products \
  -H "Content-Type: application/json" \
  -d '{"name":"Docking Station","price":149.99,"quantity":20,"warehouse":"A"}'
```

## Example Queries

```bash
curl http://localhost:3000/api/products
curl "http://localhost:3000/api/products?warehouse=A"
curl "http://localhost:3000/api/products?minPrice=50&maxPrice=200"
curl "http://localhost:3000/api/products?maxQuantity=25"
```

## Questions
1. What is the purpose of using `.env`
2. How does this work:
```js
if (query.minPrice || query.maxPrice) {
    filter.price = {};
    if (query.minPrice) filter.price.$gte = Number(query.minPrice);
    if (query.maxPrice) filter.price.$lte = Number(query.maxPrice);
}
```
3. What is the program `seed.js` used for?
4. Try all API routes using Postman
5. In terms of code what is the difference between `put` and `patch`

## Exercise
Do a repo of your own to represent whatever you want as long as it has four fields (data members), make sure that your program has the "same" API routes and to provide test data. The README file should have screenshots of using all API routes, either by using Postman, or by modifying `index.html` to have all the operations.

If you don't want to think about the object, you can do books: name, author, year, price.

