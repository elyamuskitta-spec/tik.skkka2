<!doctype html>
<html lang="id" class="h-full">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Belajar Komputasional Interaktif</title>
  <script src="https://cdn.tailwindcss.com/3.4.17"></script>
  <script src="/_sdk/element_sdk.js"></script>
  <script src="/_sdk/data_sdk.js"></script>
  <link href="https://fonts.googleapis.com/css2?family=Nunito:wght@400;600;700;800&amp;display=swap" rel="stylesheet">
  <style>
    * { font-family: 'Nunito', sans-serif; }
    .gradient-bg { background: linear-gradient(135deg, #1a1a2e 0%, #16213e 50%, #0f3460 100%); }
    .card-glass { background: rgba(255,255,255,0.1); backdrop-filter: blur(10px); border: 1px solid rgba(255,255,255,0.2); }
    .btn-glow { box-shadow: 0 0 20px rgba(79, 172, 254, 0.4); transition: all 0.3s ease; }
    .btn-glow:hover { box-shadow: 0 0 30px rgba(79, 172, 254, 0.6); transform: translateY(-2px); }
    .menu-card { transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1); }
    .menu-card:hover { transform: scale(1.05); }
    .pulse-animation { animation: pulse 2s infinite; }
    @keyframes pulse { 0%, 100% { opacity: 1; } 50% { opacity: 0.7; } }
    .slide-in { animation: slideIn 0.5s ease-out; }
    @keyframes slideIn { from { opacity: 0; transform: translateY(20px); } to { opacity: 1; transform: translateY(0); } }
    .correct-answer { animation: correctPulse 0.5s ease; }
    @keyframes correctPulse { 0% { transform: scale(1); } 50% { transform: scale(1.05); } 100% { transform: scale(1); } }
    .game-cell { transition: all 0.2s ease; }
    .game-cell:hover { transform: scale(1.1); }
    .progress-fill { transition: width 0.5s ease; }
  </style>
  <style>body { box-sizing: border-box; }</style>
 </head>
 <body class="h-full gradient-bg text-white overflow-auto">
  <div id="app" class="min-h-full w-full"><!-- Main Menu -->
   <div id="main-menu" class="min-h-full flex flex-col items-center justify-center p-6">
    <div class="text-center mb-10 slide-in">
     <div class="text-6xl mb-4">
      🖥️
     </div>
     <h1 id="app-title" class="text-4xl md:text-5xl font-extrabold bg-gradient-to-r from-cyan-400 to-blue-500 bg-clip-text text-transparent mb-3">Belajar Komputasional</h1>
     <p id="welcome-text" class="text-xl text-gray-300">Jelajahi dunia pemrograman dengan cara yang menyenangkan!</p>
    </div>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-6 max-w-4xl w-full"><button onclick="showSection('modul')" class="menu-card card-glass rounded-2xl p-8 text-center cursor-pointer">
      <div class="text-5xl mb-4">
       📚
      </div><h3 class="text-2xl font-bold text-cyan-400 mb-2">Modul Ajar</h3><p class="text-gray-300 text-sm">Pelajari materi berpikir komputasional &amp; pemrograman dasar</p></button> <button onclick="showSection('games')" class="menu-card card-glass rounded-2xl p-8 text-center cursor-pointer">
      <div class="text-5xl mb-4">
       🎮
      </div><h3 class="text-2xl font-bold text-green-400 mb-2">Games</h3><p class="text-gray-300 text-sm">Latih kemampuanmu dengan permainan edukatif</p></button> <button onclick="showSection('quiz-intro')" class="menu-card card-glass rounded-2xl p-8 text-center cursor-pointer">
      <div class="text-5xl mb-4">
       📝
      </div><h3 class="text-2xl font-bold text-purple-400 mb-2">Kuis</h3><p class="text-gray-300 text-sm">Uji pemahamanmu dengan 20 soal pilihan ganda</p></button>
    </div>
    <div class="mt-8"><button onclick="showSection('hasil')" class="text-gray-400 hover:text-white transition-colors flex items-center gap-2"> <span>📊</span> Lihat Riwayat Hasil Kuis </button>
    </div>
   </div><!-- Modul Section -->
   <div id="modul-section" class="hidden min-h-full p-6">
    <div class="max-w-4xl mx-auto"><button onclick="showSection('main')" class="mb-6 flex items-center gap-2 text-cyan-400 hover:text-cyan-300 transition-colors"> ← Kembali ke Menu </button>
     <h2 class="text-3xl font-bold mb-6 text-center">📚 Modul Ajar Interaktif</h2>
     <div class="space-y-4" id="modul-accordion"><!-- Modul 1 -->
      <div class="card-glass rounded-xl overflow-hidden"><button onclick="toggleModul(1)" class="w-full p-5 text-left flex justify-between items-center hover:bg-white/5 transition-colors">
        <div class="flex items-center gap-3"><span class="text-3xl">💻</span> <span class="text-xl font-bold">1. Pemrograman Dasar</span>
        </div><span id="arrow-1" class="text-2xl transition-transform">▼</span> </button>
       <div id="content-1" class="hidden p-5 pt-0 border-t border-white/10">
        <div class="space-y-4 text-gray-200">
         <div class="bg-cyan-500/20 p-4 rounded-lg">
          <h4 class="font-bold text-cyan-400 mb-2">📖 Definisi</h4>
          <p>Keterampilan dasar membuat program komputer yang mencakup struktur program, variabel, looping, kondisi, fungsi, dan algoritma.</p>
         </div>
         <div class="bg-green-500/20 p-4 rounded-lg">
          <h4 class="font-bold text-green-400 mb-2">🎯 Tujuan</h4>
          <p>Mengajarkan cara berpikir logis dan sistematis dalam menyelesaikan masalah.</p>
         </div>
         <div class="bg-purple-500/20 p-4 rounded-lg">
          <h4 class="font-bold text-purple-400 mb-2">🧩 Scratch</h4>
          <p>Bahasa pemrograman visual untuk anak-anak yang menggunakan sistem drag-and-drop blok kode seperti menyusun puzzle.</p>
         </div>
         <div class="bg-yellow-500/20 p-4 rounded-lg">
          <h4 class="font-bold text-yellow-400 mb-2">⚡ Konsep Dasar Scratch</h4>
          <ul class="list-disc list-inside space-y-1 mt-2">
           <li><strong>Kondisi (if-then)</strong> - Membuat keputusan</li>
           <li><strong>Looping</strong> - Mengulang aksi</li>
           <li><strong>Variabel</strong> - Menyimpan informasi</li>
           <li><strong>Fungsi</strong> - Kelompok kode bernama</li>
          </ul>
         </div>
        </div>
       </div>
      </div><!-- Modul 2 -->
      <div class="card-glass rounded-xl overflow-hidden"><button onclick="toggleModul(2)" class="w-full p-5 text-left flex justify-between items-center hover:bg-white/5 transition-colors">
        <div class="flex items-center gap-3"><span class="text-3xl">📊</span> <span class="text-xl font-bold">2. Flowchart (Diagram Alir)</span>
        </div><span id="arrow-2" class="text-2xl transition-transform">▼</span> </button>
       <div id="content-2" class="hidden p-5 pt-0 border-t border-white/10">
        <div class="space-y-4 text-gray-200">
         <div class="bg-cyan-500/20 p-4 rounded-lg">
          <h4 class="font-bold text-cyan-400 mb-2">📖 Definisi</h4>
          <p>Alat bantu berupa diagram grafis dengan simbol tertentu untuk menunjukkan alur logika program.</p>
         </div>
         <div class="bg-green-500/20 p-4 rounded-lg">
          <h4 class="font-bold text-green-400 mb-2">🔧 Kegunaan</h4>
          <p>Memecah masalah kompleks menjadi langkah sederhana dan mengidentifikasi kesalahan logika sebelum menulis kode.</p>
         </div>
         <div class="bg-purple-500/20 p-4 rounded-lg">
          <h4 class="font-bold text-purple-400 mb-2">🛠️ Aplikasi Pembuat</h4>
          <div class="flex flex-wrap gap-2 mt-2"><span class="bg-white/20 px-3 py-1 rounded-full text-sm">Microsoft Visio</span> <span class="bg-white/20 px-3 py-1 rounded-full text-sm">Lucidchart</span> <span class="bg-white/20 px-3 py-1 rounded-full text-sm">draw.io</span> <span class="bg-white/20 px-3 py-1 rounded-full text-sm">SmartDraw</span>
          </div>
         </div>
         <div class="bg-yellow-500/20 p-4 rounded-lg">
          <h4 class="font-bold text-yellow-400 mb-2">🔷 Simbol Flowchart</h4>
          <div class="grid grid-cols-2 gap-3 mt-2">
           <div class="flex items-center gap-2">
            <span class="text-2xl">⬭</span> Oval = Start/End
           </div>
           <div class="flex items-center gap-2">
            <span class="text-2xl">▭</span> Kotak = Proses
           </div>
           <div class="flex items-center gap-2">
            <span class="text-2xl">◇</span> Belah Ketupat = Keputusan
           </div>
           <div class="flex items-center gap-2">
            <span class="text-2xl">▱</span> Jajar Genjang = Input/Output
           </div>
          </div>
         </div>
        </div>
       </div>
      </div><!-- Modul 3 -->
      <div class="card-glass rounded-xl overflow-hidden"><button onclick="toggleModul(3)" class="w-full p-5 text-left flex justify-between items-center hover:bg-white/5 transition-colors">
        <div class="flex items-center gap-3"><span class="text-3xl">🧠</span> <span class="text-xl font-bold">3. Berpikir Komputasional</span>
        </div><span id="arrow-3" class="text-2xl transition-transform">▼</span> </button>
       <div id="content-3" class="hidden p-5 pt-0 border-t border-white/10">
        <div class="space-y-4 text-gray-200">
         <div class="bg-cyan-500/20 p-4 rounded-lg">
          <h4 class="font-bold text-cyan-400 mb-2">📖 Definisi</h4>
          <p>Kemampuan memecahkan masalah kompleks secara sistematis, yang merupakan keahlian penting di abad ke-21.</p>
         </div>
         <div class="bg-gradient-to-r from-purple-500/20 to-pink-500/20 p-4 rounded-lg">
          <h4 class="font-bold text-purple-400 mb-3">🔑 4 Aspek Utama</h4>
          <div class="grid grid-cols-1 md:grid-cols-2 gap-3">
           <div class="bg-white/10 p-3 rounded-lg">
            <div class="flex items-center gap-2 mb-1"><span class="text-xl">🧩</span> <span class="font-bold text-orange-400">Dekomposisi</span>
            </div>
            <p class="text-sm">Memecah masalah besar menjadi bagian-bagian kecil</p>
           </div>
           <div class="bg-white/10 p-3 rounded-lg">
            <div class="flex items-center gap-2 mb-1"><span class="text-xl">🔍</span> <span class="font-bold text-blue-400">Pengenalan Pola</span>
            </div>
            <p class="text-sm">Mencari kesamaan atau pola dalam data</p>
           </div>
           <div class="bg-white/10 p-3 rounded-lg">
            <div class="flex items-center gap-2 mb-1"><span class="text-xl">🎯</span> <span class="font-bold text-green-400">Abstraksi</span>
            </div>
            <p class="text-sm">Mengambil informasi penting, abaikan yang tidak relevan</p>
           </div>
           <div class="bg-white/10 p-3 rounded-lg">
            <div class="flex items-center gap-2 mb-1"><span class="text-xl">📋</span> <span class="font-bold text-cyan-400">Algoritma</span>
            </div>
            <p class="text-sm">Menyusun langkah-langkah terstruktur untuk solusi</p>
           </div>
          </div>
         </div>
        </div>
       </div>
      </div><!-- Modul 4 -->
      <div class="card-glass rounded-xl overflow-hidden"><button onclick="toggleModul(4)" class="w-full p-5 text-left flex justify-between items-center hover:bg-white/5 transition-colors">
        <div class="flex items-center gap-3"><span class="text-3xl">🦫</span> <span class="text-xl font-bold">4. Bebras Challenge</span>
        </div><span id="arrow-4" class="text-2xl transition-transform">▼</span> </button>
       <div id="content-4" class="hidden p-5 pt-0 border-t border-white/10">
        <div class="space-y-4 text-gray-200">
         <div class="bg-cyan-500/20 p-4 rounded-lg">
          <h4 class="font-bold text-cyan-400 mb-2">🦫 Apa itu Bebras?</h4>
          <p>Istilah dari bahasa Lithuania yang berarti "berang-berang".</p>
         </div>
         <div class="bg-green-500/20 p-4 rounded-lg">
          <h4 class="font-bold text-green-400 mb-2">🎯 Tujuan</h4>
          <p>Tantangan internasional untuk mempromosikan berpikir komputasional melalui soal-soal pendek yang menarik.</p>
         </div>
         <div class="bg-purple-500/20 p-4 rounded-lg">
          <h4 class="font-bold text-purple-400 mb-2">🌍 Fakta Menarik</h4>
          <ul class="list-disc list-inside space-y-1 mt-2">
           <li>Diikuti oleh lebih dari 60 negara</li>
           <li>Jutaan siswa berpartisipasi setiap tahun</li>
           <li>Soal dirancang untuk melatih logika</li>
           <li>Tidak memerlukan pengetahuan programming</li>
          </ul>
         </div>
        </div>
       </div>
      </div>
     </div>
    </div>
   </div><!-- Games Section -->
   <div id="games-section" class="hidden min-h-full p-6">
    <div class="max-w-4xl mx-auto"><button onclick="showSection('main')" class="mb-6 flex items-center gap-2 text-cyan-400 hover:text-cyan-300 transition-colors"> ← Kembali ke Menu </button>
     <h2 class="text-3xl font-bold mb-6 text-center">🎮 Games Edukatif</h2>
     <div class="grid grid-cols-1 md:grid-cols-2 gap-6"><!-- Game 1: Pattern Match -->
      <div class="card-glass rounded-xl p-6">
       <div class="text-center mb-4"><span class="text-4xl">🔍</span>
        <h3 class="text-xl font-bold text-green-400 mt-2">Pattern Matcher</h3>
        <p class="text-gray-300 text-sm">Temukan pola yang tepat!</p>
       </div>
       <div id="pattern-game" class="mb-4">
        <div class="text-center mb-3">
         <p class="text-gray-300 mb-2">Lanjutkan pola ini:</p>
         <div id="pattern-sequence" class="flex justify-center gap-2 text-3xl mb-4"></div>
        </div>
        <div id="pattern-options" class="flex justify-center gap-3 flex-wrap"></div>
        <div id="pattern-feedback" class="text-center mt-3 text-lg font-bold"></div>
        <div class="text-center mt-3">
         <p class="text-sm text-gray-400">Skor: <span id="pattern-score">0</span></p>
        </div>
       </div><button onclick="initPatternGame()" class="w-full bg-green-500 hover:bg-green-600 py-2 rounded-lg font-bold transition-colors"> Mulai Ulang </button>
      </div><!-- Game 2: Algorithm Sorter -->
      <div class="card-glass rounded-xl p-6">
       <div class="text-center mb-4"><span class="text-4xl">📋</span>
        <h3 class="text-xl font-bold text-purple-400 mt-2">Urutkan Algoritma</h3>
        <p class="text-gray-300 text-sm">Susun langkah dengan benar!</p>
       </div>
       <div id="algo-game" class="mb-4">
        <p class="text-center text-gray-300 mb-3" id="algo-question">Cara membuat teh:</p>
        <div id="algo-steps" class="space-y-2"></div>
        <div id="algo-feedback" class="text-center mt-3 text-lg font-bold"></div>
        <div class="text-center mt-3">
         <p class="text-sm text-gray-400">Skor: <span id="algo-score">0</span></p>
        </div>
       </div><button onclick="initAlgoGame()" class="w-full bg-purple-500 hover:bg-purple-600 py-2 rounded-lg font-bold transition-colors"> Mulai Ulang </button>
      </div><!-- Game 3: Memory Match -->
      <div class="card-glass rounded-xl p-6">
       <div class="text-center mb-4"><span class="text-4xl">🧠</span>
        <h3 class="text-xl font-bold text-cyan-400 mt-2">Memory Match</h3>
        <p class="text-gray-300 text-sm">Cocokkan istilah dengan definisi!</p>
       </div>
       <div id="memory-game" class="mb-4">
        <div id="memory-grid" class="grid grid-cols-4 gap-2"></div>
        <div id="memory-feedback" class="text-center mt-3 text-lg font-bold"></div>
        <div class="text-center mt-3">
         <p class="text-sm text-gray-400">Pairs: <span id="memory-score">0</span>/6</p>
        </div>
       </div><button onclick="initMemoryGame()" class="w-full bg-cyan-500 hover:bg-cyan-600 py-2 rounded-lg font-bold transition-colors"> Mulai Ulang </button>
      </div><!-- Game 4: Binary Quiz -->
      <div class="card-glass rounded-xl p-6">
       <div class="text-center mb-4"><span class="text-4xl">🔢</span>
        <h3 class="text-xl font-bold text-yellow-400 mt-2">Tebak Konsep</h3>
        <p class="text-gray-300 text-sm">Tebak konsep dari petunjuk!</p>
       </div>
       <div id="concept-game" class="mb-4">
        <div class="bg-white/10 p-4 rounded-lg mb-4">
         <p id="concept-hint" class="text-center text-lg"></p>
        </div>
        <div id="concept-options" class="grid grid-cols-2 gap-2"></div>
        <div id="concept-feedback" class="text-center mt-3 text-lg font-bold"></div>
        <div class="text-center mt-3">
         <p class="text-sm text-gray-400">Skor: <span id="concept-score">0</span></p>
        </div>
       </div><button onclick="initConceptGame()" class="w-full bg-yellow-500 hover:bg-yellow-600 text-black py-2 rounded-lg font-bold transition-colors"> Mulai Ulang </button>
      </div>
     </div>
    </div>
   </div><!-- Quiz Intro Section -->
   <div id="quiz-intro-section" class="hidden min-h-full flex items-center justify-center p-6">
    <div class="max-w-md w-full"><button onclick="showSection('main')" class="mb-6 flex items-center gap-2 text-cyan-400 hover:text-cyan-300 transition-colors"> ← Kembali ke Menu </button>
     <div class="card-glass rounded-2xl p-8 slide-in">
      <div class="text-center mb-6"><span class="text-5xl">📝</span>
       <h2 class="text-2xl font-bold mt-3">Kuis Berpikir Komputasional</h2>
       <p class="text-gray-300 mt-2">20 soal pilihan ganda</p>
      </div>
      <form id="quiz-form" class="space-y-4">
       <div><label class="block text-sm font-medium mb-2">Nama Lengkap *</label> <input type="text" id="nama-input" required class="w-full bg-white/10 border border-white/20 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:outline-none focus:border-cyan-400 transition-colors" placeholder="Masukkan nama lengkap">
       </div>
       <div><label class="block text-sm font-medium mb-2">Kelas *</label> <input type="text" id="kelas-input" required class="w-full bg-white/10 border border-white/20 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:outline-none focus:border-cyan-400 transition-colors" placeholder="Contoh: 7A, 8B, 9C">
       </div><button type="submit" class="w-full bg-gradient-to-r from-cyan-500 to-blue-500 hover:from-cyan-600 hover:to-blue-600 py-3 rounded-lg font-bold text-lg transition-all btn-glow mt-6"> Mulai Kuis → </button>
      </form>
     </div>
    </div>
   </div><!-- Quiz Section -->
   <div id="quiz-section" class="hidden min-h-full p-6">
    <div class="max-w-3xl mx-auto">
     <div class="flex justify-between items-center mb-6">
      <div>
       <p class="text-sm text-gray-400">Peserta: <span id="quiz-nama" class="text-cyan-400"></span></p>
       <p class="text-sm text-gray-400">Kelas: <span id="quiz-kelas" class="text-cyan-400"></span></p>
      </div>
      <div class="text-right">
       <p class="text-sm text-gray-400">Soal <span id="current-question">1</span>/20</p>
      </div>
     </div><!-- Progress Bar -->
     <div class="w-full bg-white/20 rounded-full h-3 mb-6">
      <div id="quiz-progress" class="bg-gradient-to-r from-cyan-500 to-blue-500 h-3 rounded-full progress-fill" style="width: 5%"></div>
     </div>
     <div class="card-glass rounded-2xl p-6">
      <h3 id="question-text" class="text-xl font-bold mb-6"></h3>
      <div id="options-container" class="space-y-3"></div>
     </div>
     <div class="flex justify-between mt-6"><button id="prev-btn" onclick="prevQuestion()" class="bg-white/20 hover:bg-white/30 px-6 py-3 rounded-lg font-bold transition-colors disabled:opacity-50" disabled> ← Sebelumnya </button> <button id="next-btn" onclick="nextQuestion()" class="bg-gradient-to-r from-cyan-500 to-blue-500 hover:from-cyan-600 hover:to-blue-600 px-6 py-3 rounded-lg font-bold transition-colors"> Selanjutnya → </button>
     </div>
    </div>
   </div><!-- Quiz Result Section -->
   <div id="result-section" class="hidden min-h-full flex items-center justify-center p-6">
    <div class="max-w-md w-full">
     <div class="card-glass rounded-2xl p-8 text-center slide-in">
      <div id="result-icon" class="text-6xl mb-4"></div>
      <h2 class="text-3xl font-bold mb-2">Kuis Selesai!</h2>
      <p id="result-name" class="text-gray-300 mb-4"></p>
      <div class="bg-white/10 rounded-xl p-6 mb-6">
       <p class="text-5xl font-extrabold text-cyan-400" id="result-score"></p>
       <p class="text-gray-300">Jawaban Benar</p>
       <div class="mt-3">
        <p class="text-2xl font-bold" id="result-percentage"></p>
       </div>
      </div>
      <div id="result-message" class="text-lg mb-6"></div>
      <div id="saving-status" class="text-sm text-gray-400 mb-4"><span class="pulse-animation">💾 Menyimpan hasil...</span>
      </div>
      <div class="space-y-3"><button onclick="showSection('quiz-intro')" class="w-full bg-gradient-to-r from-cyan-500 to-blue-500 hover:from-cyan-600 hover:to-blue-600 py-3 rounded-lg font-bold transition-all"> Coba Lagi </button> <button onclick="showSection('main')" class="w-full bg-white/20 hover:bg-white/30 py-3 rounded-lg font-bold transition-colors"> Kembali ke Menu </button>
      </div>
     </div>
    </div>
   </div><!-- Hasil Section -->
   <div id="hasil-section" class="hidden min-h-full p-6">
    <div class="max-w-4xl mx-auto"><button onclick="showSection('main')" class="mb-6 flex items-center gap-2 text-cyan-400 hover:text-cyan-300 transition-colors"> ← Kembali ke Menu </button>
     <h2 class="text-3xl font-bold mb-6 text-center">📊 Riwayat Hasil Kuis</h2>
     <div class="card-glass rounded-xl overflow-hidden">
      <div class="overflow-x-auto">
       <table class="w-full">
        <thead class="bg-white/10">
         <tr>
          <th class="px-4 py-3 text-left">No</th>
          <th class="px-4 py-3 text-left">Nama</th>
          <th class="px-4 py-3 text-left">Kelas</th>
          <th class="px-4 py-3 text-center">Skor</th>
          <th class="px-4 py-3 text-center">Persentase</th>
          <th class="px-4 py-3 text-left">Tanggal</th>
         </tr>
        </thead>
        <tbody id="hasil-table-body">
         <tr>
          <td colspan="6" class="px-4 py-8 text-center text-gray-400">Belum ada data hasil kuis</td>
         </tr>
        </tbody>
       </table>
      </div>
     </div>
    </div>
   </div>
  </div>
  <script>
    // Default configuration
    const defaultConfig = {
      app_title: 'Belajar Komputasional',
      welcome_text: 'Jelajahi dunia pemrograman dengan cara yang menyenangkan!',
      background_color: '#1a1a2e',
      card_color: 'rgba(255,255,255,0.1)',
      text_color: '#ffffff',
      primary_action_color: '#06b6d4',
      secondary_action_color: '#8b5cf6'
    };

    let quizResults = [];

    // Data SDK Handler
    const dataHandler = {
      onDataChanged(data) {
        quizResults = data;
        updateHasilTable();
      }
    };

    // Element SDK implementation
    async function onConfigChange(config) {
      const title = document.getElementById('app-title');
      const welcome = document.getElementById('welcome-text');
      if (title) title.textContent = config.app_title || defaultConfig.app_title;
      if (welcome) welcome.textContent = config.welcome_text || defaultConfig.welcome_text;
    }

    // Initialize SDKs
    async function initSDKs() {
      if (window.elementSdk) {
        window.elementSdk.init({
          defaultConfig,
          onConfigChange,
          mapToCapabilities: (config) => ({
            recolorables: [
              {
                get: () => config.background_color || defaultConfig.background_color,
                set: (v) => window.elementSdk.setConfig({ background_color: v })
              },
              {
                get: () => config.primary_action_color || defaultConfig.primary_action_color,
                set: (v) => window.elementSdk.setConfig({ primary_action_color: v })
              }
            ],
            borderables: [],
            fontEditable: undefined,
            fontSizeable: undefined
          }),
          mapToEditPanelValues: (config) => new Map([
            ['app_title', config.app_title || defaultConfig.app_title],
            ['welcome_text', config.welcome_text || defaultConfig.welcome_text]
          ])
        });
      }

      if (window.dataSdk) {
        const result = await window.dataSdk.init(dataHandler);
        if (!result.isOk) {
          console.error('Failed to initialize Data SDK');
        }
      }
    }

    initSDKs();

    // Quiz Questions - 20 questions
    const questions = [
      {
        question: "Apa kepanjangan dari istilah 'Bebras'?",
        options: ["Berang-berang (bahasa Lithuania)", "Belajar Bersama", "Berbasis Rasional", "Berpikir Bebas"],
        correct: 0
      },
      {
        question: "Scratch adalah bahasa pemrograman yang menggunakan sistem...",
        options: ["Typing code", "Drag-and-drop blok", "Command line", "Voice recognition"],
        correct: 1
      },
      {
        question: "Apa yang dimaksud dengan Dekomposisi dalam berpikir komputasional?",
        options: ["Menggabungkan masalah", "Memecah masalah besar menjadi bagian kecil", "Mengabaikan masalah", "Mencari pola"],
        correct: 1
      },
      {
        question: "Flowchart digunakan untuk...",
        options: ["Menulis kode", "Menunjukkan alur logika program", "Menyimpan data", "Membuat animasi"],
        correct: 1
      },
      {
        question: "Aspek berpikir komputasional yang mencari kesamaan dalam data adalah...",
        options: ["Dekomposisi", "Abstraksi", "Pengenalan Pola", "Algoritma"],
        correct: 2
      },
      {
        question: "Simbol oval dalam flowchart menunjukkan...",
        options: ["Proses", "Keputusan", "Start/End", "Input/Output"],
        correct: 2
      },
      {
        question: "Variabel dalam pemrograman berfungsi untuk...",
        options: ["Menghapus data", "Menyimpan informasi", "Membuat suara", "Menggambar grafik"],
        correct: 1
      },
      {
        question: "Looping dalam pemrograman berarti...",
        options: ["Berhenti", "Mengulang aksi", "Menghapus", "Menyimpan"],
        correct: 1
      },
      {
        question: "Aplikasi yang BUKAN pembuat flowchart adalah...",
        options: ["Microsoft Visio", "Lucidchart", "Microsoft Word", "draw.io"],
        correct: 2
      },
      {
        question: "Kondisi if-then digunakan untuk...",
        options: ["Mengulang aksi", "Membuat keputusan", "Menyimpan data", "Menghapus file"],
        correct: 1
      },
      {
        question: "Abstraksi dalam berpikir komputasional berarti...",
        options: ["Memperumit masalah", "Mengambil informasi penting dan mengabaikan yang tidak relevan", "Membuat diagram", "Menulis kode"],
        correct: 1
      },
      {
        question: "Fungsi dalam pemrograman adalah...",
        options: ["Tempat menyimpan gambar", "Kelompok kode yang diberi nama", "Jenis variabel", "Tipe flowchart"],
        correct: 1
      },
      {
        question: "Simbol belah ketupat dalam flowchart menunjukkan...",
        options: ["Start", "Proses", "Keputusan", "End"],
        correct: 2
      },
      {
        question: "Berpikir komputasional adalah kemampuan abad ke-...",
        options: ["19", "20", "21", "22"],
        correct: 2
      },
      {
        question: "Tujuan utama Bebras Challenge adalah...",
        options: ["Mempromosikan berpikir komputasional", "Mengajarkan bahasa Lithuania", "Membuat game", "Menghitung matematika"],
        correct: 0
      },
      {
        question: "Algoritma adalah...",
        options: ["Jenis komputer", "Langkah-langkah terstruktur untuk solusi", "Bahasa pemrograman", "Simbol flowchart"],
        correct: 1
      },
      {
        question: "Scratch cocok untuk...",
        options: ["Programmer profesional saja", "Anak-anak yang belajar pemrograman", "Membuat sistem operasi", "Hacking"],
        correct: 1
      },
      {
        question: "Kegunaan flowchart sebelum menulis kode adalah untuk...",
        options: ["Mempercepat komputer", "Mengidentifikasi kesalahan logika", "Menghapus virus", "Menginstal software"],
        correct: 1
      },
      {
        question: "Berapa aspek utama dalam berpikir komputasional?",
        options: ["2", "3", "4", "5"],
        correct: 2
      },
      {
        question: "Simbol jajar genjang dalam flowchart menunjukkan...",
        options: ["Start/End", "Proses", "Keputusan", "Input/Output"],
        correct: 3
      }
    ];

    let currentQuestionIndex = 0;
    let userAnswers = new Array(20).fill(null);
    let quizNama = '';
    let quizKelas = '';

    // Section Navigation
    function showSection(section) {
      const sections = ['main-menu', 'modul-section', 'games-section', 'quiz-intro-section', 'quiz-section', 'result-section', 'hasil-section'];
      sections.forEach(s => {
        document.getElementById(s).classList.add('hidden');
      });

      if (section === 'main') {
        document.getElementById('main-menu').classList.remove('hidden');
      } else if (section === 'modul') {
        document.getElementById('modul-section').classList.remove('hidden');
      } else if (section === 'games') {
        document.getElementById('games-section').classList.remove('hidden');
        initAllGames();
      } else if (section === 'quiz-intro') {
        document.getElementById('quiz-intro-section').classList.remove('hidden');
        resetQuiz();
      } else if (section === 'quiz') {
        document.getElementById('quiz-section').classList.remove('hidden');
        displayQuestion();
      } else if (section === 'result') {
        document.getElementById('result-section').classList.remove('hidden');
      } else if (section === 'hasil') {
        document.getElementById('hasil-section').classList.remove('hidden');
      }
    }

    // Modul Accordion
    function toggleModul(num) {
      const content = document.getElementById(`content-${num}`);
      const arrow = document.getElementById(`arrow-${num}`);
      
      if (content.classList.contains('hidden')) {
        content.classList.remove('hidden');
        arrow.style.transform = 'rotate(180deg)';
      } else {
        content.classList.add('hidden');
        arrow.style.transform = 'rotate(0deg)';
      }
    }

    // Quiz Form Submit
    document.getElementById('quiz-form').addEventListener('submit', function(e) {
      e.preventDefault();
      quizNama = document.getElementById('nama-input').value.trim();
      quizKelas = document.getElementById('kelas-input').value.trim();
      
      if (quizNama && quizKelas) {
        document.getElementById('quiz-nama').textContent = quizNama;
        document.getElementById('quiz-kelas').textContent = quizKelas;
        showSection('quiz');
      }
    });

    function resetQuiz() {
      currentQuestionIndex = 0;
      userAnswers = new Array(20).fill(null);
      document.getElementById('nama-input').value = '';
      document.getElementById('kelas-input').value = '';
    }

    function displayQuestion() {
      const q = questions[currentQuestionIndex];
      document.getElementById('question-text').textContent = `${currentQuestionIndex + 1}. ${q.question}`;
      document.getElementById('current-question').textContent = currentQuestionIndex + 1;
      document.getElementById('quiz-progress').style.width = `${((currentQuestionIndex + 1) / 20) * 100}%`;

      const optionsContainer = document.getElementById('options-container');
      optionsContainer.innerHTML = '';

      q.options.forEach((opt, idx) => {
        const isSelected = userAnswers[currentQuestionIndex] === idx;
        const btn = document.createElement('button');
        btn.className = `w-full text-left p-4 rounded-xl transition-all ${isSelected ? 'bg-cyan-500/30 border-2 border-cyan-400' : 'bg-white/10 hover:bg-white/20 border-2 border-transparent'}`;
        btn.innerHTML = `<span class="font-bold mr-2">${String.fromCharCode(65 + idx)}.</span> ${opt}`;
        btn.onclick = () => selectAnswer(idx);
        optionsContainer.appendChild(btn);
      });

      document.getElementById('prev-btn').disabled = currentQuestionIndex === 0;
      document.getElementById('next-btn').textContent = currentQuestionIndex === 19 ? 'Selesai →' : 'Selanjutnya →';
    }

    function selectAnswer(idx) {
      userAnswers[currentQuestionIndex] = idx;
      displayQuestion();
    }

    function prevQuestion() {
      if (currentQuestionIndex > 0) {
        currentQuestionIndex--;
        displayQuestion();
      }
    }

    function nextQuestion() {
      if (currentQuestionIndex < 19) {
        currentQuestionIndex++;
        displayQuestion();
      } else {
        finishQuiz();
      }
    }

    async function finishQuiz() {
      let score = 0;
      for (let i = 0; i < 20; i++) {
        if (userAnswers[i] === questions[i].correct) {
          score++;
        }
      }

      const percentage = Math.round((score / 20) * 100);
      
      document.getElementById('result-name').textContent = `${quizNama} - Kelas ${quizKelas}`;
      document.getElementById('result-score').textContent = `${score}/20`;
      document.getElementById('result-percentage').textContent = `${percentage}%`;

      let icon, message;
      if (percentage >= 80) {
        icon = '🏆';
        message = '<span class="text-green-400">Luar Biasa! Kamu sangat menguasai materi!</span>';
      } else if (percentage >= 60) {
        icon = '👍';
        message = '<span class="text-cyan-400">Bagus! Terus tingkatkan pemahamanmu!</span>';
      } else if (percentage >= 40) {
        icon = '📚';
        message = '<span class="text-yellow-400">Cukup baik. Pelajari lagi materi yang sulit!</span>';
      } else {
        icon = '💪';
        message = '<span class="text-orange-400">Jangan menyerah! Baca ulang modulnya ya!</span>';
      }

      document.getElementById('result-icon').textContent = icon;
      document.getElementById('result-message').innerHTML = message;

      // Save to Data SDK BEFORE showing result
      try {
        if (window.dataSdk) {
          if (quizResults.length >= 999) {
            document.getElementById('saving-status').innerHTML = '<span class="text-yellow-400">⚠️ Penyimpanan penuh (maks 999 data)</span>';
          } else {
            const now = new Date();
            const saveResult = await window.dataSdk.create({
              nama: quizNama,
              kelas: quizKelas,
              skor: score,
              total_soal: 20,
              persentase: percentage,
              tanggal: now.toLocaleDateString('id-ID'),
              waktu_selesai: now.toISOString()
            });

            if (saveResult.isOk) {
              document.getElementById('saving-status').innerHTML = '<span class="text-green-400">✅ Hasil tersimpan di Canva Sheet!</span>';
            } else {
              document.getElementById('saving-status').innerHTML = `<span class="text-red-400">❌ Error: ${saveResult.error?.message || 'Gagal menyimpan'}</span>`;
            }
          }
        } else {
          document.getElementById('saving-status').innerHTML = '<span class="text-gray-400">📊 Mode pratinjau (Data SDK tidak tersedia)</span>';
        }
      } catch (error) {
        console.error('Error saving quiz:', error);
        document.getElementById('saving-status').innerHTML = '<span class="text-red-400">❌ Terjadi kesalahan saat menyimpan</span>';
      }

      showSection('result');
    }

    function updateHasilTable() {
      const tbody = document.getElementById('hasil-table-body');
      
      if (quizResults.length === 0) {
        tbody.innerHTML = `
          <tr>
            <td colspan="6" class="px-4 py-8 text-center text-gray-400">
              Belum ada data hasil kuis
            </td>
          </tr>
        `;
        return;
      }

      const sorted = [...quizResults].sort((a, b) => new Date(b.waktu_selesai) - new Date(a.waktu_selesai));
      
      tbody.innerHTML = sorted.map((r, idx) => {
        const pctColor = r.persentase >= 80 ? 'text-green-400' : r.persentase >= 60 ? 'text-cyan-400' : r.persentase >= 40 ? 'text-yellow-400' : 'text-orange-400';
        return `
          <tr class="border-t border-white/10 hover:bg-white/5">
            <td class="px-4 py-3">${idx + 1}</td>
            <td class="px-4 py-3 font-medium">${r.nama}</td>
            <td class="px-4 py-3">${r.kelas}</td>
            <td class="px-4 py-3 text-center font-bold">${r.skor}/${r.total_soal}</td>
            <td class="px-4 py-3 text-center font-bold ${pctColor}">${r.persentase}%</td>
            <td class="px-4 py-3 text-sm text-gray-400">${r.tanggal}</td>
          </tr>
        `;
      }).join('');
    }

    // === GAMES ===
    
    // Game State
    let patternScore = 0;
    let algoScore = 0;
    let memoryScore = 0;
    let conceptScore = 0;
    let memoryCards = [];
    let flippedCards = [];
    let canFlip = true;

    function initAllGames() {
      initPatternGame();
      initAlgoGame();
      initMemoryGame();
      initConceptGame();
    }

    // Pattern Game
    const patterns = [
      { seq: ['🔵', '🔴', '🔵', '🔴', '🔵'], answer: '🔴', options: ['🔴', '🟢', '🟡'] },
      { seq: ['⭐', '⭐', '🌙', '⭐', '⭐'], answer: '🌙', options: ['⭐', '🌙', '☀️'] },
      { seq: ['1', '2', '3', '4', '5'], answer: '6', options: ['6', '7', '0'] },
      { seq: ['🍎', '🍊', '🍎', '🍊', '🍎'], answer: '🍊', options: ['🍎', '🍊', '🍇'] },
      { seq: ['▲', '■', '▲', '■', '▲'], answer: '■', options: ['▲', '■', '●'] }
    ];
    let currentPattern = 0;

    function initPatternGame() {
      patternScore = 0;
      currentPattern = 0;
      document.getElementById('pattern-score').textContent = patternScore;
      document.getElementById('pattern-feedback').textContent = '';
      showPattern();
    }

    function showPattern() {
      const p = patterns[currentPattern % patterns.length];
      document.getElementById('pattern-sequence').innerHTML = p.seq.map(s => `<span>${s}</span>`).join('') + '<span class="text-cyan-400">?</span>';
      
      const shuffled = [...p.options].sort(() => Math.random() - 0.5);
      document.getElementById('pattern-options').innerHTML = shuffled.map(opt => 
        `<button onclick="checkPattern('${opt}')" class="game-cell bg-white/20 hover:bg-white/30 w-14 h-14 rounded-xl text-2xl">${opt}</button>`
      ).join('');
    }

    function checkPattern(answer) {
      const p = patterns[currentPattern % patterns.length];
      const feedback = document.getElementById('pattern-feedback');
      
      if (answer === p.answer) {
        patternScore++;
        document.getElementById('pattern-score').textContent = patternScore;
        feedback.innerHTML = '<span class="text-green-400">✓ Benar!</span>';
        currentPattern++;
        setTimeout(showPattern, 800);
      } else {
        feedback.innerHTML = '<span class="text-red-400">✗ Coba lagi!</span>';
      }
    }

    // Algorithm Game
    const algoProblems = [
      {
        question: "Cara membuat teh:",
        steps: ["Siapkan gelas", "Masukkan teh celup", "Tuang air panas", "Aduk dan sajikan"],
        order: [0, 1, 2, 3]
      },
      {
        question: "Langkah login email:",
        steps: ["Buka browser", "Ketik alamat email", "Masukkan password", "Klik tombol login"],
        order: [0, 1, 2, 3]
      },
      {
        question: "Cara menggambar lingkaran:",
        steps: ["Siapkan jangka", "Tentukan titik pusat", "Atur radius", "Putar jangka 360°"],
        order: [0, 1, 2, 3]
      }
    ];
    let currentAlgo = 0;
    let selectedSteps = [];

    function initAlgoGame() {
      algoScore = 0;
      currentAlgo = 0;
      document.getElementById('algo-score').textContent = algoScore;
      document.getElementById('algo-feedback').textContent = '';
      showAlgo();
    }

    function showAlgo() {
      selectedSteps = [];
      const prob = algoProblems[currentAlgo % algoProblems.length];
      document.getElementById('algo-question').textContent = prob.question;
      
      const shuffled = [...prob.steps].sort(() => Math.random() - 0.5);
      document.getElementById('algo-steps').innerHTML = shuffled.map((step, idx) => 
        `<button onclick="selectStep(this, '${step}')" class="w-full text-left p-3 rounded-lg bg-white/10 hover:bg-white/20 transition-colors">${step}</button>`
      ).join('');
    }

    function selectStep(btn, step) {
      if (btn.classList.contains('bg-cyan-500/30')) {
        btn.classList.remove('bg-cyan-500/30');
        selectedSteps = selectedSteps.filter(s => s !== step);
      } else {
        btn.classList.add('bg-cyan-500/30');
        selectedSteps.push(step);
      }
      
      if (selectedSteps.length === 4) {
        checkAlgo();
      }
    }

    function checkAlgo() {
      const prob = algoProblems[currentAlgo % algoProblems.length];
      const feedback = document.getElementById('algo-feedback');
      
      let correct = true;
      for (let i = 0; i < 4; i++) {
        if (selectedSteps[i] !== prob.steps[prob.order[i]]) {
          correct = false;
          break;
        }
      }
      
      if (correct) {
        algoScore++;
        document.getElementById('algo-score').textContent = algoScore;
        feedback.innerHTML = '<span class="text-green-400">✓ Urutan benar!</span>';
        currentAlgo++;
        setTimeout(showAlgo, 1000);
      } else {
        feedback.innerHTML = '<span class="text-red-400">✗ Urutan salah, coba lagi!</span>';
        setTimeout(() => {
          showAlgo();
          document.getElementById('algo-feedback').textContent = '';
        }, 1000);
      }
    }

    // Memory Game
    const memoryPairs = [
      { term: '🧩', def: 'Dekomposisi' },
      { term: '🔍', def: 'Pola' },
      { term: '🎯', def: 'Abstraksi' },
      { term: '📋', def: 'Algoritma' },
      { term: '💻', def: 'Program' },
      { term: '📊', def: 'Flowchart' }
    ];

    function initMemoryGame() {
      memoryScore = 0;
      flippedCards = [];
      canFlip = true;
      document.getElementById('memory-score').textContent = memoryScore;
      document.getElementById('memory-feedback').textContent = '';
      
      const cards = [];
      memoryPairs.forEach((pair, idx) => {
        cards.push({ id: idx * 2, pairId: idx, content: pair.term, flipped: false, matched: false });
        cards.push({ id: idx * 2 + 1, pairId: idx, content: pair.def, flipped: false, matched: false });
      });
      
      memoryCards = cards.sort(() => Math.random() - 0.5);
      renderMemoryGrid();
    }

    function renderMemoryGrid() {
      const grid = document.getElementById('memory-grid');
      grid.innerHTML = memoryCards.map(card => `
        <button onclick="flipCard(${card.id})" 
          class="game-cell aspect-square rounded-lg text-center flex items-center justify-center text-sm font-bold
          ${card.matched ? 'bg-green-500/30 cursor-default' : card.flipped ? 'bg-cyan-500/30' : 'bg-white/20 hover:bg-white/30'}"
          ${card.matched ? 'disabled' : ''}>
          ${card.flipped || card.matched ? card.content : '?'}
        </button>
      `).join('');
    }

    function flipCard(id) {
      if (!canFlip) return;
      
      const card = memoryCards.find(c => c.id === id);
      if (!card || card.flipped || card.matched) return;
      
      card.flipped = true;
      flippedCards.push(card);
      renderMemoryGrid();
      
      if (flippedCards.length === 2) {
        canFlip = false;
        setTimeout(checkMemoryMatch, 800);
      }
    }

    function checkMemoryMatch() {
      const [card1, card2] = flippedCards;
      const feedback = document.getElementById('memory-feedback');
      
      if (card1.pairId === card2.pairId) {
        card1.matched = true;
        card2.matched = true;
        memoryScore++;
        document.getElementById('memory-score').textContent = memoryScore;
        feedback.innerHTML = '<span class="text-green-400">✓ Cocok!</span>';
        
        if (memoryScore === 6) {
          feedback.innerHTML = '<span class="text-green-400">🎉 Selesai!</span>';
        }
      } else {
        card1.flipped = false;
        card2.flipped = false;
        feedback.innerHTML = '<span class="text-red-400">✗ Tidak cocok</span>';
      }
      
      flippedCards = [];
      canFlip = true;
      renderMemoryGrid();
      
      setTimeout(() => {
        if (memoryScore < 6) {
          document.getElementById('memory-feedback').textContent = '';
        }
      }, 500);
    }

    // Concept Game
    const concepts = [
      { hint: "Memecah masalah besar menjadi bagian-bagian kecil", answer: "Dekomposisi", options: ["Dekomposisi", "Abstraksi", "Algoritma", "Looping"] },
      { hint: "Bahasa pemrograman visual dengan drag-and-drop", answer: "Scratch", options: ["Python", "Scratch", "Java", "C++"] },
      { hint: "Diagram yang menunjukkan alur logika program", answer: "Flowchart", options: ["Flowchart", "Database", "Spreadsheet", "Browser"] },
      { hint: "Mengulang aksi dalam pemrograman", answer: "Looping", options: ["Looping", "Kondisi", "Variabel", "Fungsi"] },
      { hint: "Menyimpan informasi dalam program", answer: "Variabel", options: ["Konstanta", "Variabel", "Array", "Object"] }
    ];
    let currentConcept = 0;

    function initConceptGame() {
      conceptScore = 0;
      currentConcept = 0;
      document.getElementById('concept-score').textContent = conceptScore;
      document.getElementById('concept-feedback').textContent = '';
      showConcept();
    }

    function showConcept() {
      const c = concepts[currentConcept % concepts.length];
      document.getElementById('concept-hint').textContent = `"${c.hint}"`;
      
      const shuffled = [...c.options].sort(() => Math.random() - 0.5);
      document.getElementById('concept-options').innerHTML = shuffled.map(opt => 
        `<button onclick="checkConcept('${opt}')" class="bg-white/10 hover:bg-white/20 p-3 rounded-lg font-medium transition-colors">${opt}</button>`
      ).join('');
    }

    function checkConcept(answer) {
      const c = concepts[currentConcept % concepts.length];
      const feedback = document.getElementById('concept-feedback');
      
      if (answer === c.answer) {
        conceptScore++;
        document.getElementById('concept-score').textContent = conceptScore;
        feedback.innerHTML = '<span class="text-green-400">✓ Benar!</span>';
        currentConcept++;
        setTimeout(showConcept, 800);
      } else {
        feedback.innerHTML = `<span class="text-red-400">✗ Jawaban: ${c.answer}</span>`;
        setTimeout(() => {
          currentConcept++;
          showConcept();
          document.getElementById('concept-feedback').textContent = '';
        }, 1500);
      }
    }
  </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9dae696bd0a891a1',t:'MTc3MzI3MjUwNi4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
