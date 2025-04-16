In this code we are going through Higher Order Functions



The code below is one that caused many questions we have broken down each step of the function for future reference.


-----------------------------------------------------------------------------------------------------------------------
products = [
  { name: "Laptop", price: 1000, inStock: true },
  { name: "Phone", price: 500, inStock: false },
  { name: "Tablet", price: 800, inStock: true },
  { name: "Monitor", price: 300, inStock: true },
  { name: "Keyboard", price: 100, inStock: false },
];

function productValueInStock(products) {
  return products.reduce((total, product) => {
    return product.inStock ? total + product.price : total;
  }, 0);
}


function productValueInStock(products)
Defines a function that takes one argument: products (an array of product objects).

.reduce((total, product) => { ... }, 0)
Calls .reduce() on the array.

.reduce() loops through the array and keeps a running total based on your logic.

The callback (total, product) => { ... } runs once for each product.

0 is the initial value of total.

Inside the callback:

product.inStock ? total + product.price : total;
This is a ternary operator, which is a short if/else.

It means:

If product.inStock === true
→ add product.price to total.

Else
→ leave total unchanged.
-----
Parameters:
total: The running sum, carried over from the last iteration.

product: The current item being processed in the array.
--------------------------------------------------------
🔄 Iteration Example:

// First iteration:
total = 0
product = { name: "Laptop", price: 1000, inStock: true }
// inStock → true → total + 1000 → total = 1000

// Second iteration:
total = 1000
product = { name: "Phone", price: 500, inStock: false }
// inStock → false → total stays 1000

// ...and so on
Final Return:
After all products are processed, reduce() returns the final total, which is the sum of prices for products that are in stock.

product.inStock ? total + product.price : total;

What is it '?'
The ternary operator is a shorter way to write an if...else statement.

Format:

condition ? valueIfTrue : valueIfFalse;

Applied to your code:

product.inStock ? total + product.price : total;
Means:

If product.inStock is true, return total + product.price

Otherwise, return total
-----------------------------------------------------------------------
Same result, just written shorter with ? : (ternary).

if (product.inStock) {
  return total + product.price;
} else {
  return total;
}


Execution:

Start: total = 0

1st: Laptop → inStock → total = 0 + 1000 = 1000

2nd: Phone → not inStock → total = 1000

3rd: Tablet → inStock → total = 1000 + 800 = 1800

4th: Monitor → inStock → total = 1800 + 300 = 2100

5th: Keyboard → not inStock → total = 2100

Final output: 2100


