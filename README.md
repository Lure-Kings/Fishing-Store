<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lure Kings - Premium Fishing Gear</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; background-color: #f5f5f5; color: #333; line-height: 1.6; }
        .header { background-color: #1a365d; padding: 1rem 2rem; position: sticky; top: 0; z-index: 1000; box-shadow: 0 2px 5px rgba(0,0,0,0.1); }
        .nav { display: flex; justify-content: space-between; align-items: center; max-width: 1200px; margin: 0 auto; }
        .logo { display: flex; align-items: center; gap: 1rem; cursor: pointer; color: white; text-decoration: none; }
        .logo #storeLogo { max-height: 50px; width: auto; display: none; }
        .logo .logo-text-container { display: flex; align-items: center; font-size: 2rem; font-weight: bold; gap: 0.5rem; }
        .logo .logo-text-container i { font-size: 1.8rem; color: #f8d56b; }
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
        .product-card { background: white; border: 1px solid #ddd; border-radius: 8px; overflow: hidden; box-shadow: 0 2px 5px rgba(0,0,0,0.1); transition: all 0.2s ease; display: flex; flex-direction: column; }
        .product-card:hover { transform: translateY(-5px); box-shadow: 0 5px 15px rgba(0,0,0,0.1); }
        .product-image-container { display: flex; overflow-x: auto; scroll-snap-type: x mandatory; height: 220px; border-bottom: 1px solid #ddd; }
        .product-image { width: 100%; height: 100%; object-fit: cover; flex: 0 0 100%; scroll-snap-align: start; }
        .product-info { padding: 1rem; display: flex; flex-direction: column; flex-grow: 1; }
        .product-title { font-size: 1.1rem; font-weight: bold; margin-bottom: 0.5rem; color: #1a365d; }
        .product-price { font-size: 1.2rem; font-weight: bold; color: #e74c3c; margin-bottom: 1rem; }
        .product-description { color: #666; margin-bottom: 1rem; font-size: 0.9rem; flex-grow: 1; }
        .product-buttons { display: flex; gap: 0.5rem; margin-top: auto; }
        .add-to-cart, .reviews-btn { width: 100%; background-color: #1a365d; color: white; border: none; padding: 0.5rem; border-radius: 4px; cursor: pointer; font-weight: 600; transition: all 0.2s ease; }
        .add-to-cart:hover, .reviews-btn:hover { background-color: #142a4a; }
        .reviews-btn { background-color: #555; }
        .reviews-btn:hover { background-color: #333; }
        .modal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0, 0, 0, 0.5); z-index: 2000; justify-content: center; align-items: center; }
        .modal-content { position: relative; background: white; border-radius: 8px; padding: 2rem; max-width: 90%; width: 600px; max-height: 90%; overflow-y: auto; box-shadow: 0 5px 15px rgba(0,0,0,0.2); color: #333; }
        .close { position: absolute; top: 1rem; right: 1rem; font-size: 1.5rem; cursor: pointer; color: #666; }
        .close:hover { color: #333; }
        .review-section { margin-top: 2rem; background: white; padding: 1.5rem; border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.1); }
        .review { border-bottom: 1px solid #eee; padding: 1rem 0; }
        .review-author { font-weight: bold; color: #1a365d; }
        .review-content { margin-top: 0.5rem; }
        .hidden { display: none !important; }
        .admin-form, .checkout-form { background: white; border: 1px solid #ddd; padding: 1.5rem; border-radius: 8px; margin-bottom: 2rem; }
        .form-group { margin-bottom: 1rem; }
        .form-group label { display: block; margin-bottom: 0.5rem; font-weight: 600; color: #1a365d; }
        .form-group input, .form-group textarea, .form-group select { width: 100%; padding: 0.5rem; border: 1px solid #ddd; border-radius: 4px; font-size: 1rem; }
        .toast { position: fixed; bottom: 20px; right: 20px; background: #1a365d; color: white; padding: 1rem; border-radius: 4px; box-shadow: 0 2px 10px rgba(0,0,0,0.2); z-index: 3000; opacity: 0; visibility: hidden; transition: opacity 0.3s, visibility 0.3s; }
        .toast.show { opacity: 1; visibility: visible; }
        
        /* --- MODIFICATION: Star Rating Styles --- */
        .star-rating { margin-bottom: 1rem; }
        .star-rating .fa-star {
            font-size: 1.5rem;
            color: #ccc;
            cursor: pointer;
            transition: color 0.2s;
        }
        .star-rating .fa-star.selected,
        .star-rating .fa-star.hovered {
            color: #f8d56b;
        }

        @media (max-width: 768px) {
            .nav { flex-direction: column; gap: 1rem; }
            .products-grid { grid-template-columns: 1fr; }
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
                    <span>Lure Kings</span>
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

    <div class="toast" id="toast"></div>

    <div class="container">
        <div id="storeView">
            <div class="hero">
                <h1>Premium fishing gear</h1>
                <p>High-quality fishing lures for the best prices</p>
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
                <div id="generalReviewsList"></div>
                <div class="admin-form" style="margin-top: 2rem;">
                    <h3 style="margin-bottom: 1rem; color: #1a365d;">Leave a Website Review</h3>
                    <form id="generalReviewForm" action="https://formsubmit.co/lure.kings.fishing.aus@gmail.com" method="POST">
                        <input type="hidden" name="_subject" value="New Lure Kings Website Review!">
                        <input type="hidden" name="_template" value="table">
                        <input type="hidden" name="_next" value="https://lure-kings.github.io/Fishing-Store/">
                        
                        <div class="form-group">
                            <label>Rating</label>
                            <div class="star-rating" id="generalStarRating">
                                <i class="fa-solid fa-star" data-value="1"></i>
                                <i class="fa-solid fa-star" data-value="2"></i>
                                <i class="fa-solid fa-star" data-value="3"></i>
                                <i class="fa-solid fa-star" data-value="4"></i>
                                <i class="fa-solid fa-star" data-value="5"></i>
                            </div>
                            <input type="hidden" name="Rating" id="generalRatingValue" required>
                        </div>
                        
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
                    <input type="hidden" name="_next" value="https://lure-kings.github.io/Fishing-Store/">

                    <div class="form-group">
                        <label>Rating</label>
                        <div class="star-rating" id="productStarRating">
                            <i class="fa-solid fa-star" data-value="1"></i>
                            <i class="fa-solid fa-star" data-value="2"></i>
                            <i class="fa-solid fa-star" data-value="3"></i>
                            <i class="fa-solid fa-star" data-value="4"></i>
                            <i class="fa-solid fa-star" data-value="5"></i>
                        </div>
                        <input type="hidden" name="Rating" id="productRatingValue" required>
                    </div>

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
        let generalReviews = [];
        let currentFilter = 'all';
        const defaultProducts = [];

        // --- APP INITIALIZATION ---
        document.addEventListener('DOMContentLoaded', () => init());

        function init() {
            products = JSON.parse(localStorage.getItem('products')) || defaultProducts;
            cart = JSON.parse(localStorage.getItem('cart')) || [];
            generalReviews = JSON.parse(localStorage.getItem('generalReviews')) || [];

            const savedLogo = localStorage.getItem('companyLogo');
            if (savedLogo) {
                updateLogo(savedLogo);
            }
            
            renderProducts();
            updateCartCount();
            renderAdminProducts(); // Assuming admin view HTML exists
            renderGeneralReviews();
            
            setupEventListeners();
            // MODIFICATION: Setup star rating for both forms
            setupStarRating('generalReviewForm');
            setupStarRating('productReviewForm');
        }

        // --- EVENT LISTENERS ---
        function setupEventListeners() {
            document.getElementById('logo').addEventListener('click', handleCrownClick);
            
            document.getElementById('generalReviewForm').addEventListener('submit', (e) => {
                const rating = document.getElementById('generalRatingValue').value;
                if (!rating) {
                    e.preventDefault();
                    alert('Please select a star rating.');
                    return;
                }
                saveGeneralReview(); 
            });

            document.getElementById('productReviewForm').addEventListener('submit', (e) => {
                const rating = document.getElementById('productRatingValue').value;
                if (!rating) {
                    e.preventDefault();
                    alert('Please select a star rating.');
                    return;
                }
                saveProductReview();
            });
            // Other event listeners (product form, checkout) would go here
        }

        // --- MODIFICATION: Star Rating Logic ---
        function setupStarRating(formId) {
            const form = document.getElementById(formId);
            const stars = form.querySelectorAll('.star-rating .fa-star');
            const ratingValueInput = form.querySelector('input[type="hidden"]');

            stars.forEach(star => {
                star.addEventListener('click', () => {
                    const rating = star.dataset.value;
                    ratingValueInput.value = rating;
                    updateStarSelection(stars, rating);
                });

                star.addEventListener('mouseover', () => {
                    updateStarHover(stars, star.dataset.value);
                });

                star.addEventListener('mouseout', () => {
                    const currentRating = ratingValueInput.value || 0;
                    updateStarSelection(stars, currentRating);
                });
            });
        }
        
        function updateStarSelection(stars, rating) {
            stars.forEach(s => {
                s.classList.toggle('selected', s.dataset.value <= rating);
                s.classList.remove('hovered');
            });
        }

        function updateStarHover(stars, rating) {
            stars.forEach(s => {
                s.classList.toggle('hovered', s.dataset.value <= rating);
            });
        }

        // --- DATA PERSISTENCE ---
        const saveProductsToStorage = () => localStorage.setItem('products', JSON.stringify(products));
        const saveCartToStorage = () => localStorage.setItem('cart', JSON.stringify(cart));
        const saveGeneralReviewsToStorage = () => localStorage.setItem('generalReviews', JSON.stringify(generalReviews));

        // --- VIEW MANAGEMENT & RENDERING ---
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
                grid.innerHTML = `<p style="text-align:center; grid-column: 1 / -1;">No products found. Log in to the admin panel to add some!</p>`;
                return;
            }

            filteredProducts.forEach(product => {
                const card = document.createElement('div');
                card.className = 'product-card';
                const avgRating = product.reviews && product.reviews.length > 0
                    ? (product.reviews.reduce((sum, r) => sum + parseInt(r.rating || 0), 0) / product.reviews.length).toFixed(1)
                    : 'No reviews';
                
                card.innerHTML = `
                    <div class="product-image-container">
                        ${product.images.map(imgSrc => `<img src="${imgSrc}" alt="${product.name}" class="product-image">`).join('')}
                    </div>
                    <div class="product-info">
                        <h3 class="product-title">${product.name}</h3>
                        <div class="product-price">$${product.price.toFixed(2)}</div>
                        <p class="product-description">${product.description}</p>
                        <div style="color: #f8d56b; margin-bottom: 1rem;"><i class="fa-solid fa-star"></i> ${avgRating}</div>
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
            const btnToActivate = Array.from(document.querySelectorAll('.category-btn')).find(btn => btn.getAttribute('onclick').includes(`'${category}'`));
            if(btnToActivate) btnToActivate.classList.add('active');
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
                // Display stars based on saved rating
                let starsHTML = '';
                for (let i = 1; i <= 5; i++) {
                    starsHTML += `<i class="fa-solid fa-star ${i <= review.rating ? 'selected' : ''}" style="font-size:1rem;"></i>`;
                }
                reviewEl.innerHTML = `
                    <div class="review-author">${review.name}</div>
                    <div class="review-rating">${starsHTML}</div>
                    <div class="review-content">${review.content}</div>
                `;
                container.appendChild(reviewEl);
            });
        }

        function saveGeneralReview() {
            generalReviews.push({
                name: document.getElementById('reviewerName').value,
                content: document.getElementById('reviewContent').value,
                rating: document.getElementById('generalRatingValue').value
            });
            saveGeneralReviewsToStorage();
            renderGeneralReviews();
            document.getElementById('generalReviewForm').reset();
            updateStarSelection(document.querySelectorAll('#generalStarRating .fa-star'), 0); // Reset stars
            showToast('Thank you for your review!');
        }
        
        function showProductReviews(productId) {
            const product = products.find(p => p.id === productId);
            const modal = document.getElementById('reviewModal');
            document.getElementById('reviewModalTitle').textContent = `Reviews for ${product.name}`;
            const container = document.getElementById('productReviewsList');
            container.innerHTML = '';
            
            if (!product.reviews || product.reviews.length === 0) {
                container.innerHTML = '<p>No reviews for this product yet.</p>';
            } else {
                product.reviews.forEach(review => {
                    const reviewEl = document.createElement('div');
                    reviewEl.className = 'review';
                    let starsHTML = '';
                    for (let i = 1; i <= 5; i++) {
                        starsHTML += `<i class="fa-solid fa-star ${i <= review.rating ? 'selected' : ''}" style="font-size:1rem;"></i>`;
                    }
                    reviewEl.innerHTML = `
                        <div class="review-author">${review.name}</div>
                        <div class="review-rating">${starsHTML}</div>
                        <div class="review-content">${review.content}</div>
                    `;
                    container.appendChild(reviewEl);
                });
            }

            document.getElementById('reviewProductId').value = product.id;
            document.getElementById('reviewProductName').value = product.name;
            modal.style.display = 'flex';
        }

        function saveProductReview() {
            const productId = parseInt(document.getElementById('reviewProductId').value);
            const product = products.find(p => p.id === productId);
            if(product) {
                if (!product.reviews) product.reviews = [];
                product.reviews.push({
                    name: document.getElementById('productReviewerName').value,
                    content: document.getElementById('productReviewContent').value,
                    rating: document.getElementById('productRatingValue').value
                });
                saveProductsToStorage();
                renderProducts();
            }
            document.getElementById('productReviewForm').reset();
            updateStarSelection(document.querySelectorAll('#productStarRating .fa-star'), 0);
            closeModal('reviewModal');
            showToast('Thank you for your review!');
        }

        // --- ADMIN FUNCTIONALITY ---
        function handleCrownClick() {
            clickCount++;
            clearTimeout(clickTimeout);
            clickTimeout = setTimeout(() => { clickCount = 0; }, 1500);
            if (clickCount >= 7) {
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
        
        // --- UTILITY & LOGO FUNCTIONS ---
        const updateCartCount = () => {
            document.getElementById('cartCount').textContent = cart.reduce((total, item) => total + item.quantity, 0);
        };
        const showToast = (message) => {
            const toast = document.getElementById('toast');
            toast.textContent = message;
            toast.classList.add('show');
            setTimeout(() => toast.classList.remove('show'), 3000);
        };
        
        function updateLogo(logoUrl) {
            const storeLogo = document.getElementById('storeLogo');
            storeLogo.src = logoUrl;
            storeLogo.style.display = 'block';
            // MODIFICATION: No longer hiding the text when a logo is present
            // document.getElementById('logoText').style.display = 'none'; 
        }

        // Dummy/Placeholder functions for parts of the app not included in the snippet
        function renderAdminProducts() { /* Logic to render product list in admin view */ }
        function addToCart(id) { showToast('Added to cart!'); /* In a real app, this would modify the cart array */ }

    </script>
</body>
</html>
