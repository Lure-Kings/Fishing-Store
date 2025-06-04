<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lure Kings - Premium Fishing Lures</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #f5f5f5;
            color: #333;
            line-height: 1.6;
        }

        .header {
            background-color: #1a365d;
            padding: 1rem 2rem;
            position: sticky;
            top: 0;
            z-index: 1000;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }

        .nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            max-width: 1200px;
            margin: 0 auto;
        }

        .logo {
            font-size: 2rem;
            font-weight: bold;
            color: white;
            display: flex;
            align-items: center;
            gap: 0.5rem;
            cursor: pointer;
        }

        .logo i {
            font-size: 1.8rem;
            color: #f8d56b;
        }

        .nav-buttons {
            display: flex;
            gap: 1rem;
            align-items: center;
        }

        .btn {
            padding: 0.5rem 1rem;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.2s ease;
        }

        .btn-primary {
            background-color: #1a365d;
            color: white;
        }

        .btn-secondary {
            background-color: transparent;
            color: white;
            border: 1px solid white;
        }

        .btn:hover {
            opacity: 0.9;
        }

        .cart-icon {
            position: relative;
        }

        .cart-count {
            position: absolute;
            top: -8px;
            right: -8px;
            background: #e74c3c;
            color: white;
            border-radius: 50%;
            width: 20px;
            height: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 0.75rem;
            font-weight: bold;
        }

        .container {
            max-width: 1200px;
            margin: 2rem auto;
            padding: 0 1rem;
        }

        .hero {
            text-align: center;
            margin-bottom: 3rem;
            padding: 2rem 0;
            background-color: white;
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }

        .hero h1 {
            font-size: 2.5rem;
            margin-bottom: 1rem;
            color: #1a365d;
        }

        .hero p {
            font-size: 1.1rem;
            max-width: 600px;
            margin: 0 auto;
            color: #666;
        }

        .categories {
            display: flex;
            flex-wrap: wrap;
            gap: 0.5rem;
            margin-bottom: 2rem;
            justify-content: center;
        }

        .category-btn {
            padding: 0.5rem 1rem;
            background: white;
            border: 1px solid #ddd;
            border-radius: 4px;
            cursor: pointer;
            transition: all 0.2s ease;
        }

        .category-btn:hover, .category-btn.active {
            background: #1a365d;
            border-color: #1a365d;
            color: white;
        }

        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 1.5rem;
            margin-bottom: 3rem;
        }

        .product-card {
            background: white;
            border: 1px solid #ddd;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
            transition: all 0.2s ease;
        }

        .product-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }

        .product-image {
            width: 100%;
            height: 200px;
            object-fit: cover;
            border-bottom: 1px solid #ddd;
        }

        .product-info {
            padding: 1rem;
        }

        .product-title {
            font-size: 1.1rem;
            font-weight: bold;
            margin-bottom: 0.5rem;
            color: #1a365d;
        }

        .product-price {
            font-size: 1.2rem;
            font-weight: bold;
            color: #e74c3c;
            margin-bottom: 1rem;
        }

        .product-description {
            color: #666;
            margin-bottom: 1rem;
            font-size: 0.9rem;
        }

        .add-to-cart {
            width: 100%;
            background-color: #1a365d;
            color: white;
            border: none;
            padding: 0.5rem;
            border-radius: 4px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.2s ease;
        }

        .add-to-cart:hover {
            background-color: #142a4a;
        }

        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.5);
            z-index: 2000;
        }

        .modal-content {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: white;
            border-radius: 8px;
            padding: 2rem;
            max-width: 90%;
            max-height: 90%;
            overflow-y: auto;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
            color: #333;
        }

        .close {
            position: absolute;
            top: 1rem;
            right: 1rem;
            font-size: 1.5rem;
            cursor: pointer;
            color: #666;
        }

        .close:hover {
            color: #333;
        }

        .cart-item {
            display: flex;
            align-items: center;
            padding: 1rem;
            border-bottom: 1px solid #ddd;
            gap: 1rem;
        }

        .cart-item img {
            width: 60px;
            height: 60px;
            object-fit: cover;
            border-radius: 4px;
            border: 1px solid #ddd;
        }

        .cart-item-info {
            flex-grow: 1;
        }

        .cart-item-title {
            font-weight: bold;
            margin-bottom: 0.25rem;
            color: #1a365d;
        }

        .quantity-controls {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            margin: 0.5rem 0;
        }

        .quantity-btn {
            background: #1a365d;
            color: white;
            border: none;
            width: 25px;
            height: 25px;
            border-radius: 4px;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .quantity-btn:hover {
            background: #142a4a;
        }

        .remove-item {
            background: #e74c3c;
            color: white;
            border: none;
            padding: 0.25rem 0.5rem;
            border-radius: 4px;
            cursor: pointer;
            font-size: 0.8rem;
        }

        .remove-item:hover {
            background: #c0392b;
        }

        .cart-total {
            text-align: center;
            padding: 1rem;
            font-size: 1.3rem;
            font-weight: bold;
            color: #1a365d;
            border-top: 1px solid #ddd;
            margin-top: 1rem;
        }

        .admin-form {
            background: white;
            border: 1px solid #ddd;
            padding: 1.5rem;
            border-radius: 8px;
            margin-bottom: 2rem;
        }

        .form-group {
            margin-bottom: 1rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 600;
            color: #1a365d;
        }

        .form-group input, .form-group textarea, .form-group select {
            width: 100%;
            padding: 0.5rem;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-size: 1rem;
        }

        .form-group input:focus, .form-group textarea:focus, .form-group select:focus {
            outline: none;
            border-color: #1a365d;
        }

        .hidden {
            display: none !important;
        }

        .checkout-form {
            max-width: 500px;
            margin: 0 auto;
        }

        .file-upload-area {
            border: 2px dashed #ddd;
            border-radius: 8px;
            padding: 1.5rem;
            text-align: center;
            cursor: pointer;
            margin-bottom: 1rem;
        }

        .file-upload-area:hover {
            border-color: #1a365d;
        }

        .image-preview {
            max-width: 200px;
            max-height: 200px;
            border-radius: 8px;
            margin-top: 1rem;
            border: 1px solid #ddd;
        }

        .payment-info {
            background: #f9f9f9;
            border: 1px solid #ddd;
            padding: 1rem;
            border-radius: 8px;
            margin-bottom: 1rem;
        }

        .payment-info h4 {
            color: #1a365d;
            margin-bottom: 0.5rem;
        }

        .toast {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: #1a365d;
            color: white;
            padding: 1rem;
            border-radius: 4px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.2);
            z-index: 3000;
            display: none;
        }

        .admin-logo {
            text-align: center;
            margin-bottom: 1.5rem;
        }

        .admin-logo img {
            max-width: 200px;
            height: auto;
        }

        .logo-upload-container {
            margin-bottom: 1.5rem;
            text-align: center;
        }

        .logo-preview {
            max-width: 200px;
            max-height: 200px;
            border-radius: 8px;
            margin-top: 1rem;
            border: 1px solid #ddd;
        }

        .required-field::after {
            content: " *";
            color: red;
        }

        .payment-options {
            display: flex;
            gap: 1rem;
            margin-bottom: 1rem;
        }

        .payment-option {
            flex: 1;
            padding: 1rem;
            border: 1px solid #ddd;
            border-radius: 8px;
            text-align: center;
            cursor: pointer;
            transition: all 0.2s ease;
        }

        .payment-option:hover {
            border-color: #1a365d;
        }

        .payment-option.selected {
            border-color: #1a365d;
            background-color: #f0f7ff;
        }

        .payment-option img {
            max-width: 100px;
            height: auto;
            margin-bottom: 0.5rem;
        }

        .back-to-shop {
            display: block;
            text-align: center;
            margin-top: 2rem;
            color: #1a365d;
            font-weight: 600;
            text-decoration: none;
        }

        .back-to-shop:hover {
            text-decoration: underline;
        }

        .error-message {
            color: #e74c3c;
            font-size: 0.8rem;
            margin-top: 0.25rem;
            display: none;
        }

        input.error {
            border-color: #e74c3c;
        }
    </style>
</head>
<body>
    <div class="header">
        <div class="nav">
            <div class="logo" onclick="window.location.href='index.html'">
                <i class="fas fa-fish"></i>
                <span>Lure Kings</span>
            </div>
            <div class="nav-buttons">
                <button class="btn btn-secondary" id="adminBtn">Admin</button>
                <div class="cart-icon" id="cartIcon">
                    <i class="fas fa-shopping-cart" style="font-size: 1.5rem; color: white;"></i>
                    <span class="cart-count" id="cartCount">0</span>
                </div>
            </div>
        </div>
    </div>

    <div class="container">
        <div class="hero">
            <h1>Premium Fishing Lures</h1>
            <p>Discover our handcrafted fishing lures designed to attract the biggest catches in any water condition.</p>
        </div>

        <div class="categories">
            <button class="category-btn active" data-category="all">All Products</button>
            <button class="category-btn" data-category="freshwater">Freshwater</button>
            <button class="category-btn" data-category="saltwater">Saltwater</button>
            <button class="category-btn" data-category="fly">Fly Fishing</button>
            <button class="category-btn" data-category="bass">Bass</button>
        </div>

        <div class="products-grid" id="productsGrid">
            <!-- Products will be loaded here -->
        </div>
    </div>

    <!-- Cart Modal -->
    <div class="modal" id="cartModal">
        <div class="modal-content">
            <span class="close" id="closeCart">&times;</span>
            <h2>Your Shopping Cart</h2>
            <div id="cartItems">
                <!-- Cart items will be loaded here -->
                <p>Your cart is empty</p>
            </div>
            <div class="cart-total" id="cartTotal">
                Total: $0.00
            </div>
            <button class="btn btn-primary" id="checkoutBtn" style="width: 100%;">Proceed to Checkout</button>
        </div>
    </div>

    <!-- Checkout Modal -->
    <div class="modal" id="checkoutModal">
        <div class="modal-content">
            <span class="close" id="closeCheckout">&times;</span>
            <h2>Checkout</h2>
            <div class="checkout-form">
                <h3>Shipping Information</h3>
                <div class="form-group">
                    <label class="required-field">Full Name</label>
                    <input type="text" id="fullName" required>
                    <div class="error-message" id="nameError">Please enter your full name</div>
                </div>
                <div class="form-group">
                    <label class="required-field">Email</label>
                    <input type="email" id="email" required>
                    <div class="error-message" id="emailError">Please enter a valid email address</div>
                </div>
                <div class="form-group">
                    <label class="required-field">Phone Number</label>
                    <input type="tel" id="phone" required pattern="[0-9]*">
                    <div class="error-message" id="phoneError">Please enter a valid phone number (digits only)</div>
                </div>
                <div class="form-group">
                    <label class="required-field">Address</label>
                    <input type="text" id="address" required>
                    <div class="error-message" id="addressError">Please enter your address</div>
                </div>
                <div class="form-group">
                    <label class="required-field">City</label>
                    <input type="text" id="city" required>
                    <div class="error-message" id="cityError">Please enter your city</div>
                </div>
                <div class="form-group">
                    <label class="required-field">Postal Code</label>
                    <input type="text" id="postalCode" required>
                    <div class="error-message" id="postalError">Please enter your postal code</div>
                </div>

                <h3>Payment Method</h3>
                <div class="payment-options">
                    <div class="payment-option" data-method="stripe">
                        <img src="https://stripe.com/img/v3/home/social.png" alt="Stripe">
                        <div>Credit/Debit Card</div>
                    </div>
                    <div class="payment-option" data-method="paypal">
                        <img src="https://www.paypalobjects.com/webstatic/mktg/logo/pp_cc_mark_37x23.jpg" alt="PayPal">
                        <div>PayPal</div>
                    </div>
                </div>

                <div class="payment-info" id="stripePayment">
                    <h4>Card Details</h4>
                    <div class="form-group">
                        <label class="required-field">Card Number</label>
                        <input type="text" id="cardNumber" placeholder="1234 5678 9012 3456">
                        <div class="error-message" id="cardError">Please enter a valid card number</div>
                    </div>
                    <div class="form-group">
                        <label class="required-field">Expiration Date</label>
                        <input type="text" id="expDate" placeholder="MM/YY">
                        <div class="error-message" id="expError">Please enter a valid expiration date</div>
                    </div>
                    <div class="form-group">
                        <label class="required-field">CVV</label>
                        <input type="text" id="cvv" placeholder="123">
                        <div class="error-message" id="cvvError">Please enter a valid CVV</div>
                    </div>
                </div>

                <div class="payment-info hidden" id="paypalPayment">
                    <h4>PayPal</h4>
                    <p>You will be redirected to PayPal to complete your payment after submitting this form.</p>
                </div>

                <input type="hidden" id="paymentMethod" value="stripe">

                <button class="btn btn-primary" id="placeOrderBtn" style="width: 100%; margin-top: 1rem;">Place Order</button>
                <a href="#" class="back-to-shop" id="backToShop">Continue Shopping</a>
            </div>
        </div>
    </div>

    <!-- Order Confirmation Modal -->
    <div class="modal" id="confirmationModal">
        <div class="modal-content">
            <span class="close" id="closeConfirmation">&times;</span>
            <div style="text-align: center;">
                <i class="fas fa-check-circle" style="font-size: 4rem; color: #4CAF50; margin-bottom: 1rem;"></i>
                <h2>Order Confirmed!</h2>
                <p>Thank you for your purchase. Your order has been placed successfully.</p>
                <p>An email confirmation has been sent to <span id="confirmationEmail"></span></p>
                <button class="btn btn-primary" id="returnToShop" style="margin-top: 1rem;">Return to Shop</button>
            </div>
        </div>
    </div>

    <!-- Admin Login Modal -->
    <div class="modal" id="adminLoginModal">
        <div class="modal-content">
            <span class="close" id="closeAdminLogin">&times;</span>
            <h2>Admin Login</h2>
            <div class="form-group">
                <label>Password</label>
                <input type="password" id="adminPassword">
                <div class="error-message" id="adminError">Incorrect password</div>
            </div>
            <button class="btn btn-primary" id="adminLoginBtn">Login</button>
        </div>
    </div>

    <!-- Admin Panel -->
    <div class="modal" id="adminPanel">
        <div class="modal-content">
            <span class="close" id="closeAdminPanel">&times;</span>
            <div class="admin-logo">
                <h2>Admin Panel</h2>
            </div>

            <div class="admin-form">
                <h3>Add New Product</h3>
                <div class="form-group">
                    <label>Product Name</label>
                    <input type="text" id="productName">
                </div>
                <div class="form-group">
                    <label>Product Description</label>
                    <textarea id="productDescription" rows="3"></textarea>
                </div>
                <div class="form-group">
                    <label>Price ($)</label>
                    <input type="number" id="productPrice" step="0.01">
                </div>
                <div class="form-group">
                    <label>Category</label>
                    <select id="productCategory">
                        <option value="freshwater">Freshwater</option>
                        <option value="saltwater">Saltwater</option>
                        <option value="fly">Fly Fishing</option>
                        <option value="bass">Bass</option>
                    </select>
                </div>
                <div class="form-group">
                    <label>Product Image</label>
                    <div class="file-upload-area" id="imageUploadArea">
                        <p>Click to upload product image</p>
                        <input type="file" id="productImage" accept="image/*" style="display: none;">
                        <img id="productImagePreview" class="image-preview" style="display: none;">
                    </div>
                </div>
                <button class="btn btn-primary" id="addProductBtn">Add Product</button>
            </div>

            <div class="admin-form">
                <h3>Current Products</h3>
                <div id="adminProductsList">
                    <!-- Admin products will be listed here -->
                </div>
            </div>
        </div>
    </div>

    <!-- Toast Notification -->
    <div class="toast" id="toast"></div>

    <script>
        // Products data - will be loaded from localStorage
        let products = JSON.parse(localStorage.getItem('products')) || [
            {
                id: 1,
                name: "Bass Pro Lure",
                description: "Premium bass fishing lure with realistic movement",
                price: 12.99,
                category: "bass",
                image: "https://images.unsplash.com/photo-1576872381147-7fb4b5bd4777?ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=60"
            },
            {
                id: 2,
                name: "Saltwater King",
                description: "Heavy-duty saltwater lure for big game fishing",
                price: 24.99,
                category: "saltwater",
                image: "https://images.unsplash.com/photo-1576872381147-7fb4b5bd4777?ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=60"
            },
            {
                id: 3,
                name: "Fly Fisher's Dream",
                description: "Hand-tied fly lure for trout and salmon",
                price: 8.99,
                category: "fly",
                image: "https://images.unsplash.com/photo-1576872381147-7fb4b5bd4777?ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=60"
            },
            {
                id: 4,
                name: "Freshwater Classic",
                description: "Versatile freshwater lure for all species",
                price: 9.99,
                category: "freshwater",
                image: "https://images.unsplash.com/photo-1576872381147-7fb4b5bd4777?ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=60"
            }
        ];

        // Cart data - will be loaded from localStorage
        let cart = JSON.parse(localStorage.getItem('cart')) || [];

        // DOM Elements
        const productsGrid = document.getElementById('productsGrid');
        const cartIcon = document.getElementById('cartIcon');
        const cartCount = document.getElementById('cartCount');
        const cartModal = document.getElementById('cartModal');
        const closeCart = document.getElementById('closeCart');
        const cartItems = document.getElementById('cartItems');
        const cartTotal = document.getElementById('cartTotal');
        const checkoutBtn = document.getElementById('checkoutBtn');
        const checkoutModal = document.getElementById('checkoutModal');
        const closeCheckout = document.getElementById('closeCheckout');
        const placeOrderBtn = document.getElementById('placeOrderBtn');
        const confirmationModal = document.getElementById('confirmationModal');
        const closeConfirmation = document.getElementById('closeConfirmation');
        const returnToShop = document.getElementById('returnToShop');
        const adminBtn = document.getElementById('adminBtn');
        const adminLoginModal = document.getElementById('adminLoginModal');
        const closeAdminLogin = document.getElementById('closeAdminLogin');
        const adminLoginBtn = document.getElementById('adminLoginBtn');
        const adminPanel = document.getElementById('adminPanel');
        const closeAdminPanel = document.getElementById('closeAdminPanel');
        const adminPassword = document.getElementById('adminPassword');
        const adminError = document.getElementById('adminError');
        const toast = document.getElementById('toast');
        const categoryBtns = document.querySelectorAll('.category-btn');
        const backToShop = document.getElementById('backToShop');
        const confirmationEmail = document.getElementById('confirmationEmail');

        // Payment elements
        const paymentOptions = document.querySelectorAll('.payment-option');
        const stripePayment = document.getElementById('stripePayment');
        const paypalPayment = document.getElementById('paypalPayment');
        const paymentMethod = document.getElementById('paymentMethod');

        // Admin product management elements
        const productName = document.getElementById('productName');
        const productDescription = document.getElementById('productDescription');
        const productPrice = document.getElementById('productPrice');
        const productCategory = document.getElementById('productCategory');
        const productImage = document.getElementById('productImage');
        const productImagePreview = document.getElementById('productImagePreview');
        const imageUploadArea = document.getElementById('imageUploadArea');
        const addProductBtn = document.getElementById('addProductBtn');
        const adminProductsList = document.getElementById('adminProductsList');

        // Form validation elements
        const requiredFields = document.querySelectorAll('[required]');
        const errorMessages = document.querySelectorAll('.error-message');

        // Initialize the app
        function init() {
            renderProducts();
            updateCartCount();
            setupEventListeners();
        }

        // Set up event listeners
        function setupEventListeners() {
            // Cart and checkout
            cartIcon.addEventListener('click', openCart);
            closeCart.addEventListener('click', closeModal.bind(null, cartModal));
            checkoutBtn.addEventListener('click', openCheckout);
            closeCheckout.addEventListener('click', closeModal.bind(null, checkoutModal));
            placeOrderBtn.addEventListener('click', placeOrder);
            returnToShop.addEventListener('click', returnToShopHandler);
            backToShop.addEventListener('click', backToShopHandler);

                        // Admin login
            adminLoginBtn.addEventListener('click', adminLogin);
            closeAdminPanel.addEventListener('click', closeModal.bind(null, adminPanel));

            // Product categories
            categoryBtns.forEach(btn => {
                btn.addEventListener('click', () => filterProducts(btn.dataset.category));
            });

            // Payment options
            paymentOptions.forEach(option => {
                option.addEventListener('click', () => selectPaymentMethod(option.dataset.method));
            });

            // Admin product management
            imageUploadArea.addEventListener('click', () => productImage.click());
            productImage.addEventListener('change', handleImageUpload);
            addProductBtn.addEventListener('click', addProduct);

            // Form validation
            requiredFields.forEach(field => {
                field.addEventListener('input', validateField);
            });

            // Close modals when clicking outside
            window.addEventListener('click', (e) => {
                if (e.target === cartModal) closeModal(cartModal);
                if (e.target === checkoutModal) closeModal(checkoutModal);
                if (e.target === confirmationModal) closeModal(confirmationModal);
                if (e.target === adminLoginModal) closeModal(adminLoginModal);
                if (e.target === adminPanel) closeModal(adminPanel);
            });
        }

        // Render products to the page
        function renderProducts(filteredProducts = products) {
            productsGrid.innerHTML = '';
            
            if (filteredProducts.length === 0) {
                productsGrid.innerHTML = '<p style="grid-column: 1/-1; text-align: center;">No products found in this category.</p>';
                return;
            }

            filteredProducts.forEach(product => {
                const productCard = document.createElement('div');
                productCard.className = 'product-card';
                productCard.innerHTML = `
                    <img src="${product.image}" alt="${product.name}" class="product-image">
                    <div class="product-info">
                        <h3 class="product-title">${product.name}</h3>
                        <p class="product-price">$${product.price.toFixed(2)}</p>
                        <p class="product-description">${product.description}</p>
                        <button class="add-to-cart" data-id="${product.id}">Add to Cart</button>
                    </div>
                `;
                productsGrid.appendChild(productCard);
            });

            // Add event listeners to add-to-cart buttons
            document.querySelectorAll('.add-to-cart').forEach(btn => {
                btn.addEventListener('click', addToCart);
            });
        }

        // Filter products by category
        function filterProducts(category) {
            // Update active category button
            categoryBtns.forEach(btn => {
                btn.classList.toggle('active', btn.dataset.category === category);
            });

            if (category === 'all') {
                renderProducts();
                return;
            }

            const filteredProducts = products.filter(product => product.category === category);
            renderProducts(filteredProducts);
        }

        // Cart functions
        function addToCart(e) {
            const productId = parseInt(e.target.dataset.id);
            const product = products.find(p => p.id === productId);
            
            // Check if product is already in cart
            const existingItem = cart.find(item => item.id === productId);
            
            if (existingItem) {
                existingItem.quantity += 1;
            } else {
                cart.push({
                    ...product,
                    quantity: 1
                });
            }
            
            updateCart();
            showToast(`${product.name} added to cart`);
        }

        function updateCart() {
            localStorage.setItem('cart', JSON.stringify(cart));
            updateCartCount();
            renderCartItems();
        }

        function updateCartCount() {
            const count = cart.reduce((total, item) => total + item.quantity, 0);
            cartCount.textContent = count;
            cartCount.style.display = count > 0 ? 'flex' : 'none';
        }

        function renderCartItems() {
            if (cart.length === 0) {
                cartItems.innerHTML = '<p>Your cart is empty</p>';
                cartTotal.textContent = 'Total: $0.00';
                checkoutBtn.disabled = true;
                return;
            }
            
            checkoutBtn.disabled = false;
            cartItems.innerHTML = '';
            
            let total = 0;
            
            cart.forEach(item => {
                const itemTotal = item.price * item.quantity;
                total += itemTotal;
                
                const cartItem = document.createElement('div');
                cartItem.className = 'cart-item';
                cartItem.innerHTML = `
                    <img src="${item.image}" alt="${item.name}">
                    <div class="cart-item-info">
                        <h4 class="cart-item-title">${item.name}</h4>
                        <p>$${item.price.toFixed(2)}</p>
                        <div class="quantity-controls">
                            <button class="quantity-btn" data-id="${item.id}" data-action="decrease">-</button>
                            <span>${item.quantity}</span>
                            <button class="quantity-btn" data-id="${item.id}" data-action="increase">+</button>
                        </div>
                    </div>
                    <div>
                        <p>$${itemTotal.toFixed(2)}</p>
                        <button class="remove-item" data-id="${item.id}">Remove</button>
                    </div>
                `;
                cartItems.appendChild(cartItem);
            });
            
            cartTotal.textContent = `Total: $${total.toFixed(2)}`;
            
            // Add event listeners to quantity buttons
            document.querySelectorAll('.quantity-btn').forEach(btn => {
                btn.addEventListener('click', updateQuantity);
            });
            
            // Add event listeners to remove buttons
            document.querySelectorAll('.remove-item').forEach(btn => {
                btn.addEventListener('click', removeItem);
            });
        }

        function updateQuantity(e) {
            const productId = parseInt(e.target.dataset.id);
            const action = e.target.dataset.action;
            const item = cart.find(item => item.id === productId);
            
            if (action === 'increase') {
                item.quantity += 1;
            } else if (action === 'decrease' && item.quantity > 1) {
                item.quantity -= 1;
            }
            
            updateCart();
        }

        function removeItem(e) {
            const productId = parseInt(e.target.dataset.id);
            cart = cart.filter(item => item.id !== productId);
            updateCart();
            showToast('Item removed from cart');
        }

        // Modal functions
        function openCart() {
            renderCartItems();
            cartModal.style.display = 'block';
        }

        function openCheckout() {
            closeModal(cartModal);
            checkoutModal.style.display = 'block';
        }

        function closeModal(modal) {
            modal.style.display = 'none';
        }

        function openAdminLogin() {
            adminLoginModal.style.display = 'block';
        }

        // Admin functions
        function adminLogin() {
            // In a real app, this would be a secure server-side check
            if (adminPassword.value === 'admin123') {
                closeModal(adminLoginModal);
                adminPanel.style.display = 'block';
                renderAdminProducts();
            } else {
                adminError.style.display = 'block';
            }
        }

        function renderAdminProducts() {
            adminProductsList.innerHTML = '';
            
            if (products.length === 0) {
                adminProductsList.innerHTML = '<p>No products found</p>';
                return;
            }
            
            products.forEach(product => {
                const productItem = document.createElement('div');
                productItem.className = 'product-item';
                productItem.style.marginBottom = '1rem';
                productItem.style.paddingBottom = '1rem';
                productItem.style.borderBottom = '1px solid #ddd';
                productItem.innerHTML = `
                    <div style="display: flex; justify-content: space-between; align-items: center;">
                        <div>
                            <h4>${product.name}</h4>
                            <p>$${product.price.toFixed(2)} - ${product.category}</p>
                        </div>
                        <button class="btn btn-secondary" data-id="${product.id}" style="background-color: #e74c3c; color: white;">Delete</button>
                    </div>
                `;
                adminProductsList.appendChild(productItem);
            });
            
            // Add event listeners to delete buttons
            document.querySelectorAll('.product-item button').forEach(btn => {
                btn.addEventListener('click', deleteProduct);
            });
        }

        function deleteProduct(e) {
            const productId = parseInt(e.target.dataset.id);
            products = products.filter(product => product.id !== productId);
            localStorage.setItem('products', JSON.stringify(products));
            renderAdminProducts();
            renderProducts();
            showToast('Product deleted');
        }

        function handleImageUpload(e) {
            const file = e.target.files[0];
            if (file) {
                const reader = new FileReader();
                reader.onload = function(event) {
                    productImagePreview.src = event.target.result;
                    productImagePreview.style.display = 'block';
                };
                reader.readAsDataURL(file);
            }
        }

        function addProduct() {
            if (!productName.value || !productPrice.value) {
                showToast('Please fill in all required fields');
                return;
            }
            
            const newProduct = {
                id: products.length > 0 ? Math.max(...products.map(p => p.id)) + 1 : 1,
                name: productName.value,
                description: productDescription.value,
                price: parseFloat(productPrice.value),
                category: productCategory.value,
                image: productImagePreview.src || 'https://via.placeholder.com/300'
            };
            
            products.push(newProduct);
            localStorage.setItem('products', JSON.stringify(products));
            
            // Reset form
            productName.value = '';
            productDescription.value = '';
            productPrice.value = '';
            productImagePreview.src = '';
            productImagePreview.style.display = 'none';
            productImage.value = '';
            
            renderProducts();
            renderAdminProducts();
            showToast('Product added successfully');
        }

        // Checkout functions
        function selectPaymentMethod(method) {
            paymentMethod.value = method;
            
            paymentOptions.forEach(option => {
                option.classList.toggle('selected', option.dataset.method === method);
            });
            
            if (method === 'stripe') {
                stripePayment.classList.remove('hidden');
                paypalPayment.classList.add('hidden');
            } else {
                stripePayment.classList.add('hidden');
                paypalPayment.classList.remove('hidden');
            }
        }

        function validateField(e) {
            const field = e.target;
            const errorId = `${field.id}Error`;
            const errorElement = document.getElementById(errorId);
            
            if (!field.checkValidity()) {
                field.classList.add('error');
                errorElement.style.display = 'block';
                return false;
            } else {
                field.classList.remove('error');
                errorElement.style.display = 'none';
                return true;
            }
        }

        function validateForm() {
            let isValid = true;
            
            requiredFields.forEach(field => {
                const errorId = `${field.id}Error`;
                const errorElement = document.getElementById(errorId);
                
                if (!field.checkValidity()) {
                    field.classList.add('error');
                    errorElement.style.display = 'block';
                    isValid = false;
                }
            });
            
            return isValid;
        }

        function placeOrder() {
            if (!validateForm()) {
                showToast('Please fill in all required fields correctly');
                return;
            }
            
            // In a real app, you would process the payment here
            const email = document.getElementById('email').value;
            confirmationEmail.textContent = email;
            
            // Clear cart
            cart = [];
            updateCart();
            
            // Close checkout and show confirmation
            closeModal(checkoutModal);
            confirmationModal.style.display = 'block';
        }

        function returnToShopHandler(e) {
            e.preventDefault();
            closeModal(confirmationModal);
        }

        function backToShopHandler(e) {
            e.preventDefault();
            closeModal(checkoutModal);
            openCart();
        }

        // Utility functions
        function showToast(message) {
            toast.textContent = message;
            toast.style.display = 'block';
            
            setTimeout(() => {
                toast.style.display = 'none';
            }, 3000);
        }

        // Initialize the app
        init();
    </script>
</body>
</html>
