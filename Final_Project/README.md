<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>GlamourGlow - Premium Makeup Products</title>
        <!--
                Welcome to GlamourGlow: A demo landing page showcasing featured makeup items.
                Use this file for the public homepage: it contains
                    - the hero banner and primary CTA
                    - featured product cards (click to open images)
                    - Login / Sign Up - UI forms (demo-only: stored in localStorage)
        -->
    <style>
        /*
            Large banner area with an attention-grabbing gradient and product image.
            Contains a call-to-action sign-up button that opens the sign-up UI.
        */
        /*
            The :root CSS variable block makes it easy to change the hero circle size
            across the page. The large hero circle can be adjusted for desktop & mobile
            by changing --hero-circle-size and --hero-circle-mobile-size.
        */
        :root{
            --hero-circle-size: 400px;
            --hero-circle-mobile-size: 300px;
        }

       
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            color: #333;
            padding-top: 80px; /* leave space for fixed nav */
        }
        

        .hero {
            background: linear-gradient(135deg, rgba(255, 20, 147, 0.1), rgba(102, 126, 234, 0.1)),
                        url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1200 600"><defs><linearGradient id="grad1" x1="0%25" y1="0%25" x2="100%25" y2="100%25"><stop offset="0%25" style="stop-color:rgb(255,105,180);stop-opacity:0.1" /><stop offset="100%25" style="stop-color:rgb(102,126,234);stop-opacity:0.1" /></linearGradient></linearGradient></defs><rect width="1200" height="600" fill="url(%23grad1)"/></svg>');
            background-size: cover;
            background-position: center;
            height: calc(100vh - 80px);
            display: flex;
            align-items: center;
            justify-content: center;
            /* margin-top removed; top padding on body handles nav spacing */
            flex-direction: row;
            gap: 4rem;
        }

        .hero-content {
            max-width: 500px;
            color: white;
        }

        .hero h1 {
            font-size: 3.5rem;
            margin-bottom: 1rem;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
        }

        .hero p {
            font-size: 1.3rem;
            margin-bottom: 2rem;
            line-height: 1.6;
        }

        .hero-image {
            width: var(--hero-circle-size);
            height: var(--hero-circle-size);
            background: linear-gradient(135deg, #ff69b4, #764ba2);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 10px 40px rgba(0, 0, 0, 0.3);
            font-size: 120px;
            overflow: hidden; /* make sure inner image respects the circle mask */
        }

        /* Make hero inner images fill the circular area */
        .hero-image img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            display: block;
            border-radius: 50%;
        }

        /* Products Section */
        /*
            The product grid below shows a small selection of featured products.
            On this homepage the 'Add to Cart' buttons prompt login (openLoginUI)
            because we require users to sign in first.
        */
        .products {
            padding: 4rem 2rem;             
            background: white;
        }

        .section-title {
            text-align: center;
            font-size: 2.5rem;
            margin-bottom: 3rem;
            color: #333;
        }

        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 2rem;
            max-width: 1200px;
            margin: 0 auto;
        }

        .product-card {
            background: white;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        .product-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 40px rgba(0, 0, 0, 0.2);
        }

        .product-image {
            width: 100%;
            height: 250px;
            background: linear-gradient(135deg, #ff69b4, #ffa6d1);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 80px;
            color: white;
            object-fit: cover;
        }

        .product-image img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            display: block; /* prevent inline image gap */
            cursor: zoom-in; /* indicate the image can be viewed */
        }

        /* Specific smaller size for one product image (Velvet Lipstick) */
        .product-image.small-product {
            width: var(--hero-circle-size); /* match hero circle size */
            height: var(--hero-circle-size); /* same as width for perfect circle */
            max-width: var(--hero-circle-size); /* limit width to hero circle size */
            margin: 0.6rem auto; /* center within the card */
            border-radius: 50%; /* circle */
            background: radial-gradient(circle at 30% 20%, rgba(255,105,180,0.18), rgba(118,75,162,0.18));
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden; /* clip image to circle */
            box-shadow: 0 8px 30px rgba(118,75,162,0.12);
            transition: transform 0.18s ease, box-shadow 0.18s ease;
        }

        .product-image.small-product img{
            width: 100%;
            height: 100%;
            object-fit: cover; /* fill the circular area */
            display: block;
            border-radius: 0; /* parent handles the circular mask */
        }

        .product-image.small-product:hover {
            transform: translateY(-6px) scale(1.04);
            box-shadow: 0 16px 40px rgba(118,75,162,0.14);
        }

        /* Primary Call-To-Action (CTA) button styling
           Targets the hero 'Shop Now' button which uses class .btn-signup.
           Provides a prominent gradient, padding, shadow and interactive states.
        */
        .btn {
            padding: 0.6rem 1rem;
            border-radius: 8px;
            border: 2px solid transparent;
            cursor: pointer;
            font-family: inherit;
            transition: transform 0.2s ease, box-shadow 0.2s ease, opacity 0.2s ease;
        }

        .btn-signup {
            padding: 0.9rem 1.6rem;
            font-size: 1.05rem;
            border-radius: 12px;
            background: linear-gradient(90deg,#ff8ab8 0%, #ff1493 100%);
            color: #fff;
            border: none;
            box-shadow: 0 8px 20px rgba(255, 20, 147, 0.18);
            font-weight: 700;
        }

        .hero .btn-signup {
            margin-top: 1rem;
        }

        .btn-signup:hover {
            transform: translateY(-4px);
            box-shadow: 0 14px 30px rgba(255, 20, 147, 0.28);
            opacity: 0.98;
        }

        .btn-signup:active {
            transform: translateY(-1px);
        }

        /* Make nav buttons slightly more subtle on the colorful hero background */
        nav .btn {
            background: rgba(255,255,255,0.06);
            color: white;
            border: 1px solid rgba(255,255,255,0.12);
        }

        /* Login button (outline style) - more visible and accessible */
        .btn-login {
            background: transparent; /* transparent over hero gradient */
            color: white;
            border: 1px solid rgba(255,255,255,0.9);
            padding: 0.55rem 1rem;
            border-radius: 10px;
            font-weight: 700;
            transition: background 0.15s ease, color 0.15s ease, transform 0.12s ease;
        }

        .btn-login:hover, .btn-login:focus {
            background: rgba(255,255,255,0.95);
            color: #ff1493;
            transform: translateY(-2px);
            outline: none;
        }

        /* Logo styling - stylize the brand text and make visible on hero */
        .logo {
            font-weight: 800;
            font-size: 1.2rem;
            color: white;
            text-decoration: none;
            display: inline-flex;
            align-items: center;
            gap: 0.4rem;
            letter-spacing: 0.3px;
            text-shadow: 0 2px 8px rgba(0,0,0,0.25);
        }

        .logo::before {
            content: '✨';
            margin-right: 0.25rem;
        }

        /* Navigation layout - logo on the left, nav buttons on the right */
        nav {
            display: flex;
            align-items: center;
            justify-content: space-between; /* pushes nav buttons to the right */
            gap: 0.75rem;
            padding: 1rem 2rem;
            position: sticky;
            top: 0;
            z-index: 150;
            background: transparent; /* keep hero background visible */
        }

        .nav-buttons {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            margin-left: auto; /* ensure buttons stay on the right of the nav */
        }

        /* Ensure login and sign-up buttons look consistent and the same size */
        .nav-buttons .btn {
            padding: 0.8rem 1.2rem;
            min-width: 96px;
            border-radius: 10px;
            font-size: 0.95rem;
            font-weight: 700;
            text-align: center;
        }

        /* Make nav buttons slightly more subtle on the colorful hero background */
        
        
.project-card {
    background: rgba(255,255,255,0.06);
    color: white;
    border: 1px solid rgba(255,255,255,0.2);

    
}

        .nav-buttons .btn-signup {
            padding: 0.8rem 1.2rem; /* match nav button sizing */
            font-size: 0.95rem;
            border-radius: 10px;
        }

        /* Focus outlines for keyboard users */
        .btn:focus, .btn-submit:focus, .btn-add-cart:focus, .quantity-btn:focus {
            outline: 3px solid rgba(255,105,180,0.25);
            outline-offset: 2px;
        }

        /* Make interactive images show a focus outline for keyboard users */
        img[role="button"]:focus {
            outline: 3px solid rgba(255,105,180,0.25);
            outline-offset: 2px;
        }

        .product-info {
            padding: 1.5rem;
        }

        .product-name {
            font-size: 1.3rem;
            font-weight: bold;
            color: #333;
            margin-bottom: 0.5rem;
        }

        .product-description {
            color: #666;
            font-size: 0.9rem;
            margin-bottom: 1rem;
        }

        .price-section {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1rem;
        }

        .product-price {
            font-size: 1.5rem;
            font-weight: bold;
            color: #ff69b4;
        }

        .product-rating {
            color: #ff9800;
            font-size: 0.9rem;
        }

        .btn-add-cart {
            width: 100%;
            padding: 0.8rem;
            background: linear-gradient(135deg, #ff69b4, #ff1493);
            color: white;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s ease;
        }

        .btn-add-cart:hover {
            transform: scale(1.02);
            box-shadow: 0 5px 15px rgba(255, 20, 147, 0.4);
        }

        /* Modal Styles */
        /*
            Styles used by both Login and Sign Up modals. These modals are positioned
            fixed and centered; they use subtle animations for appear/disappear.
        */
        .modal {
            display: none;
            position: fixed;
            z-index: 200;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.6);
            animation: fadeIn 0.3s ease;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        .modal-content {
            background: white;
            margin: 5% auto;
            padding: 2rem;
            border-radius: 15px;
            max-width: 450px;
            box-shadow: 0 10px 40px rgba(0, 0, 0, 0.3);
            animation: slideDown 0.3s ease;
        }

        /* Image modal content: larger, centered and transparent */
        .image-modal-content {
            background: transparent;
            margin: 3% auto;
            padding: 1rem;
            border-radius: 12px;
            max-width: 90%;
            animation: slideDown 0.25s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            flex-direction: column;
            box-shadow: none;
        }

        .image-modal-content .close {
            color: white;
            font-size: 2.2rem;
            position: absolute;
            right: 16px;
            top: 10px;
            background: rgba(0,0,0,0.35);
            padding: 6px 10px;
            border-radius: 6px;
        }

        @keyframes slideDown {
            from { transform: translateY(-50px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        .close {
            float: right;
            font-size: 2rem;
            font-weight: bold;
            color: #999;
            cursor: pointer;
        }

        .close:hover {
            color: #000;
        }

        .modal h2 {
            margin-bottom: 1.5rem;
            color: #333;
        }

        .form-group {
            margin-bottom: 1.2rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            color: #333;
            font-weight: 600;
        }

        .form-group input {
            width: 100%;
            padding: 0.8rem;
            border: 2px solid #ddd;
            border-radius: 8px;
            font-size: 1rem;
            transition: border-color 0.3s ease;
        }

        .form-group input:focus {
            outline: none;
            border-color: #ff69b4;
            box-shadow: 0 0 10px rgba(255, 105, 180, 0.2);
        }

        .btn-submit {
            width: 100%;
            padding: 0.8rem;
            background: linear-gradient(135deg, #ff69b4, #ff1493);
            color: white;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-weight: 600;
            font-size: 1rem;
            transition: all 0.3s ease;
        }

        .btn-submit:hover {
            transform: scale(1.02);
            box-shadow: 0 5px 15px rgba(255, 20, 147, 0.4);
        }

        .toggle-form {
            text-align: center;
            margin-top: 1rem;
            color: #666;
        }

        .toggle-form a {
            color: #ff69b4;
            cursor: pointer;
            font-weight: 600;
            text-decoration: none;
        }

        .toggle-form a:hover {
            text-decoration: underline;
        }

        /* Footer */
        footer {
            background: #333;
            color: white;
            text-align: center;
            padding: 2rem;
        }

        @media (max-width: 768px) {
            :root{ --hero-circle-size: var(--hero-circle-mobile-size); }
            .hero {
                flex-direction: column;
                padding: 2rem;
            }

            .hero h1 {
                font-size: 2.5rem;
            }

            .hero-image {
                width: var(--hero-circle-size);
                height: var(--hero-circle-size);
            }

            .nav-buttons {
                gap: 0.5rem;
            }

            .btn {
                padding: 0.5rem 1rem;
                font-size: 0.9rem;
            }
        }
    </style>
</head>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GlamourGlow - Shop</title>
    <!--
        Project: GlamourGlow - Shop Page
        This file code contains the logged-in shopping experience: product listing, search
        and a full cart/checkout flow implemented in client-side JavaScript. Data is
        kept in `localStorage` for demo purposes (cart and orders).
    -->
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: #f5f5f5;
            color: #333;
            padding-top: 80px; /* avoid overlap with sticky nav */
        }

          /* Navigation Bar */
          /* Navigation contains the logo, a welcome label and a cart indicator. The
              `cartCount` is clickable and opens the cart modal. */
        nav {
            background: rgba(0, 0, 0, 0.8);
            padding: 1rem 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .logo {
            font-size: 1.8rem;
            font-weight: bold;
            color: #ff69b4;
            text-decoration: none;
            cursor: pointer;
        }

        .nav-info {
            display: flex;
            align-items: center;
            gap: 2rem;
            color: white;
        }

        .user-name {
            font-weight: 600;
        }

        .btn {
            padding: 0.6rem 1.5rem;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            font-size: 1rem;
            font-weight: 600;
            transition: all 0.3s ease;
            text-decoration: none;
        }

        .btn-logout {
            background: #ff69b4;
            color: white;
        }

        .btn-logout:hover {
            background: #ff1493;
            transform: scale(1.05);
        }

        /* Search Section */
        /*
            Search area includes a free-text search input and simple filters for
            category and price. The search hooks into `filterProducts()` to update
            the product grid in real time.
        */
        .search-section {
            background: white;
            padding: 2rem;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            margin-bottom: 2rem;
        }

        .search-container {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            gap: 1rem;
            flex-wrap: wrap;
            align-items: center;
        }

        .search-input {
            flex: 1;
            min-width: 250px;
            padding: 0.8rem 1rem;
            border: 2px solid #ddd;
            border-radius: 8px;
            font-size: 1rem;
            transition: border-color 0.3s ease;
        }

        .search-input:focus {
            outline: none;
            border-color: #ff69b4;
        }

        .filter-group {
            display: flex;
            gap: 1rem;
            flex-wrap: wrap;
        }

        .filter-select {
            padding: 0.8rem 1rem;
            border: 2px solid #ddd;
            border-radius: 8px;
            font-size: 1rem;
            cursor: pointer;
            transition: border-color 0.3s ease;
        }

        .filter-select:focus {
            outline: none;
            border-color: #ff69b4;
        }

        .btn-search {
            padding: 0.8rem 2rem;
            background: linear-gradient(135deg, #ff69b4, #ff1493);
            color: white;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s ease;
        }

        .btn-search:hover {
            transform: scale(1.05);
            box-shadow: 0 5px 15px rgba(255, 20, 147, 0.4);
        }

        /* Main Content */
        /*
            The main content area contains the product listing grid. The products
            are generated dynamically by JavaScript (see `loadProducts`).
        */
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 2rem;
        }

        .products-section {
            margin-top: 2rem;
        }

        .section-title {
            font-size: 2rem;
            margin-bottom: 2rem;
            color: #333;
        }

        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 2rem;
        }

        .product-card {
            background: white;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.1);
         
