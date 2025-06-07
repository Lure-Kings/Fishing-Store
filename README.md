<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lure Kings - Premium Fishing Lures</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        /* [Previous CSS remains unchanged] */
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; background-color: #f5f5f5; color: #333; line-height: 1.6; }
        .header { background-color: #1a365d; padding: 1rem 2rem; position: sticky; top: 0; z-index: 1000; box-shadow: 0 2px 5px rgba(0,0,0,0.1); }
        .nav { display: flex; justify-content: space-between; align-items: center; max-width: 1200px; margin: 0 auto; }
        .logo { font-size: 2rem; font-weight: bold; color: white; display: flex; align-items: center; gap: 0.5rem; cursor: pointer; }
        #mainHeaderLogo { max-height: 50px; display: none; }
        #logoText { display: flex; align-items: center; gap: 0.5rem; }
        .logo i { font-size: 1.8rem; color: #f8d56b; }
        .nav-buttons { display: flex; gap: 1rem; align-items: center; }
        .btn { padding: 0.5rem 1rem; border: none; border-radius: 4px; cursor: pointer; font-weight: 600; transition: all 0.2s ease; }
        .btn-primary { background-color: #1a365d; color: white; }
        .btn-secondary { background-color: transparent; color: white; border: 1px solid white; }
        .btn:hover { opacity: 0.9; }
        .cart-icon { position: relative; }
        .cart-count { position: absolute; top: -8px; right: -8px; background: #e74c3c; color: white; border-radius: 50%; width: 20px; height: 20px; display: flex; align-items: center; justify-content: center; font-size: 0.75rem; font-weight: bold; }
        .container { max-width: 1200px; margin: 2rem auto; padding: 0 1rem; }
        .hero { text-align: center; margin-bottom: 3rem; padding: 2rem 0; background-color: white; border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.1); }
        .hero h1 { font-size: 2.5rem; margin-bottom: 1rem; color: #1a365d; }
        .hero p { font-size: 1.1rem; max-width: 600px; margin: 0 auto; color: #666; }
        .categories { display: flex; flex-wrap: wrap; gap: 0.5rem; margin-bottom: 2rem; justify-content: center; }
        .category-btn { padding: 0.5rem 1rem; background: white; border: 1px solid #ddd; border-radius: 4px; cursor: pointer; transition: all 0.2s ease; }
        .category-btn:hover, .category-btn.active { background: #1a365d; border-color: #1a365d; color: white; }
        .products-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(280px, 1fr)); gap: 1.5rem; margin-bottom: 3rem; }
        .product-card { background: white; border: 1px solid #ddd; border-radius: 8px; overflow: hidden; box-shadow: 0 2px 5px rgba(0,0,0,0.1); transition: all 0.2s ease; }
        .product-card:hover { transform: translateY(-5px); box-shadow: 0 5px 15px rgba(0,0,0,0.1); }
        .product-image { width: 100%; height: 200px; object-fit: cover; border-bottom: 1px solid #ddd; }
        .product-info { padding: 1rem; }
        .product-title { font-size: 1.1rem; font-weight: bold; margin-bottom: 0.5rem; color: #1a365d; }
        .product-price { font-size: 1.2rem; font-weight: bold; color: #e74c3c; margin-bottom: 1rem; }
        .product-description { color: #666; margin-bottom: 1rem; font-size: 0.9rem; }
        .add-to-cart { width: 100%; background-color: #1a365d; color: white; border: none; padding: 0.5rem; border-radius: 4px; cursor: pointer; font-weight: 600; transition: all 0.2s ease; }
        .add-to-cart:hover { background-color: #142a4a; }
        .modal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0, 0, 0, 0.5); z-index: 2000; }
        .modal-content { position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%); background: white; border-radius: 8px; padding: 2rem; max-width: 90%; width: 600px; max-height: 90%; overflow-y: auto; box-shadow: 0 5px 15px rgba(0,0,0,0.2); color: #333; }
        .close { position: absolute; top: 1rem; right: 1rem; font-size: 1.5rem; cursor: pointer; color: #666; }
        .close:hover { color: #333; }
        .cart-item { display: flex; align-items: center; padding: 1rem; border-bottom: 1px solid #ddd; gap: 1rem; }
        .cart-item img { width: 60px; height: 60px; object-fit: cover; border-radius: 4px; border: 1px solid #ddd; }
        .cart-item-info { flex-grow: 1; }
        .cart-item-title { font-weight: bold; margin-bottom: 0.25rem; color: #1a365d; }
        .quantity-controls { display: flex; align-items: center; gap: 0.5rem; margin: 0.5rem 0; }
        .quantity-btn { background: #1a365d; color: white; border: none; width: 25px; height: 25px; border-radius: 4px; cursor: pointer; display: flex; align-items: center; justify-content: center; }
        .quantity-btn:hover { background: #142a4a; }
        .remove-item { background: #e74c3c; color: white; border: none; padding: 0.25rem 0.5rem; border-radius: 4px; cursor: pointer; font-size: 0.8rem; }
        .remove-item:hover { background: #c0392b; }
        .cart-total { text-align: right; padding: 1rem 0; font-size: 1.3rem; font-weight: bold; color: #1a365d; border-top: 1px solid #ddd; margin-top: 1rem; }
        .admin-form { background: white; border: 1px solid #ddd; padding: 1.5rem; border-radius: 8px; margin-bottom: 2rem; }
        .form-group { margin-bottom: 1rem; }
        .form-group label { display: block; margin-bottom: 0.5rem; font-weight: 600; color: #1a365d; }
        .form-group label .required-star { color: #e74c3c; margin-left: 2px; }
        .form-group input, .form-group textarea, .form-group select { width: 100%; padding: 0.5rem; border: 1px solid #ddd; border-radius: 4px; font-size: 1rem; }
        .form-group input:focus, .form-group textarea:focus, .form-group select:focus { outline: none; border-color: #1a365d; }
        .hidden { display: none !important; }
        .checkout-form { max-width: 500px; margin: 0 auto; }
        .file-upload-area { border: 2px dashed #ddd; border-radius: 8px; padding: 1.5rem; text-align: center; cursor: pointer; margin-bottom: 1rem; }
        .file-upload-area:hover { border-color: #1a365d; }
        .image-preview { max-width: 200px; max-height: 200px; border-radius: 8px; margin-top: 1rem; border: 1px solid #ddd; }
        .payment-info { background: #f9f9f9; border: 1px solid #ddd; padding: 1rem; border-radius: 8px; margin-bottom: 1rem; }
        .payment-info h4 { color: #1a365d; margin-bottom: 0.5rem; }
        .payment-method { padding: 0.5rem; border: 1px solid #ddd; border-radius: 4px; margin-bottom: 0.5rem; }
        .toast { position: fixed; bottom: 20px; right: 20px; background: #1a365d; color: white; padding: 1rem; border-radius: 4px; box-shadow: 0 2px 10px rgba(0,0,0,0.2); z-index: 3000; opacity: 0; visibility: hidden; transition: opacity 0.3s, visibility 0.3s; }
        .toast.show { opacity: 1; visibility: visible; }
        .admin-logo { text-align: center; margin-bottom: 1.5rem; }
        .admin-logo img { max-width: 200px; height: auto; }
        .logo-upload-container { margin-bottom: 1.5rem; text-align: center; }
        .logo-preview { max-width: 200px; max-height: 100px; margin-top: 1rem; display: none; }
        .summary-line { display: flex; justify-content: space-between; font-size: 1rem; padding: 0.25rem 0; }
        .summary-line.total { font-weight: bold; font-size: 1.2rem; margin-top: 0.5rem; border-top: 1px solid #ccc; padding-top: 0.5rem; }
        @media (max-width: 768px) {
            .nav { flex-direction: column; gap: 1rem; }
            .hero h1 { font-size: 2rem; }
            .products-grid { grid-template-columns: 1fr; }
            .modal-content { width: 95%; }
        }
    </style>
</head>
<body>
    <header class="header">
        <nav class="nav">
            <div class="logo" id="logo">
                <img id="mainHeaderLogo" alt="Company Logo">
                <span id="logoText">
                    <i class="fas fa-crown"></i>
                    Lure Kings
                </span>
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
                <h1>Lure Kings</h1>
                <p>Serious value for serious anglers</p>
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
            </div>
    </div>

    <div id="cartModal" class="modal">
        <div class="modal-content">
            <span class="close" onclick="closeCart()">&times;</span>
            <h2 style="margin-bottom: 1rem; color: #1a365d;">Shopping Cart</h2>
            <div id="cartItems"></div>
            <div class="cart-total" id="cartTotalDisplay">Total: $0.00</div>
            <button class="btn btn-primary" onclick="showCheckout()" style="width: 100%; margin-top: 1rem;">
                Proceed to Checkout
            </button>
        </div>
    </div>

    <div id="checkoutModal" class="modal">
        <div class="modal-content">
            <span class="close" onclick="closeCheckout()">&times;</span>
            <h2 style="margin-bottom: 1rem; color: #1a365d;">Secure Checkout</h2>
            
            <form id="checkoutForm" method="POST">
                <input type="hidden" name="_subject" value="New Order from Lure Kings">
                <input type="hidden" name="_template" value="table">
                <input type="hidden" name="_next">
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
                
                <p style="text-align:center; padding: 0.5rem; background: #f9f9f9; border-radius: 4px; margin-bottom: 1rem; font-style: italic;">
                    DM for Shipping prices.
                </p>
                
                <div class="form-group">
                    <label for="orderNotes">Order Notes (Optional)</label>
                    <textarea id="orderNotes" name="notes" rows="2" placeholder="Any special instructions..."></textarea>
                </div>

                <div class="form-group payment-info">
                    <h4>Payment Method<span class="required-star">*</span></h4>
                    <div class="payment-method">
                        <input type="radio" id="bankTransfer" name="payment_method" value="Direct Transfer" required>
                        <label for="bankTransfer">Direct Transfer</label>
                        <div id="bankDetails" class="hidden" style="padding-left: 20px; font-size: 0.9em; opacity: 0.8;">
                            <p>DM for direct transfer.</p>
                        </div>
                    </div>
                    <div class="payment-method">
                        <input type="radio" id="stripe" name="payment_method" value="Stripe">
                        <label for="stripe">Stripe (Credit/Debit Card)</label>
                        <div id="stripe-element" class="hidden" style="padding: 10px;">
                             <p style="font-style:italic;">Stripe integration placeholder.</p>
                        </div>
                    </div>
                     <div class="payment-method">
                        <input type="radio" id="paypal" name="payment_method" value="PayPal">
                        <label for="paypal">PayPal</label>
                        <div id="paypal-button-container" class="hidden" style="padding: 10px;">
                            <p style="font-style:italic;">PayPal integration placeholder.</p>
                        </div>
                    </div>
                </div>

                <div class="form-group">
                    <label>Order Summary</label>
                    <div id="orderItemsDisplay" style="padding: 0.5rem; background: #f5f5f5; border-radius: 4px;"></div>
                </div>
                <div class="cart-total" id="checkoutTotalDisplay">Total: $0.00</div>
                
                <input type="hidden" id="orderItems" name="order_items">
                <input type="hidden" id="orderTotal" name="order_total">
                
                <button type="submit" class="btn btn-primary" style="width: 100%; margin-top: 1rem;">
                    Place Order
                </button>
            </form>
        </div>
    </div>
    
    <script>
    // --- GLOBAL STATE ---
    let isAdminLoggedIn = false;
    const ADMIN_PASSWORD = "Maxchingershambo08";
    let clickCount = 0;
    let clickTimeout;
    let products = [];
    let cart = [];
    let currentFilter = 'all';

    // --- FALLBACK DATA ---
    const defaultProducts = [ /* ... same as before ... */ ];

    // --- APP INITIALIZATION ---
    document.addEventListener('DOMContentLoaded', init);

    function init() {
        const storedProducts = localStorage.getItem('products');
        products = storedProducts ? JSON.parse(storedProducts) : defaultProducts;

        const storedCart = localStorage.getItem('cart');
        cart = storedCart ? JSON.parse(storedCart) : [];

        const savedLogo = localStorage.getItem('companyLogo');
        if (savedLogo) {
            applyLogo(savedLogo);
        } else {
            document.getElementById('logoText').style.display = 'flex';
        }
        
        // Regenerate Admin HTML in case it's needed
        createAdminView();
        
        renderProducts();
        updateCartCount();
        renderAdminProducts();
        
        setupEventListeners();
        setupImageUpload('imageUpload', 'imagePreview', 'productImageURL', '.admin-form .file-upload-area');
        setupImageUpload('logoUpload', 'logoPreview', null, '.logo-upload-container .file-upload-area', handleLogoUpload);

        const urlParams = new URLSearchParams(window.location.search);
        if (urlParams.has('order') && urlParams.get('order') === 'success') {
            showToast("Thank you! Your order has been placed successfully.");
            window.history.replaceState({}, document.title, window.location.pathname);
        }
    }

    function createAdminView() {
        const adminViewContainer = document.getElementById('adminView');
        adminViewContainer.innerHTML = `
            <div class="hero">
                <div class="admin-logo"><img id="companyLogo" src="" alt="Lure Kings Logo"></div>
                <h1>Admin Dashboard</h1><p>Manage your Lure Kings inventory</p>
            </div>
            <div class="logo-upload-container">
                <h3>Upload Company Logo</h3>
                <div class="file-upload-area">
                    <i class="fas fa-cloud-upload-alt" style="font-size: 2rem; color: #1a365d; margin-bottom: 0.5rem;"></i>
                    <p>Click to upload logo or drag & drop</p>
                </div>
                <input type="file" id="logoUpload" accept="image/*" style="display: none;">
                <img id="logoPreview" class="logo-preview">
            </div>
            <div class="admin-form">
                <h2 style="margin-bottom: 1rem; color: #1a365d;">Add/Edit Product</h2>
                <form id="productForm">
                    <input type="hidden" id="productId">
                    <div class="form-group"><label for="productName">Product Name</label><input type="text" id="productName" required></div>
                    <div class="form-group"><label for="productCategory">Category</label><select id="productCategory" required><option value="">Select Category</option><option value="jigs">Jigs</option><option value="soft-plastics">Soft Plastics</option><option value="topwaters">Topwaters</option><option value="spinnerbaits">Spinnerbaits</option></select></div>
                    <div class="form-group"><label for="productPrice">Price ($)</label><input type="number" id="productPrice" step="0.01" min="0" required></div>
                    <div class="form-group"><label for="productDescription">Description</label><textarea id="productDescription" rows="3" required></textarea></div>
                    <div class="form-group"><label for="productImage">Product Image</label><div class="file-upload-area"><i class="fas fa-cloud-upload-alt" style="font-size: 2rem; color: #1a365d; margin-bottom: 0.5rem;"></i><p>Click to upload image or drag & drop</p></div><input type="file" id="imageUpload" accept="image/*" style="display: none;"><input type="text" id="productImageURL" placeholder="Or enter image URL"><img id="imagePreview" class="image-preview" style="display: none;"></div>
                    <button type="submit" class="btn btn-primary" style="width: 100%;">Save Product</button>
                </form>
            </div>
            <div class="admin-form"><h2 style="margin-bottom: 1rem; color: #1a365d;">Manage Existing Products</h2><div id="adminProductsList"></div></div>
        `;
    }

    // --- EVENT LISTENERS ---
    function setupEventListeners() {
        document.getElementById('logo').addEventListener('click', handleCrownClick);
        
        // Re-bind listener after creating admin view
        const adminView = document.getElementById('adminView');
        adminView.querySelector('#productForm').addEventListener('submit', function(e) {
            e.preventDefault();
            saveProduct();
        });

        const checkoutForm = document.getElementById('checkoutForm');
        checkoutForm.addEventListener('submit', function(e) {
            e.preventDefault();
            const selectedPayment = checkoutForm.querySelector('input[name="payment_method"]:checked');
            if (!selectedPayment) {
                alert("Please select a payment method.");
                return;
            }
            prepareOrderForSubmission();
            checkoutForm.submit();
        });
        
        document.querySelectorAll('input[name="payment_method"]').forEach(radio => {
            radio.addEventListener('change', (e) => {
                document.getElementById('bankDetails').classList.toggle('hidden', e.target.id !== 'bankTransfer');
                document.getElementById('stripe-element').classList.toggle('hidden', e.target.id !== 'stripe');
                document.getElementById('paypal-button-container').classList.toggle('hidden', e.target.id !== 'paypal');
            });
        });
    }

    // --- CART & TOTALS ---
    function showCart() {
        updateCartDisplay();
        document.getElementById('cartModal').style.display = 'block';
    }

    function showCheckout() {
        if (cart.length === 0) {
            alert("Your cart is empty. Please add items before checking out.");
            return;
        }
        updateCheckoutDisplay();
        closeCart();
        document.getElementById('checkoutModal').style.display = 'block';
    }

    function updateCartDisplay() {
        const total = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
        document.getElementById('cartItems').innerHTML = cart.length ? cart.map(item => `
            <div class="cart-item">
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
            </div>
        `).join('') : '<p>Your cart is empty.</p>';
        document.getElementById('cartTotalDisplay').textContent = `Total: $${total.toFixed(2)}`;
    }

    function updateCheckoutDisplay() {
        const total = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
        document.getElementById('orderItemsDisplay').innerHTML = cart.map(item => `
            <div class="summary-line"><span>${item.name} (x${item.quantity})</span><span>$${(item.price * item.quantity).toFixed(2)}</span></div>
        `).join('');
        document.getElementById('checkoutTotalDisplay').textContent = `Total: $${total.toFixed(2)}`;
    }

    function updateCartItem(productId, change) {
        const item = cart.find(i => i.id === productId);
        if (item) {
            item.quantity += change;
            if (item.quantity <= 0) {
                cart = cart.filter(i => i.id !== productId);
            }
        }
        saveCartToStorage();
        updateCartCount();
        updateCartDisplay(); // Update display if cart modal is open
        updateCheckoutDisplay(); // Also update checkout if it's open
    }

    function removeFromCart(productId) {
        cart = cart.filter(item => item.id !== productId);
        saveCartToStorage();
        updateCartCount();
        updateCartDisplay();
        updateCheckoutDisplay();
    }

    function prepareOrderForSubmission() {
        const total = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
        const orderSummary = cart.map(item => `${item.name} (Qty: ${item.quantity})`).join('\n');
        
        const checkoutForm = document.getElementById('checkoutForm');
        checkoutForm.querySelector('[name="order_items"]').value = orderSummary;
        checkoutForm.querySelector('[name="order_total"]').value = `$${total.toFixed(2)}`;
        checkoutForm.action = "https://formsubmit.co/lure.kings.fishing.aus@gmail.com";
        checkoutForm.querySelector('[name="_next"]').value = `${window.location.origin}${window.location.pathname}?order=success`;

        cart = [];
        saveCartToStorage();
        updateCartCount();
    }

    // --- LOGO HANDLING ---
    function applyLogo(logoUrl) {
        const mainLogoImg = document.getElementById('mainHeaderLogo');
        const adminLogoImg = document.getElementById('companyLogo');
        const logoPreviewImg = document.getElementById('logoPreview');
        const logoText = document.getElementById('logoText');

        mainLogoImg.src = logoUrl;
        mainLogoImg.style.display = 'block';
        if (adminLogoImg) adminLogoImg.src = logoUrl;
        if (logoPreviewImg) {
            logoPreviewImg.src = logoUrl;
            logoPreviewImg.style.display = 'block';
        }
        logoText.style.display = 'none';
    }
    
    // All other functions (saveProductsToStorage, renderProducts, addToCart, etc.) can remain as they were in the previous version.
    // They are included here for completeness.
    function saveProductsToStorage() { localStorage.setItem('products', JSON.stringify(products)); }
    function saveCartToStorage() { localStorage.setItem('cart', JSON.stringify(cart)); }
    function showView(view) { if (view === 'admin' && !isAdminLoggedIn) { showAdminLogin(); return; } document.getElementById('storeView').classList.toggle('hidden', view !== 'store'); document.getElementById('adminView').classList.toggle('hidden', view !== 'admin'); }
    function renderProducts() { const grid = document.getElementById('productsGrid'); grid.innerHTML = ''; const filtered = currentFilter === 'all' ? products : products.filter(p => p.category === currentFilter); filtered.forEach(p => { const card = document.createElement('div'); card.className = 'product-card'; card.innerHTML = `<img src="${p.image}" alt="${p.name}" class="product-image"><div class="product-info"><h3 class="product-title">${p.name}</h3><div class="product-price">$${p.price.toFixed(2)}</div><p class="product-description">${p.description}</p><button class="add-to-cart" onclick="addToCart(${p.id})">Add to Cart</button></div>`; grid.appendChild(card); }); }
    function filterByCategory(category) { currentFilter = category; renderProducts(); document.querySelectorAll('.category-btn').forEach(btn => { btn.classList.remove('active'); if (btn.textContent.toLowerCase().includes(category)) btn.classList.add('active'); }); }
    function addToCart(productId) { const product = products.find(p => p.id === productId); if (!product) return; const item = cart.find(i => i.id === productId); if (item) { item.quantity++; } else { cart.push({...product, quantity: 1}); } saveCartToStorage(); updateCartCount(); showToast(`${product.name} added to cart`); }
    function updateCartCount() { document.getElementById('cartCount').textContent = cart.reduce((t, i) => t + i.quantity, 0); }
    function closeCart() { document.getElementById('cartModal').style.display = 'none'; }
    function closeCheckout() { document.getElementById('checkoutModal').style.display = 'none'; }
    function handleCrownClick() { clickCount++; clearTimeout(clickTimeout); clickTimeout = setTimeout(() => { clickCount = 0; }, 1000); if (clickCount >= 3) { clickCount = 0; showAdminLogin(); } }
    function showAdminLogin() { const pw = prompt("Enter admin password:"); if (pw === ADMIN_PASSWORD) { isAdminLoggedIn = true; showView('admin'); } else if (pw !== null) { alert('Incorrect password!'); } }
    function renderAdminProducts() { const cont = document.getElementById('adminProductsList'); if (!cont) return; cont.innerHTML = ''; if (!products.length) { cont.innerHTML = '<p>No products found</p>'; return; } products.slice().reverse().forEach(p => { const el = document.createElement('div'); el.className = 'product-card'; el.innerHTML = `<img src="${p.image}" alt="${p.name}" class="product-image"><div class="product-info"><h3 class="product-title">${p.name}</h3><p style="font-size:0.9em;color:#666">${p.category}</p><p style="font-weight:bold;color:#e74c3c">$${p.price.toFixed(2)}</p><div style="margin-top:1rem;"><button onclick="editProduct(${p.id})" class="btn btn-secondary">Edit</button><button onclick="deleteProduct(${p.id})" class="btn btn-secondary" style="background:#e74c3c;">Delete</button></div></div>`; cont.appendChild(el); }); }
    function saveProduct() { const id = document.getElementById('productId').value; const name = document.getElementById('productName').value; const cat = document.getElementById('productCategory').value; const price = parseFloat(document.getElementById('productPrice').value); const desc = document.getElementById('productDescription').value; const img = document.getElementById('productImageURL').value; if (!name || !cat || isNaN(price) || !desc || !img) { alert('Please fill all fields and provide an image.'); return; } if (id) { const i = products.findIndex(p => p.id == id); if (i > -1) products[i] = { ...products[i], name, category: cat, price, description: desc, image: img }; } else { products.push({ id: Date.now(), name, category: cat, price, description: desc, image: img }); } saveProductsToStorage(); renderProducts(); renderAdminProducts(); document.getElementById('productForm').reset(); document.getElementById('productId').value = ''; document.getElementById('imagePreview').style.display = 'none'; showToast(id ? 'Product updated!' : 'Product added!'); }
    function editProduct(id) { const p = products.find(prod => prod.id === id); if (!p) return; document.getElementById('productId').value = p.id; document.getElementById('productName').value = p.name; document.getElementById('productCategory').value = p.category; document.getElementById('productPrice').value = p.price; document.getElementById('productDescription').value = p.description; document.getElementById('productImageURL').value = p.image; const prev = document.getElementById('imagePreview'); prev.src = p.image; prev.style.display = 'block'; document.getElementById('productForm').scrollIntoView({ behavior: 'smooth' }); }
    function deleteProduct(id) { if (!confirm('Are you sure you want to delete this product?')) return; products = products.filter(p => p.id !== id); saveProductsToStorage(); renderProducts(); renderAdminProducts(); showToast('Product deleted.'); }
    function showToast(message) { const t = document.getElementById('toast'); t.textContent = message; t.classList.add('show'); setTimeout(() => { t.classList.remove('show'); }, 3000); }
    function setupImageUpload(inputId, previewId, urlInputId, areaSelector, customHandler) { const fileInput = document.getElementById(inputId); const uploadArea = document.querySelector(areaSelector); if (!uploadArea) return; const handler = customHandler || function(event) { const file = event.target.files[0]; if (!file) return; const reader = new FileReader(); reader.onload = function(e) { document.getElementById(previewId).src = e.target.result; document.getElementById(previewId).style.display = 'block'; if (urlInputId) document.getElementById(urlInputId).value = e.target.result; }; reader.readAsDataURL(file); }; fileInput.addEventListener('change', handler); uploadArea.addEventListener('click', () => fileInput.click()); ['dragover', 'drop', 'dragleave'].forEach(evt => { uploadArea.addEventListener(evt, e => { e.preventDefault(); e.stopPropagation(); if (evt === 'dragover') uploadArea.style.borderColor = '#1a365d'; else uploadArea.style.borderColor = '#ddd'; if (evt === 'drop' && e.dataTransfer.files.length) { fileInput.files = e.dataTransfer.files; handler({ target: fileInput }); } }); }); }
    function handleLogoUpload(event) { const file = event.target.files[0]; if (!file) return; const reader = new FileReader(); reader.onload = function(e) { const logoUrl = e.target.result; applyLogo(logoUrl); localStorage.setItem('companyLogo', logoUrl); }; reader.readAsDataURL(file); }
    </script>
</body>
</html>
