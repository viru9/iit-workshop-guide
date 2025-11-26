I need to create a product management table in a React TypeScript frontend. Please help me implement this with the following requirements:

1. Update the frontend\src\pages\ProductsPage.tsx for the products table at the `/products` route. 
2. Use Material-UI (MUI) components to build the table
3. Table columns should include:
   - Name
   - Price
   - Category
   - In Stock (boolean)
   - Created Date
   - Updated Date
   - Actions (with Edit and Delete buttons)

Technical requirements:
- Use TypeScript with proper type definitions
- Implement client-side pagination using MUI's TablePagination
- Use axios for API calls
- Fetch data from the endpoint defined in `frontend/src/config/api.config.ts`
- The working API endpoint is `http://localhost:4000/api/products`
- For now, the Edit and Delete buttons don't need to perform any actions (just show the buttons)

Please provide:
1. The complete code for the ProductsTable component
2. Necessary TypeScript interfaces
3. Integration with the existing routing setup
4. Proper error handling for the API call
5. Loading state handling

The table should be responsive and follow MUI's design guidelines. Include any necessary imports and make sure the component is properly typed.