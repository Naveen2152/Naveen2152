 

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Shopping Cart</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            padding: 20px;
        }
        .cart-container {
            width: 80%;
            margin: 0 auto;
            background-color: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
        }
        h2 {
            text-align: center;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
        }
        table th, table td {
            padding: 10px;
            text-align: center;
            border: 1px solid #ddd;
        }
        .cart-total {
            margin-top: 20px;
            text-align: right;
            font-size: 20px;
        }
        .cart-total span {
            font-weight: bold;
        }
        .update-btn {
            padding: 10px 20px;
            background-color: #28a745;
            color: #fff;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        .update-btn:hover {
            background-color: #218838;
        }
        .remove-btn {
            padding: 5px 10px;
            background-color: #dc3545;
            color: #fff;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        .remove-btn:hover {
            background-color: #c82333;
        }
    </style>
</head>
<body>
    <div class="cart-container">
        <h2>Shopping Cart</h2>

        <table>
            <thead>
                <tr>
                    <th>Product</th>
                    <th>Price</th>
                    <th>Quantity</th>
                    <th>Total</th>
                    <th>Remove</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td>Product 1</td>
                    <td>$10.00</td>
                    <td>
                        <input type="number" value="1" min="1" class="quantity" />
                    </td>
                    <td class="item-total">$10.00</td>
                    <td><button class="remove-btn">Remove</button></td>
                </tr>
                <tr>
                    <td>Product 2</td>
                    <td>$15.00</td>
                    <td>
                        <input type="number" value="1" min="1" class="quantity" />
                    </td>
                    <td class="item-total">$15.00</td>
                    <td><button class="remove-btn">Remove</button></td>
                </tr>
            </tbody>
        </table>

        <div class="cart-total">
            <span>Total: $<span id="total-price">25.00</span></span>
        </div>
        
        <button class="update-btn" onclick="updateCart()">Update Cart</button>
    </div>

    <script>
        // Function to update the total price based on the quantities
        function updateCart() {
            let total = 0;
            const rows = document.querySelectorAll('tbody tr');
            rows.forEach(row => {
                const price = parseFloat(row.cells[1].textContent.replace('$', ''));
                const quantity = row.querySelector('.quantity').value;
                const itemTotal = price * quantity;
                row.querySelector('.item-total').textContent = '$' + itemTotal.toFixed(2);
                total += itemTotal;
            });
            document.getElementById('total-price').textContent = total.toFixed(2);
        }

        // Optional: Remove item from cart
        const removeButtons = document.querySelectorAll('.remove-btn');
        removeButtons.forEach(button => {
            button.addEventListener('click', (e) => {
                const row = e.target.closest('tr');
                row.remove();
                updateCart();
            });
        });
    </script>
</body>
</html>

