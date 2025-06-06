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
        
        /* --- MODIFICATION START: Logo Styles --- */
        .logo #storeLogo {
            max-height: 50px; /* Adjust as needed */
            width: auto;
            display: none; /* Hidden by default */
        }

        .logo .logo-text-container {
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }
        /* --- MODIFICATION END: Logo Styles --- */

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
        
        /* --- MODIFICATION START: Multiple Product Image Carousel --- */
        .product-image-container {
            width: 100%;
            height: 200px;
            position: relative;
            overflow: hidden;
            border-bottom: 1px solid #ddd;
        }

        .product-image {
            width: 100%;
            height: 100%;
            object-fit: cover;
            position: absolute;
            transition: opacity 0.3s ease-in-out;
        }

        .carousel-btn {
            position: absolute;
            top: 50%;
            transform: translateY(-50%);
            background-color: rgba(26, 54, 93, 0.7);
            color: white;
            border: none;
            cursor: pointer;
            padding: 0.5rem;
            z-index: 10;
            border-radius: 50%;
            width: 30px;
            height: 30px;
            line-height: 20px;
        }
        
        .carousel-btn:hover {
            background-color: #1a365d;
        }

        .carousel-btn.prev {
            left: 10px;
        }

        .carousel-btn.next {
            right: 10px;
        }
        /* --- MODIFICATION END: Multiple Product Image Carousel --- */

        .product-info {
            padding: 1rem;
            display: flex;
            flex-direction: column;
            flex-grow: 1; /* Allows footer buttons to stick to the bottom */
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
        
        /* --- MODIFICATION START: Product buttons flex container --- */
        .product-buttons {
            display: flex;
            gap: 0.5rem;
            margin-top: auto; /* Pushes this container to the bottom */
        }
        /* --- MODIFICATION END: Product buttons flex container --- */

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
            position: relative; /* Changed from absolute */
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
        
        /* --- MODIFICATION START: Review System Styles --- */
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
        
        .review-rating {
            color: #f8d56b;
        }
        
        .review-content {
            margin-top: 0.5rem;
        }
        /* --- MODIFICATION END: Review System Styles --- */


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
        
        /* --- MODIFICATION START: Shipping/Payment Explainer Box --- */
        .explainer-box {
            background-color: #fffbe6;
            border: 1px solid #ffe58f;
            border-radius: 4px;
            padding: 1rem;
            margin: 1rem 0;
            font-size: 0.9rem;
            color: #614d13;
        }
        .explainer-box h5 {
            color: #d46b08;
            margin-top: 0;
        }
        .explainer-box code {
            background-color: #f0f0f0;
            padding: 2px 4px;
            border-radius: 3px;
            font-family: monospace;
        }
        /* --- MODIFICATION END: Shipping/Payment Explainer Box --- */

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
                        <label for="productImageURLs">Product Images (one URL per line)</label>
                        <textarea id="productImageURLs" rows="4" placeholder="https://example.com/image1.jpg&#10;https://example.com/image2.jpg" required></textarea>
                    </div>
                    <button type="submit" class="btn btn-primary" style="width: 100%;">
                        Save Product
                    </button>
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
            <h2 style="margin-bottom: 1rem; color: #1a365d;">
                Shopping Cart
            </h2>
            <div id="cartItems"></div>
            <div class="cart-total" id="cartTotal">Total: $0.00</div>
            <button class="btn btn-primary" onclick="showCheckout()" style="width: 100%; margin-top: 1rem;">
                Proceed to Checkout
            </button>
        </div>
    </div>

    <div id="checkoutModal" class="modal">
        <div class="modal-content">
            <span class="close" onclick="closeModal('checkoutModal')">&times;</span>
            <h2 style="margin-bottom: 1rem; color: #1a365d;">
                Secure Checkout
            </h2>
            
            <form id="checkoutForm" action="https://formsubmit.co/lure.kings.fishing.aus@gmail.com" method="POST">
                <input type="hidden" name="_next" value="https://your-domain.com/?order=success"> <input type="hidden" name="_subject" value="New Order from Lure Kings">
                <input type="hidden" name="_template" value="table">
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
                
                <div class="explainer-box">
                    <h5>Address Validation & Shipping Estimates</h5>
                    <p>
                        To enable automatic address validation and shipping cost estimates from <strong>Chatswood</strong>, you need to integrate a service like the <strong>Google Maps API</strong>.
                    </p>
                    <ol style="padding-left: 20px;">
                        <li>Create a Google Cloud account and get an API key for the "Places API" and "Distance Matrix API".</li>
                        <li>Implement JavaScript to use the Places API for address autocomplete.</li>
                        <li>Once an address is selected, send a request to your secure backend. The backend will use the Distance Matrix API (with your secret key) to calculate the distance from Chatswood and determine the shipping cost.</li>
                        <li>The shipping cost would then be added to the total.</li>
                    </ol>
                </div>
                <div class="form-group">
                    <label for="orderNotes">Order Notes (Optional)</label>
                    <textarea id="orderNotes" name="notes" rows="2" placeholder="Any special instructions..."></textarea>
                </div>

                <div class="form-group payment-info">
                    <h4>Payment Method<span class="required-star">*</span></h4>
                    <div class="payment-method">
                        <input type="radio" id="bankTransfer" name="payment_method" value="Bank Transfer" required>
                        <label for="bankTransfer">Direct Bank Transfer</label>
                        <div id="bankDetails" class="hidden" style="padding-left: 20px; font-size: 0.9em; opacity: 0.8;">
                            <p><strong>Bank:</strong> ANZ Bank | <strong>Account:</strong> Lure Kings Pty Ltd<br>
                                <strong>BSB:</strong> 012-345 | <strong>Acc No:</strong> 123456789<br>
                                Use your Order ID as reference.</p>
                        </div>
                    </div>
                    
                    <div class="explainer-box">
                        <h5>Live Payment Integration (Stripe/PayPal)</h5>
                        <p>To accept live payments, you must use a backend server.</p>
                        <p>
                            For <strong>Stripe</strong>, your frontend JavaScript would collect card details using secure "Stripe Elements". It would then request a "payment intent" from your backend. Your backend, using your <strong>secret Stripe key</strong>, would talk to Stripe to process the payment. This protects you and your customers. The same server-based approach is used for PayPal.
                        </p>
                    </div>
                     <div class="payment-method">
                        <input type="radio" id="stripe" name="payment_method" value="Stripe" disabled>
                        <label for="stripe">Stripe (Credit/Debit Card) - <em style="color:#999;">Integration required</em></label>
                    </div>
                     <div class="payment-method">
                        <input type="radio" id="paypal" name="payment_method" value="PayPal" disabled>
                        <label for="paypal">PayPal - <em style="color:#999;">Integration required</em></label>
                    </div>
                    </div>

                <div class="form-group">
                    <label>Order Summary</label>
                    <div id="orderItemsDisplay"></div>
                </div>
                <div class="cart-total" id="checkoutTotal">Total: $0.00</div>
                <input type="hidden" id="orderItems" name="order_items">
                <input type="hidden" id="orderTotal" name="order_total">
                
                <button type="submit" class="btn btn-primary" style="width: 100%; margin-top: 1rem;">
                    Place Order
                </button>
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
        const ADMIN_PASSWORD = "Maxchingershambo08";
        let clickCount = 0;
        let clickTimeout;
        let products = [];
        let cart = [];
        // MODIFICATION START: Added general reviews state
        let generalReviews = []; 
        // MODIFICATION END: Added general reviews state
        let currentFilter = 'all';
        
        // --- INITIAL DATA (FALLBACK) ---
        // MODIFICATION START: Updated product data to include multiple images and reviews
        const defaultProducts = [
             { 
                id: 1, 
                name: "Bass Pro Jig Head", 
                category: "jigs", 
                price: 12.99, 
                description: "Premium jig head perfect for bass fishing with realistic action.", 
                images: ["https://images.unsplash.com/photo-1544551763-46a013bb70d5?w=400&h=300&fit=crop"],
                reviews: []
            },
            { 
                id: 2, 
                name: "Soft Plastic Worm", 
                category: "soft-plastics", 
                price: 8.49, 
                description: "Lifelike soft plastic worm that attracts fish with its natural movement.", 
                images: ["https://images.unsplash.com/photo-1559827260-dc66d52bef19?w=400&h=300&fit=crop"],
                reviews: []
            },
            { 
                id: 3, 
                name: "Popper Topwater Lure", 
                category: "topwaters", 
                price: 15.99, 
                description: "Creates explosive surface action that drives fish wild.", 
                images: ["https://images.unsplash.com/photo-1578662996442-48f60103fc96?w=400&h=300&fit=crop"],
                reviews: []
            },
            { 
                id: 4, 
                name: "Colorado Spinnerbait", 
                category: "spinnerbaits", 
                price: 11.79, 
                description: "Classic spinnerbait with Colorado blade for maximum flash and vibration.", 
                images: [
                    "https://images.unsplash.com/photo-1559827260-dc66d52bef19?w=400&h=300&fit=crop",
                    "https://images.unsplash.com/photo-1519712461314-14c3e80a0e78?w=400&h=300&fit=crop"
                ],
                reviews: [
                    { name: 'John D.', content: 'Caught a huge bass with this! Works like a charm.' },
                    { name: 'AnglerJane', content: 'Great quality, but the color was slightly different than the photo.' }
                ]
            }
        ];
        // MODIFICATION END: Updated product data

        // --- APP INITIALIZATION ---
        document.addEventListener('DOMContentLoaded', function() {
            init();
        });

        function init() {
            // Load data from localStorage
            const storedProducts = localStorage.getItem('products');
            products = storedProducts ? JSON.parse(storedProducts) : defaultProducts;

            const storedCart = localStorage.getItem('cart');
            cart = storedCart ? JSON.parse(storedCart) : [];
            
            // MODIFICATION START: Load reviews from local storage
            const storedReviews = localStorage.getItem('generalReviews');
            generalReviews = storedReviews ? JSON.parse(storedReviews) : [];
            // MODIFICATION END: Load reviews from local storage

            const savedLogo = localStorage.getItem('companyLogo');
            if (savedLogo) {
                // MODIFICATION START: Update both admin and store logos
                document.getElementById('companyLogo').src = savedLogo;
                document.getElementById('storeLogo').src = savedLogo;
                document.getElementById('storeLogo').style.display = 'block';
                document.getElementById('logoText').style.display = 'none';
                document.getElementById('logoPreview').src = savedLogo;
                document.getElementById('logoPreview').style.display = 'block';
                // MODIFICATION END: Update both admin and store logos
            }
            
            // Render initial views
            renderProducts();
            updateCartCount();
            renderAdminProducts();
            // MODIFICATION START: Render reviews
            renderGeneralReviews();
            // MODIFICATION END: Render reviews
            
            // Setup listeners
            setupEventListeners();
            setupImageUpload('logoUpload', 'logoPreview', null, '.logo-upload-container .file-upload-area', handleLogoUpload);

            // Handle order success message
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
                const selectedPayment = document.querySelector('input[name="payment_method"]:checked');
                // Allow submission without payment if only bank transfer is selected
                if (!selectedPayment) {
                    alert("Please select a payment method.");
                    e.preventDefault();
                    return;
                }
                prepareOrderForSubmission();
            });
            
            // MODIFICATION START: Review form listeners
            document.getElementById('generalReviewForm').addEventListener('submit', function(e) {
                e.preventDefault();
                saveGeneralReview();
            });

            document.getElementById('productReviewForm').addEventListener('submit', function(e) {
                e.preventDefault();
                saveProductReview();
            });
            // MODIFICATION END: Review form listeners

            document.querySelectorAll('input[name="payment_method"]').forEach(radio => {
                radio.addEventListener('change', (e) => {
                    document.getElementById('bankDetails').classList.toggle('hidden', e.target.id !== 'bankTransfer');
                });
            });
        }

        // --- DATA PERSISTENCE ---
        function saveProductsToStorage() {
            localStorage.setItem('products', JSON.stringify(products));
        }

        function saveCartToStorage() {
            localStorage.setItem('cart', JSON.stringify(cart));
        }
        
        // MODIFICATION START: Save reviews to storage
        function saveGeneralReviewsToStorage() {
            localStorage.setItem('generalReviews', JSON.stringify(generalReviews));
        }
        // MODIFICATION END: Save reviews to storage

        // --- VIEW MANAGEMENT ---
        function showView(view) {
            document.getElementById('storeView').classList.toggle('hidden', view !== 'store');
            document.getElementById('adminView').classList.toggle('hidden', view !== 'admin');
        }
        
        // MODIFICATION START: Generic Modal Closer
        function closeModal(modalId) {
            document.getElementById(modalId).style.display = 'none';
        }
        // MODIFICATION END: Generic Modal Closer

        function renderProducts() {
            const grid = document.getElementById('productsGrid');
            grid.innerHTML = '';
            const filteredProducts = currentFilter === 'all' ? products : products.filter(p => p.category === currentFilter);
            
            filteredProducts.forEach(product => {
                const card = document.createElement('div');
                card.className = 'product-card';

                // MODIFICATION START: Product card with image carousel
                const imageContainer = document.createElement('div');
                imageContainer.className = 'product-image-container';
                
                let imageHTML = '';
                product.images.forEach((imgSrc, index) => {
                    imageHTML += `<img src="${imgSrc}" alt="${product.name}" class="product-image" style="opacity: ${index === 0 ? 1 : 0};">`;
                });
                
                if (product.images.length > 1) {
                    imageHTML += `
                        <button class="carousel-btn prev" onclick="navigateCarousel(event, ${product.id}, -1)">&lt;</button>
                        <button class="carousel-btn next" onclick="navigateCarousel(event, ${product.id}, 1)">&gt;</button>
                    `;
                }
                imageContainer.innerHTML = imageHTML;
                imageContainer.dataset.productId = product.id;
                imageContainer.dataset.currentImage = 0;
                // MODIFICATION END: Product card with image carousel
                
                const infoContainer = document.createElement('div');
                infoContainer.className = 'product-info';
                infoContainer.innerHTML = `
                    <h3 class="product-title">${product.name}</h3>
                    <div class="product-price">$${product.price.toFixed(2)}</div>
                    <p class="product-description">${product.description}</p>
                    <div class="product-buttons">
                        <button class="add-to-cart" onclick="addToCart(${product.id})">Add to Cart</button>
                        <button class="reviews-btn" onclick="showProductReviews(${product.id})">Reviews (${product.reviews.length})</button>
                    </div>
                `;
                
                card.appendChild(imageContainer);
                card.appendChild(infoContainer);
                grid.appendChild(card);
            });
        }
        
        // MODIFICATION START: Image carousel navigation
        function navigateCarousel(event, productId, direction) {
            event.stopPropagation(); // Prevents card hover effects from interfering
            const container = document.querySelector(`.product-image-container[data-product-id='${productId}']`);
            if (!container) return;

            const images = container.querySelectorAll('.product-image');
            let currentIndex = parseInt(container.dataset.currentImage);

            images[currentIndex].style.opacity = 0; // Fade out current
            
            currentIndex += direction;

            if (currentIndex >= images.length) {
                currentIndex = 0;
            } else if (currentIndex < 0) {
                currentIndex = images.length - 1;
            }

            images[currentIndex].style.opacity = 1; // Fade in next
            container.dataset.currentImage = currentIndex;
        }
        // MODIFICATION END: Image carousel navigation

        function filterByCategory(category) {
            currentFilter = category;
            renderProducts();
            document.querySelectorAll('.category-btn').forEach(btn => {
                btn.classList.remove('active');
            });
            // Find the button to activate. A bit more robust.
            const buttonToActivate = Array.from(document.querySelectorAll('.category-btn')).find(btn => btn.getAttribute('onclick').includes(`'${category}'`));
            if(buttonToActivate) buttonToActivate.classList.add('active');
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
        }
        
        function showCart() {
            const modal = document.getElementById('cartModal');
            const cartItems = document.getElementById('cartItems');
            const cartTotalEl = document.getElementById('cartTotal');
            
            cartItems.innerHTML = '';
            
            if (cart.length === 0) {
                cartItems.innerHTML = '<p>Your cart is empty</p>';
                cartTotalEl.textContent = 'Total: $0.00';
            } else {
                let total = 0;
                cart.forEach(item => {
                    const itemTotal = item.price * item.quantity;
                    total += itemTotal;
                    
                    const cartItem = document.createElement('div');
                    cartItem.className = 'cart-item';
                    cartItem.innerHTML = `
                        <img src="${item.images[0]}" alt="${item.name}"> <div class="cart-item-info">
                            <div class="cart-item-title">${item.name}</div>
                            <div>$${item.price.toFixed(2)} each</div>
                            <div class="quantity-controls">
                                <button class="quantity-btn" onclick="updateCartItem(${item.id}, -1)">-</button>
                                <span>${item.quantity}</span>
                                <button class="quantity-btn" onclick="updateCartItem(${item.id}, 1)">+</button>
                            </div>
                        </div>
                        <div>
                            <div style="font-weight: bold; text-align: right;">$${itemTotal.toFixed(2)}</div>
                            <button class="remove-item" style="margin-top: 5px;" onclick="removeFromCart(${item.id})">Remove</button>
                        </div>
                    `;
                    cartItems.appendChild(cartItem);
                });
                cartTotalEl.textContent = `Total: $${total.toFixed(2)}`;
            }
            modal.style.display = 'flex'; // Use flex for centering
        }

        function updateCartItem(productId, change) {
            const item = cart.find(item => item.id === productId);
            if (!item) return;
            
            item.quantity += change;
            
            if (item.quantity <= 0) {
                removeFromCart(productId);
            } else {
                updateCartCount();
                showCart(); // Refresh cart display
                saveCartToStorage();
            }
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
                alert("Your cart is empty. Please add items before checking out.");
                return;
            }
            const orderItemsDisplay = document.getElementById('orderItemsDisplay');
            const total = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);

            let orderItemsHTML = '<ul style="list-style-type: none; padding: 0;">';
             cart.forEach(item => {
                orderItemsHTML += `<li style="margin-bottom: 0.5rem; padding: 0.5rem; background: #f5f5f5; border-radius: 4px;">
                    ${item.name} - ${item.quantity} x $${item.price.toFixed(2)}
                </li>`;
            });
            orderItemsHTML += '</ul>';
            orderItemsDisplay.innerHTML = orderItemsHTML;

            document.getElementById('checkoutTotal').textContent = `Total: $${total.toFixed(2)}`;
            
            closeModal('cartModal');
            document.getElementById('checkoutModal').style.display = 'flex'; // Use flex for centering
        }
        
        function prepareOrderForSubmission() {
            const orderSummary = cart.map(item => 
                `${item.name} (Qty: ${item.quantity} x $${item.price.toFixed(2)}) = $${(item.quantity * item.price).toFixed(2)}`
            ).join('\n');
            
            const total = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0).toFixed(2);

            document.getElementById('orderItems').value = orderSummary;
            document.getElementById('orderTotal').value = `$${total}`;

            // Clear cart after preparing for submission
            cart = [];
            updateCartCount();
            saveCartToStorage();
        }
        
        // --- MODIFICATION START: Review System Logic ---
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
                reviewEl.innerHTML = `
                    <div class="review-author">${review.name}</div>
                    <div class="review-content">${review.content}</div>
                `;
                container.appendChild(reviewEl);
            });
        }

        function saveGeneralReview() {
            const name = document.getElementById('reviewerName').value;
            const content = document.getElementById('reviewContent').value;
            
            generalReviews.push({ name, content });
            saveGeneralReviewsToStorage();
            renderGeneralReviews();
            
            // Submit the form programmatically after saving locally
            document.getElementById('generalReviewForm').submit();
            document.getElementById('generalReviewForm').reset();
            showToast('Thank you for your review!');
        }

        function showProductReviews(productId) {
            const product = products.find(p => p.id === productId);
            if (!product) return;

            document.getElementById('reviewModalTitle').textContent = `Reviews for ${product.name}`;
            const container = document.getElementById('productReviewsList');
            container.innerHTML = '';
            if (product.reviews.length === 0) {
                container.innerHTML = '<p>No reviews for this product yet.</p>';
            } else {
                product.reviews.forEach(review => {
                    const reviewEl = document.createElement('div');
                    reviewEl.className = 'review';
                    reviewEl.innerHTML = `
                        <div class="review-author">${review.name}</div>
                        <div class="review-content">${review.content}</div>
                    `;
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
            
            document.getElementById('productReviewForm').submit();
            document.getElementById('productReviewForm').reset();
            closeModal('reviewModal');
            showToast('Thank you for your review!');
        }
        // --- MODIFICATION END: Review System Logic ---


        // --- ADMIN FUNCTIONALITY ---
        function handleCrownClick() {
            clickCount++;
            clearTimeout(clickTimeout);
            clickTimeout = setTimeout(() => { clickCount = 0; }, 1000); // Reset clicks after 1 second of inactivity
            if (clickCount >= 7) { // Set back to 7 clicks
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
            } else if (password !== null && password !== "") {
                alert('Incorrect password!');
            }
        }

        function renderAdminProducts() {
            const container = document.getElementById('adminProductsList');
            container.innerHTML = '';
            
            if (products.length === 0) {
                container.innerHTML = '<p>No products found</p>';
                return;
            }
            
            // Display newest products first
            products.slice().reverse().forEach(product => {
                const productElement = document.createElement('div');
                productElement.className = 'product-card';
                productElement.innerHTML = `
                    <img src="${product.images[0]}" alt="${product.name}" class="product-image"> <div class="product-info">
                        <h3 class="product-title">${product.name}</h3>
                        <p style="font-size:0.9em; color:#666; text-transform: capitalize;">${product.category}</p>
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
            const name = document.getElementById('productName').value;
            const category = document.getElementById('productCategory').value;
            const price = parseFloat(document.getElementById('productPrice').value);
            const description = document.getElementById('productDescription').value;
            // MODIFICATION START: Get multiple images
            const images = document.getElementById('productImageURLs').value.split('\n').map(url => url.trim()).filter(url => url);
            // MODIFICATION END: Get multiple images
            
            if (!name || !category || isNaN(price) || !description || images.length === 0) {
                alert('Please fill all fields and provide at least one image URL.');
                return;
            }

            if (id) { // Editing existing product
                const index = products.findIndex(p => p.id == id);
                if (index > -1) {
                    // Preserve reviews when editing
                    products[index] = { ...products[index], name, category, price, description, images };
                }
            } else { // Adding new product
                 const newProduct = {
                    id: Date.now(), // Use timestamp for a unique ID
                    name, category, price, description, images,
                    reviews: [] // New products start with no reviews
                };
                products.push(newProduct);
            }
            
            saveProductsToStorage();
            renderProducts();
            renderAdminProducts();
            
            document.getElementById('productForm').reset();
            document.getElementById('productId').value = '';
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
            // MODIFICATION START: Populate multiple image URLs
            document.getElementById('productImageURLs').value = product.images.join('\n');
            // MODIFICATION END: Populate multiple image URLs
            
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

        // Simplified, as image uploads are no longer needed on the product form.
        // This function is now only used for the logo upload.
        function setupImageUpload(inputId, previewId, urlInputId, areaSelector, customHandler) {
            const fileInput = document.getElementById(inputId);
            const uploadArea = document.querySelector(areaSelector);

            fileInput.addEventListener('change', customHandler);
            uploadArea.addEventListener('click', () => fileInput.click());
            
            ['dragover', 'drop', 'dragleave'].forEach(eventName => {
                uploadArea.addEventListener(eventName, (e) => {
                    e.preventDefault();
                    e.stopPropagation();
                    if (eventName === 'dragover') uploadArea.style.borderColor = '#1a365d';
                    else uploadArea.style.borderColor = '#ddd';
                    if (eventName === 'drop' && e.dataTransfer.files.length) {
                        fileInput.files = e.dataTransfer.files;
                        customHandler({ target: fileInput });
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
                // MODIFICATION START: Update all logo instances
                document.getElementById('logoPreview').src = logoUrl;
                document.getElementById('logoPreview').style.display = 'block';
                document.getElementById('companyLogo').src = logoUrl;
                document.getElementById('storeLogo').src = logoUrl;
                document.getElementById('storeLogo').style.display = 'block';
                document.getElementById('logoText').style.display = 'none';
                localStorage.setItem('companyLogo', logoUrl); // Persist logo
                // MODIFICATION END: Update all logo instances
            };
            reader.readAsDataURL(file);
        }

    </script>
</body>
</html>
