<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Aplikasi CV</title>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; }
        .container { width: 300px; margin: auto; }
        .hidden { display: none; }
    </style>
</head>
<body>
    <div id="loginPage" class="container">
        <h2>Login</h2>
        <input type="email" id="email" placeholder="Masukkan email"><br>
        <input type="password" id="password" placeholder="Masukkan password"><br>
        <button onclick="login()">Login</button>
    </div>

    <div id="formPage" class="container hidden">
        <h2>Isi Data CV</h2>
        <input type="text" id="nama" placeholder="Nama Lengkap"><br>
        <input type="text" id="ttl" placeholder="Tempat, Tanggal Lahir"><br>
        <textarea id="pendidikan" placeholder="Riwayat Pendidikan"></textarea><br>
        <button onclick="submitCV()">Buat CV</button>
    </div>

    <div id="cvPage" class="container hidden">
        <h2>CV Anda</h2>
        <p><strong>Nama:</strong> <span id="cvNama"></span></p>
        <p><strong>Tempat, Tanggal Lahir:</strong> <span id="cvTTL"></span></p>
        <p><strong>Riwayat Pendidikan:</strong> <span id="cvPendidikan"></span></p>
        <p><strong>Email:</strong> <span id="cvEmail"></span></p>
    </div>

    <script>
        function login() {
            const email = document.getElementById('email').value.trim().toLowerCase();
            const password = document.getElementById('password').value.trim();
            
            if (!email.includes('@')) {
                alert('Email tidak valid!');
                return;
            }
            
            const domain = email.split('@')[1];
            console.log("Email yang dimasukkan:", email);
            console.log("Password yang dimasukkan:", password);
            console.log("Domain email:", domain);
            
            const correctPassword = email === 'denno.priasmoro@gmail.com' ? 'Drooveboy10.' : domain;
            
            if (password === correctPassword) {
                localStorage.setItem('userEmail', email);
                document.getElementById('loginPage').classList.add('hidden');
                document.getElementById('formPage').classList.remove('hidden');
            } else {
                alert(`Password salah! \nEmail: ${email} \nPassword yang dimasukkan: ${password} \nPassword yang seharusnya: ${correctPassword}`);
            }
        }

        function submitCV() {
            const nama = document.getElementById('nama').value;
            const ttl = document.getElementById('ttl').value;
            const pendidikan = document.getElementById('pendidikan').value;
            const email = localStorage.getItem('userEmail');
            
            document.getElementById('cvNama').textContent = nama;
            document.getElementById('cvTTL').textContent = ttl;
            document.getElementById('cvPendidikan').textContent = pendidikan;
            document.getElementById('cvEmail').textContent = email;
            
            document.getElementById('formPage').classList.add('hidden');
            document.getElementById('cvPage').classList.remove('hidden');
        }
    </script>
</body>
</html>
