## 1.
-Database management for persistent data management rather than in-memory data as simulated in orders.service.ts.
-add user authentication for secure api endpoints.
-add role-based access(admin, staff, consumer).
-implement audit logging for tracking actions; easy for debugging




## 2.
HTTP status codes are not implemented; returns HTTP 200 whether fail or success
no consistent error structure

fixes:
Use proper HTTP exceptions like NotFoundException, BadRequestException from NestJS
Return consistent error format that shows status code, message, timestamp, etc
Add proper HTTP status codes like 200 for success, 404 for not found, 400 for invalid ID



## 3.
Create a separate API service file:
Put all fetch calls in one place
Every time we need to call the backend, we use this file

Create custom hooks for data fetching
Move the useEffect and useState logic into a hook
Each hook handles one specific type of data


Create separate hook for filters.
Move the filter dropdown state into its own hook as in useFilters.ts.
Handle filter logic separately from data fetching.


Use Context for shared data
If multiple components need the same data, use Context to avoid passing data through 5 levels of components


## 4.
Need more customer information like address, email, phone no., etc.
Billing fields like price, tax, payment status, payment method.
Separate dates for received, started, completed, delivered.
Delivery details like delivery status, delivery fee.
Garment details: quantity, special instructions, fabric type, damage notes.
Divide garment status into parts like processing, partial ready, completed.

## 5.
Ai might assume data exists when it doesnt.
no authentication checks
lacking error handling

debugging/review practices:
check if every API endpoint has valid input
every method and object specified in code exists
check for data redundance
ensure all edge cases are accounted for

## 6.
For real-time garment status updates, I would implement WebSockets
Create orders.gateway.ts in NestJS to handle WebSocket connections
Emit 'garment-updated' event whenever status changes
Add WebSocket client in hooks/useWebSocket.ts
Listen for updates and patch local state
Keep REST polling as fallback for disconnected clients








