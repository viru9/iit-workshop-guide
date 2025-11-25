# AI-Powered CRUD Implementation Guide

This guide provides step-by-step AI prompts to implement a complete CRUD (Create, Read, Update, Delete) API for products using Express and SQLite3.

## Prerequisites
- Basic Express.js setup (see `setup-guide.md`)
- SQLite3 installed
- Basic understanding of RESTful APIs

## 1. Set Up Database Schema

**Prompt to AI:**
```
Create an SQLite database configuration file that:
1. Creates a 'products' table with these columns:
   - id (INTEGER, PRIMARY KEY, AUTOINCREMENT)
   - name (TEXT, NOT NULL)
   - price (REAL, NOT NULL)
   - category (TEXT)
   - inStock (INTEGER, DEFAULT 1)
   - createdAt (DATETIME, DEFAULT CURRENT_TIMESTAMP)
   - updatedAt (DATETIME, DEFAULT CURRENT_TIMESTAMP)
2. Handles database connection
3. Creates the table if it doesn't exist
4. Is stored in src/config/db.js
```

## 2. Create Controller Functions

### 2.1 Get All Products

**Prompt to AI:**
```
Create a controller function that:
1. Retrieves all products from the database
2. Converts inStock (0/1) to boolean
3. Sorts by newest first
4. Handles errors appropriately
5. Returns the products array

Function signature: getProducts(req, res)
File: src/controllers/productController.js
```

### 2.2 Get Single Product

**Prompt to AI:**
```
Create a controller function that:
1. Takes a product ID from URL params
2. Retrieves a single product by ID
3. Returns 404 if not found
4. Converts inStock to boolean
5. Handles database errors

Function signature: getProduct(req, res)
File: src/controllers/productController.js
```

### 2.3 Create Product

**Prompt to AI:**
```
Create a controller function that:
1. Validates required fields (name, price)
2. Creates a new product in the database
3. Sets default values (inStock: true)
4. Returns the created product with 201 status
5. Handles validation and database errors

Function signature: createProduct(req, res)
File: src/controllers/productController.js
```

### 2.4 Update Product

**Prompt to AI:**
```
Create a controller function that:
1. Takes a product ID from URL params
2. Updates only the provided fields
3. Updates updatedAt timestamp
4. Returns the updated product
5. Handles non-existent products and errors

Function signature: updateProduct(req, res)
File: src/controllers/productController.js
```

### 2.5 Delete Product

**Prompt to AI:**
```
Create a controller function that:
1. Takes a product ID from URL params
2. Deletes the product
3. Returns 204 No Content on success
4. Returns 404 if product not found
5. Handles database errors

Function signature: deleteProduct(req, res)
File: src/controllers/productController.js
```

## 3. Set Up Routes

**Prompt to AI:**
```
Create an Express router that maps these endpoints:
- GET /api/products -> getProducts
- GET /api/products/:id -> getProduct
- POST /api/products -> createProduct
- PUT /api/products/:id -> updateProduct
- DELETE /api/products/:id -> deleteProduct

File: src/routes/productRoutes.js
```

## 4. Error Handling

**Prompt to AI:**
```
Create an error handling middleware that:
1. Logs errors to console
2. Returns appropriate status codes
3. Shows stack trace in development
4. Handles 404 errors
5. Formats error responses consistently

File: src/middleware/errorHandler.js
```

## 5. Testing the API

### 5.1 Create Test Data

**Prompt to AI:**
```
Create a script that inserts sample products for testing:
- 5 different products in various categories
- Mix of inStock true/false
- Realistic prices and names
- Output success message when done

File: scripts/seed.js
```

### 5.2 Test with cURL

**Prompt to AI:**
```
Create a markdown file with cURL commands to test:
1. Get all products
2. Get single product
3. Create new product
4. Update product
5. Delete product
6. Error cases (not found, invalid data)

File: docs/api-testing.md
```

## 6. Validation (Bonus)

**Prompt to AI:**
```
Create a validation middleware that:
1. Validates product creation:
   - name: required, string, min 2 chars
   - price: required, number, positive
   - category: optional string
   - inStock: optional boolean
2. Validates product updates (all fields optional but with same rules)
3. Returns clear error messages

File: src/middleware/validation.js
```

## 7. Documentation (Bonus)

**Prompt to AI:**
```
Create API documentation in OpenAPI/Swagger format that includes:
- All endpoints
- Request/response schemas
- Example requests
- Error responses
- Authentication (if added later)

File: docs/openapi.yaml
```

## Implementation Tips

1. **Test Each Step**: After implementing each function, test it before moving to the next
2. **Error Handling**: Pay special attention to error cases and edge conditions
3. **Environment Variables**: Use environment variables for configuration
4. **Code Organization**: Keep your code modular and well-commented
5. **Version Control**: Commit after each major feature is implemented and tested

## Next Steps After Implementation

1. Add input sanitization
2. Implement authentication/authorization
3. Add request rate limiting
4. Set up logging
5. Write unit and integration tests
6. Add API documentation
7. Set up database migrations

Remember to test all endpoints thoroughly and handle all possible error cases to ensure your API is robust and reliable.
