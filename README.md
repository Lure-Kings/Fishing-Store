<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lure Kings - Premium Fishing Lures</title>
    <script src="https://cdn.jsdelivr.net/npm/react@18.2.0/umd/react.production.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/react-dom@18.2.0/umd/react-dom.production.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/@babel/standalone@7.20.6/babel.min.js"></script>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
</head>
<body>
    <div id="root"></div>
    <script type="text/babel">
        const { useState, useEffect } = React;

        // Sample products
        const initialProducts = [
            {
                id: 1,
                name: "Bass Pro Jig Head",
                category: "jigs",
                price: 12.99,
                description: "Premium jig head for bass fishing with realistic action.",
                images: [
                    "https://images.unsplash.com/photo-1544551763-46a013bb70d5?w=400&h=300&fit=crop",
                    "https://images.unsplash.com/photo-1559827260-dc66d52bef19?w=400&h=300&fit=crop"
                ],
                reviews: [{ rating: 4, comment: "Great lure!" }],
            },
            {
                id: 2,
                name: "Soft Plastic Worm",
                category: "soft-plastics",
                price: 8.49,
                description: "Lifelike worm with natural movement.",
                images: [
                    "https://images.unsplash.com/photo-1559827260-dc66d52bef19?w=400&h=300&fit=crop",
                    "https://images.unsplash.com/photo-1578662996442-48f60103fc96?w=400&h=300&fit=crop"
                ],
                reviews: [{ rating: 5, comment: "Caught a big one!" }],
            },
        ];

        // Website reviews
        let websiteReviews = JSON.parse(localStorage.getItem('websiteReviews')) || [
            { rating: 4, comment: "Great selection of lures!" },
            { rating: 5, comment: "Fast shipping and quality products." }
        ];

        // Helper to calculate average rating
        const calculateAverageRating = (reviews) => {
            if (!reviews || reviews.length === 0) return 0;
            const total = reviews.reduce((sum, review) => sum + review.rating, 0);
            return (total / reviews.length).toFixed(1);
        };

        // Main App Component
        function App() {
            const [products, setProducts] = useState(JSON.parse(localStorage.getItem('products')) || initialProducts);
            const [cart, setCart] = useState(JSON.parse(localStorage.getItem('cart')) || []);
            const [view, setView] = useState('store');
            const [isAdmin, setIsAdmin] = useState(false);
            const [cartModal, setCartModal] = useState(false);
            const [checkoutModal, setCheckoutModal] = useState(false);
            const [toast, setToast] = useState(null);
            const [currentCategory, setCurrentCategory] = useState('all');
            const [shippingZone, setShippingZone] = useState('inner-city');
            const shippingRates = {
                'inner-city': 5,
                'metro': 10,
                'regional': 15,
                'interstate': 20,
            };

            useEffect(() => {
                localStorage.setItem('products', JSON.stringify(products));
                localStorage.setItem('cart', JSON.stringify(cart));
                localStorage.setItem('websiteReviews', JSON.stringify(websiteReviews));
            }, [products, cart]);

            const showToast = (message) => {
                setToast(message);
                setTimeout(() => setToast(null), 3000);
            };

            const addToCart = (product) => {
                setCart(prev => {
                    const existing = prev.find(item => item.id === product.id);
                    if (existing) {
                        return prev.map(item =>
                            item.id === product.id ? { ...item, quantity: item.quantity + 1 } : item
                        );
                    }
                    return [...prev, { ...product, quantity: 1 }];
                });
                showToast(`${product.name} added to cart!`);
            };

            const updateCartItem = (id, delta) => {
                setCart(prev => {
                    const item = prev.find(i => i.id === id);
                    if (!item) return prev;
                    const newQuantity = item.quantity + delta;
                    if (newQuantity <= 0) return prev.filter(i => i.id !== id);
                    return prev.map(i => i.id === id ? { ...i, quantity: newQuantity } : i);
                });
            };

            const removeFromCart = (id) => {
                setCart(prev => prev.filter(item => item.id !== id));
                showToast('Item removed from cart');
            };

            const addProduct = (product) => {
                setProducts(prev => [
                    ...prev,
                    { ...product, id: prev.length ? Math.max(...prev.map(p => p.id)) + 1 : 1, reviews: [] }
                ]);
                showToast('Product added successfully!');
            };

            const updateProduct = (id, updatedProduct) => {
                setProducts(prev => prev.map(p => p.id === id ? { ...updatedProduct, id, reviews: p.reviews } : p));
                showToast('Product updated successfully!');
            };

            const deleteProduct = (id) => {
                if (window.confirm('Are you sure you want to delete this product?')) {
                    setProducts(prev => prev.filter(p => p.id !== id));
                    showToast('Product deleted');
                }
            };

            const addProductReview = (productId, review) => {
                setProducts(prev => prev.map(p =>
                    p.id === productId ? { ...p, reviews: [...(p.reviews || []), review] } : p
                ));
                showToast('Review submitted!');
            };

            const addWebsiteReview = (review) => {
                websiteReviews = [...websiteReviews, review];
                localStorage.setItem('websiteReviews', JSON.stringify(websiteReviews));
                showToast('Website review submitted!');
            };

            const handleCheckoutSubmit = (e) => {
                e.preventDefault();
                const formData = new FormData(e.target);
                const orderDetails = {
                    name: formData.get('name'),
                    email: formData.get('email'),
                    phone: formData.get('phone'),
                    address: formData.get('address'),
                    notes: formData.get('notes'),
                    items: cart.map(item => `${item.name} (${item.quantity} x $${item.price.toFixed(2)})`).join('\n'),
                    total: (cart.reduce((sum, item) => sum + item.price * item.quantity, 0) + shippingRates[shippingZone]).toFixed(2),
                    shipping: shippingRates[shippingZone],
                };
                setCart([]);
                setCheckoutModal(false);
                showToast('Order placed successfully!');
            };

            return (
                <div className="min-h-screen bg-gray-100 font-sans">
                    {/* Header */}
                    <header className="bg-blue-900 text-white sticky top-0 z-50 shadow-md">
                        <nav className="max-w-7xl mx-auto px-4 py-4 flex justify-between items-center">
                            <div className="flex items-center gap-2 cursor-pointer" onClick={() => setView('store')}>
                                <i className="fas fa-crown text-yellow-400 text-2xl"></i>
                                <span className="text-2xl font-bold">Lure Kings</span>
                            </div>
                            <div className="flex gap-4">
                                <button
                                    className="px-4 py-2 bg-blue-900 border border-white rounded hover:bg-blue-800"
                                    onClick={() => setView('store')}
                                >
                                    Store
                                </button>
                                <button
                                    className="px-4 py-2 bg-blue-900 border border-white rounded hover:bg-blue-800"
                                    onClick={() => setView('reviews')}
                                >
                                    Reviews
                                </button>
                                <button
                                    className="px-4 py-2 bg-blue-900 border border-white rounded hover:bg-blue-800"
                                    onClick={() => {
                                        const password = prompt('Enter admin password:');
                                        if (password === 'lureking') {
                                            setIsAdmin(true);
                                            setView('admin');
                                        } else if (password) {
                                            showToast('Incorrect password');
                                        }
                                    }}
                                >
                                    Admin
                                </button>
                                <button
                                    className="relative px-4 py-2 bg-blue-900 border border-white rounded hover:bg-blue-800"
                                    onClick={() => setCartModal(true)}
                                >
                                    <i className="fas fa-shopping-cart"></i>
                                    <span className="absolute -top-2 -right-2 bg-red-600 text-white rounded-full w-5 h-5 flex items-center justify-center text-xs">
                                        {cart.reduce((sum, item) => sum + item.quantity, 0)}
                                    </span>
                                </button>
                            </div>
                        </nav>
                    </header>

                    {/* Toast Notification */}
                    {toast && (
                        <div className="fixed bottom-4 right-4 bg-blue-900 text-white px-4 py-2 rounded shadow-lg z-50">
                            {toast}
                        </div>
                    )}

                    {/* Main Content */}
                    <main className="max-w-7xl mx-auto px-4 py-8">
                        {view === 'store' && (
                            <StoreView
                                products={products}
                                currentCategory={currentCategory}
                                setCurrentCategory={setCurrentCategory}
                                addToCart={addToCart}
                                addProductReview={addProductReview}
                            />
                        )}
                        {view === 'reviews' && (
                            <ReviewsView
                                websiteReviews={websiteReviews}
                                addWebsiteReview={addWebsiteReview}
                            />
                        )}
                        {view === 'admin' && isAdmin && (
                            <AdminView
                                products={products}
                                addProduct={addProduct}
                                updateProduct={updateProduct}
                                deleteProduct={deleteProduct}
                            />
                        )}
                    </main>

                    {/* Cart Modal */}
                    {cartModal && (
                        <Modal title="Shopping Cart" onClose={() => setCartModal(false)}>
                            <CartView
                                cart={cart}
                                updateCartItem={updateCartItem}
                                removeFromCart={removeFromCart}
                                shippingCost={shippingRates[shippingZone]}
                                setCheckoutModal={setCheckoutModal}
                            />
                        </Modal>
                    )}

                    {/* Checkout Modal */}
                    {checkoutModal && (
                        <Modal title="Secure Checkout" onClose={() => setCheckoutModal(false)}>
                            <CheckoutView
                                cart={cart}
                                shippingZone={shippingZone}
                                setShippingZone={setShippingZone}
                                shippingRates={shippingRates}
                                handleCheckoutSubmit={handleCheckoutSubmit}
                            />
                        </Modal>
                    )}
                </div>
            );
        }

        // Store View Component
        function StoreView({ products, currentCategory, setCurrentCategory, addToCart, addProductReview }) {
            const categories = ['all', 'jigs', 'soft-plastics', 'topwaters', 'spinnerbaits'];

            return (
                <>
                    <div className="text-center mb-8 bg-white p-6 rounded-lg shadow">
                        <h1 className="text-3xl font-bold text-blue-900 mb-2">Premium Fishing Lures</h1>
                        <p className="text-gray-600">High-quality lures for serious anglers</p>
                    </div>

                    <div className="flex flex-wrap gap-2 justify-center mb-8">
                        {categories.map(cat => (
                            <button
                                key={cat}
                                className={`px-4 py-2 rounded border ${currentCategory === cat ? 'bg-blue-900 text-white border-blue-900' : 'bg-white border-gray-300'}`}
                                onClick={() => setCurrentCategory(cat)}
                            >
                                {cat === 'all' ? 'All Lures' : cat.replace('-', ' ').replace(/\b\w/g, c => c.toUpperCase())}
                            </button>
                        ))}
                    </div>

                    <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
                        {products
                            .filter(p => currentCategory === 'all' || p.category === currentCategory)
                            .map(product => (
                                <ProductCard
                                    key={product.id}
                                    product={product}
                                    addToCart={addToCart}
                                    addProductReview={addProductReview}
                                />
                            ))}
                    </div>
                </>
            );
        }

        // Product Card Component with Image Carousel
        function ProductCard({ product, addToCart, addProductReview }) {
            const [currentImage, setCurrentImage] = useState(0);

            const nextImage = () => setCurrentImage((currentImage + 1) % product.images.length);
            const prevImage = () => setCurrentImage((currentImage - 1 + product.images.length) % product.images.length);

            const handleReviewSubmit = (e) => {
                e.preventDefault();
                const rating = parseInt(e.target.rating.value);
                const comment = e.target.comment.value;
                if (rating && comment) {
                    addProductReview(product.id, { rating, comment });
                    e.target.reset();
                }
            };

            return (
                <div className="bg-white border rounded-lg shadow hover:shadow-lg transition transform hover:-translate-y-1">
                    <div className="relative">
                        <img
                            src={product.images[currentImage]}
                            alt={product.name}
                            className="w-full h-48 object-cover rounded-t-lg"
                        />
                        {product.images.length > 1 && (
                            <>
                                <button
                                    className="absolute left-2 top-1/ Foulkesbury Road, Chatswood NSW 2067, Australia top-1/2 -translate-y-1/2 bg-black bg-opacity-50 text-white p-2 rounded"
                                    onClick={prevImage}
                                >
                                    <i className="fas fa-chevron-left"></i>
                                </button>
                                <button
                                    className="absolute right-2 top-1/2 -translate-y-1/2 bg-black bg-opacity-50 text-white p-2 rounded"
                                    onClick={nextImage}
                                >
                                    <i className="fas fa-chevron-right"></i>
                                </button>
                            </>
                        )}
                    </div>
                    <div className="p-4">
                        <h3 className="font-bold text-blue-900">{product.name}</h3>
                        <p className="text-red-600 font-bold">${product.price.toFixed(2)}</p>
                        <p className="text-gray-600 text-sm">{product.description}</p>
                        <div className="flex items-center gap-1">
                            <span>{calculateAverageRating(product.reviews)}★</span>
                            <span>({product.reviews.length} reviews)</span>
                        </div>
                        <button
                            className="w-full mt-2 bg-blue-900 text-white py-2 rounded hover:bg-blue-800"
                            onClick={() => addToCart(product)}
                        >
                            Add to Cart
                        </button>
                        <div className="mt-4">
                            <h4 className="font-bold">Reviews</h4>
                            {product.reviews.map((review, index) => (
                                <div key={index} className="mt-2 text-sm">
                                    <span>{'★'.repeat(review.rating)}{'☆'.repeat(5 - review.rating)}</span>
                                    <p>{review.comment}</p>
                                </div>
                            ))}
                            <form onSubmit={handleReviewSubmit} className="mt-2">
                                <div className="flex gap-2">
                                    <select name="rating" className="border rounded p-1" required>
                                        <option value="">Rate</option>
                                        {[1, 2, 3, 4, 5].map(n => (
                                            <option key={n} value={n}>{n} Stars</option>
                                        ))}
                                    </select>
                                    <input
                                        type="text"
                                        name="comment"
                                        placeholder="Your review"
                                        className="border rounded p-1 flex-grow"
                                        required
                                    />
                                    <button type="submit" className="bg-blue-900 text-white px-2 py-1 rounded">
                                        Submit
                                    </button>
                                </div>
                            </form>
                        </div>
                    </div>
                </div>
            );
        }

        // Reviews View Component
        function ReviewsView({ websiteReviews, addWebsiteReview }) {
            const handleReviewSubmit = (e) => {
                e.preventDefault();
                const rating = parseInt(e.target.rating.value);
                const comment = e.target.comment.value;
                if (rating && comment) {
                    addWebsiteReview({ rating, comment });
                    e.target.reset();
                }
            };

            return (
                <div className="bg-white p-6 rounded-lg shadow">
                    <h2 className="text-2xl font-bold text-blue-900 mb-4">
                        Website Reviews ({calculateAverageRating(websiteReviews)}★)
                    </h2>
                    <form onSubmit={handleReviewSubmit} className="mb-4">
                        <div className="flex gap-2">
                            <select name="rating" className="border rounded p-2" required>
                                <option value="">Rate</option>
                                {[1, 2, 3, 4, 5].map(n => (
                                    <option key={n} value={n}>{n} Stars</option>
                                ))}
                            </select>
                            <input
                                type="text"
                                name="comment"
                                placeholder="Your review"
                                className="border rounded p-2 flex-grow"
                                required
                            />
                            <button type="submit" className="bg-blue-900 text-white px-4 py-2 rounded">
                                Submit
                            </button>
                        </div>
                    </form>
                    <div>
                        {websiteReviews.map((review, index) => (
                            <div key={index} className="mb-2 p-2 bg-gray-50 rounded">
                                <span>{'★'.repeat(review.rating)}{'☆'.repeat(5 - review.rating)}</span>
                                <p>{review.comment}</p>
                            </div>
                        ))}
                    </div>
                </div>
            );
        }

        // Admin View Component
        function AdminView({ products, addProduct, updateProduct, deleteProduct }) {
            const [editProduct, setEditProduct] = useState(null);
            const [formData, setFormData] = useState({
                name: '',
                category: '',
                price: '',
                description: '',
                images: [''],
            });

            const handleSubmit = (e) => {
                e.preventDefault();
                const product = {
                    name: formData.name,
                    category: formData.category,
                    price: parseFloat(formData.price),
                    description: formData.description,
                    images: formData.images.filter(url => url),
                };
                if (editProduct) {
                    updateProduct(editProduct.id, product);
                    setEditProduct(null);
                } else {
                    addProduct(product);
                }
                setFormData({ name: '', category: '', price: '', description: '', images: [''] });
            };

            const handleImageChange = (index, value) => {
                const newImages = [...formData.images];
                newImages[index] = value;
                setFormData({ ...formData, images: newImages });
            };

            const addImageField = () => {
                setFormData({ ...formData, images: [...formData.images, ''] });
            };

            const editProductHandler = (product) => {
                setEditProduct(product);
                setFormData({
                    name: product.name,
                    category: product.category,
                    price: product.price,
                    description: product.description,
                    images: product.images,
                });
            };

            return (
                <div className="bg-white p-6 rounded-lg shadow">
                    <h2 className="text-2xl font-bold text-blue-900 mb-4">Admin Dashboard</h2>
                    <form onSubmit={handleSubmit} className="space-y-4">
                        <div>
                            <label className="block font-bold text-blue-900">Product Name</label>
                            <input
                                type="text"
                                value={formData.name}
                                onChange={(e) => setFormData({ ...formData, name: e.target.value })}
                                className="w-full border rounded p-2"
                                required
                            />
                        </div>
                        <div>
                            <label className="block font-bold text-blue-900">Category</label>
                            <select
                                value={formData.category}
                                onChange={(e) => setFormData({ ...formData, category: e.target.value })}
                                className="w-full border rounded p-2"
                                required
                            >
                                <option value="">Select Category</option>
                                <option value="jigs">Jigs</option>
                                <option value="soft-plastics">Soft Plastics</option>
                                <option value="topwaters">Topwaters</option>
                                <option value="spinnerbaits">Spinnerbaits</option>
                            </select>
                        </div>
                        <div>
                            <label className="block font-bold text-blue-900">Price ($)</label>
                            <input
                                type="number"
                                step="0.01"
                                value={formData.price}
                                onChange={(e) => setFormData({ ...formData, price: e.target.value })}
                                className="w-full border rounded p-2"
                                required
                            />
                        </div>
                        <div>
                            <label className="block font-bold text-blue-900">Description</label>
                            <textarea
                                value={formData.description}
                                onChange={(e) => setFormData({ ...formData, description: e.target.value })}
                                className="w-full border rounded p-2"
                                rows="3"
                                required
                            ></textarea>
                        </div>
                        <div>
                            <label className="block font-bold text-blue-900">Images (URLs)</label>
                            {formData.images.map((image, index) => (
                                <input
                                    key={index}
                                    type="url"
                                    value={image}
                                    onChange={(e) => handleImageChange(index, e.target.value)}
                                    className="w-full border rounded p-2 mb-2"
                                    placeholder="Enter image URL"
                                />
                            ))}
                            <button
                                type="button"
                                className="bg-blue-900 text-white px-4 py-2 rounded"
                                onClick={addImageField}
                            >
                                Add Another Image
                            </button>
                        </div>
                        <button type="submit" className="w-full bg-blue-900 text-white py-2 rounded">
                            {editProduct ? 'Update Product' : 'Add Product'}
                        </button>
                    </form>

                    <div className="mt-8">
                        <h3 className="text-xl font-bold text-blue-900 mb-4">Manage Products</h3>
                        {products.map(product => (
                            <div key={product.id} className="p-4 bg-gray-50 rounded mb-2 flex justify-between">
                                <div>
                                    <h4 className="font-bold">{product.name}</h4>
                                    <p>Category: {product.category}</p>
                                    <p>Price: ${product.price.toFixed(2)}</p>
                                    <p>{product.description}</p>
                                </div>
                                <div className="flex gap-2">
                                    <button
                                        className="bg-blue-900 text-white px-4 py-2 rounded"
                                        onClick={() => editProductHandler(product)}
                                    >
                                        Edit
                                    </button>
                                    <button
                                        className="bg-red-600 text-white px-4 py-2 rounded"
                                        onClick={() => deleteProduct(product.id)}
                                    >
                                        Delete
                                    </button>
                                </div>
                            </div>
                        ))}
                    </div>
                </div>
            );
        }

        // Cart View Component
        function CartView({ cart, updateCartItem, removeFromCart, shippingCost, setCheckoutModal }) {
            const total = cart.reduce((sum, item) => sum + item.price * item.quantity, 0);

            return (
                <div>
                    {cart.length === 0 ? (
                        <p>Your cart is empty</p>
                    ) : (
                        <>
                            {cart.map(item => (
                                <div key={item.id} className="flex items-center p-4 border-b gap-4">
                                    <img src={item.images[0]} alt={item.name} className="w-16 h-16 object-cover rounded" />
                                    <div className="flex-grow">
                                        <h4 className="font-bold text-blue-900">{item.name}</h4>
                                        <p>${item.price.toFixed(2)} each</p>
                                        <div className="flex items-center gap-2">
                                            <button
                                                className="bg-blue-900 text-white w-6 h-6 rounded flex items-center justify-center"
                                                onClick={() => updateCartItem(item.id, -1)}
                                            >
                                                -
                                            </button>
                                            <span>{item.quantity}</span>
                                            <button
                                                className="bg-blue-900 text-white w-6 h-6 rounded flex items-center justify-center"
                                                onClick={() => updateCartItem(item.id, 1)}
                                            >
                                                +
                                            </button>
                                        </div>
                                    </div>
                                    <button
                                        className="bg-red-600 text-white px-2 py-1 rounded"
                                        onClick={() => removeFromCart(item.id)}
                                    >
                                        Remove
                                    </button>
                                </div>
                            ))}
                            <div className="p-4 text-center font-bold text-blue-900 border-t">
                                Subtotal: ${total.toFixed(2)}<br />
                                Shipping: ${shippingCost.toFixed(2)}<br />
                                Total: ${(total + shippingCost).toFixed(2)}
                            </div>
                            <button
                                className="w-full bg-blue-900 text-white py-2 rounded"
                                onClick={() => setCheckoutModal(true)}
                            >
                                Proceed to Checkout
                            </button>
                        </>
                    )}
                </div>
            );
        }

        // Checkout View Component
        function CheckoutView({ cart, shippingZone, setShippingZone, shippingRates, handleCheckoutSubmit }) {
            const total = cart.reduce((sum, item) => sum + item.price * item.quantity, 0);
            const orderItems = cart.map(item => `${item.name} (${item.quantity} x $${item.price.toFixed(2)})`).join('\n');

            return (
                <div>
                    <div className="p-4 bg-gray-50 rounded mb-4">
                        <h4 className="font-bold text-blue-900">Payment Information</h4>
                        <p><strong>Bank Details:</strong> ANZ Bank</p>
                        <p><strong>Account Name:</strong> Lure Kings Pty Ltd</p>
                        <p><strong>BSB:</strong> 012-345</p>
                        <p><strong>Account Number:</strong> 123456789</p>
                        <p className="text-sm text-gray-600">Use your order number as the payment reference</p>
                    </div>
                    <div className="mb-4">
                        <label className="block font-bold text-blue-900">Shipping Zone</label>
                        <select
                            value={shippingZone}
                            onChange={(e) => setShippingZone(e.target.value)}
                            className="w-full border rounded p-2"
                        >
                            <option value="inner-city">Inner City ($5.00)</option>
                            <option value="metro">Metro ($10.00)</option>
                            <option value="regional">Regional ($15.00)</option>
                            <option value="interstate">Interstate ($20.00)</option>
                        </select>
                    </div>
                    <form
                        action="https://formsubmit.co/lure.kings.fishing.aus@gmail.com"
                        method="POST"
                        onSubmit={handleCheckoutSubmit}
                    >
                        <input type="hidden" name="_subject" value="New Order from Lure Kings" />
                        <input type="hidden" name="_template" value="table" />
                        <input type="hidden" name="_cc" value="lure.kings.fishing.aus@gmail.com" />
                        <input type="hidden" name="_autoresponse" value="Thank you for your order! We'll process it shortly." />
                        <input type="hidden" name="order_items" value={orderItems} />
                        <input type="hidden" name="order_total" value={(total + shippingRates[shippingZone]).toFixed(2)} />
                        <div className="space-y-4">
                            <div>
                                <label className="block font-bold text-blue-900">Full Name</label>
                                <input type="text" name="name" className="w-full border rounded p-2" required />
                            </div>
                            <div>
                                <label className="block font-bold text-blue-900">Email Address</label>
                                <input type="email" name="email" className="w-full border rounded p-2" required />
                            </div>
                            <div>
                                <label className="block font-bold text-blue-900">Phone Number</label>
                                <input type="tel" name="phone" className="w-full border rounded p-2" required />
                            </div>
                            <div>
                                <label className="block font-bold text-blue-900">Delivery Address</label>
                                <textarea name="address" className="w-full border rounded p-2" rows="3" required></textarea>
                            </div>
                            <div>
                                <label className="block font-bold text-blue-900">Order Notes (Optional)</label>
                                <textarea name="notes" className="w-full border rounded p-2" rows="2"></textarea>
                            </div>
                            <button type="submit" className="w-full bg-blue-900 text-white py-2 rounded">
                                Place Order
                            </button>
                        </div>
                    </form>
                </div>
            );
        }

        // Modal Component
        function Modal({ title, onClose, children }) {
            return (
                <div className="fixed inset-0 bg-black bg-opacity-50 z-50 flex items-center justify-center">
                    <div className="bg-white rounded-lg p-6 max-w-lg w-full max-h-[90%] overflow-y-auto relative">
                        <button
                            className="absolute top-4 right-4 text-gray-600 hover:text-gray-800"
                            onClick={onClose}
                        >
                            <i className="fas fa-times text-xl"></i>
                        </button>
                        <h2 className="text-2xl font-bold text-blue-900 mb-4">{title}</h2>
                        {children}
                    </div>
                </div>
            );
        }

        // Render the app
        ReactDOM.render(<App />, document.getElementById('root'));
    </script>
</body>
</html>
