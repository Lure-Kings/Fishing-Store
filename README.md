<!DOCTYPE html>
<html lang="en">
<head>
    <!-- Existing meta tags and styles -->
    <style>
        /* Existing CSS */
        
        /* New styles for payment section */
        .payment-methods {
            margin-bottom: 2rem;
        }

        .payment-option {
            margin-bottom: 1rem;
            padding: 1rem;
            border: 1px solid #ddd;
            border-radius: 4px;
            cursor: pointer;
            transition: all 0.2s ease;
        }

        .payment-option:hover {
            border-color: #1a365d;
            background-color: #f9f9f9;
        }

        .payment-details {
            margin-top: 1rem;
            padding: 1rem;
            border: 1px solid #ddd;
            border-radius: 4px;
            display: none;
        }

        .bank-details {
            margin-bottom: 1rem;
        }

        .payment-buttons {
            display: flex;
            gap: 1rem;
            justify-content: flex-end;
        }
    </style>
</head>
<body>
    <!-- Existing header and navigation -->
    
    <!-- Checkout Modal with enhanced payment options -->
    <div id="checkoutModal" class="modal">
        <div class="modal-content">
            <span class="close" onclick="closeCheckout()">&times;</span>
            <h2 style="margin-bottom: 1rem; color: #1a365d;">
                Secure Checkout
            </h2>

            <!-- Payment Methods Selection -->
            <div class="payment-methods">
                <button class="payment-option" onclick="selectPaymentMethod('bank')">Bank Transfer</button>
                <button class="payment-option" onclick="selectPaymentMethod('stripe')">Stripe Payment</button>
                <button class="payment-option" onclick="selectPaymentMethod('paypal')">PayPal</button>
            </div>

            <!-- Bank Transfer Details -->
            <form id="bankForm">
                <div class="payment-details bank-details">
                    <h4>Bank Transfer Details</h4>
                    <div class="form-group">
                        <label for="bsb">BSB Number:</label>
                        <input type="text" id="bsb" name="bsb" required pattern="[0-9]{3}-[0-9]{3}" maxlength="7">
                        <span class="error-message">Format: XXX-XXX</span>
                    </div>
                    <div class="form-group">
                        <label for="accountNumber">Account Number:</label>
                        <input type="text" id="accountNumber" name="accountNumber" required pattern="[0-9]{6,10}">
                        <span class="error-message">Must be 6-10 digits</span>
                    </div>
                </div>
            </form>

            <!-- Customer Information -->
            <form id="customerForm">
                <input type="hidden" name="_subject" value="New Order from Lure Kings">
                <input type="hidden" name="_template" value="table">
                <input type="hidden" name="_next" value="thank-you.html">
                <input type="hidden" name="_cc" value="lure.kings.fishing.aus@gmail.com">
                <input type="hidden" name="_autoresponse" value="Thank you for your order! We'll process it shortly.">

                <div class="form-group">
                    <label for="customerName">Full Name:</label>
                    <input type="text" id="customerName" name="name" required>
                    <span class="error-message">Required field</span>
                </div>

                <div class="form-group">
                    <label for="customerEmail">Email Address:</label>
                    <input type="email" id="customerEmail" name="email" required>
                    <span class="error-message">Valid email required</span>
                </div>

                <div class="form-group">
                    <label for="customerPhone">Phone Number:</label>
                    <input type="tel" id="customerPhone" name="phone" required pattern="[0-9]{10}" maxlength="10">
                    <span class="error-message">Must be 10 digits</span>
                </div>

                <div class="form-group">
                    <label for="customerAddress">Delivery Address:</label>
                    <textarea id="customerAddress" name="address" rows="3" required></textarea>
                    <span class="error-message">Required field</span>
                </div>

                <!-- Order Summary -->
                <div class="cart-total" id="checkoutTotal">Total: $0.00</div>
            </form>

            <!-- Payment Buttons -->
            <div class="payment-buttons">
                <button type="button" onclick="showCart()" class="btn btn-secondary">Back to Cart</button>
                <button type="submit" form="bankForm" class="btn btn-primary">Complete Payment</button>
            </div>
        </div>
    </div>

    <!-- Thank You Page -->
    <div id="thankYouPage" class="modal hidden">
        <div class="modal-content">
            <h2 style="color: #1a365d;">Thank You!</h2>
            <p>Your order has been successfully placed.</p>
            <p>An order confirmation has been sent to your email.</p>
            <button onclick="returnToStore()" class="btn btn-primary">Return to Store</button>
        </div>
    </div>

    <script>
        // Updated constants
        const ADMIN_PASSWORD = "Maxchingershambo08";
        
        // Initialize products from localStorage
        let products = JSON.parse(localStorage.getItem('products')) || [
            {
                id: 1,
                name: "Bass Pro Jig Head",
                category: "jigs",
                price: 12.99,
                description: "Premium jig head perfect for bass fishing with realistic action.",
                image: "https://images.unsplash.com/photo-1544551763-46a013bb70d5?w=400&h=300&fit=crop"
            },
            // ... existing products ...
        ];

        // Enhanced cart functionality
        let cart = JSON.parse(localStorage.getItem('cart')) || [];

        // Initialize the app
        document.addEventListener('DOMContentLoaded', function() {
            init();
            
            // Load saved state
            cart = JSON.parse(localStorage.getItem('cart')) || [];
            updateCartCount();
            
            // Set up payment method selection
            const paymentButtons = document.querySelectorAll('.payment-option');
            paymentButtons.forEach(button => {
                button.addEventListener('click', () => {
                    selectPaymentMethod(button.textContent.toLowerCase().replace(/\s/g, ''));
                });
            });

            // Form validation setup
            setupFormValidation();
        });

        // Enhanced initialization
        function init() {
            renderProducts();
            updateCartCount();
            renderAdminProducts();
            setupEventListeners();
            setupImageUpload();
            setupLogoUpload();
            
            document.getElementById('logo').addEventListener('click', handleCrownClick);
            
            const savedLogo = localStorage.getItem('companyLogo');
            if (savedLogo) {
                document.getElementById('companyLogo').src = savedLogo;
                document.getElementById('logoPreview').src = savedLogo;
                document.getElementById('logoPreview').style.display = 'block';
            }
        }

        // Payment method selection
        function selectPaymentMethod(method) {
            const details = document.querySelector(`.${method}-details`);
            document.querySelectorAll('.payment-details').forEach(detail => {
                detail.style.display = 'none';
            });
            if (details) {
                details.style.display = 'block';
            }
        }

        // Form validation setup
        function setupFormValidation() {
            const phoneInput = document.getElementById('customerPhone');
            phoneInput.addEventListener('keypress', function(e) {
                return /[0-9]/.test(e.key);
            });

            const forms = document.querySelectorAll('#bankForm, #customerForm');
            forms.forEach(form => {
                form.addEventListener('submit', function(e) {
                    if (!validateForm(this)) {
                        e.preventDefault();
                        return false;
                    }
                    
                    processPayment(e);
                    return true;
                });
            });
        }

        // Form validation
        function validateForm(form) {
            let isValid = true;
            
            // Validate required fields
            const requiredFields = form.querySelectorAll('[required]');
            requiredFields.forEach(field => {
                if (!field.value.trim()) {
                    isValid = false;
                    showError(field);
                } else {
                    hideError(field);
                }
            });

            // Validate email
            const emailField = form.querySelector('[type="email"]');
            if (emailField && !validateEmail(emailField.value)) {
                isValid = false;
                showError(emailField);
            }

            // Validate phone number
            const phoneField = form.querySelector('[name="phone"]');
            if (phoneField && !validatePhoneNumber(phoneField.value)) {
                isValid = false;
                showError(phoneField);
            }

            return isValid;
        }

        // Helper functions
        function validateEmail(email) {
            return /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email);
        }

        function validatePhoneNumber(phone) {
            return /^\d{10}$/.test(phone);
        }

        function showError(field) {
            field.classList.add('error');
            const errorMessage = field.nextElementSibling;
            if (errorMessage) {
                errorMessage.style.display = 'block';
            }
        }

        function hideError(field) {
            field.classList.remove('error');
            const errorMessage = field.nextElementSibling;
            if (errorMessage) {
                errorMessage.style.display = 'none';
            }
        }

        // Enhanced cart management
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
            localStorage.setItem('cart', JSON.stringify(cart));
        }

        // Save products permanently
        function saveProducts() {
            localStorage.setItem('products', JSON.stringify(products));
        }

        // Enhanced admin functionality
        function addProduct() {
            const name = document.getElementById('productName').value;
            const category = document.getElementById('productCategory').value;
            const price = parseFloat(document.getElementById('productPrice').value);
            const description = document.getElementById('productDescription').value;
            let image = document.getElementById('productImage').value;

            // Use uploaded image if available
            const uploadedImage = document.getElementById('imagePreview').src;
            if (uploadedImage && !uploadedImage.includes('data:')) {
                image = uploadedImage;
            }

            if (!name || !category || isNaN(price) || !description || !image) {
                alert('Please fill all fields');
                return;
            }

            const newProduct = {
                id: products.length > 0 ? Math.max(...products.map(p => p.id)) + 1 : 1,
                name,
                category,
                price,
                description,
                image
            };

            products.push(newProduct);
            saveProducts(); // Save permanently
            renderProducts();
            renderAdminProducts();

            document.getElementById('productForm').reset();
            document.getElementById('imagePreview').style.display = 'none';
            alert('Product added successfully!');
        }

        // Payment processing
        async function processPayment(event) {
            event.preventDefault();
            
            const paymentMethod = document.querySelector('.payment-details:visible').className.split('-')[0];
            const customerInfo = {
                name: document.getElementById('customerName').value,
                email: document.getElementById('customerEmail').value,
                phone: document.getElementById('customerPhone').value,
                address: document.getElementById('customerAddress').value
            };

            // Simulate payment processing
            await simulatePaymentProcessing(paymentMethod);

            // Clear cart and show thank you page
            cart = [];
            localStorage.setItem('cart', JSON.stringify(cart));
            updateCartCount();
            
            document.getElementById('checkoutModal').style.display = 'none';
            document.getElementById('thankYouPage').classList.remove('hidden');
        }

        // Simulated payment processing
        async function simulatePaymentProcessing(method) {
            return new Promise(resolve => {
                setTimeout(() => {
                    resolve(true);
                    alert(`Payment processed successfully via ${method}`);
                }, 1500);
            });
        }

        // Return to store
        function returnToStore() {
            document.getElementById('thankYouPage').classList.add('hidden');
            location.reload();
        }
    </script>
</body>
</html>
