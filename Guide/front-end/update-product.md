Create an edit product modal component in React with the following specifications:

1. **Component Location**: 
   - File: `frontend/src/pages/ProductsPage.tsx`
   - Trigger: When clicking the edit button in the products table rows

2. **Modal Requirements**:
   - Use MUI Dialog or Modal component
   - Pre-fill the form with the selected product's data
   - Include the same fields as the create product form
   - Add two buttons at the bottom: "Update" and "Cancel"

3. **Form Fields** (same as create product form):
   - Name (text input)
   - Price (number input)
   - Category (text input)
   - In Stock (checkbox)

4. **Functionality**:
   - Clicking "Cancel" should close the modal without saving
   - Clicking "Update" should:
     - Validate the form
     - Send a PUT request to update the product using axios
     - Show a success/error notification using MUI Snackbar
     - Close the modal on success
     - Refresh the products list to show updated data

5. **API Integration**:
   - Use the existing axios instance from `frontend/src/config/api.config.ts`
   - Endpoint: `PUT /api/products/:id`
   - Request body: 
     ```json
     {
       "name": "string",
       "price": "number",
       "category": "string",
       "inStock": "boolean"
     }
     ```

6. **UI/UX**:
   - Use appropriate MUI components (TextField, Button, Dialog, etc.)
   - Add form validation
   - Show loading state during API call
   - Add proper error handling
   - Ensure the modal is accessible (proper ARIA labels, focus management)

7. **Code Structure**:
   - Keep the component modular and reusable
   - Use TypeScript interfaces for props and state
   - Follow existing code style and patterns
   - Add necessary comments for complex logic

8. **Example CURL for reference**:
   ```bash
   curl -X PUT http://localhost:4000/api/products/1 \
     -H "Content-Type: application/json" \
     -d '{
       "name": "Laptop",
       "price": 999.99,
       "category": "Electronics",
       "inStock": true
     }'

Please provide the complete implementation following React best practices and TypeScript type safety.     