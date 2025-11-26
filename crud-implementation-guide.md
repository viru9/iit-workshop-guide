## 10. Implement Complete CRUD API for Products

**Prompt to AI:** 
```
Create a complete CRUD (Create, Read, Update, Delete) API for products with the following operations:

### CREATE - Add New Product
Create an endpoint POST /api/products that:
1. Accepts JSON body with: name (required), price (required), category (optional), inStock (optional, default true)
2. Validates that name and price are provided
3. Validates that price is a positive number
4. Inserts the product into the database
5. Returns the created product with 201 status code
6. Handles validation errors with 400 status

### READ - Get All Products
Create an endpoint GET /api/products that:
1. Retrieves all products from the database
2. Converts inStock (0/1) to boolean in the response
3. Sorts products by newest first (createdAt DESC)
4. Returns array of products with 200 status
5. Returns empty array if no products exist

### READ - Get Single Product by ID
Create an endpoint GET /api/products/:id that:
1. Takes product ID from URL parameter
2. Retrieves the product from database by ID
3. Converts inStock (0/1) to boolean
4. Returns the product with 200 status if found
5. Returns 404 status with error message if product not found

### UPDATE - Modify Existing Product
Create an endpoint PUT /api/products/:id that:
1. Takes product ID from URL parameter
2. Accepts JSON body with any combination of: name, price, category, inStock
3. Updates only the provided fields (partial update)
4. Updates the updatedAt timestamp automatically
5. Validates that price is positive if provided
6. Returns the updated product with 200 status
7. Returns 404 if product not found
8. Returns 400 for validation errors

### DELETE - Remove Product
Create an endpoint DELETE /api/products/:id that:
1. Takes product ID from URL parameter
2. Deletes the product from database
3. Returns 204 No Content on success
4. Returns 404 if product not found
5. Handles database errors appropriately

### Integration Requirements
1. Create controller functions in src/controllers/productController.js
2. Create routes in src/routes/productRoutes.js mapping to controller functions
3. Add error handling middleware in src/middleware/errorHandler.js
4. Update src/index.js to:
   - Import and mount product routes at /api/products
   - Add error handling middleware after all routes
   - Ensure express.json() middleware is configured
   - Initialize database connection from src/config/db.js

All endpoints should handle errors gracefully and return consistent JSON error responses.

After all create a new .md file as api-testing, add curl requests of all the apis we created
```
