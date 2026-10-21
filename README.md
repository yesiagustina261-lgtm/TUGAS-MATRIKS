<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Belajar Matriks Interaktif</title>
    
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    
    <!-- KaTeX CSS -->
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.16.8/dist/katex.min.css">
    
    <!-- Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f3f4f6; /* Tailwind gray-100 */
        }
        .option-label {
            cursor: pointer;
            transition: all 0.2s;
        }
        /* Custom radio button styling */
        .option-input:checked + .option-box {
            border-color: #4f46e5; /* indigo-600 */
            background-color: #e0e7ff; /* indigo-100 */
        }
        .correct-answer {
            border-color: #10b981 !important; /* emerald-500 */
            background-color: #d1fae5 !important; /* emerald-100 */
        }
        .wrong-answer {
            border-color: #ef4444 !important; /* red-500 */
            background-color: #fee2e2 !important; /* red-100 */
        }
        
        /* Modal styling */
        #score-modal {
            transition: opacity 0.3s ease;
        }
    </style>
</head>
<body class="text-gray-800 antialiased pb-20">

    <!-- Header -->
    <header class="bg-indigo-600 text-white py-6 shadow-md mb-8">
        <div class="max-w-4xl mx-auto px-4 text-center">
            <h1 class="text-3xl font-bold mb-2">Matematika: Matriks</h1>
            <p class="text-indigo-200">Pelajari konsep dasar dan uji kemampuanmu!</p>
        </div>
    </header>

    <main class="max-w-4xl mx-auto px-4 space-y-8">
        
        <!-- Bagian Rangkuman Materi -->
        <section class="bg-white rounded-xl shadow-sm border border-gray-200 p-6 md:p-8">
            <h2 class="text-2xl font-bold text-gray-900 border-b pb-4 mb-6">📚 Rangkuman Materi Matriks</h2>
            
            <div class="space-y-6">
                <!-- Poin 1 -->
                <div>
                    <h3 class="text-lg font-semibold text-indigo-700 mb-2">1. Ordo & Elemen Matriks</h3>
                    <p class="mb-2 text-gray-700">Ordo adalah ukuran matriks (baris × kolom). Elemen adalah nilai di dalamnya.</p>
                    <div class="bg-gray-50 p-4 rounded-lg">
                        Contoh: 
                        $$ A = \begin{pmatrix} 2 & 5 & 8 \\ -1 & 3 & 0 \end{pmatrix} $$
                        <ul class="list-disc list-inside mt-2 text-sm text-gray-600">
                            <li>Ordo matriks $A$ adalah $2 \times 3$ (2 baris, 3 kolom).</li>
                            <li>Elemen baris 1 kolom 2 ($a_{12}$) adalah $5$.</li>
                        </ul>
                    </div>
                </div>

                <!-- Poin 2 -->
                <div>
                    <h3 class="text-lg font-semibold text-indigo-700 mb-2">2. Jenis-jenis Matriks</h3>
                    <ul class="list-disc list-inside text-gray-700 space-y-1">
                        <li><strong>Matriks Baris:</strong> Hanya 1 baris. Contoh: $ \begin{pmatrix} 1 & 4 & 7 \end{pmatrix} $</li>
                        <li><strong>Matriks Kolom:</strong> Hanya 1 kolom.</li>
                        <li><strong>Matriks Persegi:</strong> Jumlah baris = kolom.</li>
                        <li><strong>Matriks Identitas ($I$):</strong> Matriks persegi dengan diagonal utama bernilai 1, sisanya 0. 
                            $$ I = \begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix} $$
                        </li>
                    </ul>
                </div>

                <!-- Poin 3 -->
                <div>
                    <h3 class="text-lg font-semibold text-indigo-700 mb-2">3. Transpose Matriks ($A^T$)</h3>
                    <p class="mb-2 text-gray-700">Mengubah susunan baris menjadi kolom, dan kolom menjadi baris.</p>
                    <div class="bg-gray-50 p-4 rounded-lg text-center">
                        Jika $$ C = \begin{pmatrix} 1 & 2 \\ 3 & 4 \end{pmatrix} $$ maka $$ C^T = \begin{pmatrix} 1 & 3 \\ 2 & 4 \end{pmatrix} $$
                    </div>
                </div>

                <!-- Poin 4 -->
                <div>
                    <h3 class="text-lg font-semibold text-indigo-700 mb-2">4. Kesamaan Dua Matriks</h3>
                    <p class="mb-2 text-gray-700">Dua matriks dikatakan sama jika ordonya sama dan elemen yang seletak bernilai sama.</p>
                    <div class="bg-gray-50 p-4 rounded-lg text-center">
                        $$ \begin{pmatrix} x & 5 \\ 2 & y \end{pmatrix} = \begin{pmatrix} 3 & 5 \\ 2 & 7 \end{pmatrix} \implies x = 3, \; y = 7 $$
                    </div>
                </div>
            </div>
        </section>

        <!-- Bagian Kuis -->
        <section class="bg-white rounded-xl shadow-sm border border-gray-200 p-6 md:p-8">
            <h2 class="text-2xl font-bold text-gray-900 border-b pb-4 mb-6">📝 Kuis 10 Soal</h2>
            <p class="text-gray-600 mb-8">Jawablah pertanyaan di bawah ini. Pastikan Anda telah membaca materi di atas!</p>
            
            <div id="quiz-container" class="space-y-8">
                <!-- Pertanyaan akan di-render di sini oleh JavaScript -->
            </div>

            <div class="mt-10 border-t pt-6 text-center">
                <button id="submit-btn" onclick="checkAnswers()" class="bg-indigo-600 hover:bg-indigo-700 text-white font-bold py-3 px-8 rounded-lg shadow-lg transition duration-200 w-full sm:w-auto text-lg">
                    Cek Jawaban & Lihat Skor
                </button>
            </div>
        </section>

    </main>

    <!-- Modal Skor -->
    <div id="score-modal" class="fixed inset-0 bg-black bg-opacity-50 hidden flex items-center justify-center z-50">
        <div class="bg-white rounded-2xl shadow-2xl p-8 max-w-sm w-full mx-4 text-center">
            <div id="modal-icon" class="text-6xl mb-4">🏆</div>
            <h3 class="text-2xl font-bold text-gray-900 mb-2">Skor Kamu</h3>
            <p id="score-display" class="text-5xl font-extrabold text-indigo-600 mb-4">100</p>
            <p id="score-message" class="text-gray-600 mb-6">Luar biasa! Pertahankan prestasimu.</p>
            <button onclick="closeModal()" class="bg-gray-900 hover:bg-gray-800 text-white font-semibold py-2 px-6 rounded-lg transition duration-200 w-full">
                Tutup & Lihat Pembahasan
            </button>
        </div>
    </div>

    <!-- KaTeX JS & Auto-render extension -->
    <script defer src="https://cdn.jsdelivr.net/npm/katex@0.16.8/dist/katex.min.js"></script>
    <script defer src="https://cdn.jsdelivr.net/npm/katex@0.16.8/dist/contrib/auto-render.min.js"></script>

    <script>
        const quizData = [
            {
                question: "Ordo dari matriks $$ P = \\begin{pmatrix} 4 & 1 & 9 \\\\ -2 & 0 & 5 \\end{pmatrix} $$ adalah...",
                options: ["2x3", "3x2", "2x2", "3x3"],
                answer: 0 // Index dari "2x3"
            },
            {
                question: "Nilai elemen baris ke-2 kolom ke-3 ($$p_{23}$$) pada matriks $$ P = \\begin{pmatrix} 4 & 1 & 9 \\\\ -2 & 0 & 5 \\end{pmatrix} $$ adalah...",
                options: ["-2", "0", "5", "9"],
                answer: 2 // Index dari "5"
            },
            {
                question: "Jenis matriks $$ Q = \\begin{pmatrix} 7 \\\\ -3 \\\\ 1 \\end{pmatrix} $$ adalah...",
                options: ["Matriks Baris", "Matriks Kolom", "Matriks Identitas", "Matriks Persegi"],
                answer: 1 // Matriks Kolom
            },
            {
                question: "Nama spesifik matriks $$ R = \\begin{pmatrix} 1 & 0 \\\\ 0 & 1 \\end{pmatrix} $$ adalah...",
                options: ["Matriks Nol", "Matriks Identitas", "Matriks Skalar", "Matriks Kolom"],
                answer: 1 // Matriks Identitas
            },
            {
                question: "Transpose dari matriks $$ S = \\begin{pmatrix} 6 & -1 \\\\ 2 & 8 \\end{pmatrix} $$ adalah...",
                options: [
                    "$$ \\begin{pmatrix} 6 & 2 \\\\ -1 & 8 \\end{pmatrix} $$",
                    "$$ \\begin{pmatrix} 8 & 2 \\\\ -1 & 6 \\end{pmatrix} $$",
                    "$$ \\begin{pmatrix} -1 & 6 \\\\ 8 & 2 \\end{pmatrix} $$",
                    "$$ \\begin{pmatrix} 6 & -1 \\\\ 2 & 8 \\end{pmatrix} $$"
                ],
                answer: 0 // opsi pertama
            },
            {
                question: "Ordo dari transpose matriks $$ T = \\begin{pmatrix} 3 & 5 & 2 \\end{pmatrix} $$ adalah...",
                options: ["1x3", "3x1", "3x3", "1x1"],
                answer: 1 // 3x1 (Karena T adalah 1x3, T transpose adalah 3x1)
            },
            {
                question: "Berapakah nilai $$a$$ jika $$ \\begin{pmatrix} a & 4 \\\\ -1 & 6 \\end{pmatrix} = \\begin{pmatrix} 5 & 4 \\\\ -1 & 6 \\end{pmatrix} $$?",
                options: ["-1", "4", "5", "6"],
                answer: 2 // 5
            },
            {
                question: "Berapakah nilai $$b$$ jika $$ \\begin{pmatrix} 2 & b-1 \\\\ 3 & 4 \\end{pmatrix} = \\begin{pmatrix} 2 & 7 \\\\ 3 & 4 \\end{pmatrix} $$?",
                options: ["6", "7", "8", "9"],
                answer: 2 // 8 (b-1 = 7 => b=8)
            },
            {
                question: "Tentukan elemen $$k_{21}$$ dari **transpose** matriks $$ K = \\begin{pmatrix} 1 & 3 \\\\ 5 & 7 \\end{pmatrix} $$",
                options: ["1", "3", "5", "7"],
                answer: 1 // K transpose baris 2 kolom 1 = elemen K baris 1 kolom 2 = 3
            },
            {
                question: "Tentukan nilai $$x$$ dan $$y$$ jika $$ \\begin{pmatrix} x+y & 2 \\\\ 4 & x-y \\end{pmatrix} = \\begin{pmatrix} 8 & 2 \\\\ 4 & 2 \\end{pmatrix} $$",
                options: ["x=3 y=5", "x=5 y=3", "x=4 y=4", "x=6 y=2"],
                answer: 1 // x=5, y=3 (x+y=8, x-y=2)
            }
        ];

        let quizSubmitted = false;

        function renderQuiz() {
            const container = document.getElementById('quiz-container');
            let html = '';

            quizData.forEach((q, qIndex) => {
                html += `
                <div class="quiz-item bg-gray-50 p-6 rounded-xl border border-gray-100" id="q-block-${qIndex}">
                    <h3 class="font-medium text-lg text-gray-800 mb-4"><span class="font-bold text-indigo-600 mr-2">${qIndex + 1}.</span> ${q.question}</h3>
                    <div class="grid grid-cols-1 sm:grid-cols-2 gap-3">
                `;

                q.options.forEach((opt, optIndex) => {
                    const id = `q${qIndex}_opt${optIndex}`;
                    html += `
                        <label for="${id}" class="option-label group relative">
                            <input type="radio" id="${id}" name="q${qIndex}" value="${optIndex}" class="option-input peer sr-only">
                            <div id="box-${qIndex}-${optIndex}" class="option-box p-4 border-2 border-gray-200 rounded-lg text-gray-700 bg-white hover:border-indigo-300 peer-focus:ring-2 ring-offset-2 ring-indigo-500 flex items-center justify-center min-h-[60px] text-center">
                                <span>${opt}</span>
                            </div>
                        </label>
                    `;
                });

                html += `
                    </div>
                </div>
                `;
            });

            container.innerHTML = html;
            
            // Tunggu DOM update, lalu render persamaan matematika menggunakan KaTeX
            setTimeout(() => {
                renderMathInElement(document.body, {
                    delimiters: [
                        {left: "$$", right: "$$", display: true},
                        {left: "$", right: "$", display: false}
                    ],
                    throwOnError: false
                });
            }, 100);
        }

        function checkAnswers() {
            if (quizSubmitted) return; // Cegah submit berulang kali

            let score = 0;
            let answeredCount = 0;

            quizData.forEach((q, qIndex) => {
                const selectedOption = document.querySelector(`input[name="q${qIndex}"]:checked`);
                
                // Matikan input agar tidak bisa diubah lagi
                const allInputs = document.querySelectorAll(`input[name="q${qIndex}"]`);
                allInputs.forEach(input => input.disabled = true);

                if (selectedOption) {
                    answeredCount++;
                    const selectedVal = parseInt(selectedOption.value);
                    
                    if (selectedVal === q.answer) {
                        score += 10;
                        document.getElementById(`box-${qIndex}-${selectedVal}`).classList.add('correct-answer');
                    } else {
                        document.getElementById(`box-${qIndex}-${selectedVal}`).classList.add('wrong-answer');
                        // Tunjukkan yang benar
                        document.getElementById(`box-${qIndex}-${q.answer}`).classList.add('correct-answer');
                    }
                } else {
                    // Jika tidak dijawab, tunjukkan yang benar saja
                    document.getElementById(`box-${qIndex}-${q.answer}`).classList.add('correct-answer');
                }
            });

            if (answeredCount < 10) {
                // Opsional: peringatan jika belum dijawab semua, tapi karena tidak boleh pakai alert() standar
                // kita biarkan saja mereka mendapat skor 0 untuk soal yang tidak dijawab.
            }

            quizSubmitted = true;
            document.getElementById('submit-btn').classList.add('opacity-50', 'cursor-not-allowed');
            document.getElementById('submit-btn').innerText = "Kuis Selesai";
            
            showScoreModal(score);
        }

        function showScoreModal(score) {
            const modal = document.getElementById('score-modal');
            const scoreDisplay = document.getElementById('score-display');
            const message = document.getElementById('score-message');
            const icon = document.getElementById('modal-icon');
            
            scoreDisplay.innerText = score;
            
            if (score === 100) {
                message.innerText = "Sempurna! Kamu memahami semua materi dengan baik!";
                icon.innerText = "🥇";
            } else if (score >= 80) {
                message.innerText = "Bagus sekali! Hampir sempurna.";
                icon.innerText = "🥈";
            } else if (score >= 60) {
                message.innerText = "Lumayan, tapi pastikan pelajari lagi materi yang salah ya.";
                icon.innerText = "🥉";
            } else {
                message.innerText = "Jangan menyerah! Ayo baca lagi rangkuman materi di atas.";
                icon.innerText = "📚";
            }

            modal.classList.remove('hidden');
        }

        function closeModal() {
            document.getElementById('score-modal').classList.add('hidden');
            // Scroll sedikit ke atas agar user melihat highlight jawaban
            window.scrollBy({ top: -200, behavior: 'smooth' });
        }

        // Jalankan saat halaman dimuat
        document.addEventListener("DOMContentLoaded", () => {
            renderQuiz();
        });
    </script>
</body>
</html>
