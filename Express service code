const express = require('express');
const app = express();
const PORT = 3000;

app.use(express.json());

// Some dummy products - keeping it simple
const products = [
  { id: 1, name: "Laptop", price: 50000 },
  { id: 2, name: "Mouse", price: 1500 },
  { id: 3, name: "Keyboard", price: 3000 },
  { id: 4, name: "Monitor", price: 15000 },
  { id: 5, name: "Headphones", price: 2500 }
];

// GET /products endpoint - just return everything
app.get('/products', (req, res) => {
  res.json({
    success: true,
    products: products,
    total: products.length
  });
});

// POST /cart - calculate total based on product ID and quantity  
app.post('/cart', (req, res) => {
  const { productId, quantity } = req.body;
  
  // Basic validation - gotta check these things
  if (!productId || !quantity || quantity <= 0) {
    return res.status(400).json({
      error: "Need valid productId and quantity > 0"
    });
  }
  
  // Find the product (parseInt just in case they send a string)
  const product = products.find(p => p.id === parseInt(productId));
  
  if (!product) {
    return res.status(404).json({
      error: "Product not found"
    });
  }
  
  // Simple math - multiply price by quantity
  const totalPrice = product.price * quantity;
  
  res.json({
    success: true,
    product: product.name,
    unitPrice: product.price,
    quantity: quantity,
    totalPrice: totalPrice
  });
});

app.listen(PORT, () => {
  console.log(`Server running on port ${PORT}`);
});

/* 
To set this up:
1. npm init -y
2. npm install express
3. node server.js

Test with:
GET http://localhost:3000/products

POST http://localhost:3000/cart
{
  "productId": 1,
  "quantity": 2
}
*/
