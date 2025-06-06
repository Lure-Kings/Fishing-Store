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
        
        .logo #storeLogo {
            max-height: 50px;
            width: auto;
            display: none; /* Hidden by default, shown via JS if logo is uploaded */
        }

        .logo .logo-text-container {
            display: flex;
            align-items: center;
            gap: 0.5rem;
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
            display: flex;
            flex-direction: column;
        }

        .product-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }
        
        /* --- MODIFICATION: Horizontal Scroll Image Gallery --- */
        .product-image-container {
            display: flex;
            overflow-x: auto;
            scroll-snap-type: x mandatory;
            height: 220px;
            border-bottom: 1px solid #ddd;
        }
        .product-image-container::-webkit-scrollbar {
            height: 8px;
        }
        .product-image-container::-webkit-scrollbar-thumb {
            background: #ccc;
            border-radius: 4px;
        }
        .product-image {
            width: 100%;
            height: 100%;
            object-fit: cover;
            flex: 0 0 100%;
            scroll-snap-align: start;
        }
        /* --- END MODIFICATION --- */

        .product-info {
            padding: 1rem;
            display: flex;
            flex-direction: column;
            flex-grow: 1;
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
            flex-grow: 1; /* Pushes buttons down */
        }
        
        .product-buttons {
            display: flex;
            gap: 0.5rem;
            margin-top: auto; /* Pushes this container to the bottom */
        }

        .add-to-cart, .reviews-btn {
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

        .add-to-cart:hover, .reviews-btn:hover {
            background-color: #142a4a;
        }
        
        .reviews-btn {
            background-color: #555;
        }
        .reviews-btn:hover {
            background-color: #333;
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
            justify-content: center;
            align-items: center;
        }

        .modal-content {
            position: relative;
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
        
        /* --- Review System Styles --- */
        .review-section {
            margin-top: 2rem;
            background: white;
            padding: 1.5rem;
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }
        .review {
            border-bottom: 1px solid #eee;
            padding: 1rem 0;
        }
        .review:last-child {
            border-bottom: none;
        }
        .review-author {
            font-weight: bold;
            color: #1a365d;
        }
        .review-content {
            margin-top: 0.5rem;
        }

        .hidden {
            display: none !important;
        }

        .admin-form, .checkout-form {
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

        .logo-upload-container {
            margin-bottom: 1.5rem;
            text-align: center;
        }
        
        .file-upload-area {
            border: 2px dashed #ddd;
            border-radius: 8px;
            padding: 1.5rem;
            text-align: center;
            cursor: pointer;
            margin-bottom: 1rem;
        }

        .logo-preview {
            max-width: 200px;
            max-height: 100px;
            margin-top: 1rem;
            display: none;
        }
        
        .explainer-box {
            background-color: #fffbe6;
            border: 1px solid #ffe58f;
            border-radius: 4px;
            padding: 1rem;
            margin: 1.5rem 0;
            font-size: 0.9rem;
            color: #614d13;
        }
        .explainer-box h5 {
            color: #d46b08;
            margin-top: 0;
            margin-bottom: 0.5rem;
        }
        
        /* --- MODIFICATION: Stripe Placeholder Styles --- */
        .payment-method {
            padding: 0.75rem;
            border: 1px solid #ddd;
            border-radius: 4px;
            margin-bottom: 0.5rem;
            cursor: pointer;
        }
        .stripe-card-element {
            border: 1px solid #ddd;
            padding: 10px;
            border-radius: 4px;
            margin-top: 0.5rem;
        }

        @media (max-width: 768px) {
            .nav {
                flex-direction: column;
                gap: 1rem;
            }
            .products-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
    .star-rating {
    display: flex;
    gap: 5px;
    cursor: pointer;
}

.star-rating i {
    color: #ddd;
    transition: color 0.2s;
}

.star-rating i.active {
    color: #f8d56b;
}
</head>
<body>
    <header class="header">
        <nav class="nav">
            <div class="logo" id="logo">
                <img id="storeLogo" src="" alt="Lure Kings Logo">
                <div class="logo-text-container" id="logoText">
                    <i class="fas fa-crown"></i>
                    Lure Kings
                </div>
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

   <div class="hero">
    <h1>Premium Fishing Gear</h1>
    <p>High-quality fishing lures for the best prices</p>
</div>

            <div class="categories">
                <button class="category-btn active" onclick="filterByCategory('all')">All Lures</button>
                <button class="category-btn" onclick="filterByCategory('jigs')">Jigs</button>
                <button class="category-btn" onclick="filterByCategory('soft-plastics')">Soft Plastics</button>
                <button class="category-btn" onclick="filterByCategory('topwaters')">Topwaters</button>
                <button class="category-btn" onclick="filterByCategory('spinnerbaits')">Spinnerbaits</button>
            </div>

            <div class="products-grid" id="productsGrid">
                 </div>
            
            <div class="review-section">
                <h2 style="text-align: center; color: #1a365d; margin-bottom: 1rem;">Customer Reviews</h2>
                <div id="generalReviewsList">
                    <p style="text-align: center;">No reviews yet. Be the first!</p>
                </div>
                <div class="admin-form" style="margin-top: 2rem;">
                    <h3 style="margin-bottom: 1rem; color: #1a365d;">Leave a Website Review</h3>
                    <form id="generalReviewForm" action="https://formsubmit.co/lure.kings.fishing.aus@gmail.com" method="POST">
                        <input type="hidden" name="_subject" value="New Lure Kings Website Review!">
                        <input type="hidden" name="_template" value="table">
                        <div class="form-group">
                        <div class="form-group">
    <label>Rating</label>
    <div class="star-rating">
        <i class="fas fa-star" data-rating="1"></i>
        <i class="fas fa-star" data-rating="2"></i>
        <i class="fas fa-star" data-rating="3"></i>
        <i class="fas fa-star" data-rating="4"></i>
        <i class="fas fa-star" data-rating="5"></i>
    </div>
    <input type="hidden" id="ratingInput" name="rating" required>
</div>
<input type="hidden" name="_next" value="https://lure-kings.github.io/Fishing-Store/">
                            <label for="reviewerName">Your Name</label>
                            <input type="text" id="reviewerName" name="Reviewer_Name" required>
                        </div>
                        <div class="form-group">
                            <label for="reviewContent">Your Review</label>
                            <textarea id="reviewContent" name="Review_Content" rows="3" required></textarea>
                        </div>
                        <button type="submit" class="btn btn-primary" style="width: 100%;">Submit Review</button>
                    </form>
                </div>
            </div>
        </div>

        <div id="adminView" class="hidden">
            <div class="hero">
                <h1>Admin Dashboard</h1>
                <p>Manage your Lure Kings inventory</p>
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
                        <label for="productImageURLs">Product Images (one URL per line)</label>
                        <textarea id="productImageURLs" rows="4" placeholder="https://example.com/image1.jpg&#10;https://example.com/image2.jpg" required></textarea>
                    </div>
                    <button type="submit" class="btn btn-primary" style="width: 100%;">Save Product</button>
                </form>
            </div>

            <div class="admin-form">
                <h2 style="margin-bottom: 1rem; color: #1a365d;">Manage Existing Products</h2>
                <div id="adminProductsList"></div>
            </div>
        </div>
    </div>

    <div id="cartModal" class="modal">
        <div class="modal-content">
            <span class="close" onclick="closeModal('cartModal')">&times;</span>
            <h2 style="margin-bottom: 1rem; color: #1a365d;">Shopping Cart</h2>
            <div id="cartItems"></div>
            <div class="cart-total" id="cartTotal" style="text-align:right; font-size:1.3rem; margin-top:1rem;">Total: $0.00</div>
            <button class="btn btn-primary" onclick="showCheckout()" style="width: 100%; margin-top: 1rem;">Proceed to Checkout</button>
        </div>
    </div>

    <div id="checkoutModal" class="modal">
        <div class="modal-content">
            <span class="close" onclick="closeModal('checkoutModal')">&times;</span>
            <h2 style="margin-bottom: 1rem; color: #1a365d;">Secure Checkout</h2>
            <form id="checkoutForm" action="https://formsubmit.co/lure.kings.fishing.aus@gmail.com" method="POST">
                <input type="hidden" name="_subject" value="New Order from Lure Kings!">
                <input type="hidden" name="_template" value="table">
                
                <div class="form-group">
                    <label for="customerName">Full Name<span class="required-star">*</span></label>
                    <input type="text" id="customerName" name="name" required>
                </div>
                <div class="form-group">
                    <label for="customerEmail">Email Address<span class="required-star">*</span></label>
                    <input type="email" id="customerEmail" name="email" required>
                </div>
                <div class="form-group">
                    <label for="customerAddress">Delivery Address<span class="required-star">*</span></label>
                    <textarea id="customerAddress" name="address" rows="3" required></textarea>
                </div>

                <h4>Payment Method<span class="required-star">*</span></h4>
                <div class="payment-method">
                    <input type="radio" id="bankTransfer" name="payment_method" value="Bank Transfer" required>
                    <label for="bankTransfer">Direct Bank Transfer</label>
                    <div id="bankDetails" class="hidden" style="padding: 10px; font-size: 0.9em;">
                        <p><strong>Bank:</strong> Your Bank | <strong>Account:</strong> Your Name<br>
                           <strong>BSB:</strong> 000-000 | <strong>Acc No:</strong> 123456789<br>
                           Please use your Order ID as the payment reference.</p>
                    </div>
                </div>
                
                <div class="payment-method">
                    <input type="radio" id="stripe" name="payment_method" value="Stripe" required>
                    <label for="stripe">Credit/Debit Card (Stripe)</label>
                    <div id="stripe-card-container" class="hidden" style="margin-top: 10px;">
                        <label for="card-element">Card Details</label>
                        <div id="card-element" class="stripe-card-element">
                          </div>
                        <div id="card-errors" role="alert" style="color: #e74c3c; margin-top: 5px;"></div>
                    </div>
                </div>

                <div class="explainer-box">
                    <h5>Live Payment Integration (Stripe)</h5>
                    <p>The credit card form above is a visual placeholder. To accept live payments, you must connect this site to a secure backend server. Client-side-only sites cannot securely process payments.</p>
                </div>
                
                <input type="hidden" id="orderItems" name="order_items">
                <input type="hidden" id="orderTotal" name="order_total">
                
                <button type="submit" class="btn btn-primary" style="width: 100%; margin-top: 1rem;">Place Order</button>
            </form>
        </div>
    </div>

    <div id="reviewModal" class="modal">
        <div class="modal-content">
            <span class="close" onclick="closeModal('reviewModal')">&times;</span>
            <h2 id="reviewModalTitle" style="margin-bottom: 1rem; color: #1a365d;">Product Reviews</h2>
            <div id="productReviewsList"></div>
            <div class="admin-form" style="margin-top: 2rem; border: none; padding: 0;">
                <h3 style="margin-bottom: 1rem; color: #1a365d;">Leave a Review</h3>
                <form id="productReviewForm" action="https://formsubmit.co/lure.kings.fishing.aus@gmail.com" method="POST">
                    <input type="hidden" id="reviewProductId" name="product_id">
                    <input type="hidden" id="reviewProductName" name="Product_Name">
                    <input type="hidden" name="_subject" value="New Product Review!">
                    <input type="hidden" name="_template" value="table">
                    <div class="form-group">
                        <label for="productReviewerName">Your Name</label>
                        <input type="text" id="productReviewerName" name="Reviewer_Name" required>
                    </div>
                    <div class="form-group">
                        <label for="productReviewContent">Your Review</label>
                        <textarea id="productReviewContent" name="Review_Content" rows="3" required></textarea>
                    </div>
                    <button type="submit" class="btn btn-primary" style="width: 100%;">Submit Review</button>
                </form>
            </div>
        </div>
    </div>

    <script>
        // --- GLOBAL STATE ---
        let isAdminLoggedIn = false;
        const ADMIN_PASSWORD = "Maxchingershambo08"; // Change this password
        let clickCount = 0;
        let clickTimeout;
        let products = [];
        let cart = [];
        let generalReviews = [];
        let currentFilter = 'all';
        
        // --- MODIFICATION: Default product list is now empty ---
        // Add your products via the admin dashboard after logging in.
        const defaultProducts = [];

        // --- APP INITIALIZATION ---
        document.addEventListener('DOMContentLoaded', () => init());

        function init() {
            // Load data from localStorage or use defaults
            products = JSON.parse(localStorage.getItem('products')) || defaultProducts;
            cart = JSON.parse(localStorage.getItem('cart')) || [];
            generalReviews = JSON.parse(localStorage.getItem('generalReviews')) || [];

            const savedLogo = localStorage.getItem('companyLogo');
            if (savedLogo) {
                updateLogo(savedLogo);
            }
            
            // Render initial views
            renderProducts();
            updateCartCount();
            renderAdminProducts();
            renderGeneralReviews();
            
            // Setup listeners
            setupEventListeners();
        }
document.querySelectorAll('.star-rating i').forEach(star => {
    star.addEventListener('click', (e) => {
        const rating = e.target.dataset.rating;
        document.getElementById('ratingInput').value = rating;
        
        document.querySelectorAll('.star-rating i').forEach(s => {
            s.classList.toggle('active', s.dataset.rating <= rating);
        });
    });
});
        // --- EVENT LISTENERS ---
        function setupEventListeners() {
            document.getElementById('logo').addEventListener('click', handleCrownClick);
            
            document.getElementById('productForm').addEventListener('submit', (e) => {
                e.preventDefault();
                saveProduct();
            });

            document.getElementById('checkoutForm').addEventListener('submit', (e) => {
                prepareOrderForSubmission();
            });
            
            document.getElementById('generalReviewForm').addEventListener('submit', (e) => {
                e.preventDefault();
                // This submits to FormSubmit and saves locally
                document.getElementById('generalReviewForm').submit();
                saveGeneralReview(); 
            });

            document.getElementById('productReviewForm').addEventListener('submit', (e) => {
                e.preventDefault();
                // This submits to FormSubmit and saves locally
                document.getElementById('productReviewForm').submit();
                saveProductReview();
            });

            // Payment method selection logic
            document.querySelectorAll('input[name="payment_method"]').forEach(radio => {
                radio.addEventListener('change', (e) => {
                    document.getElementById('bankDetails').classList.toggle('hidden', e.target.id !== 'bankTransfer');
                    document.getElementById('stripe-card-container').classList.toggle('hidden', e.target.id !== 'stripe');
                });
            });
            
             // Logo Upload Listeners
            const fileInput = document.getElementById('logoUpload');
            const uploadArea = document.querySelector('.file-upload-area');
            uploadArea.addEventListener('click', () => fileInput.click());
            fileInput.addEventListener('change', handleLogoUpload);
        }

        // --- DATA PERSISTENCE ---
        const saveProductsToStorage = () => localStorage.setItem('products', JSON.stringify(products));
        const saveCartToStorage = () => localStorage.setItem('cart', JSON.stringify(cart));
        const saveGeneralReviewsToStorage = () => localStorage.setItem('generalReviews', JSON.stringify(generalReviews));

        // --- VIEW MANAGEMENT ---
        const showView = (view) => {
            document.getElementById('storeView').classList.toggle('hidden', view !== 'store');
            document.getElementById('adminView').classList.toggle('hidden', view !== 'admin');
        };
        const closeModal = (modalId) => document.getElementById(modalId).style.display = 'none';

        function renderProducts() {
            const grid = document.getElementById('productsGrid');
            grid.innerHTML = '';
            const filteredProducts = currentFilter === 'all' ? products : products.filter(p => p.category === currentFilter);
            
            if(filteredProducts.length === 0 && currentFilter === 'all') {
                grid.innerHTML = `<p>No products yet. Log in to the admin panel to add some!</p>`;
                return;
            }

            filteredProducts.forEach(product => {
                const card = document.createElement('div');
                card.className = 'product-card';
                card.innerHTML = `
                    <div class="product-image-container">
                        ${product.images.map(imgSrc => `<img src="${imgSrc}" alt="${product.name}" class="product-image">`).join('')}
                    </div>
                    <div class="product-info">
                        <h3 class="product-title">${product.name}</h3>
                        <div class="product-price">$${product.price.toFixed(2)}</div>
                        <p class="product-description">${product.description}</p>
                        <div class="product-buttons">
                            <button class="add-to-cart" onclick="addToCart(${product.id})">Add to Cart</button>
                            <button class="reviews-btn" onclick="showProductReviews(${product.id})">Reviews (${product.reviews.length})</button>
                        </div>
                    </div>
                `;
                grid.appendChild(card);
            });
        }
        
        function filterByCategory(category) {
            currentFilter = category;
            renderProducts();
            document.querySelectorAll('.category-btn').forEach(btn => btn.classList.remove('active'));
            const buttonToActivate = Array.from(document.querySelectorAll('.category-btn')).find(btn => btn.getAttribute('onclick').includes(`'${category}'`));
            if(buttonToActivate) buttonToActivate.classList.add('active');
        }

        // --- CART FUNCTIONALITY ---
        function addToCart(productId) {
            const product = products.find(p => p.id === productId);
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

        const updateCartCount = () => {
            document.getElementById('cartCount').textContent = cart.reduce((total, item) => total + item.quantity, 0);
        };
        
        function showCart() {
            const modal = document.getElementById('cartModal');
            const cartItemsEl = document.getElementById('cartItems');
            cartItemsEl.innerHTML = '';
            
            if (cart.length === 0) {
                cartItemsEl.innerHTML = '<p>Your cart is empty</p>';
            } else {
                cart.forEach(item => {
                    const cartItem = document.createElement('div');
                    cartItem.className = 'cart-item'; // You would need to add CSS for this class
                    cartItem.style.cssText = 'display: flex; gap: 1rem; padding: 1rem 0; border-bottom: 1px solid #eee; align-items: center;';
                    cartItem.innerHTML = `
                        <img src="${item.images[0]}" alt="${item.name}" style="width:60px; height:60px; object-fit:cover; border-radius:4px;">
                        <div style="flex-grow:1;">
                            <div style="font-weight:bold;">${item.name}</div>
                            <div>$${item.price.toFixed(2)}</div>
                        </div>
                        <div style="text-align:right;">
                             <div style="font-weight:bold;">$${(item.price * item.quantity).toFixed(2)}</div>
                             <button onclick="removeFromCart(${item.id})" style="background:none; border:none; color:red; cursor:pointer; font-size:0.8rem;">Remove</button>
                        </div>
                    `;
                    cartItemsEl.appendChild(cartItem);
                });
            }
            document.getElementById('cartTotal').textContent = `Total: $${cart.reduce((sum, item) => sum + (item.price * item.quantity), 0).toFixed(2)}`;
            modal.style.display = 'flex';
        }

        function removeFromCart(productId) {
            cart = cart.filter(item => item.id !== productId);
            updateCartCount();
            showCart(); // Refresh cart display
            saveCartToStorage();
        }

        // --- CHECKOUT FUNCTIONALITY ---
        function showCheckout() {
            if (cart.length === 0) {
                alert("Your cart is empty.");
                return;
            }
            closeModal('cartModal');
            document.getElementById('checkoutModal').style.display = 'flex';
        }
        
        function prepareOrderForSubmission() {
            const orderSummary = cart.map(item => `${item.name} (Qty: ${item.quantity})`).join(', ');
            const total = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0).toFixed(2);
            document.getElementById('orderItems').value = orderSummary;
            document.getElementById('orderTotal').value = `$${total}`;
            cart = [];
            updateCartCount();
            saveCartToStorage();
        }
        
        // --- REVIEW SYSTEM LOGIC ---
        function renderGeneralReviews() {
            const container = document.getElementById('generalReviewsList');
            container.innerHTML = '';
            if (generalReviews.length === 0) {
                container.innerHTML = '<p style="text-align: center;">No reviews yet. Be the first!</p>';
                return;
            }
            generalReviews.forEach(review => {
                const reviewEl = document.createElement('div');
                reviewEl.className = 'review';
                reviewEl.innerHTML = `<div class="review-author">${review.name}</div><div class="review-content">${review.content}</div>`;
                container.appendChild(reviewEl);
            });
        }

        function saveGeneralReview() {
            const name = document.getElementById('reviewerName').value;
            const content = document.getElementById('reviewContent').value;
            generalReviews.push({ name, content });
            saveGeneralReviewsToStorage();
            renderGeneralReviews();
            document.getElementById('generalReviewForm').reset();
            showToast('Thank you for your review!');
        }

        function showProductReviews(productId) {
            const product = products.find(p => p.id === productId);
            document.getElementById('reviewModalTitle').textContent = `Reviews for ${product.name}`;
            const container = document.getElementById('productReviewsList');
            container.innerHTML = '';
            if (product.reviews.length === 0) {
                container.innerHTML = '<p>No reviews for this product yet.</p>';
            } else {
                product.reviews.forEach(review => {
                    const reviewEl = document.createElement('div');
                    reviewEl.className = 'review';
                    reviewEl.innerHTML = `<div class="review-author">${review.name}</div><div class="review-content">${review.content}</div>`;
                    container.appendChild(reviewEl);
                });
            }
            document.getElementById('reviewProductId').value = product.id;
            document.getElementById('reviewProductName').value = product.name;
            document.getElementById('reviewModal').style.display = 'flex';
        }

        function saveProductReview() {
            const productId = document.getElementById('reviewProductId').value;
            const name = document.getElementById('productReviewerName').value;
            const content = document.getElementById('productReviewContent').value;
            const product = products.find(p => p.id == productId);
            if(product) {
                product.reviews.push({ name, content });
                saveProductsToStorage();
                renderProducts(); // To update review count on card
            }
            document.getElementById('productReviewForm').reset();
            closeModal('reviewModal');
            showToast('Thank you for your review!');
        }

        // --- ADMIN FUNCTIONALITY ---
        function handleCrownClick() {
    clickCount++;
    clearTimeout(clickTimeout);
    clickTimeout = setTimeout(() => { clickCount = 0; }, 1000);
    if (clickCount >= 3) { // Changed from 7 to 3 clicks
        clickCount = 0;
        showAdminLogin();
    }
}

        function showAdminLogin() {
            if (isAdminLoggedIn) {
                showView('admin');
                return;
            }
            const password = prompt("Enter admin password:");
            if (password === ADMIN_PASSWORD) {
                isAdminLoggedIn = true;
                showView('admin');
            } else if (password) {
                alert('Incorrect password!');
            }
        }

        function renderAdminProducts() {
            const container = document.getElementById('adminProductsList');
            container.innerHTML = '';
            if (products.length === 0) {
                container.innerHTML = '<p>No products found. Add one above.</p>';
                return;
            }
            products.slice().reverse().forEach(product => {
                const productElement = document.createElement('div');
                productElement.className = 'product-card';
                productElement.innerHTML = `
                    <div class="product-info">
                        <h3 class="product-title">${product.name}</h3>
                        <p style="font-weight:bold; color: #e74c3c;">$${product.price.toFixed(2)}</p>
                        <div style="margin-top: 1rem; display: flex; gap: 0.5rem;">
                            <button onclick="editProduct(${product.id})" class="btn btn-primary" style="flex:1;">Edit</button>
                            <button onclick="deleteProduct(${product.id})" class="btn btn-primary" style="background: #e74c3c; flex:1;">Delete</button>
                        </div>
                    </div>
                `;
                container.appendChild(productElement);
            });
        }
        
        function saveProduct() {
            const id = document.getElementById('productId').value;
            const newProductData = {
                name: document.getElementById('productName').value,
                category: document.getElementById('productCategory').value,
                price: parseFloat(document.getElementById('productPrice').value),
                description: document.getElementById('productDescription').value,
                images: document.getElementById('productImageURLs').value.split('\n').map(url => url.trim()).filter(url => url),
            };

            if (id) { // Editing
                const index = products.findIndex(p => p.id == id);
                products[index] = { ...products[index], ...newProductData };
            } else { // Adding
                products.push({ id: Date.now(), ...newProductData, reviews: [] });
            }
            
            saveProductsToStorage();
            renderProducts();
            renderAdminProducts();
            document.getElementById('productForm').reset();
            document.getElementById('productId').value = '';
            showToast(id ? 'Product updated!' : 'Product added!');
        }

        function editProduct(id) {
            const product = products.find(p => p.id === id);
            document.getElementById('productId').value = product.id;
            document.getElementById('productName').value = product.name;
            document.getElementById('productCategory').value = product.category;
            document.getElementById('productPrice').value = product.price;
            document.getElementById('productDescription').value = product.description;
            document.getElementById('productImageURLs').value = product.images.join('\n');
            document.getElementById('productForm').scrollIntoView({ behavior: 'smooth' });
        }

        function deleteProduct(id) {
            if (!confirm('Are you sure you want to delete this product?')) return;
            products = products.filter(p => p.id !== id);
            saveProductsToStorage();
            renderProducts();
            renderAdminProducts();
            showToast('Product deleted.');
        }

        // --- UTILITY FUNCTIONS ---
        const showToast = (message) => {
            const toast = document.getElementById('toast');
            toast.textContent = message;
            toast.classList.add('show');
            setTimeout(() => toast.classList.remove('show'), 3000);
        };
        
        function handleLogoUpload(event) {
            const file = event.target.files[0];
            if (!file) return;
            const reader = new FileReader();
            reader.onload = (e) => {
                const logoUrl = e.target.result;
                updateLogo(logoUrl);
                localStorage.setItem('companyLogo', logoUrl);
            };
            reader.readAsDataURL(file);
        }

        function updateLogo(logoUrl) {
            document.getElementById('logoPreview').src = logoUrl;
            document.getElementById('logoPreview').style.display = 'block';
            document.getElementById('storeLogo').src = logoUrl;
            document.getElementById('storeLogo').style.display = 'block';
            document.getElementById('logoText').style.display = 'none';
        }
    </script>
</body>
</html>
