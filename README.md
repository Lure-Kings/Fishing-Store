# Fishing-Store
// Global variables
let isAdminLoggedIn = false;
const ADMIN_PASSWORD = "lureking2024";
let products = [
    {
        id: 1,
        name: "Bass Pro Jig Head",
        category: "jigs",
        price: 12.99,
        description: "Premium jig head perfect for bass fishing with realistic action.",
        image: "https://images.unsplash.com/photo-1544551763-46a013bb70d5?w=400&h=300&fit=crop"
    },
    // ... (your other products)
];
let cart = [];
let currentFilter = 'all';

// Initialize the app when DOM is loaded
document.addEventListener('DOMContentLoaded', function() {
    init();
});

function init() {
    renderProducts();
    updateCartCount();
    renderAdminProducts();
    updateNavigation();
    checkAdminAccess();
    setupImageUpload();
    setupEventListeners();
}

// Setup all event listeners
function setupEventListeners() {
    // Admin form submission
    document.getElementById('productForm').addEventListener('submit', function(e) {
        e.preventDefault();
        addProduct();
    });

    // Checkout form submission
    document.getElementById('checkoutForm').addEventListener('submit', function(e) {
        e.preventDefault();
        processCheckout();
    });

    // Admin login form submission
    document.getElementById('adminLoginForm').addEventListener('submit', function(e) {
        e.preventDefault();
        const password = document.getElementById('adminPassword').value;
        if (password === ADMIN_PASSWORD) {
            isAdminLoggedIn = true;
            closeAdminLogin();
            showView('admin');
            document.getElementById('adminPassword').value = '';
        } else {
            alert('Incorrect password!');
        }
    });

    // Image upload handling
    document.getElementById('imageUpload').addEventListener('change', function(e) {
        handleImageUpload(e);
    });
}

// View management
function showView(view) {
    if (view === 'admin' && !isAdminLoggedIn) {
        showAdminLogin();
        return;
    }
    
    document.getElementById('storeView').classList.toggle('hidden', view !== 'store');
    document.getElementById('adminView').classList.toggle('hidden', view !== 'admin');
    updateNavigation();
}

function updateNavigation() {
    // Update active state of navigation buttons
}

// Product rendering
function renderProducts() {
    const grid = document.getElementById('productsGrid');
    grid.innerHTML = '';
    
    const filteredProducts = currentFilter === 'all' 
        ? products 
        : products.filter(p => p.category === currentFilter);
    
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
    
    // Update active state of category buttons
    document.querySelectorAll('.category-btn').forEach(btn => {
        btn.classList.toggle('active', btn.textContent.toLowerCase().includes(category));
    });
}

// Cart functionality
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
    showCartNotification(product.name);
}

function updateCartCount() {
    const count = cart.reduce((total, item) => total + item.quantity, 0);
    document.getElementById('cartCount').textContent = count;
}

function showCartNotification(productName) {
    // Could implement a toast notification here
    console.log(`${productName} added to cart`);
}

function showCart() {
    const modal = document.getElementById('cartModal');
    const cartItems = document.getElementById('cartItems');
    const cartTotal = document.getElementById('cartTotal');
    
    cartItems.innerHTML = '';
    
    if (cart.length === 0) {
        cartItems.innerHTML = '<p>Your cart is empty</p>';
        cartTotal.textContent = 'Total: $0.00';
    } else {
        let total = 0;
        
        cart.forEach(item => {
            const itemTotal = item.price * item.quantity;
            total += itemTotal;
            
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
                    <div>$${itemTotal.toFixed(2)}</div>
                </div>
                <button class="remove-item" onclick="removeFromCart(${item.id})">Remove</button>
            `;
            cartItems.appendChild(cartItem);
        });
        
        cartTotal.textContent = `Total: $${total.toFixed(2)}`;
        document.getElementById('checkoutTotal').textContent = `Total: $${total.toFixed(2)}`;
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
        updateCartCount();
        showCart(); // Refresh cart display
    }
}

function removeFromCart(productId) {
    cart = cart.filter(item => item.id !== productId);
    updateCartCount();
    showCart(); // Refresh cart display
}

// Checkout functionality
function showCheckout() {
    closeCart();
    document.getElementById('checkoutModal').style.display = 'block';
}

function closeCheckout() {
    document.getElementById('checkoutModal').style.display = 'none';
}

function processCheckout() {
    const name = document.getElementById('customerName').value;
    const email = document.getElementById('customerEmail').value;
    
    if (cart.length === 0) {
        alert('Your cart is empty!');
        return;
    }
    
    // Generate order number
    const orderNumber = 'LK-' + Date.now().toString().slice(-6);
    
    // In a real app, you would send this data to your server
    const order = {
        orderNumber,
        customer: { name, email },
        items: cart,
        total: cart.reduce((sum, item) => sum + (item.price * item.quantity), 0),
        date: new Date().toISOString()
    };
    
    console.log('Order placed:', order);
    alert(`Order #${orderNumber} placed successfully!\nA confirmation has been sent to ${email}`);
    
    // Reset cart and close modals
    cart = [];
    updateCartCount();
    closeCheckout();
    document.getElementById('checkoutForm').reset();
}

// Admin functionality
function showAdminLogin() {
    document.getElementById('adminLoginModal').style.display = 'block';
}

function closeAdminLogin() {
    document.getElementById('adminLoginModal').style.display = 'none';
}

function checkAdminAccess() {
    if (window.location.hash === '#admin') {
        showAdminLogin();
    }
}

function renderAdminProducts() {
    const container = document.getElementById('adminProductsList');
    container.innerHTML = '';
    
    if (products.length === 0) {
        container.innerHTML = '<p>No products found</p>';
        return;
    }
    
    products.forEach(product => {
        const productElement = document.createElement('div');
        productElement.className = 'product-card';
        productElement.innerHTML = `
            <div class="product-info">
                <h3 class="product-title">${product.name}</h3>
                <p>Category: ${product.category}</p>
                <p>Price: $${product.price.toFixed(2)}</p>
                <p>${product.description}</p>
                <button onclick="editProduct(${product.id})" class="btn btn-secondary">Edit</button>
                <button onclick="deleteProduct(${product.id})" class="btn btn-secondary" style="background: #ef4444;">Delete</button>
            </div>
        `;
        container.appendChild(productElement);
    });
}

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
    renderProducts();
    renderAdminProducts();
    
    // Reset form
    document.getElementById('productForm').reset();
    document.getElementById('imagePreview').style.display = 'none';
    alert('Product added successfully!');
}

function editProduct(id) {
    const product = products.find(p => p.id === id);
    if (!product) return;
    
    // Fill the form with product data
    document.getElementById('productName').value = product.name;
    document.getElementById('productCategory').value = product.category;
    document.getElementById('productPrice').value = product.price;
    document.getElementById('productDescription').value = product.description;
    document.getElementById('productImage').value = product.image;
    
    // Show image preview if exists
    if (product.image) {
        const preview = document.getElementById('imagePreview');
        preview.src = product.image;
        preview.style.display = 'block';
    }
    
    // Remove the product (will be re-added when form is submitted)
    products = products.filter(p => p.id !== id);
    
    // Scroll to form
    document.getElementById('productForm').scrollIntoView();
}

function deleteProduct(id) {
    if (!confirm('Are you sure you want to delete this product?')) return;
    
    products = products.filter(p => p.id !== id);
    renderProducts();
    renderAdminProducts();
}

// Image upload handling
function setupImageUpload() {
    const uploadArea = document.querySelector('.file-upload-area');
    const fileInput = document.getElementById('imageUpload');
    const preview = document.getElementById('imagePreview');
    
    uploadArea.addEventListener('dragover', (e) => {
        e.preventDefault();
        uploadArea.classList.add('dragover');
    });
    
    uploadArea.addEventListener('dragleave', () => {
        uploadArea.classList.remove('dragover');
    });
    
    uploadArea.addEventListener('drop', (e) => {
        e.preventDefault();
        uploadArea.classList.remove('dragover');
        
        if (e.dataTransfer.files.length) {
            fileInput.files = e.dataTransfer.files;
            handleImageUpload({ target: fileInput });
        }
    });
}

function handleImageUpload(event) {
    const file = event.target.files[0];
    if (!file) return;
    
    if (!file.type.match('image.*')) {
        alert('Please select an image file');
        return;
    }
    
    const reader = new FileReader();
    reader.onload = function(e) {
        const preview = document.getElementById('imagePreview');
        preview.src = e.target.result;
        preview.style.display = 'block';
        
        // Also set the image URL field
        document.getElementById('productImage').value = e.target.result;
    };
    reader.readAsDataURL(file);
}

// Initialize the app
init();
