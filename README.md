# Products Service API

A simple Node.js Express service that provides product management and cart functionality.

## Features

- ✅ Get list of all products
- ✅ Add items to cart with quantity calculation
- ✅ Input validation and error handling
- ✅ RESTful API design

## Quick Start

### Prerequisites
- Node.js (v14 or higher)
- npm

### Installation

1. Clone the repository:
```bash
git clone <your-repo-url>
cd products-service
```

2. Install dependencies:
```bash
npm install
```

3. Start the server:
```bash
npm start
```

The server will start on `http://localhost:3000`

## API Documentation

### Get Products
**GET** `/products`

Returns a list of all available products.

**Response:**
```json
{
  "success": true,
  "products": [
    {
      "id": 1,
      "name": "Laptop",
      "price": 50000
    }
  ],
  "total": 5
}
```

### Add to Cart
**POST** `/cart`

Calculate total price for a product with specified quantity.

**Request Body:**
```json
{
  "productId": 1,
  "quantity": 2
}
```

**Response:**
```json
{
  "success": true,
  "product": "Laptop",
  "unitPrice": 50000,
  "quantity": 2,
  "totalPrice": 100000
}
```

**Error Responses:**
- `400` - Invalid input (missing productId/quantity or quantity <= 0)
- `404` - Product not found

## Testing Examples

### Using curl

Get all products:
```bash
curl -X GET http://localhost:3000/products
```

Add item to cart:
```bash
curl -X POST http://localhost:3000/cart \
  -H "Content-Type: application/json" \
  -d '{"productId": 1, "quantity": 2}'
```

### Using Postman

1. **GET Products:**
   - Method: GET
   - URL: `http://localhost:3000/products`

2. **POST Cart:**
   - Method: POST
   - URL: `http://localhost:3000/cart`
   - Headers: `Content-Type: application/json`
   - Body (raw JSON):
     ```json
     {
       "productId": 1,
       "quantity": 2
     }
     ```

## Available Products

The service comes with these hardcoded products:

| ID | Name | Price (₹) |
|----|------|-----------|
| 1  | Laptop | 50,000 |
| 2  | Mouse | 1,500 |
| 3  | Keyboard | 3,000 |
| 4  | Monitor | 15,000 |
| 5  | Headphones | 2,500 |

## Development

For development with auto-restart:
```bash
npm run dev
```

## Project Structure
```
products-service/
├── server.js          # Main application file
├── package.json       # Dependencies and scripts
├── README.md          # This file
└── .gitignore         # Git ignore rules
```

## Tech Stack
- **Runtime:** Node.js
- **Framework:** Express.js
- **Data:** In-memory (hardcoded products)

## License
MIT
