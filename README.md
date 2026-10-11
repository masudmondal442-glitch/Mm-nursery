<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>M.M. Nursery - Fruit Plants App & Store</title>
    <link rel="manifest" href="data:application/json;charset=utf-8,{
        %22name%22: %22M.M. Nursery%22,
        %22short_name%22: %22MM Nursery%22,
        %22start_url%22: %22.%22,
        %22display%22: %22standalone%22,
        %22background_color%22: %22%23f1f8f1%22,
        %22theme_color%22: %22%231b5e20%22,
        %22icons%22: [{%22src%22: %221000620391.png%22, %22sizes%22: %22192x192%22, %22type%22: %22image/png%22}]
    }">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        :root {
            --primary-color: #1b5e20;
            --secondary-color: #2e7d32;
            --accent-color: #fbc02d;
            --dark-color: #0d2810;
            --light-bg: #f1f8f1;
            --text-color: #333;
        }

        body {
            background-color: var(--light-bg);
            color: var(--text-color);
            line-height: 1.6;
            padding-bottom: 70px; /* Space for mobile bottom nav */
        }

        /* Top Bar */
        .top-bar {
            background-color: var(--dark-color);
            color: white;
            padding: 8px 5%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-size: 0.85rem;
            flex-wrap: wrap;
            gap: 10px;
        }

        .top-bar a {
            color: white;
            text-decoration: none;
            margin-right: 15px;
        }

        .install-app-btn {
            background-color: var(--accent-color);
            color: #000;
            border: none;
            padding: 4px 10px;
            border-radius: 15px;
            font-weight: bold;
            cursor: pointer;
            font-size: 0.8rem;
        }

        /* Header */
        header {
            background-color: white;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            position: sticky;
            top: 0;
            z-index: 1000;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 10px 5%;
        }

        .logo-container {
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .logo-container img {
            width: 55px;
            height: 55px;
            border-radius: 50%;
            object-fit: cover;
            border: 2px solid var(--primary-color);
        }

        .logo-text h1 {
            font-size: 1.3rem;
            color: var(--primary-color);
        }

        .logo-text p {
            font-size: 0.75rem;
            color: #555;
            font-weight: bold;
        }

        nav ul {
            display: flex;
            list-style: none;
            gap: 15px;
            align-items: center;
        }

        nav ul li a, nav ul li button {
            text-decoration: none;
            color: var(--text-color);
            font-weight: 600;
            background: none;
            border: none;
            font-size: 1rem;
            cursor: pointer;
            transition: color 0.3s;
        }

        nav ul li a:hover, nav ul li button:hover {
            color: var(--secondary-color);
        }

        /* Banner */
        .hero-banner {
            width: 100%;
            max-height: 380px;
            overflow: hidden;
            background: #000;
        }

        .hero-banner img {
            width: 100%;
            height: auto;
            display: block;
            object-fit: cover;
        }

        /* Views Container */
        .view-section {
            display: none;
            padding: 20px 5%;
        }

        .view-section.active {
            display: block;
        }

        /* Search Section */
        .filter-section {
            padding: 25px 5% 10px;
            text-align: center;
        }

        .search-box {
            width: 100%;
            max-width: 500px;
            padding: 12px 20px;
            font-size: 1rem;
            border: 2px solid #c8e6c9;
            border-radius: 30px;
            outline: none;
            transition: border 0.3s;
        }

        .search-box:focus {
            border-color: var(--primary-color);
        }

        /* Products Catalog */
        .section-title {
            text-align: center;
            font-size: 1.8rem;
            color: var(--primary-color);
            margin-bottom: 25px;
        }

        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
            gap: 20px;
        }

        .product-card {
            background: white;
            border-radius: 12px;
            overflow: hidden;
            box-shadow: 0 4px 12px rgba(0,0,0,0.08);
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            transition: transform 0.3s;
        }

        .product-card:hover {
            transform: translateY(-5px);
        }

        .product-img {
            width: 100%;
            height: 180px;
            object-fit: cover;
            background-color: #e8f5e9;
        }

        .product-details {
            padding: 15px;
            flex-grow: 1;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
        }

        .product-title {
            font-size: 1.1rem;
            color: var(--dark-color);
            margin-bottom: 5px;
            font-weight: bold;
        }

        .product-meta {
            font-size: 0.85rem;
            color: #666;
            margin-bottom: 10px;
        }

        .product-meta span {
            background: #e8f5e9;
            padding: 2px 6px;
            border-radius: 4px;
            color: var(--primary-color);
            font-weight: 600;
        }

        .product-footer {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-top: 10px;
        }

        .product-price {
            font-size: 1.15rem;
            font-weight: bold;
            color: #d32f2f;
        }

        .order-btn {
            background-color: #25D366;
            color: white;
            border: none;
            padding: 8px 14px;
            border-radius: 20px;
            cursor: pointer;
            font-size: 0.9rem;
            font-weight: bold;
            text-decoration: none;
            display: inline-flex;
            align-items: center;
            gap: 5px;
            transition: background 0.3s;
        }

        .order-btn:hover {
            background-color: #1ebe57;
        }

        /* Admin / Management Panel Styles */
        .admin-container {
            background: white;
            padding: 25px;
            border-radius: 12px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.08);
            max-width: 800px;
            margin: 0 auto;
        }

        .admin-container h2 {
            color: var(--primary-color);
            margin-bottom: 20px;
            border-bottom: 2px solid #e8f5e9;
            padding-bottom: 10px;
        }

        .form-group {
            margin-bottom: 15px;
        }

        .form-group label {
            display: block;
            margin-bottom: 5px;
            font-weight: 600;
            color: var(--dark-color);
        }

        .form-group input, .form-group textarea {
            width: 100%;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 6px;
            font-size: 0.95rem;
        }

        .btn-primary {
            background-color: var(--primary-color);
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 6px;
            cursor: pointer;
            font-weight: bold;
            font-size: 1rem;
        }

        .btn-primary:hover {
            background-color: var(--secondary-color);
        }

        .admin-products-table {
            width: 100%;
            margin-top: 20px;
            border-collapse: collapse;
        }

        .admin-products-table th, .admin-products-table td {
            border: 1px solid #ddd;
            padding: 10px;
            text-align: left;
            font-size: 0.9rem;
        }

        .admin-products-table th {
            background-color: #e8f5e9;
            color: var(--primary-color);
        }

        .del-btn {
            background-color: #d32f2f;
            color: white;
            border: none;
            padding: 5px 10px;
            border-radius: 4px;
            cursor: pointer;
        }

        /* Mobile Bottom App Bar */
        .mobile-nav {
            display: none;
            position: fixed;
            bottom: 0;
            left: 0;
            width: 100%;
            background: white;
            box-shadow: 0 -2px 10px rgba(0,0,0,0.1);
            justify-content: space-around;
            padding: 10px 0;
            z-index: 1000;
        }

        .mobile-nav-item {
            text-align: center;
            text-decoration: none;
            color: #555;
            font-size: 0.75rem;
            font-weight: 600;
            background: none;
            border: none;
            cursor: pointer;
        }

        .mobile-nav-item span {
            display: block;
            font-size: 1.2rem;
        }

        .mobile-nav-item.active {
            color: var(--primary-color);
        }

        /* Info Section */
        .info-section {
            background-color: white;
            padding: 40px 5%;
            margin-top: 30px;
            border-top: 3px solid var(--primary-color);
        }

        .info-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 30px;
        }

        .info-box h3 {
            color: var(--primary-color);
            margin-bottom: 15px;
        }

        .info-box p {
            margin-bottom: 10px;
            color: #555;
        }

        footer {
            background-color: var(--dark-color);
            color: white;
            text-align: center;
            padding: 20px;
            font-size: 0.9rem;
        }

        @media(max-width: 768px) {
            nav {
                display: none;
            }
            .mobile-nav {
                display: flex;
            }
            body {
                padding-bottom: 70px;
            }
        }
    </style>
</head>
<body>

    <!-- Top Bar -->
    <div class="top-bar">
        <div>
            <span>📞 <a href="tel:9002152934">9002152934</a></span>
            <span>✉️ <a href="mailto:mmnursery7@gmail.com">mmnursery7@gmail.com</a></span>
        </div>
        <div>
            <button id="installBtn" class="install-app-btn" style="display:none;">📲 Download App</button>
            <span>🌱 Fruit Plants Special</span>
        </div>
    </div>

    <!-- Header -->
    <header>
        <div class="logo-container">
            <img src="1000620391.png" alt="M.M Nursery Logo">
            <div class="logo-text">
                <h1>M.M. NURSERY</h1>
                <p>Grow With Nature, Live Better</p>
            </div>
        </div>
        <nav>
            <ul>
                <li><a href="#" onclick="switchView('home')">Home</a></li>
                <li><a href="#" onclick="switchView('catalog')">Fruit Plants</a></li>
                <li><a href="#" onclick="switchView('admin')">⚙️ Management</a></li>
                <li><a href="#" onclick="switchView('contact')">Contact</a></li>
            </ul>
        </nav>
    </header>

    <!-- HOME VIEW -->
    <div id="home-view" class="view-section active">
        <!-- Banner -->
        <div class="hero-banner">
            <img src="1000614451.png" alt="M.M Nursery Banner" onerror="this.src='https://images.unsplash.com/photo-1585320806297-9794b3e4eeae?auto=format&fit=crop&w=1200&q=80'">
        </div>

        <!-- Search Section -->
        <div class="filter-section">
            <input type="text" id="searchInput" class="search-box" placeholder="Apna pasandida fruit plant search karein (e.g. Mango, Anar, Guava)..." onkeyup="searchPlants()">
        </div>

        <!-- Catalog Section -->
        <section id="catalog" class="catalog-container" style="padding: 20px 0;">
            <h2 class="section-title">Available Fruit Plants Catalog</h2>
            <div class="products-grid" id="productGrid">
                <!-- Dynamic Plants Will Load Here -->
            </div>
        </section>

        <!-- Info & Contact Section -->
        <section id="contact" class="info-section">
            <div class="info-grid">
                <div class="info-box">
                    <h3>M.M. Nursery</h3>
                    <p><strong>Grow with nature, live better.</strong> Humare yahan sabhi prakar ke uchch gunwatta wale fruit plants (falon ke poudhe) uplabdh hain.</p>
                    <p><strong>Phone:</strong> +91 9002152934</p>
                    <p><strong>Email:</strong> mmnursery7@gmail.com</p>
                </div>
                <div class="info-box">
                    <h3>Address</h3>
                    <p>📍 West Bengal, Boheragachi, Prithiba,</p>
                    <p>Habra, North 24 Parganas</p>
                </div>
                <div class="info-box">
                    <h3>Quick Order</h3>
                    <p>Kisi bhi poudhe ko order karne ke liye seedhe WhatsApp par message karein.</p>
                    <a href="https://wa.me/919002152934?text=Hi%20M.M.%20Nursery,%20mujhe%20plants%20chahiye" class="order-btn" target="_blank" style="margin-top: 10px;">💬 Chat on WhatsApp</a>
                </div>
            </div>
        </section>
    </div>

    <!-- MANAGEMENT / ADMIN VIEW -->
    <div id="admin-view" class="view-section">
        <div class="admin-container">
            <h2>⚙️ Plant & Inventory Management</h2>
            <p style="margin-bottom: 20px; color: #555;">Yahan se aap naye plants add kar sakte hain ya existing prices update/delete kar sakte hain.</p>
            
            <form id="addPlantForm" onsubmit="addNewPlant(event)">
                <div class="form-group">
                    <label>Plant Name (Poudhe ka naam)</label>
                    <input type="text" id="newTitle" placeholder="e.g. Alphanso Mango" required>
                </div>
                <div class="form-group">
                    <label>Height / Details</label>
                    <input type="text" id="newHeight" placeholder="e.g. 3 feet" required>
                </div>
                <div class="form-group">
                    <label>Price (₹)</label>
                    <input type="number" id="newPrice" placeholder="e.g. 350" required>
                </div>
                <div class="form-group">
                    <label>Image URL (Photo link)</label>
                    <input type="url" id="newImg" placeholder="https://images.unsplash.com/..." required>
                </div>
                <button type="submit" class="btn-primary">➕ Add Plant to Catalog</button>
            </form>

            <h3 style="margin-top: 30px; color: var(--primary-color);">Manage Current List</h3>
            <div style="overflow-x: auto;">
                <table class="admin-products-table">
                    <thead>
                        <tr>
                            <th>Name</th>
                            <th>Height</th>
                            <th>Price</th>
                            <th>Action</th>
                        </tr>
                    </thead>
                    <tbody id="adminTableBody">
                        <!-- Dynamic Rows -->
                    </tbody>
                </table>
            </div>
        </div>
    </div>

    <!-- Footer -->
    <footer>
        <p>&copy; 2026 M.M. Nursery. All Rights Reserved. Designed for Mobile & Web.</p>
    </footer>

    <!-- Mobile Bottom Navigation -->
    <div class="mobile-nav">
        <button class="mobile-nav-item active" onclick="switchView('home')">
            <span>🏠</span>Home
        </button>
        <button class="mobile-nav-item" onclick="switchView('catalog')">
            <span>🌱</span>Catalog
        </button>
        <button class="mobile-nav-item" onclick="switchView('admin')">
            <span>⚙️</span>Manage
        </button>
        <button class="mobile-nav-item" onclick="switchView('contact')">
            <span>📞</span>Contact
        </button>
    </div>

    <!-- App Logic Script -->
    <script>
        // Default Initial Plants
        const defaultPlants = [
            { id: 1, title: "Ganesh Anar", height: "2.5/3 feet", price: 349, img: "https://images.unsplash.com/photo-1541336115167-124b898a9668?auto=format&fit=crop&w=400&q=80", searchKey: "ganesh anar pomegranate" },
            { id: 2, title: "Kalapati Chiku", height: "2.5/3 feet", price: 299, img: "https://images.unsplash.com/photo-1592150621744-aca64f48394a?auto=format&fit=crop&w=400&q=80", searchKey: "kalapati chiku sapota" },
            { id: 3, title: "Keshar Mango", height: "3 feet", price: 500, img: "https://images.unsplash.com/photo-1553279768-865429fa0078?auto=format&fit=crop&w=400&q=80", searchKey: "keshar mango aam" },
            { id: 4, title: "Barbados Cherry", height: "3 feet", price: 350, img: "https://images.unsplash.com/photo-1528821128474-27f963b062bf?auto=format&fit=crop&w=400&q=80", searchKey: "barbados cherry" },
            { id: 5, title: "All Time Kakji Lemon", height: "2/2.5 feet", price: 250, img: "https://images.unsplash.com/photo-1563822249548-9a72b63ea351?auto=format&fit=crop&w=400&q=80", searchKey: "all time kakji lemon nimbu" },
            { id: 6, title: "Ball Sundari Apple Ber", height: "1.5 feet", price: 199, img: "https://images.unsplash.com/photo-1560806887-1e4cd0b6cbd6?auto=format&fit=crop&w=400&q=80", searchKey: "ball sundari apple ber" },
            { id: 7, title: "Super Bhagava Anar", height: "2.5/3 feet", price: 299, img: "https://images.unsplash.com/photo-1541336115167-124b898a9668?auto=format&fit=crop&w=400&q=80", searchKey: "super bhagava anar" },
            { id: 8, title: "L 49 Guava", height: "3 feet", price: 250, img: "https://images.unsplash.com/photo-1536590158227-e3499fa0d44e?auto=format&fit=crop&w=400&q=80", searchKey: "l 49 guava amrood" },
            { id: 9, title: "Amrupali Mango", height: "3/4 feet", price: 280, img: "https://images.unsplash.com/photo-1553279768-865429fa0078?auto=format&fit=crop&w=400&q=80", searchKey: "amrupali mango aam" },
            { id: 10, title: "Red Guava", height: "2/2.5 feet", price: 250, img: "https://images.unsplash.com/photo-1536590158227-e3499fa0d44e?auto=format&fit=crop&w=400&q=80", searchKey: "red guava amrood" },
            { id: 11, title: "G9 Banana", height: "1.5 feet", price: 200, img: "https://images.unsplash.com/photo-1571771894821-ce9b6c11b08e?auto=format&fit=crop&w=400&q=80", searchKey: "g9 banana kela" },
            { id: 12, title: "Himsagor Mango", height: "3/4 feet", price: 299, img: "https://images.unsplash.com/photo-1553279768-865429fa0078?auto=format&fit=crop&w=400&q=80", searchKey: "himsagor mango aam" }
        ];

        // Load from LocalStorage or Default
        let plants = JSON.parse(localStorage.getItem('mm_nursery_plants')) || defaultPlants;

        function savePlants() {
            localStorage.setItem('mm_nursery_plants', JSON.stringify(plants));
        }

        // Render Catalog & Admin Table
        function renderApp() {
            const grid = document.getElementById('productGrid');
            const tableBody = document.getElementById('adminTableBody');
            
            grid.innerHTML = '';
            tableBody.innerHTML = '';

            plants.forEach(p => {
                // Catalog Card
                grid.innerHTML += `
                    <div class="product-card" data-name="${p.title.toLowerCase()}">
                        <img src="${p.img}" alt="${p.title}" class="product-img">
                        <div class="product-details">
                            <div>
                                <div class="product-title">${p.title}</div>
                                <div class="product-meta">Height: <span>${p.height}</span></div>
                            </div>
                            <div class="product-footer">
                                <div class="product-price">₹${p.price}.00</div>
                                <a href="https://wa.me/919002152934?text=Hi%20M.M.%20Nursery,%20I%20want%20to%20order%20${encodeURIComponent(p.title)}%20(Price:%20₹${p.price})" class="order-btn" target="_blank">Order</a>
                            </div>
                        </div>
                    </div>
                `;

                // Admin Table Row
                tableBody.innerHTML += `
                    <tr>
                        <td><b>${p.title}</b></td>
                        <td>${p.height}</td>
                        <td>₹${p.price}</td>
                        <td><button class="del-btn" onclick="deletePlant(${p.id})">Delete</button></td>
                    </tr>
                `;
            });
        }

        // Add New Plant from Management
        function addNewPlant(e) {
            e.preventDefault();
            const title = document.getElementById('newTitle').value;
            const height = document.getElementById('newHeight').value;
            const price = Number(document.getElementById('newPrice').value);
            const img = document.getElementById('newImg').value;

            const newObj = {
                id: Date.now(),
                title,
                height,
                price,
                img,
                searchKey: title.toLowerCase()
            };

            plants.push(newObj);
            savePlants();
            renderApp();
            document.getElementById('addPlantForm').reset();
            alert('Plant successfully added to store!');
            switchView('catalog');
        }

        // Delete Plant
        function deletePlant(id) {
            if(confirm('Kya aap is plant ko delete karna chahte hain?')) {
                plants = plants.filter(p => p.id !== id);
                savePlants();
                renderApp();
            }
        }

        // Search Filter
        function searchPlants() {
            const input = document.getElementById('searchInput').value.toLowerCase();
            const cards = document.querySelectorAll('.product-card');

            cards.forEach(card => {
                const name = card.getAttribute('data-name');
                if (name.includes(input)) {
                    card.style.display = 'flex';
                } else {
                    card.style.display = 'none';
                }
            });
        }

        // Switch Views (SPA Navigation)
        function switchView(viewName) {
            document.querySelectorAll('.view-section').forEach(el => el.classList.remove('active'));
            document.querySelectorAll('.mobile-nav-item').forEach(el => el.classList.remove('active'));

            if(viewName === 'home') {
                document.getElementById('home-view').classList.add('active');
                window.scrollTo(0,0);
            } else if(viewName === 'catalog') {
                document.getElementById('home-view').classList.add('active');
                document.getElementById('catalog').scrollIntoView({behavior: 'smooth'});
            } else if(viewName === 'admin') {
                document.getElementById('admin-view').classList.add('active');
                window.scrollTo(0,0);
            } else if(viewName === 'contact') {
                document.getElementById('home-view').classList.add('active');
                document.getElementById('contact').scrollIntoView({behavior: 'smooth'});
            }
        }

        // PWA Install Prompt Logic
        let deferredPrompt;
        window.addEventListener('beforeinstallprompt', (e) => {
            e.preventDefault();
            deferredPrompt = e;
            document.getElementById('installBtn').style.display = 'inline-block';
        });

        document.getElementById('installBtn').addEventListener('click', async () => {
            if (deferredPrompt) {
                deferredPrompt.prompt();
                const { outcome } = await deferredPrompt.userChoice;
                if (outcome === 'accepted') {
                    document.getElementById('installBtn').style.display = 'none';
                }
                deferredPrompt = null;
            }
        });

        // Initial Load
        renderApp();
    </script>
</body>
</html>
