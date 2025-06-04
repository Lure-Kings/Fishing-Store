<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lure Kings - Premium Fishing Lures</title>
    <style>
        /* Global Styles */
        :root {
            --primary: #2c3e50;
            --secondary: #3498db;
            --light: #ecf0f1;
            --dark: #2c3e50;
            --success: #27ae60;
            --danger: #e74c3c;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f5f5f5;
            color: #333;
            line-height: 1.6;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }
        
        /* Header Styles */
        header {
            background-color: var(--primary);
            color: white;
            padding: 20px 0;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }
        
        .header-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .logo {
            font-size: 24px;
            font-weight: bold;
        }
        
        .logo span {
            color: var(--secondary);
        }
        
        nav ul {
            display: flex;
            list-style: none;
        }
        
        nav ul li {
            margin-left: 20px;
        }
        
        nav ul li a {
            color: white;
            text-decoration: none;
            font-weight: 500;
            transition: color 0.3s;
        }
        
        nav ul li a:hover {
            color: var(--secondary);
        }
        
        .cart-icon {
            position: relative;
        }
        
        .cart-count {
            position: absolute;
            top: -10px;
            right: -10px;
            background-color: var(--danger);
            color: white;
            border-radius: 50%;
            width: 20px;
            height: 20px;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 12px;
        }
        
        /* Hero Section */
        .hero {
            background-image: linear-gradient(rgba(0,0,0,0.5), rgba(0,0,0,0.5)), url('https://images.unsplash.com/photo-1513828583688-c52646db42da');
            background-size: cover;
            background-position: center;
            height: 400px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            color: white;
            margin-bottom: 40px;
        }
        
        .hero h1 {
            font-size: 48px;
            margin-bottom: 20px;
        }
        
        .hero p {
            font-size: 20px;
            max-width: 600px;
        }
        
        /* Categories Section */
        .categories {
            padding: 40px 0;
        }
        
        .section-title {
            text-align: center;
            margin-bottom: 40px;
            font-size: 32px;
            color: var(--dark);
        }
        
        .category-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 20px;
        }
        
        .category-card {
            background-color: white;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 3px 10px rgba(0,0,0,0.1);
            transition: transform 0.3s, box-shadow 0.3s;
            text-align: center;
            padding: 20px;
        }
        
        .category-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
        }
        
        .category-card img {
            width: 100%;
            height: 150px;
            object-fit: contain;
            margin-bottom: 15px;
        }
        
        .category-card h3 {
            margin-bottom: 10px;
            color: var(--primary);
        }
        
        /* Products Section */
        .products-container {
            padding: 40px 0;
        }
        
        .product-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 20px;
        }
        
        .product-card {
            background-color: white;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 3px 10px rgba(0,0,0,0.1);
            transition: transform 0.3s, box-shadow 0.3s;
        }
        
        .product-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
        }
        
        .product-card img {
            width: 100%;
            height: 200px;
            object-fit: cover;
        }
        
        .product-info {
            padding: 15px;
        }
        
        .product-info h3 {
            margin-bottom: 10px;
            color: var(--primary);
        }
        
        .product-info p {
            color: #666;
            margin-bottom: 15px;
        }
        
        .product-price {
            font-weight: bold;
            color: var(--secondary);
            font-size: 18px;
            margin-bottom: 15px;
        }
        
        .btn {
            display: inline-block;
            padding: 10px 20px;
            background-color: var(--secondary);
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            text-decoration: none;
            transition: background-color 0.3s;
        }
        
        .btn:hover {
            background-color: #2980b9;
        }
        
        .btn-block {
            display: block;
            width: 100%;
        }
        
        /* Cart Styles */
        .cart-container {
            padding: 40px 0;
        }
        
        .cart-table {
            width: 100%;
            border-collapse: collapse;
            margin-bottom: 30px;
        }
        
        .cart-table th, .cart-table td {
            padding: 12px;
            text-align: left;
            border-bottom: 1px solid #ddd;
        }
        
        .cart-table th {
            background-color: var(--primary);
            color: white;
        }
        
        .cart-table tr:hover {
            background-color: #f5f5f5;
        }
        
        .cart-total {
            text-align: right;
            margin-bottom: 30px;
        }
        
        .checkout-form {
            background-color: white;
            padding: 30px;
            border-radius: 8px;
            box-shadow: 0 3px 10px rgba(0,0,0,0.1);
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 5px;
            font-weight: 500;
        }
        
        .form-control {
            width: 100%;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-size: 16px;
        }
        
        textarea.form-control {
            min-height: 100px;
        }
        
        .bank-details {
            background-color: #f8f9fa;
            padding: 15px;
            border-radius: 4px;
            margin: 20px 0;
        }
        
        /* Footer */
        footer {
            background-color: var(--dark);
            color: white;
            padding: 30px 0;
            text-align: center;
            margin-top: 40px;
        }
        
        /* Modal */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.5);
            z-index: 1000;
            justify-content: center;
            align-items: center;
        }
        
        .modal-content {
            background-color: white;
            padding: 30px;
            border-radius: 8px;
            max-width: 500px;
            width: 90%;
        }
        
        .modal-header {
            margin-bottom: 20px;
        }
        
        .modal-footer {
            margin-top: 20px;
            text-align: right;
        }
        
        /* Responsive */
        @media (max-width: 768px) {
            .header-container {
                flex-direction: column;
                text-align: center;
            }
            
            nav ul {
                margin-top: 20px;
            }
            
            .hero h1 {
                font-size: 36px;
            }
            
            .hero p {
                font-size: 18px;
            }
            
            .category-grid, .product-grid {
                grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            }
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header>
        <div class="container header-container">
            <div class="logo">LURE <span>KINGS</span></div>
            <nav>
                <ul>
                    <li><a href="#" onclick="showPage('home')">Home</a></li>
                    <li><a href="#" onclick="showPage('products')">Products</a></li>
                    <li>
                        <a href="#" onclick="showPage('cart')" class="cart-icon">
                            Cart <span class="cart-count">0</span>
                        </a>
                    </li>
                </ul>
            </nav>
        </div>
    </header>

    <!-- Home Page -->
    <section id="home-page" class="page">
        <div class="hero">
            <h1>Premium Fishing Lures</h1>
            <p>Quality lures for the serious angler. Catch more fish with Lure Kings!</p>
        </div>
        
        <div class="container categories">
            <h2 class="section-title">Shop by Category</h2>
            <div class="category-grid">
                <div class="category-card" onclick="showCategory('jigs')">
                    <img src="https://via.placeholder.com/250x150?text=Jigs" alt="Jigs">
                    <h3>Jigs</h3>
                    <p>Versatile lures for all conditions</p>
                </div>
                <div class="category-card" onclick="showCategory('soft-plastics')">
                    <img src="https://via.placeholder.com/250x150?text=Soft+Plastics" alt="Soft Plastics">
                    <h3>Soft Plastics</h3>
                    <p>Realistic action and feel</p>
                </div>
                <div class="category-card" onclick="showCategory('topwaters')">
                    <img src="https://via.placeholder.com/250x150?text=Topwaters" alt="Topwaters">
                    <h3>Topwaters</h3>
                    <p>Explosive surface strikes</p>
                </div>
                <div class="category-card" onclick="showCategory('spinnerbaits')">
                    <img src="https://via.placeholder.com/250x150?text=Spinnerbaits" alt="Spinnerbaits">
                    <h3>Spinnerbaits</h3>
                    <p>Vibration and flash combo</p>
                </div>
                <div class="category-card" onclick="showCategory('bladed-jigs')">
                    <img src="https://via.placeholder.com/250x150?text=Bladed+Jigs" alt="Bladed Jigs">
                    <h3>Bladed Jigs</h3>
                    <p>Powerful vibration action</p>
                </div>
                <div class="category-card" onclick="showCategory('crankbaits')">
                    <img src="https://via.placeholder.com/250x150?text=Crankbaits" alt="Crankbaits">
                    <h3>Crankbaits</h3>
                    <p>Diving action at various depths</p>
                </div>
                <div class="category-card" onclick="showCategory('jerkbaits')">
                    <img src="https://via.placeholder.com/250x150?text=Jerkbaits" alt="Jerkbaits">
                    <h3>Jerkbaits</h3>
                    <p>Erratic action triggers strikes</p>
                </div>
                <div class="category-card" onclick="showCategory('swimbaits')">
                    <img src="https://via.placeholder.com/250x150?text=Swimbaits" alt="Swimbaits">
                    <h3>Swimbaits</h3>
                    <p>Realistic swimming action</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Products Page -->
    <section id="products-page" class="page" style="display: none;">
        <div class="container products-container">
            <h1 id="category-title">PRODUCTS</h1>
            <div class="product-grid" id="product-grid">
                <!-- Products will be loaded here -->
            </div>
        </div>
    </section>

    <!-- Cart Page -->
    <section id="cart-page" class="page" style="display: none;">
        <div class="container cart-container">
            <h1>Your Cart</h1>
            <div id="cart-content">
                <p>Your cart is empty</p>
            </div>
            <div id="checkout-form" style="display: none;">
                <h2>Customer Information</h2>
                <form id="order-form">
                    <div class="form-group">
                        <label for="name">Full Name</label>
                        <input type="text" id="name" class="form-control" required>
                    </div>
                    <div class="form-group">
                        <label for="email">Email</label>
                        <input type="email" id="email" class="form-control" required>
                    </div>
                    <div class="form-group">
                        <label for="address">Shipping Address</label>
                        <textarea id="address" class="form-control" required></textarea>
                    </div>
                    <div class="form-group">
                        <label for="phone">Phone Number</label>
                        <input type="tel" id="phone" class="form-control">
                    </div>
                    
                    <h3>Payment Method</h3>
                    <div class="form-group">
                        <label>
                            <input type="radio" name="payment" value="bank-transfer" checked> Bank Transfer
                        </label>
                        <label>
                            <input type="radio" name="payment" value="credit-card"> Credit Card
                        </label>
                    </div>
                    
                    <div id="bank-details" class="bank-details">
                        <h4>Bank Transfer Details</h4>
                        <p>Bank Name: Lure Kings Bank</p>
                        <p>Account Number: 1234567890</p>
                        <p>Routing Number: 987654321</p>
                        <p>Please include your order number in the transfer reference.</p>
                    </div>
                    
                    <button type="button" class="btn btn-block" onclick="placeOrder()">Complete Order</button>
                </form>
            </div>
        </div>
    </section>

    <!-- Order Confirmation Modal -->
    <div id="order-modal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h2>Order Confirmed!</h2>
            </div>
            <div class="modal-body" id="modal-body">
                <p>Thank you for your order!</p>
                <p>A confirmation has been sent to your email.</p>
            </div>
            <div class="modal-footer">
                <button class="btn" onclick="closeModal()">Continue Shopping</button>
            </div>
        </div>
    </div>

    <!-- Footer -->
    <footer>
        <div class="container">
            <p>&copy; 2023 Lure Kings. All rights reserved.</p>
        </div>
    </footer>

    <script>
        // Sample product data
        const products = {
            'jigs': [
                { id: 1, name: 'Football Jig', price: 5.99, description: 'Perfect for rocky bottoms', image: 'https://via.placeholder.com/300x200?text=Football+Jig' },
                { id: 2, name: 'Arky Head Jig', price: 4.99, description: 'Great for dragging', image: 'https://via.placeholder.com/300x200?text=Arky+Head+Jig' },
                { id: 3, name: 'Flipping Jig', price: 6.49, description: 'Heavy cover specialist', image: 'https://via.placeholder.com/300x200?text=Flipping+Jig' },
                { id: 4, name: 'Swim Jig', price: 5.49, description: 'Versatile swimming action', image: 'https://via.placeholder.com/300x200?text=Swim+Jig' }
            ],
            'soft-plastics': [
                { id: 5, name: 'Worm 7"', price: 3.99, description: 'Classic worm design', image: 'https://via.placeholder.com/300x200?text=Worm+7' },
                { id: 6, name: 'Craw', price: 4.49, description: 'Realistic craw imitation', image: 'https://via.placeholder.com/300x200?text=Craw' },
                { id: 7, name: 'Stick Bait', price: 3.49, description: 'Wacky rig favorite', image: 'https://via.placeholder.com/300x200?text=Stick+Bait' },
                { id: 8, name: 'Swimbait 4"', price: 4.99, description: 'Swimming tail action', image: 'https://via.placeholder.com/300x200?text=Swimbait+4' }
            ],
            'topwaters': [
                { id: 9, name: 'Popper', price: 8.99, description: 'Chugging surface action', image: 'https://via.placeholder.com/300x200?text=Popper' },
                { id: 10, name: 'Walking Bait', price: 12.99, description: 'Side-to-side action', image: 'https://via.placeholder.com/300x200?text=Walking+Bait' },
                { id: 11, name: 'Buzzbait', price: 7.49, description: 'Blade creates surface commotion', image: 'https://via.placeholder.com/300x200?text=Buzzbait' }
            ],
            'spinnerbaits': [
                { id: 12, name: 'Willow Leaf Spinnerbait', price: 6.99, description: 'Flashy blade for clear water', image: 'https://via.placeholder.com/300x200?text=Willow+Leaf' },
                { id: 13, name: 'Colorado Spinnerbait', price: 6.49, description: 'Thumping vibration', image: 'https://via.placeholder.com/300x200?text=Colorado' }
            ],
            'bladed-jigs': [
                { id: 14, name: 'Chatterbait', price: 9.99, description: 'Powerful vibration', image: 'https://via.placeholder.com/300x200?text=Chatterbait' }
            ],
            'crankbaits': [
                { id: 15, name: 'Squarebill', price: 7.99, description: 'Shallow running', image: 'https://via.placeholder.com/300x200?text=Squarebill' },
                { id: 16, name: 'Deep Diver', price: 8.99, description: 'Dives to 15ft', image: 'https://via.placeholder.com/300x200?text=Deep+Diver' }
            ],
            'jerkbaits': [
                { id: 17, name: 'Suspending Jerkbait', price: 10.99, description: 'Hangs in strike zone', image: 'https://via.placeholder.com/300x200?text=Suspending+Jerkbait' }
            ],
            'swimbaits': [
                { id: 18, name: 'Glide Bait', price: 15.99, description: 'Realistic swimming action', image: 'https://via.placeholder.com/300x200?text=Glide+Bait' },
                { id: 19, name: 'Paddle Tail Swimbait', price: 6.99, description: 'Tail creates vibration', image: 'https://via.placeholder.com/300x200?text=Paddle+Tail' }
            ]
        };

        // Shopping cart
        let cart = [];

        // Page navigation
        function showPage(pageId) {
            document.querySelectorAll('.page').forEach(page => {
                page.style.display = 'none';
            });
            document.getElementById(`${pageId}-page`).style.display = 'block';
            
            if (pageId === 'cart') {
                updateCartDisplay();
            }
        }

        function showCategory(category) {
            showPage('products');
            document.getElementById('category-title').textContent = category.replace('-', ' ').toUpperCase();
            
            const productGrid = document.getElementById('product-grid');
            productGrid.innerHTML = '';
            
            const categoryProducts = products[category.replace('-', ' ')];
            
            if (categoryProducts && categoryProducts.length > 0) {
                categoryProducts.forEach(product => {
                    const productCard = document.createElement('div');
                    productCard.className = 'product-card';
                    productCard.innerHTML = `
                        <img src="${product.image}" alt="${product.name}">
                        <div class="product-info">
                            <h3>${product.name}</h3>
                            <p>${product.description}</p>
                            <p class="product-price">$${product.price.toFixed(2)}</p>
                            <button class="btn btn-block" onclick="addToCart(${product.id})">Add to Cart</button>
                        </div>
                    `;
                    productGrid.appendChild(productCard);
                });
            } else {
                productGrid.innerHTML = '<p>No products found in this category.</p>';
            }
        }

        // Cart functions
        function addToCart(productId) {
            // Find the product in all categories
            let productToAdd = null;
            for (const category in products) {
                const foundProduct = products[category].find(p => p.id === productId);
                if (foundProduct) {
                    productToAdd = foundProduct;
                    break;
                }
            }
            
            if (productToAdd) {
                const existingItem = cart.find(item => item.id === productId);
                if (existingItem) {
                    existingItem.quantity++;
                } else {
                    cart.push({
                        id: productToAdd.id,
                        name: productToAdd.name,
                        price: productToAdd.price,
                        quantity: 1
                    });
                }
                
                updateCartCount();
                alert(`${productToAdd.name} added to cart!`);
            }
        }

        function updateCartCount() {
            const totalItems = cart.reduce((total, item) => total + item.quantity, 0);
            document.querySelector('.cart-count').textContent = totalItems;
        }

        function updateCartDisplay() {
            const cartContent = document.getElementById('cart-content');
            const checkoutForm = document.getElementById('checkout-form');
            
            if (cart.length === 0) {
                cartContent.innerHTML = '<p>Your cart is empty</p>';
                checkoutForm.style.display = 'none';
            } else {
                let cartHTML = `
                    <table class="cart-table">
                        <thead>
                            <tr>
                                <th>Product</th>
                                <th>Price</th>
                                <th>Quantity</th>
                                <th>Total</th>
                                <th>Action</th>
                            </tr>
                        </thead>
                        <tbody>
                `;
                
                let cartTotal = 0;
                
                cart.forEach(item => {
                    const itemTotal = item.price * item.quantity;
                    cartTotal += itemTotal;
                    
                    cartHTML += `
                        <tr>
                            <td>${item.name}</td>
                            <td>$${item.price.toFixed(2)}</td>
                            <td>${item.quantity}</td>
                            <td>$${itemTotal.toFixed(2)}</td>
                            <td><button class="btn" onclick="removeFromCart(${item.id})">Remove</button></td>
                        </tr>
                    `;
                });
                
                cartHTML += `
                        </tbody>
                    </table>
                    <div class="cart-total">
                        <h3>Total: $${cartTotal.toFixed(2)}</h3>
                    </div>
                `;
                
                cartContent.innerHTML = cartHTML;
                checkoutForm.style.display = 'block';
            }
        }

        function removeFromCart(productId) {
            cart = cart.filter(item => item.id !== productId);
            updateCartDisplay();
            updateCartCount();
        }

        // Order functions
        function placeOrder() {
            const name = document.getElementById('name').value;
            const email = document.getElementById('email').value;
            const address = document.getElementById('address').value;
            const phone = document.getElementById('phone').value;
            const paymentMethod = document.querySelector('input[name="payment"]:checked').value;
            
            if (!name || !email || !address) {
                alert('Please fill in all required fields');
                return;
            }
            
            // In a real app, you would send this data to your server
            const orderTotal = cart.reduce((total, item) => total + (item.price * item.quantity), 0);
            
            // Show order confirmation
            document.getElementById('modal-body').innerHTML = `
                <p>Thank you for your order, ${name}!</p>
                ${paymentMethod === 'bank-transfer' ? '<p>Please complete your bank transfer to the account details provided.</p>' : ''}
                <p>Order Total: $${orderTotal.toFixed(2)}</p>
                <p>A confirmation has been sent to ${email}.</p>
            `;
            
            // Show modal
            document.getElementById('order-modal').style.display = 'flex';
            
            // Clear cart
            cart = [];
            updateCartCount();
            updateCartDisplay();
            
            // Reset form
            document.getElementById('order-form').reset();
        }

        function closeModal() {
            document.getElementById('order-modal').style.display = 'none';
            showPage('home');
        }

        // Initialize
        document.addEventListener('DOMContentLoaded', () => {
            showPage('home');
            updateCartCount();
            
            // Set up payment method toggle
            document.querySelectorAll('input[name="payment"]').forEach(radio => {
                radio.addEventListener('change', function() {
                    document.getElementById('bank-details').style.display = 
                        this.value === 'bank-transfer' ? 'block' : 'none';
                });
            });
        });
    </script>
</body>
</html>
