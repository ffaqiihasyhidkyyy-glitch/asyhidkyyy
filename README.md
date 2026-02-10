<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Portofolio Pribadi - [Nama Anda]</title>
    <!-- Tambahan Font Awesome untuk ikon sosial media -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        /* Reset dan Font */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        body {
            font-family: 'Playfair Display', serif; /* Font mewah serif */
            background: linear-gradient(135deg, #1a1a1a, #2c2c2c); /* Gradien gelap */
            color: #f4f4f4;
            line-height: 1.6;
            overflow-x: hidden;
        }
        h1, h2, h3 {
            font-weight: 700;
        }
        a {
            text-decoration: none;
            color: #1b5fc5; /* Aksen emas */
            transition: color 0.3s ease;
        }
        a:hover {
            color: #1f77db;
        }

        /* Header */
        header {
            position: fixed;
            top: 0;
            width: 100%;
            background: rgba(26, 26, 26, 0.9);
            backdrop-filter: blur(10px);
            padding: 1rem 2rem;
            z-index: 100;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 2px 10px rgba(0,0,0,0.5);
        }
        nav ul {
            list-style: none;
            display: flex;
        }
        nav ul li {
            margin-left: 2rem;
        }
        nav ul li a {
            font-size: 1.1rem;
            transition: transform 0.3s ease;
        }
        nav ul li a:hover {
            transform: scale(1.1);
        }

        /* Section Umum */
        section {
            padding: 5rem 2rem;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            opacity: 0;
            transform: translateY(50px);
            transition: opacity 1s ease, transform 1s ease;
        }
        section.visible {
            opacity: 1;
            transform: translateY(0);
        }

        /* Hero Section - Background diganti dengan foto Anda */
        #hero {
            background: url('x.jpg') no-repeat center/cover; /* Ganti dengan URL foto Anda */
            position: relative;
        }
        #hero::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.5); /* Overlay untuk keterbacaan teks */
        }
        #hero .content {
            position: relative;
            z-index: 1;
        }
        #hero h1 {
            font-size: 3rem;
            margin-bottom: 1rem;
            animation: fadeInUp 1.5s ease;
        }
        #hero p {
            font-size: 1.5rem;
            margin-bottom: 2rem;
            animation: fadeInUp 2s ease;
        }
        .btn {
            background: linear-gradient(45deg, #1e87e9, #2478d8);
            color: #1a1a1a;
            padding: 1rem 2rem;
            border-radius: 50px;
            font-weight: bold;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        .btn:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 20px rgba(28, 98, 189, 0.5);
        }

        /* About Section - Foto horizontal dan ukuran 30% */
        #about {
            background: #2c2c2c;
        }
        #about .content {
            max-width: 1200px;
            display: flex;
            align-items: center;
            gap: 3rem; /* Jarak rapih antara foto dan teks */
            text-align: left; /* Teks rata kiri untuk keseimbangan */
        }
        #about .photos {
            width: 30%; /* Ukuran foto dikecilkan menjadi 30% */
            display: flex;
            flex-direction: row; /* Foto disusun horizontal (ke samping) */
            gap: 1rem; /* Jarak antara 2 foto */
        }
        #about .photos img {
            width: 48%; /* Setiap foto mengisi setengah dari container (dengan gap) */
            height: auto;
            border-radius: 10px;
            box-shadow: 0 10px 20px rgba(0,0,0,0.5);
            transition: transform 0.3s ease;
        }
        #about .photos img:hover {
            transform: scale(1.05);
        }
        #about .text {
            flex: 1; /* Teks mengisi sisa ruang */
        }
        #about h2 {
            margin-bottom: 1rem;
        }

        /* Portfolio Section - Ukuran diperkecil ~28% dan 7 proyek tersusun rapih */
        #portfolio {
            background: #1a1a1a;
        }
        .portfolio-grid {
            display: grid;
            grid-template-columns: repeat(5, 1fr); /* 5 kolom untuk ukuran ~28% per proyek (dengan gap) */
            gap: 1rem; /* Jarak rapih antar proyek */
            max-width: 1200px;
            width: 100%;
        }
        .project {
            background: rgba(255,255,255,0.1);
            padding: 1rem; /* Padding dikurangi untuk ukuran kecil */
            border-radius: 10px;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        .project:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(0,0,0,0.5);
        }
        .project img {
            width: 100%;
            height: 150px; /* Tinggi dikurangi untuk ukuran kecil */
            object-fit: cover;
            border-radius: 10px;
            margin-bottom: 0.5rem; /* Margin dikurangi */
            cursor: pointer; /* Menunjukkan gambar bisa diklik */
            transition: opacity 0.3s ease;
        }
        .project img:hover {
            opacity: 0.8;
        }
        .project h3 {
            font-size: 1rem; /* Font dikurangi untuk ukuran kecil */
            margin-bottom: 0.5rem;
        }
        .project p {
            font-size: 0.9rem; /* Font dikurangi */
            margin-bottom: 0.5rem;
        }
        .project .btn {
            font-size: 0.9rem; /* Font tombol dikurangi */
            padding: 0.5rem 1rem; /* Padding dikurangi */
            margin-top: 0.5rem;
            display: inline-block;
        }

        /* Contact Section - Diganti dengan sosial media */
        #contact {
            background: #2c2c2c;
        }
        #contact .content {
            max-width: 800px;
        }
        .social-media {
            display: flex;
            justify-content: center;
            gap: 3rem; /* Jarak rapih antar ikon */
            margin-top: 2rem;
        }
        .social-item {
            text-align: center;
        }
        .social-item a {
            display: inline-block;
            font-size: 3rem; /* Ikon besar untuk kesan mewah */
            transition: transform 0.3s ease, color 0.3s ease;
        }
        .social-item a:hover {
            transform: scale(1.2);
            color: #bb0c0c;
        }
        .social-item p {
            margin-top: 0.5rem;
            font-size: 1rem;
            color: #1c92c0;
        }

        /* Footer */
        footer {
            background: #1a1a1a;
            padding: 2rem;
            text-align: center;
        }

        /* Animasi Keyframes */
        @keyframes fadeInUp {
            from { opacity: 0; transform: translateY(30px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* Responsif */
        @media (max-width: 768px) {
            #hero h1 { font-size: 2rem; }
            nav ul { flex-direction: column; }
            #about .content {
                flex-direction: column; /* Stack vertikal di mobile */
                text-align: center;
            }
            #about .photos {
                width: 100%; /* Foto penuh di mobile */
                flex-direction: column; /* Stack vertikal di mobile untuk foto */
            }
            #about .photos img {
                width: 100%; /* Foto penuh di mobile */
            }
            .portfolio-grid {
                grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); /* Responsif di mobile */
            }
            .social-media {
                flex-direction: column; /* Stack vertikal di mobile */
                gap: 2rem;
            }
        }
    </style>
</head>
<body>
    <header>
        <h2>Fakih Asyhidkyy</h2>
        <nav>
            <ul>
                <li><a href="#hero">Beranda</a></li>
                <li><a href="#about">Tentang</a></li>
                <li><a href="#portfolio">Portofolio</a></li>
                <li><a href="#contact">Kontak</a></li>
            </ul>
        </nav>
    </header>

    <section id="hero" class="visible">
        <div class="content">
            <h1>Welcome to my website</h1>
            <p>Development tools ai</p>
            <a href="#about" class="btn">Pelajari Lebih Lanjut</a>
        </div>
    </section>

    <section id="about">
        <div class="content">
            <div class="photos">
                <img src="q.jpeg" alt="Foto 1 [Fakih]"> <!-- Ganti dengan URL foto pertama Anda -->
                <img src="e.jpeg" alt="Foto 2 [Nama Anda]"> <!-- Ganti dengan URL foto kedua Anda -->
            </div>
            <div class="text">
                <h2>Tentang Saya</h2>
                <p>saya seorang pelajar yang menyukai teknologi dan saya berinovasi membuat berbagai tools ai yang simpel dan mudah digunakan , dan saya juga sangat tertarik dengan hal-hal baru maka dari itu saya mempelajari ai dan cara membuat tools nya,</p>
            </div>
        </div>
    </section>

    <section id="portfolio">
        <div class="content">
            <h2>Portofolio</h2>
            <div class="portfolio-grid">
                <div class="project">
                    <a href="https://example.com/project1" target="_blank"> <!-- Ganti dengan URL proyek Anda -->
                        <img src="aii.png" alt="Proyek 1">
                    </a>
                    <h3>GEMINI NANO </h3>
                    <p>Gunakan kekuatan AI Gemini untuk membuat foto produk instan atau gabungkan kenangan Anda menjadi satu mahakarya baru.</p>
                    <a href="https://gemini.google.com/share/16e7cd80c13d" target="_blank" class="btn">Lihat Proyek</a> <!-- Ganti dengan URL proyek Anda -->
                </div>
                <div class="project">
                    <a href="https://example.com/project2" target="_blank"> <!-- Ganti dengan URL proyek Anda -->
                        <img src="https://via.placeholder.com/300x200/333333/ffffff?text=Proyek+2" alt="Proyek 2">
                    </a>
                    <h3>Proyek Mewah 2</h3>
                    <p>Deskripsi singkat proyek ini.</p>
                    <a href="https://example.com/project2" target="_blank" class="btn">Lihat Proyek</a> <!-- Ganti dengan URL proyek Anda -->
                </div>
                <!-- Tambahkan 5 proyek lagi -->
                <div class="project">
                    <a href="https://example.com/project3" target="_blank">
                        <img src="https://via.placeholder.com/300x200/333333/ffffff?text=Proyek+3" alt="Proyek 3">
                    </a>
                    <h3>Proyek Mewah 3</h3>
                    <p>Deskripsi singkat proyek ini.</p>
                    <a href="https://example.com/project3" target="_blank" class="btn">Lihat Proyek</a>
                </div>
                <div class="project">
                    <a href="https://example.com/project4" target="_blank">
                        <img src="https://via.placeholder.com/300x200/333333/ffffff?text=Proyek+4" alt="Proyek 4">
                    </a>
                    <h3>Proyek Mewah 4</h3>
                    <p>Deskripsi singkat proyek ini.</p>
                    <a href="https://example.com/project4" target="_blank" class="btn">Lihat Proyek</a>
                </div>
                <div class="project">
                    <a href="https://example.com/project5" target="_blank">
                        <img src="https://via.placeholder.com/300x200/333333/ffffff?text=Proyek+5" alt="Proyek 5">
                    </a>
                    <h3>Proyek Mewah 5</h3>
                    <p>Deskripsi singkat proyek ini.</p>
                    <a href="https://example.com/project5" target="_blank" class="btn">Lihat Proyek</a>
                </div>
                <div class="project">
                    <a href="https://example.com/project6" target="_blank">
                        <img src="https://via.placeholder.com/300x200/333333/ffffff?text=Proyek+6" alt="Proyek 6">
                    </a>
                    <h3>Proyek Mewah 6</h3>
                    <p>Deskripsi singkat proyek ini.</p>
                    <a href="https://example.com/project6" target="_blank" class="btn">Lihat Proyek</a>
                </div>
                <div class="project">
                    <a href="https://example.com/project7" target="_blank">
                        <img src="https://via.placeholder.com/300x200/333333/ffffff?text=Proyek+7" alt="Proyek 7">
                    </a>
                    <h3>Proyek Mewah 7</h3>
                    <p>Deskripsi singkat proyek ini.</p>
                    <a href="https://example.com/project7" target="_blank" class="btn">Lihat Proyek</a>
                </div>
            </div>
        </div>
    </section>

    <section id="contact">
        <div class="content">
            <h2>Hubungi Saya</h2>
            <p>Ikuti saya di sosial media untuk update terbaru dan kolaborasi!</p>
            <div class="social-media">
                <div class="social-item">
                    <a href="https://www.tiktok.com/@asyhidkyclip?is_from_webapp=1&sender_device=pc" target="_blank"><i class="fab fa-tiktok"></i></a> <!-- Ganti dengan URL TikTok Anda -->
                    <p>TikTok</p>
                </div>
                <div class="social-item">
                    <a href="https://wa.me/yourphonenumber" target="_blank"><i class="fab fa-whatsapp"></i></a> <!-- Ganti dengan nomor WhatsApp Anda (format: wa.me/628xxxxxxxxx) -->
                    <p>WhatsApp</p>
                </div>
                <div class="social-item">
                    <a href="https://www.instagram.com/ffaqiih19?igsh=MWdhY2xpcnB4ZXVyeA==" target="_blank"><i class="fab fa-instagram"></i></a> <!-- Ganti dengan URL Instagram Anda -->
                    <p>Instagram</p>
                </div>
            </div>
        </div>
    </section>

    <footer>
        <p>&copy; 2026 ~ Asyhidkyyy</p>
    </footer>

    <script>
        // Animasi smooth scroll dan visibility
        const sections = document.querySelectorAll('section');
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                }
            });
        }, { threshold: 0.1 });

        sections.forEach(section => observer.observe(section));

        // Smooth scroll untuk navigasi
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                document.querySelector(this.getAttribute('href')).scrollIntoView({
                    behavior: 'smooth'
                });
            });
        });
    </script>
</body>
</html>
