I need to implement an "Add New Product" feature in a React TypeScript application using Material-UI (MUI) components. The feature should include:

1. A button above the products table that opens a modal dialog
2. The modal should contain a form with these fields:
   - Name (text input)
   - Price (number input)
   - Category (dropdown with options: Electronics, Sport, Furniture, Cosmetics)
   - In Stock (toggle switch)

3. The modal should have two buttons:
   - Cancel: Closes the modal and clears the form
   - Save: Sends the form data to the backend

4. Technical Requirements:
   - Use Material-UI (MUI) components for all UI elements
   - Use React Hook Form for form handling
   - Implement form validation:
     - Name: required
     - Price: required, must be a positive number
     - Category: required
   - Use axios for API calls
   - The API endpoint is already configured in `frontend/src/config/api.config.ts`
   - The backend expects a POST request to `/api/products` with the following JSON body:
     ```json
     {
       "name": "string",
       "price": number,
       "category": "string",
       "inStock": boolean
     }
     ```
   - Show a success/error notification using MUI's Snackbar component after form submission

5. File to modify:
   - `frontend/src/pages/ProductsPage.tsx`

6. Additional Notes:
   - The component should be responsive
   - Follow TypeScript best practices
   - Include proper TypeScript interfaces/types
   - Ensure the modal is accessible (proper ARIA labels, focus management)
   - Use MUI's theming system for consistent styling

Please provide the complete implementation following React best practices and TypeScript type safety.