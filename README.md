<!DOCTYPE html>
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

        /* Styling for the new main header logo image */
        #mainHeaderLogo {
            max-height: 50px; /* Controls the height of the logo in the header */
            width: auto;
            display: none; /* Hidden by default, shown via JS if a logo exists */
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
        
        .btn:disabled {
            background-color: #ccc;
            cursor: not-allowed;
            opacity: 0.7;
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
            display: flex;
            flex-direction: column;
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
            flex-grow: 1;
            display: flex;
            flex-direction: column;
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
            flex-grow: 1;
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
            margin-top: auto;
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
            width: 600px;
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
            padding-bottom: 1rem;
            margin-bottom: 1rem;
            border-bottom: 1px solid #ddd;
            gap: 1rem;
        }
        .cart-item:last-child {
            border-bottom: none;
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
            text-align: right;
            padding-top: 1rem;
            font-size: 1.3rem;
            font-weight: bold;
            color: #1a365d;
            border-top: 2px solid #ddd;
            margin-top: 1rem;
        }
        
        .shipping-total, .grand-total {
            font-size: 1.1rem;
            font-weight: normal;
            margin-top: 0.5rem;
        }
        .grand-total {
             font-size: 1.3rem;
             font-weight: bold;
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
        .form-group label .required-star {
            color: #e74c3c;
            margin-left: 2px;
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
        
        .payment-method {
            padding: 0.5rem;
            border: 1px solid #ddd;
            border-radius: 4px;
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
            opacity: 0;
            visibility: hidden;
            transition: opacity 0.3s, visibility 0.3s;
        }
        .toast.show {
            opacity: 1;
            visibility: visible;
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
            max-height: 100px;
            margin-top: 1rem;
            display: none;
        }

        @media (max-width: 768px) {
            .nav {
                flex-direction: column;
                gap: 1rem;
            }
            .hero h1 {
                font-size: 2rem;
            }
            .products-grid {
                grid-template-columns: 1fr;
            }
            .modal-content {
                width: 95%;
            }
        }
    </style>
</head>
<body>
    <header class="header">
        <nav class="nav">
            <div class="logo" id="logo" onclick="showView('store')">
                <img id="mainHeaderLogo" alt="Lure Kings Logo">
                <i id="defaultLogoIcon" class="fas fa-crown"></i>
                <span id="defaultLogoText">Lure Kings</span>
            </div>
            <div class="nav-buttons">
                <button class="btn btn-secondary" onclick="showView('store')">Store</button>
                <button class="btn btn-primary cart-icon" onclick="showCart()">
                    <i class="fas fa-shopping-cart"></i>
                    <span class="cart-count" id="cartCount">0</span>
                </button>
            </div>
        </nav>
    </header>

    <div class="toast" id="toast">Item added to cart!</div>

    <div class="container">
        <div id="storeView">
            <div class="hero">
                <h1>Premium Fishing Lures</h1>
                <p>High-quality fishing lures for the serious angler</p>
            </div>

            <div class="categories">
                <button class="category-btn active" onclick="filterByCategory('all')">All Lures</button>
                <button class="category-btn" onclick="filterByCategory('jigs')">Jigs</button>
                <button class="category-btn" onclick="filterByCategory('soft-plastics')">Soft Plastics</button>
                <button class="category-btn" onclick="filterByCategory('topwaters')">Topwaters</button>
                <button class="category-btn" onclick="filterByCategory('spinnerbaits')">Spinnerbaits</button>
            </div>

            <div class="products-grid" id="productsGrid"></div>
        </div>

        <div id="adminView" class="hidden">
            <div class="hero">
                <div class="admin-logo">
                    <img id="companyLogo" src="" alt="Lure Kings Logo">
                </div>
                <h1>Admin Dashboard</h1>
                <p>Manage your Lure Kings inventory</p>
            </div>

            <div class="logo-upload-container">
                <h3>Upload Company Logo</h3>
                <div class="file-upload-area" onclick="document.getElementById('logoUpload').click()">
                    <i class="fas fa-cloud-upload-alt" style="font-size: 2rem; color: #1a365d; margin-bottom: 0.5rem;"></i>
                    <p>Click to upload logo or drag & drop</p>
                    <p style="font-size: 0.9rem; opacity: 0.7;">Supports JPG, PNG</p>
                </div>
                <input type="file" id="logoUpload" accept="image/*" style="display: none;">
                <img id="logoPreview" class="logo-preview">
            </div>

            <div class="admin-form">
                <h2 style="margin-bottom: 1rem; color: #1a365d;">Add/Edit Product</h2>
                <form id="productForm">
                    <input type="hidden" id="productId">
                    <div class="form-group">
                        <label for="productName">Product Name</label>
                        <input type="text" id="productName" required>
                    </div>
                    <div class="form-group">
                        <label for="productCategory">Category</label>
                        <select id="productCategory" required>
                            <option value="">Select Category</option>
                            <option value="jigs">Jigs</option>
                            <option value="soft-plastics">Soft Plastics</option>
                            <option value="topwaters">Topwaters</option>
                            <option value="spinnerbaits">Spinnerbaits</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="productPrice">Price ($)</label>
                        <input type="number" id="productPrice" step="0.01" min="0" required>
                    </div>
                    <div class="form-group">
                        <label for="productDescription">Description</label>
                        <textarea id="productDescription" rows="3" required></textarea>
                    </div>
                    <div class="form-group">
                        <label for="productImage">Product Image</label>
                        <div class="file-upload-area" onclick="document.getElementById('imageUpload').click()">
                            <i class="fas fa-cloud-upload-alt" style="font-size: 2rem; color: #1a365d; margin-bottom: 0.5rem;"></i>
                            <p>Click to upload image or drag & drop</p>
                            <p style="font-size: 0.9rem; opacity: 0.7;">Supports JPG, PNG, GIF</p>
                        </div>
                        <input type="file" id="imageUpload" accept="image/*" style="display: none;">
                        <input type="text" id="productImageURL" placeholder="Or enter image URL">
                        <img id="imagePreview" class="image-preview" style="display: none;">
                    </div>
                    <button type="submit" class="btn btn-primary" style="width: 100%;">
                        Save Product
                    </button>
                </form>
            </div>

            <div class="admin-form">
                <h2 style="margin-bottom: 1rem; color: #1a365d;">Manage Existing Products</h2>
                <div id="adminProductsList" class="products-grid"></div>
            </div>
        </div>
    </div>

    <div id="cartModal" class="modal">
        <div class="modal-content">
            <span class="close" onclick="closeCart()">&times;</span>
            <h2 style="margin-bottom: 1rem; color: #1a365d;">
                Shopping Cart
            </h2>
            <div id="cartItems"></div>
            <div class="cart-total" id="cartTotal">Total: $0.00</div>
            <button class="btn btn-primary" id="checkoutBtn" onclick="showCheckout()" style="width: 100%; margin-top: 1rem;">
                Proceed to Checkout
            </button>
        </div>
    </div>

    <div id="checkoutModal" class="modal">
        <div class="modal-content">
            <span class="close" onclick="closeCheckout()">&times;</span>
            <h2 style="margin-bottom: 1rem; color: #1a365d;">
                Secure Checkout
            </h2>
            
            <form id="checkoutForm" action="https://formsubmit.co/lure.kings.fishing.aus@gmail.com" method="POST">
                <input type="hidden" name="_subject" value="New Order from Lure Kings">
                <input type="hidden" name="_template" value="table">
                <input type="hidden" name="_next" id="formSubmitRedirect">
                <input type="hidden" name="_cc" value="lure.kings.fishing.aus@gmail.com">
                <input type="hidden" name="_autoresponse" value="Thank you for your order! We'll process it shortly.">
                
                <div class="form-group">
                    <label for="customerName">Full Name<span class="required-star">*</span></label>
                    <input type="text" id="customerName" name="name" required>
                </div>
                <div class="form-group">
                    <label for="customerEmail">Email Address<span class="required-star">*</span></label>
                    <input type="email" id="customerEmail" name="email" required>
                </div>
                <div class="form-group">
                    <label for="customerPhone">Phone Number<span class="required-star">*</span></label>
                    <input type="tel" id="customerPhone" name="phone" pattern="[0-9]*" oninput="this.value = this.value.replace(/[^0-9]/g, '');" required>
                </div>
                <div class="form-group">
                    <label for="customerAddress">Delivery Address<span class="required-star">*</span></label>
                    <textarea id="customerAddress" name="address" rows="3" required></textarea>
                </div>

                <div class="form-group payment-info">
                    <h4>Shipping from Chatswood, NSW<span class="required-star">*</span></h4>
                    <p style="font-size: 0.8em; opacity:0.7; margin-bottom: 10px;">This is a placeholder for a real shipping calculator.</p>
                     <select id="shippingOptions" name="shipping_zone" required>
                         <option value="">-- Select Shipping Zone --</option>
                         <option value="10.00">Local (5km Radius) - $10.00</option>
                         <option value="15.00">Sydney Metro - $15.00</option>
                         <option value="25.00">NSW Regional - $25.00</option>
                         <option value="35.00">Interstate - $35.00</option>
                     </select>
                </div>
                
                <div class="form-group payment-info">
                    <h4>Payment Method<span class="required-star">*</span></h4>
                    <div class="payment-method">
                        <input type="radio" id="bankTransfer" name="payment_method" value="Bank Transfer" required>
                        <label for="bankTransfer">Direct Bank Transfer</label>
                        <div id="bankDetails" class="hidden" style="padding: 10px; font-size: 0.9em; opacity: 0.8; background: #fff; border-radius: 4px; margin-top: 5px;">
                            <p><strong>Bank:</strong> ANZ Bank | <strong>Account:</strong> Lure Kings Pty Ltd<br>
                               <strong>BSB:</strong> 012-345 | <strong>Acc No:</strong> 123456789<br>
                               Use your Order ID as reference.</p>
                        </div>
                    </div>
                    <div class="payment-method">
                        <input type="radio" id="stripe" name="payment_method" value="Stripe">
                        <label for="stripe">Stripe (Credit/Debit Card)</label>
                        <div id="stripe-element" class="hidden" style="padding: 10px;">
                            </div>
                    </div>
                     <div class="payment-method">
                        <input type="radio" id="paypal" name="payment_method" value="PayPal">
                        <label for="paypal">PayPal</label>
                        <div id="paypal-button-container" class="hidden" style="padding: 10px;">
                            </div>
                    </div>
                </div>

                <div class="form-group">
                    <label>Order Summary</label>
                    <div id="orderItemsDisplay" style="padding: 0.5rem; background: #f5f5f5; border-radius: 4px;"></div>
                </div>
                <div class="cart-total" id="checkoutTotal"></div>
                
                <input type="hidden" id="orderItems" name="order_items">
                <input type="hidden" id="orderTotal" name="order_grand_total">
                <input type="hidden" id="shippingCost" name="shipping_cost">
                
                <button type="submit" class="btn btn-primary" style="width: 100%; margin-top: 1rem;">
                    Place Order
                </button>
            </form>
        </div>
    </div>

    <script>
        // --- GLOBAL STATE ---
        let isAdminLoggedIn = false;
        const ADMIN_PASSWORD = "Maxchingershambo08"; // Changed password
        let clickCount = 0;
        let clickTimeout;
        let products = [];
        let cart = [];
        let currentFilter = 'all';
        let currentShippingCost = 0;
        
        // --- INITIAL DATA (FALLBACK) ---
        const defaultProducts = [
            { id: 1, name: "Bass Pro Jig Head", category: "jigs", price: 12.99, description: "Premium jig head perfect for bass fishing with realistic action.", image: "https://images.unsplash.com/photo-1544551763-46a013bb70d5?w=400&h=300&fit=crop" },
            { id: 2, name: "Soft Plastic Worm", category: "soft-plastics", price: 8.49, description: "Lifelike soft plastic worm that attracts fish with its natural movement.", image: "https://images.unsplash.com/photo-1559827260-dc66d52bef19?w=400&h=300&fit=crop" },
            { id: 3, name: "Popper Topwater Lure", category: "topwaters", price: 15.99, description: "Creates explosive surface action that drives fish wild.", image: "https://images.unsplash.com/photo-1578662996442-48f60103fc96?w=400&h=300&fit=crop" },
            { id: 4, name: "Colorado Spinnerbait", category: "spinnerbaits", price: 11.79, description: "Classic spinnerbait with Colorado blade for maximum flash and vibration.", image: "https://images.unsplash.com/photo-1559827260-dc66d52bef19?w=400&h=300&fit=crop" }
        ];

        // --- APP INITIALIZATION ---
        document.addEventListener('DOMContentLoaded', function() {
            init();
        });

        function init() {
            // Load data from localStorage
            const storedProducts = localStorage.getItem('products');
            if (storedProducts) {
                products = JSON.parse(storedProducts);
            } else {
                products = defaultProducts;
                saveProductsToStorage();
            }

            const storedCart = localStorage.getItem('cart');
            cart = storedCart ? JSON.parse(storedCart) : [];

            // Load logo and apply it to both admin and customer views
            const savedLogo = localStorage.getItem('companyLogo');
            if (savedLogo) {
                applyLogo(savedLogo);
            }
            
            // Render initial views
            renderProducts();
            updateCartCount();
            renderAdminProducts();
            
            // Setup listeners
            setupEventListeners();
            setupImageUpload('imageUpload', 'imagePreview', 'productImageURL', '.admin-form .file-upload-area');
            setupImageUpload('logoUpload', 'logoPreview', null, '.logo-upload-container .file-upload-area', handleLogoUpload);

            // Handle order success message from redirect
            const urlParams = new URLSearchParams(window.location.search);
            if (urlParams.has('order') && urlParams.get('order') === 'success') {
                showToast("Thank you! Your order has been placed successfully.");
                // Clean up the URL
                window.history.replaceState({}, document.title, window.location.pathname);
            }
        }

        // --- EVENT LISTENERS ---
        function setupEventListeners() {
            document.getElementById('logo').addEventListener('click', handleCrownClick);
            
            document.getElementById('productForm').addEventListener('submit', function(e) {
                e.preventDefault();
                saveProduct();
            });

            document.getElementById('checkoutForm').addEventListener('submit', function(e) {
                if (!this.checkValidity()) {
                    e.preventDefault();
                    alert("Please fill out all required fields.");
                    return;
                }
                prepareOrderForSubmission();
            });
            
            document.querySelectorAll('input[name="payment_method"]').forEach(radio => {
                radio.addEventListener('change', (e) => {
                    document.getElementById('bankDetails').classList.toggle('hidden', e.target.id !== 'bankTransfer');
                    document.getElementById('stripe-element').classList.toggle('hidden', e.target.id !== 'stripe');
                    document.getElementById('paypal-button-container').classList.toggle('hidden', e.target.id !== 'paypal');
                });
            });
            
            // NEW: Shipping options listener
            document.getElementById('shippingOptions').addEventListener('change', (e) => {
                currentShippingCost = parseFloat(e.target.value) || 0;
                updateCheckoutSummary(); // Update total when shipping changes
            });
        }
        
        // --- DATA PERSISTENCE ---
        function saveProductsToStorage() {
            localStorage.setItem('products', JSON.stringify(products));
        }

        function saveCartToStorage() {
            localStorage.setItem('cart', JSON.stringify(cart));
        }
        
        // --- VIEW MANAGEMENT & RENDERING ---
        function showView(view) {
            if (view === 'admin' && !isAdminLoggedIn) {
                showAdminLogin();
                return;
            }
            document.getElementById('storeView').classList.toggle('hidden', view !== 'store');
            document.getElementById('adminView').classList.toggle('hidden', view !== 'admin');
        }

        function renderProducts() {
            const grid = document.getElementById('productsGrid');
            grid.innerHTML = '';
            const filteredProducts = currentFilter === 'all' ? products : products.filter(p => p.category === currentFilter);
            
            filteredProducts.forEach(product => {
                const card = document.createElement('div');
                card.className = 'product-card';
                card.innerHTML = `
                    <img src="${product.image}" alt="${product.name}" class="product-image">
                    <div class="product-info">
                        <h3 class="product-title">${product.name}</h3>
                        <div class="product-price">$${product.price.toFixed(2)}</div>
                        <p class="product-description">${product.description}</p>
                        <button class="add-to-cart" onclick="addToCart(${product.id})">Add to Cart</button>
                    </div>
                `;
                grid.appendChild(card);
            });
        }

        function filterByCategory(category) {
            currentFilter = category;
            renderProducts();
            document.querySelectorAll('.category-btn').forEach(btn => {
                btn.classList.remove('active');
                if (btn.textContent.toLowerCase().includes(category)) {
                    btn.classList.add('active');
                }
            });
        }

        // --- CART FUNCTIONALITY ---
        function addToCart(productId) {
            const product = products.find(p => p.id === productId);
            if (!product) return;
            
            const existingItem = cart.find(item => item.id === productId);
            if (existingItem) {
                existingItem.quantity++;
            } else {
                cart.push({...product, quantity: 1});
            }
            
            updateCartCount();
            showToast(`${product.name} added to cart`);
            saveCartToStorage();
        }

        function updateCartCount() {
            const count = cart.reduce((total, item) => total + item.quantity, 0);
            document.getElementById('cartCount').textContent = count;
            document.getElementById('checkoutBtn').disabled = count === 0;
        }
        
        function showCart() {
            const modal = document.getElementById('cartModal');
            const cartItems = document.getElementById('cartItems');
            const cartTotalEl = document.getElementById('cartTotal');
            
            cartItems.innerHTML = '';
            
            if (cart.length === 0) {
                cartItems.innerHTML = '<p>Your cart is empty.</p>';
                cartTotalEl.textContent = 'Total: $0.00';
            } else {
                let total = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
                cart.forEach(item => {
                    const cartItem = document.createElement('div');
                    cartItem.className = 'cart-item';
                    cartItem.innerHTML = `
                        <img src="${item.image}" alt="${item.name}">
                        <div class="cart-item-info">
                            <div class="cart-item-title">${item.name}</div>
                            <div>$${item.price.toFixed(2)} each</div>
                            <div class="quantity-controls">
                                <button class="quantity-btn" onclick="updateCartItem(${item.id}, -1)">-</button>
                                <span>${item.quantity}</span>
                                <button class="quantity-btn" onclick="updateCartItem(${item.id}, 1)">+</button>
                            </div>
                        </div>
                        <div>
                           <div style="font-weight: bold; text-align: right;">$${(item.price * item.quantity).toFixed(2)}</div>
                           <button class="remove-item" style="margin-top: 5px;" onclick="removeFromCart(${item.id})">Remove</button>
                        </div>
                    `;
                    cartItems.appendChild(cartItem);
                });
                cartTotalEl.textContent = `Total: $${total.toFixed(2)}`;
            }
            modal.style.display = 'block';
        }

        function closeCart() {
            document.getElementById('cartModal').style.display = 'none';
        }

        function updateCartItem(productId, change) {
            const item = cart.find(item => item.id === productId);
            if (!item) return;
            
            item.quantity += change;
            
            if (item.quantity <= 0) {
                removeFromCart(productId);
            } else {
                showCart(); // Refresh cart display
                updateCartCount();
                saveCartToStorage();
            }
        }

        function removeFromCart(productId) {
            cart = cart.filter(item => item.id !== productId);
            showCart(); // Refresh cart display
            updateCartCount();
            saveCartToStorage();
        }

        // --- CHECKOUT FUNCTIONALITY ---
        function showCheckout() {
            if (cart.length === 0) { return; }
            // Set the dynamic redirect URL for FormSubmit
            const redirectUrl = `${window.location.origin}${window.location.pathname}?order=success`;
            document.getElementById('formSubmitRedirect').value = redirectUrl;

            updateCheckoutSummary();
            closeCart();
            document.getElementById('checkoutModal').style.display = 'block';
        }
        
        function updateCheckoutSummary() {
            const orderItemsDisplay = document.getElementById('orderItemsDisplay');
            const checkoutTotalEl = document.getElementById('checkoutTotal');
            const subtotal = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
            const grandTotal = subtotal + currentShippingCost;

            let orderItemsHTML = '<ul style="list-style-type: none; padding: 0;">';
             cart.forEach(item => {
                orderItemsHTML += `<li style="margin-bottom: 0.5rem; ">
                    ${item.name} (x${item.quantity}) - $${(item.price * item.quantity).toFixed(2)}
                </li>`;
            });
            orderItemsHTML += '</ul>';
            orderItemsDisplay.innerHTML = orderItemsHTML;
            
            checkoutTotalEl.innerHTML = `
                <div>Subtotal: $${subtotal.toFixed(2)}</div>
                <div class="shipping-total">Shipping: $${currentShippingCost.toFixed(2)}</div>
                <div class="grand-total">Grand Total: $${grandTotal.toFixed(2)}</div>
            `;
        }

        function closeCheckout() {
            document.getElementById('checkoutModal').style.display = 'none';
        }
        
        function prepareOrderForSubmission() {
            const subtotal = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
            const grandTotal = subtotal + currentShippingCost;

            const orderSummary = cart.map(item => 
                `${item.name} (Qty: ${item.quantity})`
            ).join(', ');
            
            document.getElementById('orderItems').value = orderSummary;
            document.getElementById('shippingCost').value = `$${currentShippingCost.toFixed(2)}`;
            document.getElementById('orderTotal').value = `$${grandTotal.toFixed(2)}`;

            // Clear cart after preparing for submission
            cart = [];
            updateCartCount();
            saveCartToStorage();
        }

        // --- ADMIN FUNCTIONALITY ---
        function handleCrownClick() {
            if (document.getElementById('adminView').classList.contains('hidden')) {
                clickCount++;
                clearTimeout(clickTimeout);
                clickTimeout = setTimeout(() => { clickCount = 0; }, 1000);
                if (clickCount >= 3) {
                    clickCount = 0;
                    showAdminLogin();
                }
            } else {
                 showView('store');
            }
        }

        function showAdminLogin() {
            const password = prompt("Enter admin password:");
            if (password === ADMIN_PASSWORD) {
                isAdminLoggedIn = true;
                showView('admin');
            } else if (password !== null) {
                alert('Incorrect password!');
            }
        }

        function renderAdminProducts() {
            const container = document.getElementById('adminProductsList');
            container.innerHTML = '';
            
            products.slice().reverse().forEach(product => {
                const productElement = document.createElement('div');
                productElement.className = 'product-card';
                productElement.innerHTML = `
                    <img src="${product.image}" alt="${product.name}" class="product-image">
                    <div class="product-info">
                        <h3 class="product-title">${product.name}</h3>
                        <p style="font-size:0.9em; color:#666; text-transform: capitalize;">${product.category}</p>
                        <p style="font-weight:bold; color: #e74c3c;">$${product.price.toFixed(2)}</p>
                        <div style="margin-top: 1rem;">
                           <button onclick="editProduct(${product.id})" class="btn btn-secondary" style="color: #333; border-color: #333;">Edit</button>
                           <button onclick="deleteProduct(${product.id})" class="btn" style="background: #e74c3c; color: white;">Delete</button>
                        </div>
                    </div>
                `;
                container.appendChild(productElement);
            });
        }
        
        function saveProduct() {
            const id = document.getElementById('productId').value;
            const name = document.getElementById('productName').value;
            const category = document.getElementById('productCategory').value;
            const price = parseFloat(document.getElementById('productPrice').value);
            const description = document.getElementById('productDescription').value;
            const image = document.getElementById('productImageURL').value;
            
            if (!name || !category || isNaN(price) || !description || !image) {
                alert('Please fill all fields and provide an image URL or upload.');
                return;
            }

            if (id) { // Editing existing product
                const index = products.findIndex(p => p.id == id);
                if (index > -1) {
                    products[index] = { ...products[index], name, category, price, description, image };
                }
            } else { // Adding new product
                 const newProduct = {
                    id: Date.now(), // Use timestamp for a unique ID
                    name, category, price, description, image
                };
                products.push(newProduct);
            }
            
            saveProductsToStorage();
            renderProducts();
            renderAdminProducts();
            
            document.getElementById('productForm').reset();
            document.getElementById('productId').value = '';
            document.getElementById('imagePreview').style.display = 'none';
            showToast(id ? 'Product updated successfully!' : 'Product added successfully!');
        }

        function editProduct(id) {
            const product = products.find(p => p.id === id);
            if (!product) return;
            
            document.getElementById('productId').value = product.id;
            document.getElementById('productName').value = product.name;
            document.getElementById('productCategory').value = product.category;
            document.getElementById('productPrice').value = product.price;
            document.getElementById('productDescription').value = product.description;
            document.getElementById('productImageURL').value = product.image;
            
            const preview = document.getElementById('imagePreview');
            preview.src = product.image;
            preview.style.display = 'block';
            
            document.getElementById('productForm').scrollIntoView({ behavior: 'smooth' });
        }

        function deleteProduct(id) {
            if (!confirm('Are you sure you want to delete this product? This action cannot be undone.')) return;
            
            products = products.filter(p => p.id !== id);
            saveProductsToStorage();
            renderProducts();
            renderAdminProducts();
            showToast('Product deleted successfully.');
        }

        // --- UTILITY FUNCTIONS ---
        function showToast(message) {
            const toast = document.getElementById('toast');
            toast.textContent = message;
            toast.classList.add('show');
            setTimeout(() => {
                toast.classList.remove('show');
            }, 3000);
        }
        
        function applyLogo(logoUrl) {
            // Apply to customer-facing logo
            document.getElementById('mainHeaderLogo').src = logoUrl;
            document.getElementById('mainHeaderLogo').style.display = 'inline';
            document.getElementById('defaultLogoIcon').style.display = 'none';
            document.getElementById('defaultLogoText').style.display = 'none';
            // Apply to admin panel logo
            document.getElementById('companyLogo').src = logoUrl;
        }

        function setupImageUpload(inputId, previewId, urlInputId, areaSelector, customHandler) {
            const fileInput = document.getElementById(inputId);
            const uploadArea = document.querySelector(areaSelector);

            const handler = customHandler || function(event) {
                const file = event.target.files[0];
                if (!file) return;

                const reader = new FileReader();
                reader.onload = function(e) {
                    document.getElementById(previewId).src = e.target.result;
                    document.getElementById(previewId).style.display = 'block';
                    if (urlInputId) {
                        document.getElementById(urlInputId).value = e.target.result;
                    }
                };
                reader.readAsDataURL(file);
            };

            fileInput.addEventListener('change', handler);
            uploadArea.addEventListener('click', () => fileInput.click());

            ['dragover', 'drop', 'dragleave'].forEach(eventName => {
                uploadArea.addEventListener(eventName, (e) => {
                    e.preventDefault();
                    e.stopPropagation();
                    if (eventName === 'dragover') uploadArea.style.borderColor = '#1a365d';
                    else uploadArea.style.borderColor = '#ddd';
                    if (eventName === 'drop' && e.dataTransfer.files.length) {
                        fileInput.files = e.dataTransfer.files;
                        handler({ target: fileInput });
                    }
                });
            });
        }
        
        function handleLogoUpload(event) {
            const file = event.target.files[0];
            if (!file) return;
            
            const reader = new FileReader();
            reader.onload = function(e) {
                const logoUrl = e.target.result;
                // Preview in admin panel
                document.getElementById('logoPreview').src = logoUrl;
                document.getElementById('logoPreview').style.display = 'block';
                // Apply logo everywhere
                applyLogo(logoUrl);
                // Persist logo
                localStorage.setItem('companyLogo', logoUrl);
            };
            reader.readAsDataURL(file);
        }

    </script>
</body>
</html>
