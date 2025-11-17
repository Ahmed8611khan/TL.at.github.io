<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>YL @T.ME - Premium Fashion</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --primary: #7c3aed;
            --primary-dark: #6d28d9;
            --secondary: #64748b;
            --success: #10b981;
            --danger: #ef4444;
            --warning: #f59e0b;
            --light: #f8fafc;
            --dark: #1e293b;
            --gray: #6b7280;
            --shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
            --shadow-lg: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
        }

        body {
            font-family: 'Segoe UI', system-ui, sans-serif;
            background-color: var(--light);
            color: var(--dark);
            line-height: 1.6;
        }

        /* Mobile First Styles */
        .mobile-view {
            display: block;
        }

        .desktop-view {
            display: none;
        }

        /* Mobile Header */
        .mobile-header {
            background: white;
            box-shadow: var(--shadow);
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            z-index: 1000;
            padding: 12px 16px;
        }

        .mobile-header .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 1.5rem;
            font-weight: bold;
            color: var(--primary);
        }

        /* Bottom Navigation */
        .bottom-nav {
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
            background: white;
            border-top: 1px solid #e5e7eb;
            display: flex;
            justify-content: space-around;
            padding: 8px 0;
            z-index: 1000;
        }

        .nav-item {
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 8px 12px;
            color: var(--gray);
            text-decoration: none;
            font-size: 0.75rem;
            transition: all 0.3s ease;
        }

        .nav-item.active {
            color: var(--primary);
        }

        .nav-item i {
            font-size: 1.25rem;
            margin-bottom: 4px;
        }

        /* Main Content */
        .main-content {
            padding: 70px 16px 70px;
            min-height: 100vh;
        }

        /* Hero Section */
        .hero {
            background: linear-gradient(135deg, var(--primary), #8b5cf6);
            border-radius: 16px;
            padding: 24px;
            color: white;
            margin-bottom: 24px;
            text-align: center;
        }

        .hero h1 {
            font-size: 1.75rem;
            margin-bottom: 8px;
        }

        .hero p {
            opacity: 0.9;
            margin-bottom: 20px;
        }

        .btn {
            background: white;
            color: var(--primary);
            padding: 12px 24px;
            border-radius: 12px;
            text-decoration: none;
            font-weight: 600;
            display: inline-block;
            transition: all 0.3s ease;
            border: none;
            cursor: pointer;
        }

        .btn:hover {
            transform: translateY(-2px);
            box-shadow: var(--shadow-lg);
        }

        .btn-primary {
            background: var(--primary);
            color: white;
        }

        .btn-success {
            background: var(--success);
            color: white;
        }

        .btn-danger {
            background: var(--danger);
            color: white;
        }

        .btn-warning {
            background: var(--warning);
            color: white;
        }

        /* Product Cards */
        .section-title {
            font-size: 1.25rem;
            font-weight: 600;
            margin: 24px 0 16px;
        }

        .product-grid {
            display: grid;
            gap: 16px;
        }

        .product-card {
            background: white;
            border-radius: 12px;
            padding: 16px;
            box-shadow: var(--shadow);
            transition: all 0.3s ease;
            position: relative;
        }

        .product-card:hover {
            transform: translateY(-4px);
            box-shadow: var(--shadow-lg);
        }

        .product-badge {
            background: var(--primary);
            color: white;
            padding: 4px 8px;
            border-radius: 6px;
            font-size: 0.7rem;
            font-weight: 600;
            position: absolute;
            top: 15px;
            left: 15px;
        }

        .product-image {
            width: 100%;
            height: 160px;
            object-fit: cover;
            border-radius: 8px;
            margin-bottom: 12px;
        }

        .product-title {
            font-weight: 600;
            margin-bottom: 8px;
            font-size: 1rem;
        }

        .product-description {
            color: var(--gray);
            font-size: 0.875rem;
            margin-bottom: 12px;
            display: -webkit-box;
            -webkit-line-clamp: 2;
            -webkit-box-orient: vertical;
            overflow: hidden;
        }

        .product-footer {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .product-price {
            font-weight: bold;
            color: var(--primary);
            font-size: 1.125rem;
        }

        .add-to-cart {
            background: var(--primary);
            color: white;
            border: none;
            padding: 8px 16px;
            border-radius: 8px;
            cursor: pointer;
            transition: background 0.3s ease;
        }

        .add-to-cart:hover {
            background: var(--primary-dark);
        }

        /* Categories */
        .categories-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 12px;
            margin-bottom: 24px;
        }

        .category-card {
            background: white;
            padding: 20px;
            border-radius: 12px;
            text-align: center;
            box-shadow: var(--shadow);
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .category-card:hover {
            transform: translateY(-2px);
            box-shadow: var(--shadow-lg);
        }

        .category-icon {
            font-size: 2rem;
            margin-bottom: 8px;
        }

        /* Payment Gateway Styles */
        .payment-container {
            background: white;
            border-radius: 16px;
            padding: 24px;
            box-shadow: var(--shadow-lg);
            margin: 20px 0;
        }

        .payment-methods {
            display: grid;
            gap: 16px;
            margin: 20px 0;
        }

        .payment-method {
            background: var(--light);
            border: 2px solid #e5e7eb;
            border-radius: 12px;
            padding: 20px;
            cursor: pointer;
            transition: all 0.3s ease;
            text-align: center;
        }

        .payment-method:hover {
            border-color: var(--primary);
            transform: translateY(-2px);
        }

        .payment-method.active {
            border-color: var(--primary);
            background: rgba(124, 58, 237, 0.05);
        }

        .payment-icon {
            font-size: 2.5rem;
            margin-bottom: 12px;
            color: var(--primary);
        }

        .payment-details {
            display: none;
            margin-top: 20px;
            padding: 20px;
            background: var(--light);
            border-radius: 12px;
            border: 1px solid #e5e7eb;
        }

        .payment-details.active {
            display: block;
        }

        .upi-qr-container {
            text-align: center;
            padding: 20px;
        }

        .upi-qr-code {
            width: 200px;
            height: 200px;
            background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
            border-radius: 12px;
            margin: 0 auto 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 3rem;
        }

        .card-form {
            display: grid;
            gap: 16px;
        }

        .card-input-group {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 12px;
        }

        .card-logos {
            display: flex;
            gap: 10px;
            margin-bottom: 15px;
            justify-content: center;
        }

        .card-logo {
            width: 50px;
            height: 30px;
            background: var(--light);
            border-radius: 4px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            color: var(--gray);
            border: 1px solid #e5e7eb;
        }

        .payment-success {
            text-align: center;
            padding: 40px 20px;
        }

        .success-icon {
            font-size: 4rem;
            color: var(--success);
            margin-bottom: 20px;
        }

        /* Forms */
        .auth-container {
            max-width: 400px;
            margin: 40px auto;
            padding: 0 16px;
        }

        .auth-card {
            background: white;
            padding: 24px;
            border-radius: 16px;
            box-shadow: var(--shadow-lg);
        }

        .auth-title {
            text-align: center;
            margin-bottom: 24px;
            font-size: 1.5rem;
            color: var(--dark);
        }

        .form-group {
            margin-bottom: 16px;
        }

        .form-label {
            display: block;
            margin-bottom: 6px;
            font-weight: 500;
            color: var(--dark);
        }

        .form-input {
            width: 100%;
            padding: 12px 16px;
            border: 2px solid #e5e7eb;
            border-radius: 8px;
            font-size: 1rem;
            transition: border-color 0.3s ease;
        }

        .form-input:focus {
            outline: none;
            border-color: var(--primary);
        }

        .form-textarea {
            width: 100%;
            padding: 12px 16px;
            border: 2px solid #e5e7eb;
            border-radius: 8px;
            font-size: 1rem;
            transition: border-color 0.3s ease;
            resize: vertical;
            min-height: 100px;
        }

        .form-select {
            width: 100%;
            padding: 12px 16px;
            border: 2px solid #e5e7eb;
            border-radius: 8px;
            font-size: 1rem;
            background: white;
            cursor: pointer;
        }

        .btn-block {
            width: 100%;
            text-align: center;
        }

        .auth-link {
            text-align: center;
            margin-top: 16px;
        }

        .auth-link a {
            color: var(--primary);
            text-decoration: none;
        }

        /* Cart */
        .cart-item {
            display: flex;
            background: white;
            padding: 16px;
            border-radius: 12px;
            margin-bottom: 12px;
            box-shadow: var(--shadow);
        }

        .cart-item-image {
            width: 80px;
            height: 80px;
            object-fit: cover;
            border-radius: 8px;
            margin-right: 12px;
        }

        .cart-item-details {
            flex: 1;
        }

        .cart-item-title {
            font-weight: 600;
            margin-bottom: 4px;
        }

        .cart-item-price {
            color: var(--primary);
            font-weight: 600;
        }

        .cart-actions {
            display: flex;
            gap: 8px;
            align-items: center;
        }

        .quantity-btn {
            background: var(--light);
            border: none;
            width: 32px;
            height: 32px;
            border-radius: 6px;
            cursor: pointer;
        }

        .cart-total {
            background: white;
            padding: 20px;
            border-radius: 12px;
            margin-top: 20px;
            box-shadow: var(--shadow);
        }

        .total-row {
            display: flex;
            justify-content: space-between;
            margin-bottom: 8px;
        }

        .total-final {
            font-size: 1.25rem;
            font-weight: bold;
            color: var(--primary);
            border-top: 1px solid #e5e7eb;
            padding-top: 12px;
            margin-top: 12px;
        }

        /* Admin Styles */
        .admin-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 24px;
        }

        .admin-stats {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 16px;
            margin-bottom: 24px;
        }

        .stat-card {
            background: white;
            padding: 20px;
            border-radius: 12px;
            text-align: center;
            box-shadow: var(--shadow);
        }

        .stat-number {
            font-size: 2rem;
            font-weight: bold;
            color: var(--primary);
            margin-bottom: 8px;
        }

        .stat-label {
            color: var(--gray);
            font-size: 0.9rem;
        }

        .admin-tabs {
            background: white;
            border-radius: 12px;
            padding: 20px;
            box-shadow: var(--shadow);
            margin-bottom: 24px;
        }

        .tabs-header {
            display: flex;
            border-bottom: 2px solid #e5e7eb;
            margin-bottom: 20px;
            overflow-x: auto;
        }

        .tab {
            padding: 12px 20px;
            cursor: pointer;
            font-weight: 500;
            border-bottom: 3px solid transparent;
            transition: all 0.3s ease;
            white-space: nowrap;
        }

        .tab.active {
            color: var(--primary);
            border-bottom-color: var(--primary);
        }

        .tab-content {
            display: none;
        }

        .tab-content.active {
            display: block;
        }

        .table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 16px;
        }

        .table th, .table td {
            padding: 12px;
            text-align: left;
            border-bottom: 1px solid #e5e7eb;
        }

        .table th {
            background: var(--light);
            font-weight: 600;
            color: var(--dark);
        }

        .action-buttons {
            display: flex;
            gap: 8px;
        }

        /* Desktop Styles */
        @media (min-width: 768px) {
            .mobile-view {
                display: none;
            }

            .desktop-view {
                display: block;
            }

            .desktop-header {
                background: white;
                box-shadow: var(--shadow);
                padding: 16px 0;
                position: fixed;
                top: 0;
                left: 0;
                right: 0;
                z-index: 1000;
            }

            .header-content {
                max-width: 1200px;
                margin: 0 auto;
                padding: 0 24px;
                display: flex;
                justify-content: space-between;
                align-items: center;
            }

            .desktop-nav {
                display: flex;
                gap: 32px;
                align-items: center;
            }

            .desktop-nav a {
                text-decoration: none;
                color: var(--dark);
                font-weight: 500;
                transition: color 0.3s ease;
            }

            .desktop-nav a:hover {
                color: var(--primary);
            }

            .cart-count {
                background: var(--primary);
                color: white;
                border-radius: 50%;
                padding: 2px 6px;
                font-size: 0.75rem;
                margin-left: 4px;
            }

            .desktop-main {
                max-width: 1200px;
                margin: 80px auto 0;
                padding: 24px;
            }

            .hero {
                text-align: left;
                padding: 48px;
            }

            .hero h1 {
                font-size: 2.5rem;
            }

            .product-grid {
                grid-template-columns: repeat(3, 1fr);
            }

            .categories-grid {
                grid-template-columns: repeat(4, 1fr);
            }

            .admin-stats {
                grid-template-columns: repeat(4, 1fr);
            }

            .payment-methods {
                grid-template-columns: repeat(2, 1fr);
            }

            .categories-grid {
                grid-template-columns: repeat(6, 1fr);
            }

            .product-grid {
                grid-template-columns: repeat(4, 1fr);
            }

            .cart-item {
                padding: 24px;
            }

            .auth-container {
                max-width: 500px;
                padding: 0 24px;
            }
        }

        /* Utility Classes */
        .hidden {
            display: none;
        }

        .text-center {
            text-align: center;
        }

        .mb-4 {
            margin-bottom: 16px;
        }

        .mt-4 {
            margin-top: 16px;
        }

        .page {
            display: none;
        }

        .page.active {
            display: block;
        }

        /* Hi Page Styles */
        .hi-container {
            text-align: center;
            padding: 60px 20px;
            background: white;
            border-radius: 20px;
            box-shadow: var(--shadow-lg);
            margin: 40px auto;
            max-width: 600px;
        }

        .hi-icon {
            font-size: 4rem;
            color: var(--primary);
            margin-bottom: 20px;
        }

        .hi-title {
            font-size: 2.5rem;
            font-weight: bold;
            margin-bottom: 15px;
            color: var(--dark);
        }

        .hi-subtitle {
            font-size: 1.2rem;
            color: var(--gray);
            margin-bottom: 30px;
        }

        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 20px;
            margin: 40px 0;
        }

        .feature-card {
            background: var(--light);
            padding: 20px;
            border-radius: 12px;
            text-align: center;
        }

        .feature-icon {
            font-size: 2rem;
            color: var(--primary);
            margin-bottom: 10px;
        }

        /* Notification */
        .notification {
            position: fixed;
            top: 100px;
            right: 20px;
            background: var(--success);
            color: white;
            padding: 15px 20px;
            border-radius: 8px;
            box-shadow: var(--shadow-lg);
            z-index: 10000;
            animation: slideIn 0.3s ease;
        }

        @keyframes slideIn {
            from {
                transform: translateX(100%);
                opacity: 0;
            }
            to {
                transform: translateX(0);
                opacity: 1;
            }
        }

        /* Modal Styles */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.5);
            z-index: 2000;
            align-items: center;
            justify-content: center;
        }

        .modal-content {
            background: white;
            border-radius: 16px;
            padding: 24px;
            box-shadow: var(--shadow-lg);
            max-width: 500px;
            width: 90%;
            max-height: 90vh;
            overflow-y: auto;
            margin: 20px;
        }

        /* Product Upload Form */
        .upload-area {
            border: 2px dashed #e5e7eb;
            border-radius: 12px;
            padding: 40px 20px;
            text-align: center;
            margin-bottom: 20px;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .upload-area:hover {
            border-color: var(--primary);
            background: rgba(124, 58, 237, 0.05);
        }

        .upload-icon {
            font-size: 3rem;
            color: var(--primary);
            margin-bottom: 16px;
        }

        /* Help & Support */
        .help-grid {
            display: grid;
            gap: 16px;
            margin-top: 20px;
        }

        .help-card {
            background: white;
            padding: 20px;
            border-radius: 12px;
            box-shadow: var(--shadow);
            text-align: center;
        }

        .help-icon {
            font-size: 2.5rem;
            color: var(--primary);
            margin-bottom: 12px;
        }

        /* WhatsApp Contact */
        .whatsapp-contact {
            background: #25D366;
            color: white;
            padding: 16px;
            border-radius: 12px;
            text-align: center;
            margin-top: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }

        /* Activity Feed */
        .activity-item {
            background: white;
            padding: 16px;
            border-radius: 12px;
            margin-bottom: 12px;
            box-shadow: var(--shadow);
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .activity-icon {
            width: 40px;
            height: 40px;
            background: var(--light);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--primary);
        }

        /* Deal Page Styles */
        .deal-banner {
            background: linear-gradient(135deg, var(--primary), #a78bfa);
            color: white;
            padding: 20px;
            margin: 12px;
            border-radius: 12px;
            text-align: center;
            box-shadow: var(--shadow);
        }

        .deal-banner h2 {
            font-size: 1.8rem;
            margin-bottom: 8px;
        }

        .deal-banner p {
            font-size: 1rem;
            margin-bottom: 16px;
        }

        .deal-timer {
            display: flex;
            justify-content: center;
            gap: 12px;
            margin-top: 16px;
        }

        .timer-unit {
            background: rgba(255,255,255,0.2);
            padding: 8px 12px;
            border-radius: 8px;
        }

        .timer-value {
            font-size: 1.5rem;
            font-weight: bold;
        }

        .timer-label {
            font-size: 0.8rem;
        }

        /* Order Status Styles */
        .status {
            padding: 6px 12px;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: 600;
        }

        .status-delivered {
            background: #dcfce7;
            color: #166534;
        }

        .status-pending {
            background: #fef3c7;
            color: #92400e;
        }

        .status-cancelled {
            background: #fee2e2;
            color: #991b1b;
        }

        /* Login Tabs */
        .login-tabs {
            display: flex;
            border-bottom: 1px solid #e5e7eb;
            margin-bottom: 20px;
        }

        .login-tab {
            flex: 1;
            text-align: center;
            padding: 12px;
            cursor: pointer;
            border-bottom: 2px solid transparent;
        }

        .login-tab.active {
            border-bottom-color: var(--primary);
            color: var(--primary);
            font-weight: 600;
        }

        .login-form {
            display: none;
        }

        .login-form.active {
            display: block;
        }
    </style>
</head>
<body>
    <!-- Mobile View -->
    <div class="mobile-view">
        <!-- Mobile Header -->
        <header class="mobile-header">
            <div class="header-content">
                <div class="logo">YL @T.ME</div>
                <div class="header-actions">
                    <i class="fas fa-search"></i>
                </div>
            </div>
        </header>

        <!-- Main Content -->
        <main class="main-content">
            <!-- Home Page -->
            <div id="home-page" class="page active">
                <section class="hero">
                    <h1>Premium Fashion Products</h1>
                    <p>Discover amazing shoes, watches, coats, and pants for your style</p>
                    <button class="btn" onclick="showPage('products-page')">Explore Products</button>
                </section>

                <h2 class="section-title">Featured Products</h2>
                <div class="product-grid" id="featured-products">
                    <!-- Products will be loaded by JavaScript -->
                </div>

                <h2 class="section-title">Categories</h2>
                <div class="categories-grid" id="categories-grid">
                    <!-- Categories will be loaded by JavaScript -->
                </div>
            </div>

            <!-- Products Page -->
            <div id="products-page" class="page">
                <div class="admin-header">
                    <h2 class="section-title">All Products</h2>
                    <select class="form-select" id="category-filter" onchange="filterProducts()" style="width: auto;">
                        <option value="all">All Categories</option>
                    </select>
                </div>
                <div class="product-grid" id="all-products">
                    <!-- Products will be loaded by JavaScript -->
                </div>
            </div>

            <!-- Categories Page -->
            <div id="categories-page" class="page">
                <h2 class="section-title">Browse Categories</h2>
                <div class="categories-grid" id="all-categories">
                    <!-- Categories will be loaded by JavaScript -->
                </div>
            </div>

            <!-- Deal Page -->
            <div id="deal-page" class="page">
                <div class="deal-banner">
                    <h2>FLASH SALE</h2>
                    <p>Limited time offers! Don't miss out on these amazing deals</p>
                    <div class="deal-timer">
                        <div class="timer-unit">
                            <div class="timer-value" id="hours">24</div>
                            <div class="timer-label">HOURS</div>
                        </div>
                        <div class="timer-unit">
                            <div class="timer-value" id="minutes">60</div>
                            <div class="timer-label">MINUTES</div>
                        </div>
                        <div class="timer-unit">
                            <div class="timer-value" id="seconds">60</div>
                            <div class="timer-label">SECONDS</div>
                        </div>
                    </div>
                </div>
                
                <div class="filter-bar">
                    <div class="filter-item active">All Deals</div>
                    <div class="filter-item">Ending Soon</div>
                    <div class="filter-item">Popular</div>
                    <div class="filter-item">Bestsellers</div>
                </div>
                
                <div class="section-header">
                    <h2>Hot Deals</h2>
                    <div class="view-all">View All</div>
                </div>
                <div class="products-grid" id="deals-products-grid"></div>
                
                <div class="section-header">
                    <h2>Limited Time Offers</h2>
                    <div class="view-all">View All</div>
                </div>
                <div class="products-grid" id="limited-products-grid"></div>
            </div>

            <!-- Cart Page -->
            <div id="cart-page" class="page">
                <h2 class="section-title">Your Cart</h2>
                <div id="cart-items">
                    <!-- Cart items will be loaded by JavaScript -->
                </div>
                <div class="cart-total">
                    <div class="total-row">
                        <span>Subtotal:</span>
                        <span id="cart-subtotal">$0.00</span>
                    </div>
                    <div class="total-row">
                        <span>Tax:</span>
                        <span id="cart-tax">$0.00</span>
                    </div>
                    <div class="total-row total-final">
                        <span>Total:</span>
                        <span id="cart-total">$0.00</span>
                    </div>
                    <button class="btn btn-primary btn-block mt-4" onclick="showPage('payment-page')">Proceed to Payment</button>
                </div>
            </div>

            <!-- Payment Page -->
            <div id="payment-page" class="page">
                <h2 class="section-title">Payment Gateway</h2>
                
                <div class="payment-container">
                    <h3 style="text-align: center; margin-bottom: 20px;">Choose Payment Method</h3>
                    
                    <div class="payment-methods">
                        <div class="payment-method" onclick="selectPaymentMethod('upi')">
                            <div class="payment-icon">📱</div>
                            <h4>UPI Payment</h4>
                            <p>Pay using UPI QR Code</p>
                        </div>

                        <div class="payment-method" onclick="selectPaymentMethod('card')">
                            <div class="payment-icon">💳</div>
                            <h4>Credit/Debit Card</h4>
                            <p>Visa, Mastercard, RuPay</p>
                        </div>

                        <div class="payment-method" onclick="selectPaymentMethod('netbanking')">
                            <div class="payment-icon">🏦</div>
                            <h4>Net Banking</h4>
                            <p>All major banks</p>
                        </div>

                        <div class="payment-method" onclick="selectPaymentMethod('wallet')">
                            <div class="payment-icon">👛</div>
                            <h4>Digital Wallet</h4>
                            <p>Paytm, PhonePe, Google Pay</p>
                        </div>
                    </div>

                    <!-- UPI Payment Details -->
                    <div id="upi-details" class="payment-details">
                        <div class="upi-qr-container">
                            <div class="upi-qr-code">
                                <i class="fas fa-qrcode"></i>
                            </div>
                            <h4>Scan QR Code to Pay</h4>
                            <p>Amount: <strong id="upi-amount">$0.00</strong></p>
                            <p>UPI ID: <strong>yl@paytm</strong></p>
                            <button class="btn btn-success mt-4" onclick="processUPIPayment()">
                                <i class="fas fa-check"></i> I have made the payment
                            </button>
                        </div>
                    </div>

                    <!-- Card Payment Details -->
                    <div id="card-details" class="payment-details">
                        <div class="card-logos">
                            <div class="card-logo">VISA</div>
                            <div class="card-logo">MC</div>
                            <div class="card-logo">RUPAY</div>
                        </div>
                        
                        <form id="card-form" class="card-form">
                            <div class="form-group">
                                <label class="form-label">Card Number</label>
                                <input type="text" class="form-input" placeholder="1234 5678 9012 3456" maxlength="19" required>
                            </div>
                            
                            <div class="card-input-group">
                                <div class="form-group">
                                    <label class="form-label">Expiry Date</label>
                                    <input type="text" class="form-input" placeholder="MM/YY" maxlength="5" required>
                                </div>
                                
                                <div class="form-group">
                                    <label class="form-label">CVV</label>
                                    <input type="text" class="form-input" placeholder="123" maxlength="3" required>
                                </div>
                            </div>
                            
                            <div class="form-group">
                                <label class="form-label">Cardholder Name</label>
                                <input type="text" class="form-input" placeholder="John Doe" required>
                            </div>
                            
                            <button type="submit" class="btn btn-success btn-block">
                                <i class="fas fa-lock"></i> Pay $<span id="card-amount">0.00</span>
                            </button>
                        </form>
                    </div>

                    <!-- Net Banking Details -->
                    <div id="netbanking-details" class="payment-details">
                        <div class="form-group">
                            <label class="form-label">Select Bank</label>
                            <select class="form-select" required>
                                <option value="">Choose your bank</option>
                                <option value="sbi">State Bank of India</option>
                                <option value="hdfc">HDFC Bank</option>
                                <option value="icici">ICICI Bank</option>
                                <option value="axis">Axis Bank</option>
                                <option value="kotak">Kotak Mahindra Bank</option>
                            </select>
                        </div>
                        <button class="btn btn-success btn-block" onclick="processNetBankingPayment()">
                            Continue to Bank Portal
                        </button>
                    </div>

                    <!-- Wallet Payment Details -->
                    <div id="wallet-details" class="payment-details">
                        <div class="payment-methods" style="grid-template-columns: 1fr;">
                            <div class="payment-method" onclick="selectWallet('paytm')">
                                <div class="payment-icon" style="color: #002e6e;">P</div>
                                <h4>Paytm</h4>
                            </div>
                            <div class="payment-method" onclick="selectWallet('phonepe')">
                                <div class="payment-icon" style="color: #673ab7;">P</div>
                                <h4>PhonePe</h4>
                            </div>
                            <div class="payment-method" onclick="selectWallet('gpay')">
                                <div class="payment-icon" style="color: #4285f4;">G</div>
                                <h4>Google Pay</h4>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Payment Success Page -->
            <div id="payment-success-page" class="page">
                <div class="payment-container">
                    <div class="payment-success">
                        <div class="success-icon">
                            <i class="fas fa-check-circle"></i>
                        </div>
                        <h3>Payment Successful!</h3>
                        <p>Thank you for your purchase. Your order has been confirmed.</p>
                        <p><strong>Order ID: </strong><span id="success-order-id">YL-123456</span></p>
                        <p><strong>Amount Paid: </strong><span id="success-amount">$0.00</span></p>
                        <div style="margin-top: 30px;">
                            <button class="btn btn-primary" onclick="showPage('home-page')">
                                Continue Shopping
                            </button>
                            <button class="btn btn-secondary" onclick="showPage('profile-page')" style="margin-left: 10px;">
                                View Orders
                            </button>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Profile Page -->
            <div id="profile-page" class="page">
                <div class="auth-card">
                    <h3 class="auth-title">User Profile</h3>
                    <div id="user-info">
                        <!-- User info will be loaded by JavaScript -->
                    </div>
                    <div class="auth-link">
                        <a href="#" onclick="logout()">Logout</a>
                    </div>
                </div>

                <h3 class="section-title">My Orders</h3>
                <div id="user-orders">
                    <!-- Orders will be loaded by JavaScript -->
                </div>
            </div>

            <!-- Admin Page -->
            <div id="admin-page" class="page">
                <div class="admin-header">
                    <h2 class="section-title">Admin Dashboard</h2>
                    <button class="btn btn-primary" onclick="showAdminTab('products')">Manage Products</button>
                </div>

                <div class="admin-stats">
                    <div class="stat-card">
                        <div class="stat-number" id="total-products">0</div>
                        <div class="stat-label">Total Products</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-number" id="total-orders">0</div>
                        <div class="stat-label">Total Orders</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-number" id="total-users">0</div>
                        <div class="stat-label">Total Users</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-number" id="total-revenue">$0</div>
                        <div class="stat-label">Total Revenue</div>
                    </div>
                </div>

                <div class="admin-tabs">
                    <div class="tabs-header">
                        <div class="tab active" onclick="showAdminTab('products')">Products</div>
                        <div class="tab" onclick="showAdminTab('orders')">Orders</div>
                        <div class="tab" onclick="showAdminTab('users')">Users</div>
                        <div class="tab" onclick="showAdminTab('upload')">Add Product</div>
                    </div>

                    <div id="admin-products" class="tab-content active">
                        <table class="table">
                            <thead>
                                <tr>
                                    <th>ID</th>
                                    <th>Name</th>
                                    <th>Category</th>
                                    <th>Price</th>
                                    <th>Status</th>
                                    <th>Actions</th>
                                </tr>
                            </thead>
                            <tbody id="admin-products-table">
                                <!-- Products will be loaded by JavaScript -->
                            </tbody>
                        </table>
                    </div>

                    <div id="admin-orders" class="tab-content">
                        <table class="table">
                            <thead>
                                <tr>
                                    <th>Order ID</th>
                                    <th>Customer</th>
                                    <th>Amount</th>
                                    <th>Status</th>
                                    <th>Date</th>
                                    <th>Actions</th>
                                </tr>
                            </thead>
                            <tbody id="admin-orders-table">
                                <!-- Orders will be loaded by JavaScript -->
                            </tbody>
                        </table>
                    </div>

                    <div id="admin-users" class="tab-content">
                        <table class="table">
                            <thead>
                                <tr>
                                    <th>ID</th>
                                    <th>Name</th>
                                    <th>Email</th>
                                    <th>Role</th>
                                    <th>Joined</th>
                                    <th>Actions</th>
                                </tr>
                            </thead>
                            <tbody id="admin-users-table">
                                <!-- Users will be loaded by JavaScript -->
                            </tbody>
                        </table>
                    </div>

                    <div id="admin-upload" class="tab-content">
                        <h3 class="auth-title">Add New Product</h3>
                        <form id="product-upload-form">
                            <div class="form-group">
                                <label class="form-label">Product Name</label>
                                <input type="text" class="form-input" id="product-name" required>
                            </div>
                            <div class="form-group">
                                <label class="form-label">Description</label>
                                <textarea class="form-textarea" id="product-description" required></textarea>
                            </div>
                            <div class="form-group">
                                <label class="form-label">Category</label>
                                <select class="form-select" id="product-category" required>
                                    <option value="">Select Category</option>
                                    <option value="shoes">Shoes</option>
                                    <option value="watches">Watches</option>
                                    <option value="coats">Coats</option>
                                    <option value="pants">Pants</option>
                                </select>
                            </div>
                            <div class="form-group">
                                <label class="form-label">Price ($)</label>
                                <input type="number" class="form-input" id="product-price" step="0.01" required>
                            </div>
                            <div class="form-group">
                                <label class="form-label">Product Image URL</label>
                                <input type="url" class="form-input" id="product-image" placeholder="https://example.com/image.jpg" required>
                            </div>
                            <div class="upload-area" onclick="document.getElementById('product-image-upload').click()">
                                <div class="upload-icon">
                                    <i class="fas fa-cloud-upload-alt"></i>
                                </div>
                                <p>Click to upload product image</p>
                                <input type="file" id="product-image-upload" accept="image/*" style="display: none;" onchange="handleImageUpload(event)">
                            </div>
                            <button type="submit" class="btn btn-primary btn-block">Add Product</button>
                        </form>
                    </div>
                </div>
            </div>

            <!-- Activity Page -->
            <div id="activity-page" class="page">
                <h2 class="section-title">Recent Activity</h2>
                <div id="activity-feed">
                    <!-- Activity items will be loaded by JavaScript -->
                </div>
            </div>

            <!-- Help Page -->
            <div id="help-page" class="page">
                <h2 class="section-title">Help & Support</h2>
                <div class="help-grid">
                    <div class="help-card">
                        <div class="help-icon">
                            <i class="fas fa-phone"></i>
                        </div>
                        <h4>Call Us</h4>
                        <p>+1 234 567 8900</p>
                        <p>24/7 Customer Support</p>
                    </div>
                    <div class="help-card">
                        <div class="help-icon">
                            <i class="fas fa-envelope"></i>
                        </div>
                        <h4>Email Us</h4>
                        <p>support@yl.com</p>
                        <p>Response within 24 hours</p>
                    </div>
                    <div class="help-card">
                        <div class="help-icon">
                            <i class="fas fa-comments"></i>
                        </div>
                        <h4>Live Chat</h4>
                        <p>Available 9AM - 9PM</p>
                        <p>Instant support</p>
                    </div>
                </div>

                <div class="whatsapp-contact">
                    <i class="fab fa-whatsapp"></i>
                    <div>
                        <h4>WhatsApp Support</h4>
                        <p>+1 234 567 8901</p>
                    </div>
                </div>

                <h3 class="section-title">Frequently Asked Questions</h3>
                <div class="help-grid">
                    <div class="help-card">
                        <h4>How can I track my order?</h4>
                        <p>You can track your order from the Orders section in your profile.</p>
                    </div>
                    <div class="help-card">
                        <h4>What is your return policy?</h4>
                        <p>We offer 30-day returns for all products in original condition.</p>
                    </div>
                    <div class="help-card">
                        <h4>Do you ship internationally?</h4>
                        <p>Yes, we ship to over 50 countries worldwide.</p>
                    </div>
                </div>
            </div>

            <!-- Login Page -->
            <div id="login-page" class="page">
                <div class="auth-container">
                    <div class="auth-card">
                        <h3 class="auth-title">Login</h3>
                        <form id="login-form">
                            <div class="form-group">
                                <label class="form-label">Email</label>
                                <input type="email" class="form-input" id="login-email" required>
                            </div>
                            <div class="form-group">
                                <label class="form-label">Password</label>
                                <input type="password" class="form-input" id="login-password" required>
                            </div>
                            <button type="submit" class="btn btn-primary btn-block">Login</button>
                        </form>
                        <div class="auth-link">
                            Don't have an account? <a href="#" onclick="showPage('register-page')">Sign up</a>
                        </div>
                        <div class="auth-link">
                            <a href="#" onclick="loginAsAdmin()">Login as Admin (Demo)</a>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Register Page -->
            <div id="register-page" class="page">
                <div class="auth-container">
                    <div class="auth-card">
                        <h3 class="auth-title">Create Account</h3>
                        <form id="register-form">
                            <div class="form-group">
                                <label class="form-label">Full Name</label>
                                <input type="text" class="form-input" id="register-name" required>
                            </div>
                            <div class="form-group">
                                <label class="form-label">Email</label>
                                <input type="email" class="form-input" id="register-email" required>
                            </div>
                            <div class="form-group">
                                <label class="form-label">Password</label>
                                <input type="password" class="form-input" id="register-password" required>
                            </div>
                            <div class="form-group">
                                <label class="form-label">Confirm Password</label>
                                <input type="password" class="form-input" id="register-confirm-password" required>
                            </div>
                            <button type="submit" class="btn btn-primary btn-block">Create Account</button>
                        </form>
                        <div class="auth-link">
                            Already have an account? <a href="#" onclick="showPage('login-page')">Login</a>
                        </div>
                    </div>
                </div>
            </div>
        </main>

        <!-- Bottom Navigation -->
        <nav class="bottom-nav">
            <a href="#" class="nav-item active" onclick="showPage('home-page')">
                <i class="fas fa-home"></i>
                <span>Home</span>
            </a>
            <a href="#" class="nav-item" onclick="showPage('products-page')">
                <i class="fas fa-store"></i>
                <span>Shop</span>
            </a>
            <a href="#" class="nav-item" onclick="showPage('deal-page')">
                <i class="fas fa-tag"></i>
                <span>Deals</span>
            </a>
            <a href="#" class="nav-item" onclick="showPage('cart-page')">
                <i class="fas fa-shopping-cart"></i>
                <span>Cart</span>
            </a>
            <a href="#" class="nav-item" onclick="showPage('profile-page')">
                <i class="fas fa-user"></i>
                <span>Profile</span>
            </a>
        </nav>
    </div>

    <!-- Desktop View -->
    <div class="desktop-view">
        <!-- Desktop Header -->
        <header class="desktop-header">
            <div class="header-content">
                <div class="logo">YL @T.ME</div>
                <nav class="desktop-nav">
                    <a href="#" onclick="showPage('home-page')">Home</a>
                    <a href="#" onclick="showPage('deal-page')">Deals</a>
                    <a href="#" onclick="showPage('products-page')">Products</a>
                    <a href="#" onclick="showPage('activity-page')">Activity</a>
                    <a href="#" onclick="showPage('help-page')">Help</a>
                    <a href="#" onclick="showPage('cart-page')">
                        <i class="fas fa-shopping-cart"></i> Cart
                        <span id="desktop-cart-count" class="cart-count">0</span>
                    </a>
                    <a href="#" onclick="showPage('profile-page')">
                        <i class="fas fa-user"></i> Profile
                    </a>
                </nav>
            </div>
        </header>

        <main class="desktop-main">
            <!-- Desktop Home Page -->
            <div id="desktop-home-page" class="page active">
                <section class="hero">
                    <h1>Welcome to YL @T.ME</h1>
                    <p>Your one-stop destination for premium fashion products</p>
                    <button class="btn btn-primary" onclick="showPage('products-page')">Shop Now</button>
                </section>

                <h2 class="section-title">Featured Products</h2>
                <div class="product-grid" id="desktop-featured-products">
                    <!-- Products will be loaded by JavaScript -->
                </div>

                <h2 class="section-title">Categories</h2>
                <div class="categories-grid" id="desktop-categories">
                    <!-- Categories will be loaded by JavaScript -->
                </div>
            </div>

            <!-- Desktop Products Page -->
            <div id="desktop-products-page" class="page">
                <div class="admin-header">
                    <h2 class="section-title">All Products</h2>
                    <select class="form-select" id="desktop-category-filter" onchange="filterProducts()" style="width: auto; margin-left: auto;">
                        <option value="all">All Categories</option>
                    </select>
                </div>
                <div class="product-grid" id="desktop-all-products">
                    <!-- Products will be loaded by JavaScript -->
                </div>
            </div>

            <!-- Desktop Categories Page -->
            <div id="desktop-categories-page" class="page">
                <h2 class="section-title">Browse Categories</h2>
                <div class="categories-grid" id="desktop-all-categories">
                    <!-- Categories will be loaded by JavaScript -->
                </div>
            </div>

            <!-- Desktop Deal Page -->
            <div id="desktop-deal-page" class="page">
                <div class="deal-banner">
                    <h2>FLASH SALE</h2>
                    <p>Limited time offers! Don't miss out on these amazing deals</p>
                    <div class="deal-timer">
                        <div class="timer-unit">
                            <div class="timer-value" id="desktop-hours">24</div>
                            <div class="timer-label">HOURS</div>
                        </div>
                        <div class="timer-unit">
                            <div class="timer-value" id="desktop-minutes">60</div>
                            <div class="timer-label">MINUTES</div>
                        </div>
                        <div class="timer-unit">
                            <div class="timer-value" id="desktop-seconds">60</div>
                            <div class="timer-label">SECONDS</div>
                        </div>
                    </div>
                </div>
                
                <div class="filter-bar">
                    <div class="filter-item active">All Deals</div>
                    <div class="filter-item">Ending Soon</div>
                    <div class="filter-item">Popular</div>
                    <div class="filter-item">Bestsellers</div>
                </div>
                
                <div class="section-header">
                    <h2>Hot Deals</h2>
                    <div class="view-all">View All</div>
                </div>
                <div class="product-grid" id="desktop-deals-products-grid"></div>
                
                <div class="section-header">
                    <h2>Limited Time Offers</h2>
                    <div class="view-all">View All</div>
                </div>
                <div class="product-grid" id="desktop-limited-products-grid"></div>
            </div>

            <!-- Desktop Cart Page -->
            <div id="desktop-cart-page" class="page">
                <h2 class="section-title">Your Cart</h2>
                <div id="desktop-cart-items">
                    <!-- Cart items will be loaded by JavaScript -->
                </div>
                <div class="cart-total">
                    <div class="total-row">
                        <span>Subtotal:</span>
                        <span id="desktop-cart-subtotal">$0.00</span>
                    </div>
                    <div class="total-row">
                        <span>Tax:</span>
                        <span id="desktop-cart-tax">$0.00</span>
                    </div>
                    <div class="total-row total-final">
                        <span>Total:</span>
                        <span id="desktop-cart-total">$0.00</span>
                    </div>
                    <button class="btn btn-primary btn-block mt-4" onclick="showPage('payment-page')">Proceed to Payment</button>
                </div>
            </div>

            <!-- Desktop Payment Page -->
            <div id="desktop-payment-page" class="page">
                <h2 class="section-title">Payment Gateway</h2>
                
                <div class="payment-container">
                    <h3 style="text-align: center; margin-bottom: 20px;">Choose Payment Method</h3>
                    
                    <div class="payment-methods">
                        <div class="payment-method" onclick="selectPaymentMethod('upi')">
                            <div class="payment-icon">📱</div>
                            <h4>UPI Payment</h4>
                            <p>Pay using UPI QR Code</p>
                        </div>

                        <div class="payment-method" onclick="selectPaymentMethod('card')">
                            <div class="payment-icon">💳</div>
                            <h4>Credit/Debit Card</h4>
                            <p>Visa, Mastercard, RuPay</p>
                        </div>

                        <div class="payment-method" onclick="selectPaymentMethod('netbanking')">
                            <div class="payment-icon">🏦</div>
                            <h4>Net Banking</h4>
                            <p>All major banks</p>
                        </div>

                        <div class="payment-method" onclick="selectPaymentMethod('wallet')">
                            <div class="payment-icon">👛</div>
                            <h4>Digital Wallet</h4>
                            <p>Paytm, PhonePe, Google Pay</p>
                        </div>
                    </div>

                    <!-- UPI Payment Details -->
                    <div id="desktop-upi-details" class="payment-details">
                        <div class="upi-qr-container">
                            <div class="upi-qr-code">
                                <i class="fas fa-qrcode"></i>
                            </div>
                            <h4>Scan QR Code to Pay</h4>
                            <p>Amount: <strong id="desktop-upi-amount">$0.00</strong></p>
                            <p>UPI ID: <strong>yl@paytm</strong></p>
                            <button class="btn btn-success mt-4" onclick="processUPIPayment()">
                                <i class="fas fa-check"></i> I have made the payment
                            </button>
                        </div>
                    </div>

                    <!-- Card Payment Details -->
                    <div id="desktop-card-details" class="payment-details">
                        <div class="card-logos">
                            <div class="card-logo">VISA</div>
                            <div class="card-logo">MC</div>
                            <div class="card-logo">RUPAY</div>
                        </div>
                        
                        <form id="desktop-card-form" class="card-form">
                            <div class="form-group">
                                <label class="form-label">Card Number</label>
                                <input type="text" class="form-input" placeholder="1234 5678 9012 3456" maxlength="19" required>
                            </div>
                            
                            <div class="card-input-group">
                                <div class="form-group">
                                    <label class="form-label">Expiry Date</label>
                                    <input type="text" class="form-input" placeholder="MM/YY" maxlength="5" required>
                                </div>
                                
                                <div class="form-group">
                                    <label class="form-label">CVV</label>
                                    <input type="text" class="form-input" placeholder="123" maxlength="3" required>
                                </div>
                            </div>
                            
                            <div class="form-group">
                                <label class="form-label">Cardholder Name</label>
                                <input type="text" class="form-input" placeholder="John Doe" required>
                            </div>
                            
                            <button type="submit" class="btn btn-success btn-block">
                                <i class="fas fa-lock"></i> Pay $<span id="desktop-card-amount">0.00</span>
                            </button>
                        </form>
                    </div>

                    <!-- Net Banking Details -->
                    <div id="desktop-netbanking-details" class="payment-details">
                        <div class="form-group">
                            <label class="form-label">Select Bank</label>
                            <select class="form-select" required>
                                <option value="">Choose your bank</option>
                                <option value="sbi">State Bank of India</option>
                                <option value="hdfc">HDFC Bank</option>
                                <option value="icici">ICICI Bank</option>
                                <option value="axis">Axis Bank</option>
                                <option value="kotak">Kotak Mahindra Bank</option>
                            </select>
                        </div>
                        <button class="btn btn-success btn-block" onclick="processNetBankingPayment()">
                            Continue to Bank Portal
                        </button>
                    </div>

                    <!-- Wallet Payment Details -->
                    <div id="desktop-wallet-details" class="payment-details">
                        <div class="payment-methods" style="grid-template-columns: 1fr;">
                            <div class="payment-method" onclick="selectWallet('paytm')">
                                <div class="payment-icon" style="color: #002e6e;">P</div>
                                <h4>Paytm</h4>
                            </div>
                            <div class="payment-method" onclick="selectWallet('phonepe')">
                                <div class="payment-icon" style="color: #673ab7;">P</div>
                                <h4>PhonePe</h4>
                            </div>
                            <div class="payment-method" onclick="selectWallet('gpay')">
                                <div class="payment-icon" style="color: #4285f4;">G</div>
                                <h4>Google Pay</h4>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Desktop Payment Success Page -->
            <div id="desktop-payment-success-page" class="page">
                <div class="payment-container">
                    <div class="payment-success">
                        <div class="success-icon">
                            <i class="fas fa-check-circle"></i>
                        </div>
                        <h3>Payment Successful!</h3>
                        <p>Thank you for your purchase. Your order has been confirmed.</p>
                        <p><strong>Order ID: </strong><span id="desktop-success-order-id">YL-123456</span></p>
                        <p><strong>Amount Paid: </strong><span id="desktop-success-amount">$0.00</span></p>
                        <div style="margin-top: 30px;">
                            <button class="btn btn-primary" onclick="showPage('home-page')">
                                Continue Shopping
                            </button>
                            <button class="btn btn-secondary" onclick="showPage('profile-page')" style="margin-left: 10px;">
                                View Orders
                            </button>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Desktop Profile Page -->
            <div id="desktop-profile-page" class="page">
                <div class="auth-card" style="max-width: 500px; margin: 0 auto;">
                    <h3 class="auth-title">User Profile</h3>
                    <div id="desktop-user-info">
                        <!-- User info will be loaded by JavaScript -->
                    </div>
                    <div class="auth-link">
                        <a href="#" onclick="logout()">Logout</a>
                    </div>
                </div>

                <h3 class="section-title" style="text-align: center;">My Orders</h3>
                <div id="desktop-user-orders">
                    <!-- Orders will be loaded by JavaScript -->
                </div>
            </div>

            <!-- Desktop Admin Page -->
            <div id="desktop-admin-page" class="page">
                <div class="admin-header">
                    <h2 class="section-title">Admin Dashboard</h2>
                    <button class="btn btn-primary" onclick="showAdminTab('products')">Manage Products</button>
                </div>

                <div class="admin-stats">
                    <div class="stat-card">
                        <div class="stat-number" id="desktop-total-products">0</div>
                        <div class="stat-label">Total Products</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-number" id="desktop-total-orders">0</div>
                        <div class="stat-label">Total Orders</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-number" id="desktop-total-users">0</div>
                        <div class="stat-label">Total Users</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-number" id="desktop-total-revenue">$0</div>
                        <div class="stat-label">Total Revenue</div>
                    </div>
                </div>

                <div class="admin-tabs">
                    <div class="tabs-header">
                        <div class="tab active" onclick="showAdminTab('products')">Products</div>
                        <div class="tab" onclick="showAdminTab('orders')">Orders</div>
                        <div class="tab" onclick="showAdminTab('users')">Users</div>
                        <div class="tab" onclick="showAdminTab('upload')">Add Product</div>
                    </div>

                    <div id="desktop-admin-products" class="tab-content active">
                        <table class="table">
                            <thead>
                                <tr>
                                    <th>ID</th>
                                    <th>Name</th>
                                    <th>Category</th>
                                    <th>Price</th>
                                    <th>Status</th>
                                    <th>Actions</th>
                                </tr>
                            </thead>
                            <tbody id="desktop-admin-products-table">
                                <!-- Products will be loaded by JavaScript -->
                            </tbody>
                        </table>
                    </div>

                    <div id="desktop-admin-orders" class="tab-content">
                        <table class="table">
                            <thead>
                                <tr>
                                    <th>Order ID</th>
                                    <th>Customer</th>
                                    <th>Amount</th>
                                    <th>Status</th>
                                    <th>Date</th>
                                    <th>Actions</th>
                                </tr>
                            </thead>
                            <tbody id="desktop-admin-orders-table">
                                <!-- Orders will be loaded by JavaScript -->
                            </tbody>
                        </table>
                    </div>

                    <div id="desktop-admin-users" class="tab-content">
                        <table class="table">
                            <thead>
                                <tr>
                                    <th>ID</th>
                                    <th>Name</th>
                                    <th>Email</th>
                                    <th>Role</th>
                                    <th>Joined</th>
                                    <th>Actions</th>
                                </tr>
                            </thead>
                            <tbody id="desktop-admin-users-table">
                                <!-- Users will be loaded by JavaScript -->
                            </tbody>
                        </table>
                    </div>

                    <div id="desktop-admin-upload" class="tab-content">
                        <h3 class="auth-title">Add New Product</h3>
                        <form id="desktop-product-upload-form">
                            <div class="form-group">
                                <label class="form-label">Product Name</label>
                                <input type="text" class="form-input" id="desktop-product-name" required>
                            </div>
                            <div class="form-group">
                                <label class="form-label">Description</label>
                                <textarea class="form-textarea" id="desktop-product-description" required></textarea>
                            </div>
                            <div class="form-group">
                                <label class="form-label">Category</label>
                                <select class="form-select" id="desktop-product-category" required>
                                    <option value="">Select Category</option>
                                    <option value="shoes">Shoes</option>
                                    <option value="watches">Watches</option>
                                    <option value="coats">Coats</option>
                                    <option value="pants">Pants</option>
                                </select>
                            </div>
                            <div class="form-group">
                                <label class="form-label">Price ($)</label>
                                <input type="number" class="form-input" id="desktop-product-price" step="0.01" required>
                            </div>
                            <div class="form-group">
                                <label class="form-label">Product Image URL</label>
                                <input type="url" class="form-input" id="desktop-product-image" placeholder="https://example.com/image.jpg" required>
                            </div>
                            <div class="upload-area" onclick="document.getElementById('desktop-product-image-upload').click()">
                                <div class="upload-icon">
                                    <i class="fas fa-cloud-upload-alt"></i>
                                </div>
                                <p>Click to upload product image</p>
                                <input type="file" id="desktop-product-image-upload" accept="image/*" style="display: none;" onchange="handleDesktopImageUpload(event)">
                            </div>
                            <button type="submit" class="btn btn-primary btn-block">Add Product</button>
                        </form>
                    </div>
                </div>
            </div>

            <!-- Desktop Activity Page -->
            <div id="desktop-activity-page" class="page">
                <h2 class="section-title">Recent Activity</h2>
                <div id="desktop-activity-feed">
                    <!-- Activity items will be loaded by JavaScript -->
                </div>
            </div>

            <!-- Desktop Help Page -->
            <div id="desktop-help-page" class="page">
                <h2 class="section-title">Help & Support</h2>
                <div class="help-grid">
                    <div class="help-card">
                        <div class="help-icon">
                            <i class="fas fa-phone"></i>
                        </div>
                        <h4>Call Us</h4>
                        <p>+1 234 567 8900</p>
                        <p>24/7 Customer Support</p>
                    </div>
                    <div class="help-card">
                        <div class="help-icon">
                            <i class="fas fa-envelope"></i>
                        </div>
                        <h4>Email Us</h4>
                        <p>support@yl.com</p>
                        <p>Response within 24 hours</p>
                    </div>
                    <div class="help-card">
                        <div class="help-icon">
                            <i class="fas fa-comments"></i>
                        </div>
                        <h4>Live Chat</h4>
                        <p>Available 9AM - 9PM</p>
                        <p>Instant support</p>
                    </div>
                </div>

                <div class="whatsapp-contact">
                    <i class="fab fa-whatsapp"></i>
                    <div>
                        <h4>WhatsApp Support</h4>
                        <p>+1 234 567 8901</p>
                    </div>
                </div>

                <h3 class="section-title">Frequently Asked Questions</h3>
                <div class="help-grid">
                    <div class="help-card">
                        <h4>How can I track my order?</h4>
                        <p>You can track your order from the Orders section in your profile.</p>
                    </div>
                    <div class="help-card">
                        <h4>What is your return policy?</h4>
                        <p>We offer 30-day returns for all products in original condition.</p>
                    </div>
                    <div class="help-card">
                        <h4>Do you ship internationally?</h4>
                        <p>Yes, we ship to over 50 countries worldwide.</p>
                    </div>
                </div>
            </div>

            <!-- Desktop Login Page -->
            <div id="desktop-login-page" class="page">
                <div class="auth-container">
                    <div class="auth-card">
                        <h3 class="auth-title">Login</h3>
                        <form id="desktop-login-form">
                            <div class="form-group">
                                <label class="form-label">Email</label>
                                <input type="email" class="form-input" id="desktop-login-email" required>
                            </div>
                            <div class="form-group">
                                <label class="form-label">Password</label>
                                <input type="password" class="form-input" id="desktop-login-password" required>
                            </div>
                            <button type="submit" class="btn btn-primary btn-block">Login</button>
                        </form>
                        <div class="auth-link">
                            Don't have an account? <a href="#" onclick="showPage('desktop-register-page')">Sign up</a>
                        </div>
                        <div class="auth-link">
                            <a href="#" onclick="loginAsAdmin(true)">Login as Admin (Demo)</a>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Desktop Register Page -->
            <div id="desktop-register-page" class="page">
                <div class="auth-container">
                    <div class="auth-card">
                        <h3 class="auth-title">Create Account</h3>
                        <form id="desktop-register-form">
                            <div class="form-group">
                                <label class="form-label">Full Name</label>
                                <input type="text" class="form-input" id="desktop-register-name" required>
                            </div>
                            <div class="form-group">
                                <label class="form-label">Email</label>
                                <input type="email" class="form-input" id="desktop-register-email" required>
                            </div>
                            <div class="form-group">
                                <label class="form-label">Password</label>
                                <input type="password" class="form-input" id="desktop-register-password" required>
                            </div>
                            <div class="form-group">
                                <label class="form-label">Confirm Password</label>
                                <input type="password" class="form-input" id="desktop-register-confirm-password" required>
                            </div>
                            <button type="submit" class="btn btn-primary btn-block">Create Account</button>
                        </form>
                        <div class="auth-link">
                            Already have an account? <a href="#" onclick="showPage('desktop-login-page')">Login</a>
                        </div>
                    </div>
                </div>
            </div>
        </main>
    </div>

    <script>
        // Database Structure
        const DB = {
            init() {
                if (!localStorage.getItem('yl_users')) {
                    localStorage.setItem('yl_users', JSON.stringify([]));
                }
                if (!localStorage.getItem('yl_products')) {
                    const sampleProducts = this.generateSampleProducts();
                    localStorage.setItem('yl_products', JSON.stringify(sampleProducts));
                }
                if (!localStorage.getItem('yl_categories')) {
                    const sampleCategories = [
                        { id: "shoes", name: "Shoes", icon: "👟" },
                        { id: "watches", name: "Watches", icon: "⌚" },
                        { id: "coats", name: "Coats", icon: "🧥" },
                        { id: "pants", name: "Pants", icon: "👖" },
                        { id: "shirts", name: "Shirts", icon: "👔" },
                        { id: "bags", name: "Bags", icon: "👜" },
                        { id: "accessories", name: "Accessories", icon: "👓" },
                        { id: "jewelry", name: "Jewelry", icon: "💍" }
                    ];
                    localStorage.setItem('yl_categories', JSON.stringify(sampleCategories));
                }
                if (!localStorage.getItem('yl_orders')) {
                    localStorage.setItem('yl_orders', JSON.stringify([]));
                }
                if (!localStorage.getItem('yl_cart')) {
                    localStorage.setItem('yl_cart', JSON.stringify([]));
                }
                if (!localStorage.getItem('yl_activity')) {
                    localStorage.setItem('yl_activity', JSON.stringify([]));
                }
                
                const users = JSON.parse(localStorage.getItem('yl_users'));
                if (!users.find(u => u.email === 'admin@yl.com')) {
                    users.push({
                        id: Date.now(),
                        name: "Admin User",
                        email: "admin@yl.com",
                        password: "admin123",
                        role: "admin",
                        createdAt: new Date().toISOString()
                    });
                    localStorage.setItem('yl_users', JSON.stringify(users));
                }
            },

            generateSampleProducts() {
                const categories = ["shoes", "watches", "coats", "pants", "shirts", "bags", "accessories", "jewelry"];
                const products = [];
                
                // Shoe products
                const shoeNames = ["Running Shoes", "Casual Sneakers", "Formal Shoes", "Sports Shoes", "Boots", "Sandals", "Loafers", "Flip Flops"];
                const shoeImages = [
                    "https://images.unsplash.com/photo-1542291026-7eec264c27ff?w=400",
                    "https://images.unsplash.com/photo-1606107557195-0e29a4b5b4aa?w=400",
                    "https://images.unsplash.com/photo-1560769684-5503c4d4e7a9?w=400",
                    "https://images.unsplash.com/photo-1595950653106-6c9ebd614d3a?w=400",
                    "https://images.unsplash.com/photo-1542280756-74b2f55e73ab?w=400",
                    "https://images.unsplash.com/photo-1581101767113-1677fc2beaa8?w=400",
                    "https://images.unsplash.com/photo-1525966222134-fcfa99b8ae77?w=400",
                    "https://images.unsplash.com/photo-1560343090-f0409e92791a?w=400"
                ];
                
                // Watch products
                const watchNames = ["Luxury Watch", "Smart Watch", "Sports Watch", "Classic Watch", "Digital Watch", "Chronograph", "Diver Watch", "Pilot Watch"];
                const watchImages = [
                    "https://images.unsplash.com/photo-1523170335258-f5ed11844a49?w=400",
                    "https://images.unsplash.com/photo-1579586337278-3f436f9389b8?w=400",
                    "https://images.unsplash.com/photo-1523275335684-37898b6baf30?w=400",
                    "https://images.unsplash.com/photo-1547996160-81dfd9c4b1b3?w=400",
                    "https://images.unsplash.com/photo-1508685096489-7aacd43bd3b1?w=400",
                    "https://images.unsplash.com/photo-1434056886845-dac89ffe9b56?w=400",
                    "https://images.unsplash.com/photo-1549972574-8e3e1ed6a3a0?w=400",
                    "https://images.unsplash.com/photo-1587836374828-4dbafa94cf0e?w=400"
                ];
                
                // Coat products
                const coatNames = ["Winter Coat", "Rain Coat", "Leather Jacket", "Trench Coat", "Blazer", "Parka", "Peacoat", "Bomber Jacket"];
                const coatImages = [
                    "https://images.unsplash.com/photo-1551028719-00167b16eac5?w=400",
                    "https://images.unsplash.com/photo-1591047139829-d91aecb6caea?w=400",
                    "https://images.unsplash.com/photo-1551028412-550a67606ac7?w=400",
                    "https://images.unsplash.com/photo-1591047598423-500c3250f5f1?w=400",
                    "https://images.unsplash.com/photo-1593030103066-0093718efeb9?w=400",
                    "https://images.unsplash.com/photo-1539533018447-63fcce2678e3?w=400",
                    "https://images.unsplash.com/photo-1548126032-079a0fb0099d?w=400",
                    "https://images.unsplash.com/photo-1556821840-3a63f95609a7?w=400"
                ];
                
                // Pants products
                const pantsNames = ["Designer Jeans", "Chino Pants", "Cargo Pants", "Formal Trousers", "Joggers", "Leggings", "Shorts", "Slacks"];
                const pantsImages = [
                    "https://images.unsplash.com/photo-1542272604-787c3835535d?w=400",
                    "https://images.unsplash.com/photo-1582418702059-97ebafb35d09?w=400",
                    "https://images.unsplash.com/photo-1586790170083-2f9ceadc732d?w=400",
                    "https://images.unsplash.com/photo-1473966968600-fa801b869a1a?w=400",
                    "https://images.unsplash.com/photo-1506629905607-e91e2ce7fc96?w=400",
                    "https://images.unsplash.com/photo-1506629905608-5a8c58453eba?w=400",
                    "https://images.unsplash.com/photo-1506629905609-9e4f5f9d7e3b?w=400",
                    "https://images.unsplash.com/photo-1506629905602-0a8c58453eb9?w=400"
                ];
                
                // Generate 300+ products
                let id = 1;
                
                // Generate 50 shoes
                for (let i = 0; i < 50; i++) {
                    const nameIndex = i % shoeNames.length;
                    const imageIndex = i % shoeImages.length;
                    products.push({
                        id: id++,
                        name: `${shoeNames[nameIndex]} ${i+1}`,
                        description: `Premium quality ${shoeNames[nameIndex].toLowerCase()} with comfortable design and durable materials.`,
                        price: 49.99 + (i * 5),
                        category: "shoes",
                        image: shoeImages[imageIndex],
                        featured: i < 8,
                        status: "active"
                    });
                }
                
                // Generate 50 watches
                for (let i = 0; i < 50; i++) {
                    const nameIndex = i % watchNames.length;
                    const imageIndex = i % watchImages.length;
                    products.push({
                        id: id++,
                        name: `${watchNames[nameIndex]} ${i+1}`,
                        description: `Elegant ${watchNames[nameIndex].toLowerCase()} with precision movement and stylish design.`,
                        price: 99.99 + (i * 10),
                        category: "watches",
                        image: watchImages[imageIndex],
                        featured: i < 8,
                        status: "active"
                    });
                }
                
                // Generate 50 coats
                for (let i = 0; i < 50; i++) {
                    const nameIndex = i % coatNames.length;
                    const imageIndex = i % coatImages.length;
                    products.push({
                        id: id++,
                        name: `${coatNames[nameIndex]} ${i+1}`,
                        description: `Stylish ${coatNames[nameIndex].toLowerCase()} perfect for any weather condition.`,
                        price: 79.99 + (i * 8),
                        category: "coats",
                        image: coatImages[imageIndex],
                        featured: i < 8,
                        status: "active"
                    });
                }
                
                // Generate 50 pants
                for (let i = 0; i < 50; i++) {
                    const nameIndex = i % pantsNames.length;
                    const imageIndex = i % pantsImages.length;
                    products.push({
                        id: id++,
                        name: `${pantsNames[nameIndex]} ${i+1}`,
                        description: `Comfortable ${pantsNames[nameIndex].toLowerCase()} with perfect fit and modern style.`,
                        price: 39.99 + (i * 4),
                        category: "pants",
                        image: pantsImages[imageIndex],
                        featured: i < 8,
                        status: "active"
                    });
                }
                
                // Generate additional products for other categories
                const additionalCategories = ["shirts", "bags", "accessories", "jewelry"];
                const additionalNames = {
                    shirts: ["Casual Shirt", "Formal Shirt", "T-Shirt", "Polo Shirt", "Dress Shirt", "Flannel Shirt", "Oxford Shirt", "Linen Shirt"],
                    bags: ["Backpack", "Handbag", "Messenger Bag", "Tote Bag", "Clutch", "Duffel Bag", "Crossbody Bag", "Satchel"],
                    accessories: ["Sunglasses", "Belt", "Hat", "Scarf", "Tie", "Wallet", "Gloves", "Cap"],
                    jewelry: ["Necklace", "Bracelet", "Earrings", "Ring", "Anklet", "Brooch", "Cufflinks", "Pendant"]
                };
                
                const additionalImages = {
                    shirts: [
                        "https://images.unsplash.com/photo-1621072156002-e2fccdc0b176?w=400",
                        "https://images.unsplash.com/photo-1596755094514-f87e34085b2c?w=400",
                        "https://images.unsplash.com/photo-1521572163474-6864f9cf17ab?w=400",
                        "https://images.unsplash.com/photo-1503341504253-dff4815485f1?w=400",
                        "https://images.unsplash.com/photo-1503342217502-59b82b9a9d6e?w=400",
                        "https://images.unsplash.com/photo-1503342217502-59b82b9a9d6f?w=400",
                        "https://images.unsplash.com/photo-1503342217502-59b82b9a9d70?w=400",
                        "https://images.unsplash.com/photo-1503342217502-59b82b9a9d71?w=400"
                    ],
                    bags: [
                        "https://images.unsplash.com/photo-1553062407-98eeb64c6a62?w=400",
                        "https://images.unsplash.com/photo-1584917865442-de89df76afd3?w=400",
                        "https://images.unsplash.com/photo-1548036328-c9fa89d128fa?w=400",
                        "https://images.unsplash.com/photo-1553062407-98eeb64c6a63?w=400",
                        "https://images.unsplash.com/photo-1553062407-98eeb64c6a64?w=400",
                        "https://images.unsplash.com/photo-1553062407-98eeb64c6a65?w=400",
                        "https://images.unsplash.com/photo-1553062407-98eeb64c6a66?w=400",
                        "https://images.unsplash.com/photo-1553062407-98eeb64c6a67?w=400"
                    ],
                    accessories: [
                        "https://images.unsplash.com/photo-1572635196237-14b3f281503f?w=400",
                        "https://images.unsplash.com/photo-1582142306909-195724d1a6ec?w=400",
                        "https://images.unsplash.com/photo-1534215754734-18e55d13e346?w=400",
                        "https://images.unsplash.com/photo-1572635196237-14b3f281503e?w=400",
                        "https://images.unsplash.com/photo-1572635196237-14b3f281503d?w=400",
                        "https://images.unsplash.com/photo-1572635196237-14b3f281503c?w=400",
                        "https://images.unsplash.com/photo-1572635196237-14b3f281503b?w=400",
                        "https://images.unsplash.com/photo-1572635196237-14b3f281503a?w=400"
                    ],
                    jewelry: [
                        "https://images.unsplash.com/photo-1515562141207-7a88fb7ce338?w=400",
                        "https://images.unsplash.com/photo-1599643478518-a784e5dc4c8f?w=400",
                        "https://images.unsplash.com/photo-1602173574767-37ac01994b2a?w=400",
                        "https://images.unsplash.com/photo-1515562141207-7a88fb7ce339?w=400",
                        "https://images.unsplash.com/photo-1515562141207-7a88fb7ce340?w=400",
                        "https://images.unsplash.com/photo-1515562141207-7a88fb7ce341?w=400",
                        "https://images.unsplash.com/photo-1515562141207-7a88fb7ce342?w=400",
                        "https://images.unsplash.com/photo-1515562141207-7a88fb7ce343?w=400"
                    ]
                };
                
                // Generate 25 products for each additional category
                for (const category of additionalCategories) {
                    for (let i = 0; i < 25; i++) {
                        const nameIndex = i % additionalNames[category].length;
                        const imageIndex = i % additionalImages[category].length;
                        products.push({
                            id: id++,
                            name: `${additionalNames[category][nameIndex]} ${i+1}`,
                            description: `High-quality ${additionalNames[category][nameIndex].toLowerCase()} with elegant design and premium materials.`,
                            price: 29.99 + (i * 3),
                            category: category,
                            image: additionalImages[category][imageIndex],
                            featured: i < 4,
                            status: "active"
                        });
                    }
                }
                
                return products;
            },

            getUsers() {
                return JSON.parse(localStorage.getItem('yl_users') || '[]');
            },
            
            addUser(user) {
                const users = this.getUsers();
                user.id = Date.now();
                user.createdAt = new Date().toISOString();
                user.role = user.role || 'user';
                users.push(user);
                localStorage.setItem('yl_users', JSON.stringify(users));
                return user;
            },

            getProducts() {
                return JSON.parse(localStorage.getItem('yl_products') || '[]');
            },

            addProduct(product) {
                const products = this.getProducts();
                product.id = Date.now();
                product.createdAt = new Date().toISOString();
                product.status = product.status || 'active';
                products.push(product);
                localStorage.setItem('yl_products', JSON.stringify(products));
                return product;
            },

            updateProduct(id, updates) {
                const products = this.getProducts();
                const index = products.findIndex(p => p.id === id);
                if (index !== -1) {
                    products[index] = { ...products[index], ...updates };
                    localStorage.setItem('yl_products', JSON.stringify(products));
                    return products[index];
                }
                return null;
            },

            deleteProduct(id) {
                const products = this.getProducts();
                const filtered = products.filter(p => p.id !== id);
                localStorage.setItem('yl_products', JSON.stringify(filtered));
                return filtered;
            },

            getCategories() {
                return JSON.parse(localStorage.getItem('yl_categories') || '[]');
            },

            addCategory(category) {
                const categories = this.getCategories();
                category.id = category.name.toLowerCase().replace(/\s+/g, '-');
                categories.push(category);
                localStorage.setItem('yl_categories', JSON.stringify(categories));
                return category;
            },

            getOrders() {
                return JSON.parse(localStorage.getItem('yl_orders') || '[]');
            },

            addOrder(order) {
                const orders = this.getOrders();
                order.id = 'YL-' + Date.now();
                order.createdAt = new Date().toISOString();
                order.status = 'completed';
                orders.push(order);
                localStorage.setItem('yl_orders', JSON.stringify(orders));
                
                // Add activity
                this.addActivity({
                    type: 'order',
                    message: `New order #${order.id} placed for $${order.total}`,
                    timestamp: new Date().toISOString()
                });
                
                return order;
            },

            getCart() {
                return JSON.parse(localStorage.getItem('yl_cart') || '[]');
            },

            saveCart(cart) {
                localStorage.setItem('yl_cart', JSON.stringify(cart));
            },

            getActivity() {
                return JSON.parse(localStorage.getItem('yl_activity') || '[]');
            },

            addActivity(activity) {
                const activities = this.getActivity();
                activity.id = Date.now();
                activities.unshift(activity);
                // Keep only last 50 activities
                if (activities.length > 50) {
                    activities.splice(50);
                }
                localStorage.setItem('yl_activity', JSON.stringify(activities));
                return activity;
            }
        };

        // Initialize database
        DB.init();

        // App State
        let currentUser = JSON.parse(localStorage.getItem('currentUser')) || null;
        let cart = DB.getCart();
        let selectedPaymentMethod = null;
        let selectedWallet = null;

        // Initialize App
        document.addEventListener('DOMContentLoaded', function() {
            loadProducts();
            loadCategories();
            updateCartUI();
            checkAuthStatus();
            updateNavigation();
            setupPaymentForms();
            loadActivity();
            updateAdminStats();
            startFlashSaleTimer();
        });

        // Payment Gateway Functions
        function setupPaymentForms() {
            // Card form submission for mobile
            document.getElementById('card-form')?.addEventListener('submit', function(e) {
                e.preventDefault();
                processCardPayment();
            });
            // Card form submission for desktop
            document.getElementById('desktop-card-form')?.addEventListener('submit', function(e) {
                e.preventDefault();
                processCardPayment();
            });
        }

        function selectPaymentMethod(method) {
            selectedPaymentMethod = method;
            
            // Remove active class from all payment methods
            document.querySelectorAll('.payment-method').forEach(pm => {
                pm.classList.remove('active');
            });
            
            // Add active class to selected method
            event.currentTarget.classList.add('active');
            
            // Hide all payment details
            document.querySelectorAll('.payment-details').forEach(detail => {
                detail.classList.remove('active');
            });
            
            // Show selected payment details
            document.getElementById(method + '-details').classList.add('active');
            
            // Update amounts
            updatePaymentAmounts();
        }

        function selectWallet(wallet) {
            selectedWallet = wallet;
            processWalletPayment();
        }

        function updatePaymentAmounts() {
            const total = calculateCartTotal();
            document.getElementById('upi-amount').textContent = '$' + total.toFixed(2);
            document.getElementById('card-amount').textContent = total.toFixed(2);
            document.getElementById('desktop-upi-amount').textContent = '$' + total.toFixed(2);
            document.getElementById('desktop-card-amount').textContent = total.toFixed(2);
        }

        function processUPIPayment() {
            const total = calculateCartTotal();
            showNotification('UPI payment initiated. Please complete the payment in your UPI app.');
            
            // Simulate payment processing
            setTimeout(() => {
                completePayment('upi');
            }, 3000);
        }

        function processCardPayment() {
            const total = calculateCartTotal();
            showNotification('Processing card payment...');
            
            // Simulate payment processing
            setTimeout(() => {
                completePayment('card');
            }, 2000);
        }

        function processNetBankingPayment() {
            const total = calculateCartTotal();
            showNotification('Redirecting to net banking portal...');
            
            // Simulate payment processing
            setTimeout(() => {
                completePayment('netbanking');
            }, 2500);
        }

        function processWalletPayment() {
            const total = calculateCartTotal();
            showNotification(`Processing ${selectedWallet} payment...`);
            
            // Simulate payment processing
            setTimeout(() => {
                completePayment('wallet');
            }, 1500);
        }

        function completePayment(method) {
            // Create order
            const order = {
                userId: currentUser.id,
                items: [...cart],
                total: calculateCartTotal(),
                paymentMethod: method,
                status: 'completed'
            };

            const newOrder = DB.addOrder(order);

            // Clear cart
            cart = [];
            DB.saveCart(cart);
            updateCartUI();

            // Show success page
            document.getElementById('success-order-id').textContent = newOrder.id;
            document.getElementById('success-amount').textContent = '$' + order.total.toFixed(2);
            document.getElementById('desktop-success-order-id').textContent = newOrder.id;
            document.getElementById('desktop-success-amount').textContent = '$' + order.total.toFixed(2);
            showPage('payment-success-page');
            
            showNotification('Payment completed successfully!');
        }

        function calculateCartTotal() {
            const subtotal = cart.reduce((total, item) => total + (item.price * item.quantity), 0);
            const tax = subtotal * 0.1;
            return subtotal + tax;
        }

        // Page Navigation
        function showPage(pageId) {
            // Hide all mobile pages
            document.querySelectorAll('.mobile-view .page').forEach(page => {
                page.classList.remove('active');
            });

            // Hide all desktop pages
            document.querySelectorAll('.desktop-view .page').forEach(page => {
                page.classList.remove('active');
            });

            // Show target mobile page
            const targetMobilePage = document.getElementById(pageId);
            if (targetMobilePage) {
                targetMobilePage.classList.add('active');
            }

            // Show target desktop page
            const targetDesktopPage = document.getElementById('desktop-' + pageId);
            if (targetDesktopPage) {
                targetDesktopPage.classList.add('active');
            }

            updateNavigation();

            if (pageId === 'cart-page') {
                loadCartPage();
            } else if (pageId === 'profile-page') {
                loadProfilePage();
            } else if (pageId === 'payment-page') {
                updatePaymentAmounts();
            } else if (pageId === 'admin-page') {
                loadAdminPage();
            } else if (pageId === 'activity-page') {
                loadActivity();
            } else if (pageId === 'deal-page') {
                startFlashSaleTimer();
            }
        }

        function loadProducts() {
            const products = DB.getProducts().filter(p => p.status === 'active');
            const featuredProducts = products.filter(p => p.featured);
            const categories = DB.getCategories();

            const productHTML = (product) => `
                <div class="product-card">
                    ${product.featured ? '<span class="product-badge">Featured</span>' : ''}
                    <img src="${product.image}" alt="${product.name}" class="product-image">
                    <h3 class="product-title">${product.name}</h3>
                    <p class="product-description">${product.description}</p>
                    <div class="product-footer">
                        <span class="product-price">$${product.price.toFixed(2)}</span>
                        <button class="add-to-cart" onclick="addToCart(${product.id})">
                            Add to Cart
                        </button>
                    </div>
                </div>
            `;

            const mobileContainers = [
                { id: 'featured-products', products: featuredProducts },
                { id: 'all-products', products: products },
                { id: 'deals-products-grid', products: featuredProducts.slice(0, 4) },
                { id: 'limited-products-grid', products: products.slice(4, 8) }
            ];

            const desktopContainers = [
                { id: 'desktop-featured-products', products: featuredProducts },
                { id: 'desktop-all-products', products: products },
                { id: 'desktop-deals-products-grid', products: featuredProducts.slice(0, 4) },
                { id: 'desktop-limited-products-grid', products: products.slice(4, 8) }
            ];

            [...mobileContainers, ...desktopContainers].forEach(container => {
                const elem = document.getElementById(container.id);
                if (elem) {
                    elem.innerHTML = container.products.map(p => productHTML(p)).join('');
                }
            });

            // Category filters
            const filters = ['category-filter', 'desktop-category-filter'];
            filters.forEach(filterId => {
                const filter = document.getElementById(filterId);
                if (filter) {
                    filter.innerHTML = `
                        <option value="all">All Categories</option>
                        ${categories.map(cat => `<option value="${cat.id}">${cat.name}</option>`).join('')}
                    `;
                }
            });
        }

        function loadCategories() {
            const categories = DB.getCategories();
            
            const categoryHTML = (category) => `
                <div class="category-card" onclick="filterByCategory('${category.id}')">
                    <div class="category-icon">${category.icon}</div>
                    <h4>${category.name}</h4>
                </div>
            `;

            const containers = [
                'categories-grid', 'all-categories',
                'desktop-categories', 'desktop-all-categories'
            ];

            containers.forEach(containerId => {
                const container = document.getElementById(containerId);
                if (container) {
                    container.innerHTML = categories.map(c => categoryHTML(c)).join('');
                }
            });
        }

        function addToCart(productId) {
            if (!currentUser) {
                showPage('login-page');
                showNotification('Please login to add items to cart');
                return;
            }

            const products = DB.getProducts();
            const product = products.find(p => p.id === productId);
            const existingItem = cart.find(item => item.id === productId);

            if (existingItem) {
                existingItem.quantity += 1;
            } else {
                cart.push({
                    ...product,
                    quantity: 1
                });
            }

            DB.saveCart(cart);
            updateCartUI();
            showNotification('Product added to cart!');
            
            // Add activity
            DB.addActivity({
                type: 'cart',
                message: `${currentUser.name} added ${product.name} to cart`,
                timestamp: new Date().toISOString()
            });
        }

        function loadCartPage() {
            // Load for both mobile and desktop
            const containers = ['cart-items', 'desktop-cart-items'];
            const subtotalIds = ['cart-subtotal', 'desktop-cart-subtotal'];
            const taxIds = ['cart-tax', 'desktop-cart-tax'];
            const totalIds = ['cart-total', 'desktop-cart-total'];

            if (cart.length === 0) {
                containers.forEach(containerId => {
                    const container = document.getElementById(containerId);
                    if (container) {
                        container.innerHTML = `
                            <div class="text-center">
                                <p>Your cart is empty</p>
                                <button class="btn btn-primary mt-4" onclick="showPage('products-page')">
                                    Continue Shopping
                                </button>
                            </div>
                        `;
                    }
                });
                return;
            }

            const cartHTML = cart.map(item => `
                <div class="cart-item">
                    <img src="${item.image}" alt="${item.name}" class="cart-item-image">
                    <div class="cart-item-details">
                        <h4 class="cart-item-title">${item.name}</h4>
                        <p class="cart-item-price">$${item.price.toFixed(2)}</p>
                    </div>
                    <div class="cart-actions">
                        <button class="quantity-btn" onclick="updateQuantity(${item.id}, -1)">-</button>
                        <span>${item.quantity}</span>
                        <button class="quantity-btn" onclick="updateQuantity(${item.id}, 1)">+</button>
                        <button class="quantity-btn" onclick="removeFromCart(${item.id})" style="color: var(--danger);">
                            <i class="fas fa-trash"></i>
                        </button>
                    </div>
                </div>
            `).join('');

            containers.forEach(containerId => {
                const container = document.getElementById(containerId);
                if (container) container.innerHTML = cartHTML;
            });

            updateCartTotals(subtotalIds, taxIds, totalIds);
        }

        function updateCartTotals(subtotalIds, taxIds, totalIds) {
            const subtotal = cart.reduce((total, item) => total + (item.price * item.quantity), 0);
            const tax = subtotal * 0.1;
            const total = subtotal + tax;

            subtotalIds.forEach(id => {
                const elem = document.getElementById(id);
                if (elem) elem.textContent = `$${subtotal.toFixed(2)}`;
            });

            taxIds.forEach(id => {
                const elem = document.getElementById(id);
                if (elem) elem.textContent = `$${tax.toFixed(2)}`;
            });

            totalIds.forEach(id => {
                const elem = document.getElementById(id);
                if (elem) elem.textContent = `$${total.toFixed(2)}`;
            });
        }

        function updateCartUI() {
            const cartCount = cart.reduce((total, item) => total + item.quantity, 0);
            
            // Mobile cart nav
            const mobileCartNav = document.querySelector('.bottom-nav .nav-item:nth-child(4)');
            if (mobileCartNav && cartCount > 0) {
                mobileCartNav.innerHTML = `
                    <i class="fas fa-shopping-cart"></i>
                    <span>Cart (${cartCount})</span>
                `;
            }

            // Desktop cart count
            const desktopCartCount = document.getElementById('desktop-cart-count');
            if (desktopCartCount) {
                desktopCartCount.textContent = cartCount;
                desktopCartCount.style.display = cartCount > 0 ? 'inline' : 'none';
            }
        }

        function removeFromCart(productId) {
            cart = cart.filter(item => item.id !== productId);
            DB.saveCart(cart);
            loadCartPage();
            updateCartUI();
        }

        function updateQuantity(productId, change) {
            const item = cart.find(item => item.id === productId);
            if (item) {
                item.quantity += change;
                if (item.quantity <= 0) {
                    removeFromCart(productId);
                } else {
                    DB.saveCart(cart);
                    loadCartPage();
                    updateCartUI();
                }
            }
        }

        function filterByCategory(categoryId) {
            showPage('products-page');
            const filters = document.getElementById('category-filter');
            const desktopFilter = document.getElementById('desktop-category-filter');
            if (filters) filters.value = categoryId;
            if (desktopFilter) desktopFilter.value = categoryId;
            filterProducts();
        }

        function filterProducts() {
            const category = document.getElementById('category-filter')?.value || document.getElementById('desktop-category-filter')?.value || 'all';
            const products = DB.getProducts().filter(p => p.status === 'active');
            const filteredProducts = category === 'all' ? products : products.filter(p => p.category === category);
            
            const allContainer = document.getElementById('all-products');
            const desktopAllContainer = document.getElementById('desktop-all-products');
            if (allContainer || desktopAllContainer) {
                const productHTML = (product) => `
                    <div class="product-card">
                        ${product.featured ? '<span class="product-badge">Featured</span>' : ''}
                        <img src="${product.image}" alt="${product.name}" class="product-image">
                        <h3 class="product-title">${product.name}</h3>
                        <p class="product-description">${product.description}</p>
                        <div class="product-footer">
                            <span class="product-price">$${product.price.toFixed(2)}</span>
                            <button class="add-to-cart" onclick="addToCart(${product.id})">
                                Add to Cart
                            </button>
                        </div>
                    </div>
                `;
                if (allContainer) allContainer.innerHTML = filteredProducts.map(productHTML).join('');
                if (desktopAllContainer) desktopAllContainer.innerHTML = filteredProducts.map(productHTML).join('');
            }
        }

        // Authentication functions
        function loginUser(email, password, isDesktop = false) {
            const users = DB.getUsers();
            const user = users.find(u => u.email === email && u.password === password);
            
            if (user) {
                currentUser = user;
                localStorage.setItem('currentUser', JSON.stringify(user));
                
                showUserInfo(isDesktop);
                if (user.role === 'admin') {
                    showPage('admin-page');
                } else {
                    showPage('home-page');
                }
                showNotification('Login successful!');
                
                // Add activity
                DB.addActivity({
                    type: 'auth',
                    message: `${user.name} logged in`,
                    timestamp: new Date().toISOString()
                });
            } else {
                showNotification('Invalid email or password');
            }
        }

        function loginAsAdmin(isDesktop = false) {
            const emailId = isDesktop ? 'desktop-login-email' : 'login-email';
            const passId = isDesktop ? 'desktop-login-password' : 'login-password';
            document.getElementById(emailId).value = 'admin@yl.com';
            document.getElementById(passId).value = 'admin123';
            loginUser('admin@yl.com', 'admin123', isDesktop);
        }

        function registerUser(name, email, password, isDesktop = false) {
            const users = DB.getUsers();
            const existingUser = users.find(u => u.email === email);
            
            if (existingUser) {
                showNotification('User already exists with this email');
                return;
            }

            const user = DB.addUser({ name, email, password, role: 'user' });
            currentUser = user;
            localStorage.setItem('currentUser', JSON.stringify(user));
            
            showUserInfo(isDesktop);
            showPage('home-page');
            showNotification('Registration successful!');
            
            // Add activity
            DB.addActivity({
                type: 'auth',
                message: `New user ${name} registered`,
                timestamp: new Date().toISOString()
            });
        }

        function showUserInfo(isDesktop = false) {
            const userInfoId = isDesktop ? 'desktop-user-info' : 'user-info';
            const userInfo = document.getElementById(userInfoId);
            if (userInfo && currentUser) {
                userInfo.innerHTML = `
                    <div class="form-group">
                        <label class="form-label">Name</label>
                        <input type="text" class="form-input" value="${currentUser.name}" readonly>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Email</label>
                        <input type="email" class="form-input" value="${currentUser.email}" readonly>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Role</label>
                        <input type="text" class="form-input" value="${currentUser.role}" readonly>
                    </div>
                `;
            }
        }

        function loadProfilePage(isDesktop = false) {
            if (!currentUser) {
                showPage('login-page');
                return;
            }

            showUserInfo(isDesktop);
            loadUserOrders(isDesktop);
        }

        function loadUserOrders(isDesktop = false) {
            const ordersContainerId = isDesktop ? 'desktop-user-orders' : 'user-orders';
            const ordersContainer = document.getElementById(ordersContainerId);
            if (ordersContainer) {
                const orders = DB.getOrders().filter(order => order.userId === currentUser.id);
                
                if (orders.length === 0) {
                    ordersContainer.innerHTML = `
                        <div class="text-center">
                            <p>No orders found</p>
                        </div>
                    `;
                    return;
                }

                ordersContainer.innerHTML = orders.map(order => `
                    <div class="product-card">
                        <h4 class="product-title">Order #${order.id}</h4>
                        <p>Date: ${new Date(order.createdAt).toLocaleDateString()} | Total: $${order.total.toFixed(2)} | Status: ${order.status}</p>
                        <p><strong>Payment Method:</strong> ${order.paymentMethod}</p>
                        <p><strong>Items:</strong> ${order.items.map(item => `${item.name} (x${item.quantity})`).join(', ')}</p>
                        <button class="btn" style="margin-top: 8px;">Download Invoice</button>
                    </div>
                `).join('');
            }
        }

        function logout() {
            // Add activity
            if (currentUser) {
                DB.addActivity({
                    type: 'auth',
                    message: `${currentUser.name} logged out`,
                    timestamp: new Date().toISOString()
                });
            }
            
            currentUser = null;
            localStorage.removeItem('currentUser');
            showPage('home-page');
            showNotification('Logged out successfully');
        }

        function updateNavigation() {
            // Update mobile nav active
            document.querySelectorAll('.bottom-nav .nav-item').forEach(item => {
                item.classList.remove('active');
            });
            const mobileActive = document.querySelector('.bottom-nav a[onclick="showPage(\'home-page\')"]');
            if (mobileActive) mobileActive.parentElement.classList.add('active');

            // Desktop nav no active class needed as it's links
        }

        function checkAuthStatus() {
            if (currentUser) {
                showUserInfo(false);
                showUserInfo(true);
            }
        }

        function showNotification(message) {
            const notification = document.createElement('div');
            notification.className = 'notification';
            notification.textContent = message;
            
            document.body.appendChild(notification);
            
            setTimeout(() => {
                notification.remove();
            }, 3000);
        }

        // Admin Functions
        function showAdminTab(tabName) {
            // Mobile tabs
            document.querySelectorAll('.admin-tabs .tab').forEach(tab => {
                tab.classList.remove('active');
            });
            document.querySelectorAll('.admin-tabs .tab-content').forEach(content => {
                content.classList.remove('active');
            });
            
            document.querySelector(`.tab:nth-child(${['products', 'orders', 'users', 'upload'].indexOf(tabName) + 1})`).classList.add('active');
            document.getElementById(`admin-${tabName}`).classList.add('active');
            
            // Desktop tabs
            document.querySelectorAll('.desktop-view .admin-tabs .tab').forEach(tab => {
                tab.classList.remove('active');
            });
            document.querySelectorAll('.desktop-view .admin-tabs .tab-content').forEach(content => {
                content.classList.remove('active');
            });
            
            document.querySelector(`.desktop-view .tab:nth-child(${['products', 'orders', 'users', 'upload'].indexOf(tabName) + 1})`).classList.add('active');
            document.getElementById(`desktop-admin-${tabName}`).classList.add('active');
            
            if (tabName === 'products') {
                loadAdminProducts();
            } else if (tabName === 'orders') {
                loadAdminOrders();
            } else if (tabName === 'users') {
                loadAdminUsers();
            }
        }

        function loadAdminPage() {
            if (!currentUser || currentUser.role !== 'admin') {
                showPage('login-page');
                showNotification('Admin access required');
                return;
            }
            
            updateAdminStats();
            loadAdminProducts();
        }

        function updateAdminStats() {
            const products = DB.getProducts();
            const orders = DB.getOrders();
            const users = DB.getUsers();
            const revenue = orders.reduce((total, order) => total + order.total, 0);
            
            // Mobile stats
            document.getElementById('total-products').textContent = products.length;
            document.getElementById('total-orders').textContent = orders.length;
            document.getElementById('total-users').textContent = users.length;
            document.getElementById('total-revenue').textContent = '$' + revenue.toFixed(2);
            
            // Desktop stats
            document.getElementById('desktop-total-products').textContent = products.length;
            document.getElementById('desktop-total-orders').textContent = orders.length;
            document.getElementById('desktop-total-users').textContent = users.length;
            document.getElementById('desktop-total-revenue').textContent = '$' + revenue.toFixed(2);
        }

        function loadAdminProducts() {
            const products = DB.getProducts();
            const categories = DB.getCategories();
            
            const productRowHTML = (product) => {
                const category = categories.find(c => c.id === product.category) || { name: 'Unknown' };
                return `
                    <tr>
                        <td>${product.id}</td>
                        <td>${product.name}</td>
                        <td>${category.name}</td>
                        <td>$${product.price.toFixed(2)}</td>
                        <td>${product.status}</td>
                        <td class="action-buttons">
                            <button class="btn btn-primary" onclick="editProduct(${product.id})">Edit</button>
                            <button class="btn btn-danger" onclick="deleteProduct(${product.id})">Delete</button>
                        </td>
                    </tr>
                `;
            };
            
            // Mobile table
            const mobileTable = document.getElementById('admin-products-table');
            if (mobileTable) {
                mobileTable.innerHTML = products.map(p => productRowHTML(p)).join('');
            }
            
            // Desktop table
            const desktopTable = document.getElementById('desktop-admin-products-table');
            if (desktopTable) {
                desktopTable.innerHTML = products.map(p => productRowHTML(p)).join('');
            }
        }

        function loadAdminOrders() {
            const orders = DB.getOrders();
            const users = DB.getUsers();
            
            const orderRowHTML = (order) => {
                const user = users.find(u => u.id === order.userId) || { name: 'Unknown' };
                return `
                    <tr>
                        <td>${order.id}</td>
                        <td>${user.name}</td>
                        <td>$${order.total.toFixed(2)}</td>
                        <td>${order.status}</td>
                        <td>${new Date(order.createdAt).toLocaleDateString()}</td>
                        <td class="action-buttons">
                            <button class="btn btn-primary">View</button>
                        </td>
                    </tr>
                `;
            };
            
            // Mobile table
            const mobileTable = document.getElementById('admin-orders-table');
            if (mobileTable) {
                mobileTable.innerHTML = orders.map(o => orderRowHTML(o)).join('');
            }
            
            // Desktop table
            const desktopTable = document.getElementById('desktop-admin-orders-table');
            if (desktopTable) {
                desktopTable.innerHTML = orders.map(o => orderRowHTML(o)).join('');
            }
        }

        function loadAdminUsers() {
            const users = DB.getUsers();
            
            const userRowHTML = (user) => `
                <tr>
                    <td>${user.id}</td>
                    <td>${user.name}</td>
                    <td>${user.email}</td>
                    <td>${user.role}</td>
                    <td>${new Date(user.createdAt).toLocaleDateString()}</td>
                    <td class="action-buttons">
                        <button class="btn btn-primary">Edit</button>
                    </td>
                </tr>
            `;
            
            // Mobile table
            const mobileTable = document.getElementById('admin-users-table');
            if (mobileTable) {
                mobileTable.innerHTML = users.map(u => userRowHTML(u)).join('');
            }
            
            // Desktop table
            const desktopTable = document.getElementById('desktop-admin-users-table');
            if (desktopTable) {
                desktopTable.innerHTML = users.map(u => userRowHTML(u)).join('');
            }
        }

        function editProduct(productId) {
            const products = DB.getProducts();
            const product = products.find(p => p.id === productId);
            if (product) {
                // In a real app, you would show a modal or form to edit the product
                showNotification(`Editing product: ${product.name}`);
            }
        }

        function deleteProduct(productId) {
            if (confirm('Are you sure you want to delete this product?')) {
                DB.deleteProduct(productId);
                loadAdminProducts();
                updateAdminStats();
                showNotification('Product deleted successfully');
                
                // Add activity
                DB.addActivity({
                    type: 'admin',
                    message: `${currentUser.name} deleted product #${productId}`,
                    timestamp: new Date().toISOString()
                });
            }
        }

        function handleImageUpload(event) {
            const file = event.target.files[0];
            if (file) {
                // In a real app, you would upload the file to a server
                // For this demo, we'll just show a notification
                showNotification('Image uploaded: ' + file.name);
                // You would then set the image URL in the form
                // document.getElementById('product-image').value = uploadedImageUrl;
            }
        }

        function handleDesktopImageUpload(event) {
            const file = event.target.files[0];
            if (file) {
                // In a real app, you would upload the file to a server
                // For this demo, we'll just show a notification
                showNotification('Image uploaded: ' + file.name);
                // You would then set the image URL in the form
                // document.getElementById('desktop-product-image').value = uploadedImageUrl;
            }
        }

        // Activity Functions
        function loadActivity() {
            const activities = DB.getActivity();
            
            const activityHTML = (activity) => {
                const icons = {
                    'order': '🛒',
                    'cart': '🛍️',
                    'auth': '👤',
                    'admin': '⚙️'
                };
                
                return `
                    <div class="activity-item">
                        <div class="activity-icon">
                            ${icons[activity.type] || '📝'}
                        </div>
                        <div>
                            <p>${activity.message}</p>
                            <small>${new Date(activity.timestamp).toLocaleString()}</small>
                        </div>
                    </div>
                `;
            };
            
            // Mobile activity
            const mobileActivity = document.getElementById('activity-feed');
            if (mobileActivity) {
                mobileActivity.innerHTML = activities.map(a => activityHTML(a)).join('');
            }
            
            // Desktop activity
            const desktopActivity = document.getElementById('desktop-activity-feed');
            if (desktopActivity) {
                desktopActivity.innerHTML = activities.map(a => activityHTML(a)).join('');
            }
        }

        // Deal Page Functions
        function startFlashSaleTimer() {
            let hours = 24;
            let minutes = 0;
            let seconds = 0;
            
            const timer = setInterval(() => {
                seconds--;
                if (seconds < 0) {
                    seconds = 59;
                    minutes--;
                    if (minutes < 0) {
                        minutes = 59;
                        hours--;
                        if (hours < 0) {
                            clearInterval(timer);
                            // Reset timer when it reaches 0
                            hours = 24;
                            minutes = 0;
                            seconds = 0;
                        }
                    }
                }
                
                // Update mobile timer
                document.getElementById('hours').textContent = hours.toString().padStart(2, '0');
                document.getElementById('minutes').textContent = minutes.toString().padStart(2, '0');
                document.getElementById('seconds').textContent = seconds.toString().padStart(2, '0');
                
                // Update desktop timer
                document.getElementById('desktop-hours').textContent = hours.toString().padStart(2, '0');
                document.getElementById('desktop-minutes').textContent = minutes.toString().padStart(2, '0');
                document.getElementById('desktop-seconds').textContent = seconds.toString().padStart(2, '0');
            }, 1000);
        }

        // Event listeners for mobile
        document.getElementById('login-form')?.addEventListener('submit', function(e) {
            e.preventDefault();
            const email = document.getElementById('login-email').value;
            const password = document.getElementById('login-password').value;
            if (email && password) {
                loginUser(email, password, false);
            }
        });

        document.getElementById('register-form')?.addEventListener('submit', function(e) {
            e.preventDefault();
            const name = document.getElementById('register-name').value;
            const email = document.getElementById('register-email').value;
            const password = document.getElementById('register-password').value;
            const confirmPassword = document.getElementById('register-confirm-password').value;

            if (password !== confirmPassword) {
                showNotification('Passwords do not match');
                return;
            }

            registerUser(name, email, password, false);
        });

        // Product upload form for mobile
        document.getElementById('product-upload-form')?.addEventListener('submit', function(e) {
            e.preventDefault();
            const name = document.getElementById('product-name').value;
            const description = document.getElementById('product-description').value;
            const category = document.getElementById('product-category').value;
            const price = parseFloat(document.getElementById('product-price').value);
            const image = document.getElementById('product-image').value;

            const product = {
                name,
                description,
                category,
                price,
                image,
                featured: false,
                status: 'active'
            };

            DB.addProduct(product);
            showNotification('Product added successfully!');
            this.reset();
            
            // Add activity
            DB.addActivity({
                type: 'admin',
                message: `${currentUser.name} added new product: ${name}`,
                timestamp: new Date().toISOString()
            });
            
            // Update admin stats and products list
            updateAdminStats();
            loadAdminProducts();
        });

        // Event listeners for desktop
        document.getElementById('desktop-login-form')?.addEventListener('submit', function(e) {
            e.preventDefault();
            const email = document.getElementById('desktop-login-email').value;
            const password = document.getElementById('desktop-login-password').value;
            if (email && password) {
                loginUser(email, password, true);
            }
        });

        document.getElementById('desktop-register-form')?.addEventListener('submit', function(e) {
            e.preventDefault();
            const name = document.getElementById('desktop-register-name').value;
            const email = document.getElementById('desktop-register-email').value;
            const password = document.getElementById('desktop-register-password').value;
            const confirmPassword = document.getElementById('desktop-register-confirm-password').value;

            if (password !== confirmPassword) {
                showNotification('Passwords do not match');
                return;
            }

            registerUser(name, email, password, true);
        });

        // Product upload form for desktop
        document.getElementById('desktop-product-upload-form')?.addEventListener('submit', function(e) {
            e.preventDefault();
            const name = document.getElementById('desktop-product-name').value;
            const description = document.getElementById('desktop-product-description').value;
            const category = document.getElementById('desktop-product-category').value;
            const price = parseFloat(document.getElementById('desktop-product-price').value);
            const image = document.getElementById('desktop-product-image').value;

            const product = {
                name,
                description,
                category,
                price,
                image,
                featured: false,
                status: 'active'
            };

            DB.addProduct(product);
            showNotification('Product added successfully!');
            this.reset();
            
            // Add activity
            DB.addActivity({
                type: 'admin',
                message: `${currentUser.name} added new product: ${name}`,
                timestamp: new Date().toISOString()
            });
            
            // Update admin stats and products list
            updateAdminStats();
            loadAdminProducts();
        });

        // Override showPage for profile and cart to handle desktop
        const originalShowPage = showPage;
        showPage = function(pageId) {
            originalShowPage(pageId);
            if (pageId === 'profile-page') {
                loadProfilePage(window.innerWidth >= 768);
            } else if (pageId === 'cart-page') {
                loadCartPage();
            } else if (pageId === 'admin-page') {
                loadAdminPage();
            } else if (pageId === 'activity-page') {
                loadActivity();
            } else if (pageId === 'deal-page') {
                startFlashSaleTimer();
            }
        };
    </script>
</body>
</html>

<!-- Add to head section -->
<meta name="description" content="YL Premium Fashion - Amazing shoes, watches, coats, and pants for your style">
<meta name="keywords" content="fashion, shoes, watches, coats, pants, online shopping">
<meta property="og:title" content="YL Premium Fashion">
<meta property="og:description" content="Discover amazing fashion products">
<meta property="og:image" content="https://your-site.com/logo.png">

