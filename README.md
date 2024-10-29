<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Galeri X-8</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Poppins', sans-serif;
        }

        body {
            background-color: #f0f2f5;
        }

        /* Navbar Styles */
        .navbar {
            position: fixed;
            top: 0;
            width: 100%;
            background: rgba(255, 255, 255, 0.95);
            padding: 1rem 2rem;
            z-index: 1000;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
        }

        .nav-container {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .nav-logo {
            font-size: 1.5rem;
            font-weight: bold;
            color: #1a73e8;
        }

        .nav-menu {
            display: flex;
            gap: 2rem;
        }

        .nav-item {
            list-style: none;
        }

        .nav-link {
            text-decoration: none;
            color: #333;
            font-weight: 500;
            transition: color 0.3s;
        }

        .nav-link:hover {
            color: #1a73e8;
        }

        /* Hero Section */
        .hero {
            height: 60vh;
            background: linear-gradient(rgba(0,0,0,0.6), rgba(0,0,0,0.6)), url('/api/placeholder/1920/1080');
            background-size: cover;
            background-position: center;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            color: white;
            padding: 0 20px;
        }

        .hero-content {
            opacity: 0;
            transform: translateY(20px);
            animation: fadeInUp 1s forwards;
        }

        @keyframes fadeInUp {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .hero h1 {
            font-size: 3.5rem;
            margin-bottom: 1rem;
        }

        .hero p {
            font-size: 1.2rem;
            margin-bottom: 2rem;
        }

        /* Gallery Section */
        .gallery-section {
            padding: 5rem 2rem;
            max-width: 1200px;
            margin: 0 auto;
        }

        .section-title {
            text-align: center;
            margin-bottom: 3rem;
        }

        .section-title h2 {
            font-size: 2.5rem;
            color: #333;
            margin-bottom: 1rem;
        }

        .section-title p {
            color: #666;
        }

        .filter-buttons {
            display: flex;
            justify-content: center;
            gap: 1rem;
            margin-bottom: 2rem;
            flex-wrap: wrap;
        }

        .filter-btn {
            padding: 0.8rem 1.5rem;
            border: none;
            border-radius: 25px;
            background: white;
            color: #333;
            cursor: pointer;
            transition: all 0.3s;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }

        .filter-btn.active {
            background: #1a73e8;
            color: white;
        }

        .gallery-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 2rem;
        }

        .gallery-item {
            position: relative;
            overflow: hidden;
            border-radius: 10px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.1);
            cursor: pointer;
            transition: transform 0.3s;
        }

        .gallery-item:hover {
            transform: translateY(-10px);
        }

        .gallery-item img {
            width: 100%;
            height: 300px;
            object-fit: cover;
            transition: transform 0.3s;
        }

        .gallery-item:hover img {
            transform: scale(1.1);
        }

        .item-overlay {
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            background: linear-gradient(transparent, rgba(0,0,0,0.8));
            padding: 20px;
            color: white;
            transform: translateY(100%);
            transition: transform 0.3s;
        }

        .gallery-item:hover .item-overlay {
            transform: translateY(0);
        }

        /* Modal */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.9);
            z-index: 2000;
            padding: 2rem;
        }

        .modal.active {
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .modal-content {
            max-width: 90%;
            max-height: 90vh;
            position: relative;
        }

        .modal-img {
            max-width: 100%;
            max-height: 90vh;
            object-fit: contain;
        }

        .modal-close {
            position: absolute;
            top: -40px;
            right: 0;
            color: white;
            font-size: 2rem;
            cursor: pointer;
        }

        .modal-nav {
            position: absolute;
            top: 50%;
            transform: translateY(-50%);
            color: white;
            font-size: 2rem;
            cursor: pointer;
            padding: 1rem;
        }

        .modal-prev {
            left: 1rem;
        }

        .modal-next {
            right: 1rem;
        }

        /* Footer */
        footer {
            background: #333;
            color: white;
            padding: 3rem 2rem;
            text-align: center;
        }

        .social-links {
            margin-top: 1.5rem;
            display: flex;
            justify-content: center;
            gap: 1.5rem;
        }

        .social-links a {
            color: white;
            font-size: 1.5rem;
            transition: color 0.3s;
        }

        .social-links a:hover {
            color: #1a73e8;
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .hero h1 {
                font-size: 2.5rem;
            }

            .nav-menu {
                display: none;
            }

            .section-title h2 {
                font-size: 2rem;
            }

            .gallery-grid {
                gap: 1rem;
            }
        }
    </style>
</head>
<body>
    <!-- Navbar -->
    <nav class="navbar">
        <div class="nav-container">
            <div class="nav-logo">Class X-8</div>
            <ul class="nav-menu">
                <li class="nav-item"><a href="kelas.html" class="nav-link">Beranda</a></li>
                <li class="nav-item"><a href="galeri.html" class="nav-link">Galeri</a></li>
                <li class="nav-item"><a href="#about" class="nav-link">Tentang</a></li>
            </ul>
        </div>
    </nav>

    <!-- Hero Section -->
    <section class="hero" id="home">
        <div class="hero-content">
            <h1>Galeri Kelas X-8</h1>
            <p>Suka-suka admin deh</p>
        </div>
    </section>

    <!-- Gallery Section -->
    <section class="gallery-section" id="gallery">
        <div class="section-title">
            <h2>Galeri Foto</h2>
            <p>Koleksi foto kegiatan dan momen di kelas X-8</p>
        </div>

        <div class="filter-buttons">
            <button class="filter-btn active" data-filter="all">Semua</button>
        </div>

        <div class="gallery-grid">
            <!-- Academic -->
            <div class="gallery-item" data-category="all">
                <img src="Hari Santri.jpg" alt="Peringatan Hari Santri">
                <div class="item-overlay">
                    <h3>Hari Santri</h3>
                    <p>Peringatan Hari Santri</p>
                </div>
            </div>

            <!-- Social -->
            <div class="gallery-item" data-category="all">
                <img src="Batik Styling.jpg" alt="Batik Styling">
                <div class="item-overlay">
                    <h3>Batik Styling</h3>
                    <p>Foto Bersama Setelah ICF Vol.2</p>
                </div>
            </div>

            <!-- Sport -->
            <div class="gallery-item" data-category="all">
                <img src="Juara Bilik suara.jpg" alt="Lomba">
                <div class="item-overlay">
                    <h3>Lomba Bilik Suara </h3>
                    <p>Juara 1 Pembuatan Bilik Suara</p>
                </div>
            </div>

            <!-- Art -->
            <div class="gallery-item" data-category="all">
                <img src="Dies Natalis 1.jpg" alt="Foto Bersama">
                <div class="item-overlay">
                    <h3>Class X-8</h3>
                    <p>Foto Bersama dengan Ibu Walikelas saat Perayaan Dies Natalis</p>
                </div>
            </div>

            <!-- Additional items -->
            <div class="gallery-item" data-category="all">
                <img src="Dies Natalis 2.jpg" alt="Foto Bersama">
                <div class="item-overlay">
                    <h3>Class X-8</h3>
                    <p>Foto bersama saat Perayaan Dies Natalis</p>
                </div>
            </div>

            <div class="gallery-item" data-category="all">
                <img src="17 Agustus.jpg" alt="Hari Kemerdekaan">
                <div class="item-overlay">
                    <h3>17 Agustus </h3>
                    <p>Foto Bersama setelah Upacara Peringatan Hari Kemerdekaan</p>
                </div>
            </div>

            <div class="gallery-item" data-category="all">
                <img src="nobar.jpg" alt="Nonton Bersama">
                <div class="item-overlay">
                    <h3>Nobar Sepulang Sekolah</h3>
                    <p>After Nobar Film Perewangan</p>
                </div>
            </div>

            <div class="gallery-item" data-category="all">
                <img src="kumpul (1).jpg" alt="Foto Bersama">
                <div class="item-overlay">
                    <h3>Kumpul Sepulang Sekolah</h3>
                    <p>Kumpul-kumpul sepulang sekolah dirumah Bian</p>
                </div>
            </div>

            <div class="gallery-item" data-category="all">
                <img src="kumpul (3).jpg" alt="Foto Bersama">
                <div class="item-overlay">
                    <h3>MPlS Hari terakhir</h3>
                    <p>Foto bersama kakak PJ setelah MPLS Hari terakhir</p>
                </div>
            </div>

            <div class="gallery-item" data-category="all">
                <img src="kumpul (2).jpg" alt="Foto Bersama">
                <div class="item-overlay">
                    <h3>KBM normal</h3>
                    <p>Foto bersama setelah KBM berjalan dengan normal</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Modal -->
    <div class="modal">
        <div class="modal-content">
            <span class="modal-close">&times;</span>
            <img src="" alt="" class="modal-img">
            <div class="modal-nav modal-prev">
                <i class="fas fa-chevron-left"></i>
            </div>
            <div class="modal-nav modal-next">
                <i class="fas fa-chevron-right"></i>
            </div>
        </div>
    </div>

    <!-- Footer -->
    <footer id="contact">
        <h3>X-8 - Angkatan 2024</h3>
        <div class="social-links">
            <a href="https://www.instagram.com/16greatmen?utm_source=ig_web_button_share_sheet&igsh=ZDNlZDc0MzIxNw=="><i class="fab fa-instagram"></i></a>
        </div>
    </footer>

    <script>
        // Filter Gallery
        const filterButtons = document.querySelectorAll('.filter-btn');
        const galleryItems = document.querySelectorAll('.gallery-item');

        filterButtons.forEach(btn => {
            btn.addEventListener('click', () => {
                // Remove active class from all buttons
                filterButtons.forEach(button => button.classList.remove('active'));
                // Add active class to clicked button
                btn.classList.add('active');

                const filter = btn.getAttribute('data-filter');

                galleryItems.forEach(item => {
                    if (filter === 'all' || item.getAttribute('data-category') === filter) {
                        item.style.display = 'block';
                    } else {
                        item.style.display = 'none';
                    }
                });
            });
        });

        // Modal Gallery
        const modal = document.querySelector('.modal');
        const modalImg = document.querySelector('.modal-img');
        const closeBtn = document.querySelector('.modal-close');
        const prevBtn = document.querySelector('.modal-prev');
        const nextBtn = document.querySelector('.modal-next');
        let currentImageIndex = 0;

        // Open Modal
        galleryItems.forEach((item, index) => {
            item.addEventListener('click', () => {
                currentImageIndex = index;
                updateModalImage();
                modal.classList.add('active');
            });
        });

        // Close Modal
        closeBtn.addEventListener('click', () => {
            modal.classList.remove('active');
        });

        // Navigate Images
        function updateModalImage() {
            const currentItem = galleryItems[currentImageIndex];
            const imgSrc = currentItem.querySelector('img').src;
            modalImg.src = imgSrc;
        }

        prevBtn.addEventListener('click', () => {
            currentImageIndex = (currentImageIndex - 1 + galleryItems.length) % galleryItems.length;
            updateModalImage();
        });

        nextBtn.addEventListener('click', () => {
            currentImageIndex = (currentImageIndex + 1) % galleryItems.length;
            updateModalImage();
        });

        // Close modal on outside click
        modal.addEventListener('click', (e) => {
            if (e.target === modal) {
                modal.classList.remove('active');
            }
        });

        // Smooth Scrolling
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function(e) {
                e.preventDefault();
                document.querySelector(this.getAttribute('href')).scrollIntoView({
                    behavior: 'smooth'
                })
            })
        })
