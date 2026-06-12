<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Undangan Latihan Futsal</title>
    <style>
        /* --- CSS: Desain dan Tampilan --- */
        body {
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #e3f2fd; /* Biru Muda Sangat Tipis */
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            overflow: hidden; /* Mencegah scroll saat button bergerak */
        }

        .card {
            background-color: #ffffff;
            width: 90%;
            max-width: 400px;
            padding: 40px;
            border-radius: 20px;
            box-shadow: 0 10px 25px rgba(33, 150, 243, 0.3);
            text-align: center;
            border: 2px solid #2196f3;
            position: relative;
            z-index: 10;
            transition: all 0.3s ease;
        }

        .stiker {
            font-size: 80px;
            margin-bottom: 10px;
            display: block;
            animation: bounce 2s infinite;
        }

        h1 {
            color: #1565c0; /* Biru Tua */
            margin: 10px 0;
            font-size: 24px;
        }

        p {
            color: #555;
            margin-bottom: 30px;
            font-size: 16px;
            line-height: 1.5;
        }

        .button-container {
            display: flex;
            justify-content: center;
            gap: 15px;
            position: relative;
            height: 50px; /* Area tetap agar layout tidak berantakan */
        }

        .btn {
            padding: 12px 30px;
            border: none;
            border-radius: 50px;
            font-size: 16px;
            font-weight: bold;
            cursor: pointer;
            transition: transform 0.2s;
        }

        .btn:active {
            transform: scale(0.95);
        }

        /* Tombol Ya (Positif) */
        .btn-ya {
            background-color: #2196f3; /* Biru Utama */
            color: white;
            box-shadow: 0 4px 10px rgba(33, 150, 243, 0.4);
        }

        .btn-ya:hover {
            background-color: #1976d2;
        }

        /* Tombol Tidak (Negatif) */
        .btn-tidak {
            background-color: #ffebee;
            color: #c62828;
            border: 1px solid #ef9a9a;
            /* Posisi awal */
            position: absolute; 
            left: 0; 
        }

        .btn-tidak:hover {
            background-color: #ffcdd2;
        }

        /* State setelah klik Ya (Tersembunyi dulu) */
        .hasil-konfirmasi {
            display: none;
            flex-direction: column;
            align-items: center;
            animation: popIn 0.5s ease;
        }

        .hasil-teks {
            font-size: 20px;
            color: #2196f3;
            font-weight: bold;
        }

        /* Animasi */
        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% {transform: translateY(0);}
            40% {transform: translateY(-20px);}
            60% {transform: translateY(-10px);}
        }

        @keyframes popIn {
            0% { opacity: 0; transform: scale(0.8); }
            100% { opacity: 1; transform: scale(1); }
        }

    </style>
</head>
<body>

    <!-- Konten Utama Undangan -->
    <div class="card" id="kartuUndangan">
        <!-- Stiker Futsal -->
        <span class="stiker">⚽️🏃</span>
        
        <h1>Ajakan Latihan Futsal!</h1>
        <p>Halo teman-teman! Kita ada latihan Futsal nih besok malam, jam 19:00 di GOR Jaya. Siapa yang mau gabung?</p>

        <div class="button-container">
            <!-- Tombol Ya -->
            <button class="btn btn-ya" onclick="klikYa()">Ya, Mau!</button>
            
            <!-- Tombol Tidak -->
            <button class="btn btn-tidak" id="tombolTidak" onclick="klikTidak()">Tidak</button>
        </div>
    </div>

    <!-- Tampilan Hasil (Jika Klik Ya) -->
    <div class="card hasil-konfirmasi" id="kartuHasil">
        <span class="stiker">🎉👏</span>
        <h1>Sip! Kita Tunggu!</h1>
        <p class="hasil-teks">Konfirmasi diterima! Jangan lupa pakai sepatu futsal ya. Sampai jumpa di lapangan!</p>
        <button class="btn btn-ya" onclick="location.reload()">Kirim Lagi</button>
    </div>

    <script>
        /* --- JavaScript: Logika dan Interaksi --- */

        function klikYa() {
            // 1. Sembunyikan kartu asli
            document.getElementById('kartuUndangan').style.display = 'none';
            
            // 2. Tampilkan kartu hasil/konfirmasi
            const kartuHasil = document.getElementById('kartuHasil');
            kartuHasil.style.display = 'flex';
            
            // 3. (Optional) Ubah judul dokumen
            document.title = "Kamu Mau Futsal!";
        }

        function klikTidak() {
            const tombolTidak = document.getElementById('tombolTidak');
            
            // Dapatkan dimensi layar (layar HP/Laptop)
            const lebarLayar = window.innerWidth;
            const tinggiLayar = window.innerHeight;
            
            // Offset tolerate agar button tidak hilang sepenuhnya dari view
            const offset = 100;

            // Generate angka acak (random) untuk posisi Baru
            // Math.random() menghasilkan angka 0-1, kita kalikan agar sesuai pixel layar dikurangi ukuran button
            const posisiBaruX = Math.random() * (lebarLayar - offset);
            const posisiBaruY = Math.random() * (tinggiLayar - offset);

            // Terapkan posisi ke button menggunakan CSS styles
            // fixed membuat tombol terlepas dari flow layout dan bergerak bebas di layar
            tombolTidak.style.position = 'fixed'; 
            tombolTidak.style.left = posisiBaruX + 'px';
           汤姆bolTidak.style.top = posisiBaruY + 'px';
            
            // Opsional: Mainkan suara kecil atau efek lainnya di sini
            console.log("Button kabur...");
        }
    </script>

</body>
</html>
