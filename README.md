<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>أسئلة قانونية - خريجات إدارة أعمال شعبة 13</title>
    <script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Cairo:wght@400;600;700;800;900&display=swap');
        body {
            font-family: 'Cairo', sans-serif;
        }
        .gold-gradient-text {
            background: linear-gradient(135deg, #fef08a 0%, #facc15 50%, #eab308 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        .gold-border {
            border-color: rgba(234, 179, 8, 0.4);
        }
    </style>
</head>
<body class="bg-gradient-to-br from-slate-950 via-purple-950 to-slate-900 min-h-screen text-white flex items-center justify-center p-4">

    <div class="max-w-xl w-full bg-purple-950/60 backdrop-blur-xl rounded-3xl shadow-2xl border gold-border p-6 sm:p-8 relative overflow-hidden">
        
        <!-- Background Accent Glows -->
        <div class="absolute -top-20 -left-20 w-40 h-40 bg-purple-600/20 rounded-full blur-3xl pointer-events-none"></div>
        <div class="absolute -bottom-20 -right-20 w-40 h-40 bg-amber-500/20 rounded-full blur-3xl pointer-events-none"></div>

        <!-- Header -->
        <div class="text-center mb-6">
            <div class="inline-flex items-center gap-2 bg-amber-500/10 border border-amber-500/30 text-amber-300 text-xs sm:text-sm font-semibold px-4 py-1.5 rounded-full mb-3 shadow-inner">
                🎓 تقديم: خريجات إدارة أعمال شعبة 13
            </div>
            <h1 class="text-3xl sm:text-4xl font-extrabold gold-gradient-text tracking-wide drop-shadow-md">أسئلة قانونية</h1>
            <p class="text-purple-200/80 text-xs sm:text-sm mt-2">اختبر وعيك بالأنظمة ومكافحة الجرائم المعلوماتية</p>
        </div>

        <!-- Quiz Container -->
        <div id="quiz-container">
            <!-- Progress Bar -->
            <div class="w-full bg-purple-900/50 h-2.5 rounded-full mb-6 overflow-hidden border border-purple-700/30 p-0.5">
                <div id="progress-bar" class="bg-gradient-to-r from-amber-400 to-amber-500 h-full rounded-full transition-all duration-300" style="width: 33%;"></div>
            </div>

            <!-- Question Box -->
            <div class="mb-6 bg-purple-900/30 p-4 rounded-2xl border border-purple-800/40">
                <div class="flex justify-between items-center text-xs text-amber-300/80 mb-2 font-semibold">
                    <span id="question-count">السؤال 1 من 3</span>
                    <span id="score-display">النقاط: 0</span>
                </div>
                <h2 id="question-text" class="text-base sm:text-lg font-bold text-slate-100 leading-relaxed"></h2>
            </div>

            <!-- Options Box -->
            <div id="options-container" class="space-y-3">
                <!-- Dynamic Options injected here -->
            </div>

            <!-- Next Button -->
            <div class="mt-6 flex justify-end">
                <button id="next-btn" onclick="nextQuestion()" class="hidden bg-gradient-to-r from-amber-500 to-amber-600 hover:from-amber-400 hover:to-amber-500 text-slate-950 font-bold px-7 py-2.5 rounded-xl transition-all shadow-lg shadow-amber-500/20 cursor-pointer">
                    السؤال التالي ➔
                </button>
            </div>
        </div>

        <!-- Result Container -->
        <div id="result-container" class="hidden text-center py-6">
            <div class="text-6xl mb-4">⚖️</div>
            <h2 class="text-2xl font-bold text-white mb-2">ممتاز! أتممت الاختبار القانوني بنجاح</h2>
            <p id="final-score" class="gold-gradient-text text-xl font-bold mb-3"></p>
            <p class="text-purple-200/70 text-xs sm:text-sm mb-6 max-w-md mx-auto">
                شكراً لمشاركتك! التوعية بالأنظمة والقوانين هي الدرع الأول لحماية الفرد والمجتمع.
            </p>
            <div class="text-xs text-amber-300/90 mb-6 bg-purple-900/40 py-2 px-4 rounded-lg inline-block border border-amber-500/20">
                إهداء من: خريجات إدارة أعمال شعبة 13 ✨
            </div>
            <br>
            <button onclick="restartQuiz()" class="bg-gradient-to-r from-amber-500 to-amber-600 hover:from-amber-400 hover:to-amber-500 text-slate-950 font-bold px-8 py-3 rounded-xl transition-all shadow-lg shadow-amber-500/20 cursor-pointer">
                إعادة المحاولة 🔄
            </button>
        </div>

    </div>

    <script>
        const quizData = [
            {
                question: "ما هو التصرف الصحيح الأول عند استلام تهديد بالابتزاز؟",
                options: [
                    { text: "التوقف عن التواصل فوراً، توثيق المحادثات، والإبلاغ الرسمي عبر تطبيق \"كلنا أمن\".", isCorrect: true },
                    { text: "التفاهم مع المبتز ومحاولة إرضائه لدفع الضرر مؤقتاً.", isCorrect: false },
                    { text: "حذف التطبيقات والهروب من المشكلة دون إبلاغ الجهات.", isCorrect: false },
                    { text: "مواجهة المبتز وتهديده بنشر أخباره الشخصية.", isCorrect: false }
                ]
            },
            {
                question: "هل يحمي الخفاء والخلفيات الافتراضية المبتز من العقاب؟",
                options: [
                    { text: "نعم، إذا استخدم حسابات وهمية يصعب الوصول إليه تماماً.", isCorrect: false },
                    { text: "لا، للجهات الأمنية إمكانيات تقنية متقدمة لتتبع الأثر الرقمي ومعرفة هوية الجاني وموقعه.", isCorrect: true },
                    { text: "نعم، لأن الإنترنت عالم افتراضي مجهول بطبيعته القانونية.", isCorrect: false },
                    { text: "يعتمد ذلك على قوة كلمة المرور الخاصة بالمبتز.", isCorrect: false }
                ]
            },
            {
                question: "هل يعاقب نظام مكافحة الجرائم المعلوماتية السعودي على التشهير وإعادة النشر؟",
                options: [
                    { text: "لا، إعادة النشر لا تعتبر جريمة بحد ذاتها.", isCorrect: false },
                    { text: "يعاقب فقط إذا كان النشر بقصد الابتزاز المالي المباشر.", isCorrect: false },
                    { text: "نعم، يعاقب النظام كل من يمس بالحياة الخاصة أو ينشر ويشارك المحتوى المسيء.", isCorrect: true },
                    { text: "يعاقب المنشئ الأساسي فقط ويستثني المعيدين للنشر.", isCorrect: false }
                ]
            }
        ];

        let currentQuestionIndex = 0;
        let score = 0;
        let answered = false;

        const questionText = document.getElementById("question-text");
        const optionsContainer = document.getElementById("options-container");
        const questionCount = document.getElementById("question-count");
        const scoreDisplay = document.getElementById("score-display");
        const progressBar = document.getElementById("progress-bar");
        const nextBtn = document.getElementById("next-btn");
        const quizContainer = document.getElementById("quiz-container");
        const resultContainer = document.getElementById("result-container");
        const finalScore = document.getElementById("final-score");

        function loadQuestion() {
            answered = false;
            nextBtn.classList.add("hidden");
            
            const currentData = quizData[currentQuestionIndex];
            questionText.textContent = currentData.question;
            questionCount.textContent = `السؤال ${currentQuestionIndex + 1} من ${quizData.length}`;
            scoreDisplay.textContent = `النقاط: ${score}`;
            progressBar.style.width = `${((currentQuestionIndex + 1) / quizData.length) * 100}%`;

            // Shuffle options for randomness
            const shuffledOptions = [...currentData.options].sort(() => Math.random() - 0.5);

            optionsContainer.innerHTML = "";
            shuffledOptions.forEach((option) => {
                const btn = document.createElement("button");
                btn.className = "w-full text-right p-3.5 rounded-xl border border-purple-800/50 bg-purple-900/40 hover:bg-purple-800/60 hover:border-amber-500/50 transition-all text-purple-100 font-medium text-xs sm:text-sm cursor-pointer leading-relaxed shadow-sm";
                btn.textContent = option.text;
                btn.onclick = () => selectOption(btn, option.isCorrect);
                optionsContainer.appendChild(btn);
            });
        }

        function selectOption(button, isCorrect) {
            if (answered) return;
            answered = true;

            const buttons = optionsContainer.getElementsByTagName("button");
            Array.from(buttons).forEach(btn => {
                btn.disabled = true;
                const optText = btn.textContent;
                const originalOpt = quizData[currentQuestionIndex].options.find(o => o.text === optText);
                if (originalOpt.isCorrect) {
                    btn.classList.remove("bg-purple-900/40", "border-purple-800/50");
                    btn.classList.add("bg-emerald-900/60", "border-emerald-500", "text-emerald-200");
                }
            });

            if (isCorrect) {
                score += 10;
                scoreDisplay.textContent = `النقاط: ${score}`;
            } else {
                button.classList.remove("bg-purple-900/40", "border-purple-800/50");
                button.classList.add("bg-rose-900/60", "border-rose-500", "text-rose-200");
            }

            nextBtn.classList.remove("hidden");
        }

        function nextQuestion() {
            currentQuestionIndex++;
            if (currentQuestionIndex < quizData.length) {
                loadQuestion();
            } else {
                quizContainer.classList.add("hidden");
                resultContainer.classList.remove("hidden");
                finalScore.textContent = `النتيجة النهائية: ${score} من ${quizData.length * 10} نقطة`;
            }
        }

        function restartQuiz() {
            currentQuestionIndex = 0;
            score = 0;
            resultContainer.classList.add("hidden");
            quizContainer.classList.remove("hidden");
            loadQuestion();
        }

        loadQuestion();
    </script>
</body>
</html>
