<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Forely - Đấu trí & Nhận thưởng</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700;800&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Plus Jakarta Sans', sans-serif;
            background-color: #f1f5f9;
            color: #0f172a;
            user-select: none;
            -webkit-tap-highlight-color: transparent;
        }

        .safe-area-bottom {
            padding-bottom: env(safe-area-inset-bottom);
        }

        .tab-content {
            display: none;
            animation: slideUp 0.3s ease-out;
        }

        .tab-content.active {
            display: block;
        }

        @keyframes slideUp {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .gacha-shake {
            animation: shake 0.5s cubic-bezier(.36,.07,.19,.97) both infinite;
        }

        @keyframes shake {
            10%, 90% { transform: translate3d(-1px, 0, 0); }
            20%, 80% { transform: translate3d(2px, 0, 0); }
            30%, 50%, 70% { transform: translate3d(-4px, 0, 0); }
            40%, 60% { transform: translate3d(4px, 0, 0); }
        }

        .gradient-brand {
            background: linear-gradient(135deg, #4f46e5 0%, #7c3aed 100%);
        }

        .market-card {
            transition: transform 0.2s;
        }
        .market-card:active {
            transform: scale(0.98);
        }

        /* Hide scrollbar for Chrome, Safari and Opera */
        .no-scrollbar::-webkit-scrollbar {
            display: none;
        }
    </style>
</head>
<body class="max-w-md mx-auto bg-white min-h-screen shadow-2xl relative overflow-x-hidden">

    <!-- Top Status Bar Simulation -->
    <header class="sticky top-0 z-50 bg-white/80 backdrop-blur-md border-b border-slate-100 px-6 py-4 flex justify-between items-center">
        <div class="flex items-center gap-2">
            <div class="w-8 h-8 gradient-brand rounded-lg flex items-center justify-center text-white font-black text-xl">F</div>
            <span class="font-extrabold text-xl tracking-tight">FORELY</span>
        </div>
        <div class="bg-indigo-50 px-3 py-1.5 rounded-full flex items-center gap-2 border border-indigo-100">
            <span class="text-indigo-600 font-bold text-sm" id="global-fp">2,450</span>
            <span class="text-xs font-bold text-indigo-400">FP</span>
        </div>
    </header>

    <!-- Main Content Containers -->
    <main class="pb-24 pt-4 px-4 overflow-y-auto no-scrollbar">

        <!-- TAB 1: MARKETS (HOME) -->
        <div id="tab-home" class="tab-content active space-y-6">
            <!-- AI Welcome -->
            <div class="bg-slate-900 rounded-2xl p-5 text-white relative overflow-hidden">
                <div class="absolute -right-4 -top-4 w-24 h-24 bg-indigo-500/20 rounded-full blur-2xl"></div>
                <div class="relative z-10">
                    <p class="text-xs font-bold text-indigo-400 uppercase tracking-widest mb-1">AI Insights • Gemini 1.5</p>
                    <h2 class="text-lg font-bold leading-tight mb-2 italic">"Vàng SJC đang hạ nhiệt sau đấu thầu, nhưng VN-Index vẫn kẹt tại mốc 1250..."</h2>
                    <p class="text-[11px] text-slate-400">Dựa trên 45 tin tức mới nhất từ CafeF & VnExpress.</p>
                </div>
            </div>

            <!-- Market Feed -->
            <div class="space-y-4">
                <h3 class="font-bold text-slate-800 flex items-center justify-between px-1">
                    Thị trường nóng hổi
                    <span class="text-xs text-indigo-600 font-medium">Xem tất cả</span>
                </h3>

                <!-- Market Card 1 -->
                <div class="market-card bg-white border border-slate-200 rounded-2xl p-4 shadow-sm space-y-4">
                    <div class="flex justify-between items-start">
                        <span class="bg-amber-100 text-amber-700 text-[10px] font-bold px-2 py-0.5 rounded uppercase">Kinh tế</span>
                        <div class="flex items-center gap-1 text-rose-500 text-xs font-bold">
                            <span class="animate-pulse">⏳</span> 02:45:12
                        </div>
                    </div>
                    <h4 class="font-bold text-slate-800 leading-tight">VN-Index có vượt mốc 1.300 điểm vào cuối phiên Thứ Sáu tuần này?</h4>
                    
                    <div class="flex gap-3">
                        <button onclick="openPredictModal('VN-Index', 'CÓ', '3.2x')" class="flex-1 py-3 rounded-xl border-2 border-indigo-600 text-indigo-600 font-bold hover:bg-indigo-50 transition-colors">
                            CÓ (3.2x)
                        </button>
                        <button onclick="openPredictModal('VN-Index', 'KHÔNG', '1.4x')" class="flex-1 py-3 rounded-xl border-2 border-orange-500 text-orange-500 font-bold hover:bg-orange-50 transition-colors">
                            KHÔNG (1.4x)
                        </button>
                    </div>

                    <div class="pt-2">
                        <div class="flex justify-between text-[10px] font-bold text-slate-400 mb-1">
                            <span>PHE CÓ: 28%</span>
                            <span>PHE KHÔNG: 72%</span>
                        </div>
                        <div class="w-full h-1.5 bg-slate-100 rounded-full overflow-hidden flex">
                            <div class="h-full bg-indigo-500" style="width: 28%"></div>
                            <div class="h-full bg-orange-400" style="width: 72%"></div>
                        </div>
                    </div>
                </div>

                <!-- Market Card 2 -->
                <div class="market-card bg-white border border-slate-200 rounded-2xl p-4 shadow-sm space-y-4">
                    <div class="flex justify-between items-start">
                        <span class="bg-blue-100 text-blue-700 text-[10px] font-bold px-2 py-0.5 rounded uppercase">Thể thao</span>
                        <div class="flex items-center gap-1 text-slate-400 text-xs font-bold">
                            <span>🏁</span> Đã đóng dự báo
                        </div>
                    </div>
                    <h4 class="font-bold text-slate-800 leading-tight">Đội tuyển U23 Việt Nam có giữ sạch lưới trong trận gặp Uzbekistan?</h4>
                    <div class="bg-slate-50 p-3 rounded-xl text-center text-xs text-slate-500 font-medium">
                        Đang chờ xác minh sự thật từ BTC...
                    </div>
                </div>
            </div>
        </div>

        <!-- TAB 2: BRAND ZONE -->
        <div id="tab-brand" class="tab-content space-y-6">
            <div class="border-b border-slate-100 pb-4">
                <h2 class="text-2xl font-black text-slate-900">Brand Zone</h2>
                <p class="text-sm text-slate-500">Làm nhiệm vụ, nhận FP bảo chứng bởi nhãn hàng.</p>
            </div>

            <div class="space-y-4">
                <!-- Mission 1 -->
                <div class="bg-white border border-slate-200 rounded-2xl p-4 flex gap-4 items-center">
                    <div class="w-14 h-14 bg-blue-50 rounded-xl flex items-center justify-center shrink-0 border border-blue-100">
                        <span class="text-2xl">🥛</span>
                    </div>
                    <div class="flex-grow">
                        <h4 class="font-bold text-sm">Vinamilk: Ý tưởng bao bì</h4>
                        <p class="text-[11px] text-slate-500">Khảo sát Gen Z • 3 phút</p>
                    </div>
                    <button onclick="simulateSurvey(500)" class="bg-indigo-600 text-white px-4 py-2 rounded-xl text-xs font-bold shadow-lg shadow-indigo-200">
                        +500 FP
                    </button>
                </div>

                <!-- Mission 2 -->
                <div class="bg-white border border-slate-200 rounded-2xl p-4 flex gap-4 items-center">
                    <div class="w-14 h-14 bg-orange-50 rounded-xl flex items-center justify-center shrink-0 border border-orange-100">
                        <span class="text-2xl">🛍️</span>
                    </div>
                    <div class="flex-grow">
                        <h4 class="font-bold text-sm">Shopee: Review xu hướng</h4>
                        <p class="text-[11px] text-slate-500">Xem video • 1 phút</p>
                    </div>
                    <button onclick="simulateSurvey(200)" class="bg-indigo-600 text-white px-4 py-2 rounded-xl text-xs font-bold shadow-lg shadow-indigo-200">
                        +200 FP
                    </button>
                </div>

                <!-- Mission 3 -->
                <div class="bg-white border border-slate-200 rounded-2xl p-4 flex gap-4 items-center opacity-60">
                    <div class="w-14 h-14 bg-slate-50 rounded-xl flex items-center justify-center shrink-0 border border-slate-100">
                        <span class="text-2xl">☕</span>
                    </div>
                    <div class="flex-grow">
                        <h4 class="font-bold text-sm">Highlands Coffee</h4>
                        <p class="text-[11px] text-slate-500 italic">Đã hết ngân sách FP</p>
                    </div>
                    <div class="bg-slate-200 text-slate-500 px-3 py-2 rounded-xl text-[10px] font-bold">
                        ĐÃ ĐÓNG
                    </div>
                </div>
            </div>
        </div>

        <!-- TAB 3: GACHA (REWARDS) -->
        <div id="tab-gacha" class="tab-content space-y-8">
            <div class="text-center space-y-2">
                <h2 class="text-2xl font-black text-slate-900">Hộp Quà May Mắn</h2>
                <p class="text-sm text-slate-500 px-10">Dùng 500 FP mở hộp quà may mắn. Cơ hội nổ Voucher Shopee, Grab, Highlands!</p>
            </div>

            <div class="relative flex justify-center py-10" id="gacha-machine">
                <div id="gacha-box" class="w-48 h-48 gradient-brand rounded-3xl shadow-2xl flex items-center justify-center text-6xl relative z-10 transition-transform cursor-pointer">
                    🎁
                    <div class="absolute inset-0 bg-white/20 rounded-3xl animate-pulse"></div>
                </div>
                <div class="absolute bottom-4 w-56 h-10 bg-slate-200 rounded-full blur-xl opacity-50"></div>
            </div>

            <div class="flex flex-col gap-3 px-6">
                <button id="btn-spin" onclick="spinGacha()" class="w-full py-4 gradient-brand text-white font-black rounded-2xl shadow-xl shadow-indigo-200 text-lg active:scale-95 transition-transform">
                    MỞ 1 LẦN (500 FP)
                </button>
                <p class="text-[10px] text-center text-slate-400 font-medium uppercase tracking-widest">Mọi kết quả được băm mã hóa on-chain</p>
            </div>

            <div class="bg-indigo-50 rounded-2xl p-5 border border-indigo-100">
                <h4 class="font-bold text-indigo-900 text-sm mb-3">Vừa trúng thưởng:</h4>
                <div class="space-y-3">
                    <div class="flex items-center gap-3">
                        <div class="w-8 h-8 rounded-full bg-indigo-200 flex items-center justify-center text-xs">👤</div>
                        <p class="text-xs text-indigo-700"><span class="font-bold">Minh_GenZ</span> vừa trúng <span class="font-bold">Voucher Highlands 50k</span></p>
                    </div>
                    <div class="flex items-center gap-3">
                        <div class="w-8 h-8 rounded-full bg-indigo-200 flex items-center justify-center text-xs">👤</div>
                        <p class="text-xs text-indigo-700"><span class="font-bold">An_Trader</span> vừa trúng <span class="font-bold">300 FP (Hoàn vốn)</span></p>
                    </div>
                </div>
            </div>
        </div>

        <!-- TAB 4: GUILDS -->
        <div id="tab-guild" class="tab-content space-y-6">
            <div class="flex justify-between items-end">
                <div>
                    <h2 class="text-2xl font-black text-slate-900">Bang Hội</h2>
                    <p class="text-sm text-slate-500">Đua Top nhận Quỹ Thưởng Bang.</p>
                </div>
                <button class="bg-slate-900 text-white px-4 py-2 rounded-xl text-xs font-bold">TẠO BANG</button>
            </div>

            <div class="bg-white border border-slate-200 rounded-2xl overflow-hidden shadow-sm">
                <div class="bg-slate-50 p-3 flex justify-between text-[10px] font-bold text-slate-400 uppercase tracking-widest">
                    <span>Hạng / Tên Bang</span>
                    <span>Quyền lực</span>
                </div>
                <div class="divide-y divide-slate-100">
                    <!-- Rank 1 -->
                    <div class="p-4 flex items-center gap-4">
                        <span class="text-amber-500 font-black text-lg">1</span>
                        <div class="w-10 h-10 gradient-brand rounded-full flex items-center justify-center text-white font-bold">🐺</div>
                        <div class="flex-grow">
                            <h4 class="font-bold text-sm text-slate-800">Sói Già Phố Wall</h4>
                            <p class="text-[10px] text-slate-400">452 thành viên</p>
                        </div>
                        <div class="text-right">
                            <p class="font-black text-indigo-600">852.4k</p>
                            <p class="text-[9px] text-slate-400 font-bold uppercase">FP Power</p>
                        </div>
                    </div>
                    <!-- Rank 2 -->
                    <div class="p-4 flex items-center gap-4">
                        <span class="text-slate-400 font-black text-lg">2</span>
                        <div class="w-10 h-10 bg-indigo-100 rounded-full flex items-center justify-center text-indigo-600 font-bold">📈</div>
                        <div class="flex-grow">
                            <h4 class="font-bold text-sm text-slate-800">Hội F0 Chứng Khoán</h4>
                            <p class="text-[10px] text-slate-400">210 thành viên</p>
                        </div>
                        <div class="text-right">
                            <p class="font-black text-slate-700">421.9k</p>
                            <p class="text-[9px] text-slate-400 font-bold uppercase">FP Power</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- TAB 5: PROFILE / WALLET -->
        <div id="tab-profile" class="tab-content space-y-6">
            <div class="flex items-center gap-4">
                <div class="w-20 h-20 rounded-3xl gradient-brand flex items-center justify-center text-4xl text-white shadow-xl shadow-indigo-200">
                    🦊
                </div>
                <div>
                    <h2 class="text-xl font-black text-slate-900">Hoàng Long <span class="text-xs bg-indigo-100 text-indigo-600 px-2 py-0.5 rounded-full ml-1 font-bold">Lv. 12</span></h2>
                    <p class="text-sm text-slate-500 font-mono">UUID: 8a2f-91b3-4c5d</p>
                </div>
            </div>

            <!-- Stats Chart -->
            <div class="bg-white border border-slate-200 rounded-2xl p-5 shadow-sm">
                <h3 class="font-bold text-slate-800 text-sm mb-4">Hiệu suất Đấu trí (7 ngày)</h3>
                <div class="h-40 w-full">
                    <canvas id="profileChart"></canvas>
                </div>
            </div>

            <!-- Transaction History -->
            <div class="space-y-4">
                <h3 class="font-bold text-slate-800 text-sm">Nhật ký giao dịch</h3>
                <div class="space-y-3">
                    <div class="bg-white p-4 rounded-2xl border border-slate-200 flex justify-between items-center">
                        <div class="flex gap-3 items-center">
                            <div class="w-8 h-8 bg-emerald-50 text-emerald-600 rounded-full flex items-center justify-center text-xs">💰</div>
                            <div>
                                <p class="text-xs font-bold">Thắng dự báo VN-Index</p>
                                <p class="text-[10px] text-slate-400">12:05 • 25/04/2024</p>
                            </div>
                        </div>
                        <span class="text-emerald-500 font-black text-sm">+850 FP</span>
                    </div>
                    <div class="bg-white p-4 rounded-2xl border border-slate-200 flex justify-between items-center">
                        <div class="flex gap-3 items-center">
                            <div class="w-8 h-8 bg-rose-50 text-rose-600 rounded-full flex items-center justify-center text-xs">🎰</div>
                            <div>
                                <p class="text-xs font-bold">Mở Hộp quà may mắn</p>
                                <p class="text-[10px] text-slate-400">09:12 • 25/04/2024</p>
                            </div>
                        </div>
                        <span class="text-rose-500 font-black text-sm">-500 FP</span>
                    </div>
                </div>
            </div>
        </div>
    </main>

    <!-- Global Modals -->
    <!-- Predict Modal -->
    <div id="predict-modal" class="fixed inset-0 z-[100] bg-slate-900/60 backdrop-blur-sm flex items-end justify-center hidden">
        <div class="bg-white w-full max-w-md rounded-t-3xl p-6 space-y-6 animate-slide-up">
            <div class="flex justify-between items-center">
                <h3 class="font-black text-xl" id="modal-title">Bảo vệ nhận định</h3>
                <button onclick="closeModal('predict-modal')" class="text-slate-400 text-2xl">&times;</button>
            </div>
            
            <div class="bg-slate-50 p-4 rounded-2xl flex justify-between items-center">
                <div>
                    <p class="text-xs text-slate-500 font-bold uppercase tracking-widest">Lựa chọn của bạn</p>
                    <p class="text-lg font-black text-indigo-600" id="modal-option">CÓ</p>
                </div>
                <div class="text-right">
                    <p class="text-xs text-slate-500 font-bold uppercase tracking-widest">Tỷ lệ ROI</p>
                    <p class="text-lg font-black text-emerald-500" id="modal-roi">3.2x</p>
                </div>
            </div>

            <div class="space-y-3">
                <p class="text-xs font-bold text-slate-500 uppercase tracking-widest">Số điểm muốn đầu tư (FP)</p>
                <div class="grid grid-cols-3 gap-2">
                    <button onclick="setInputVal(100)" class="py-2 rounded-lg bg-slate-100 text-slate-800 font-bold text-sm">100</button>
                    <button onclick="setInputVal(500)" class="py-2 rounded-lg bg-slate-100 text-slate-800 font-bold text-sm">500</button>
                    <button onclick="setInputVal(1000)" class="py-2 rounded-lg bg-slate-100 text-slate-800 font-bold text-sm">1,000</button>
                </div>
                <input type="number" id="predict-amount" class="w-full bg-slate-100 p-4 rounded-xl font-black text-2xl text-center outline-none focus:ring-2 ring-indigo-500" value="100">
            </div>

            <button onclick="confirmPrediction()" class="w-full py-4 gradient-brand text-white font-black rounded-2xl shadow-xl shadow-indigo-200">
                XÁC NHẬN BẢO VỆ
            </button>
        </div>
    </div>

    <!-- Gacha Result Modal -->
    <div id="gacha-result-modal" class="fixed inset-0 z-[100] bg-slate-900/90 backdrop-blur-md flex items-center justify-center hidden px-6">
        <div class="bg-white w-full rounded-3xl p-8 text-center space-y-6 scale-0 transition-transform duration-500" id="gacha-result-card">
            <div class="text-7xl" id="result-emoji">🎇</div>
            <div class="space-y-1">
                <h3 class="text-2xl font-black text-slate-900" id="result-title">XUẤT SẮC!</h3>
                <p class="text-slate-500 text-sm" id="result-desc">Bạn vừa mở trúng Voucher Highlands 50k</p>
            </div>
            <div class="bg-slate-50 border-2 border-dashed border-slate-200 p-4 rounded-2xl font-mono font-bold text-indigo-600 text-xl tracking-widest" id="result-code">
                HL-8291-FZ
            </div>
            <button onclick="closeModal('gacha-result-modal')" class="w-full py-4 gradient-brand text-white font-black rounded-2xl shadow-lg">
                TUYỆT VỜI
            </button>
        </div>
    </div>

    <!-- Bottom Tab Bar -->
    <nav class="fixed bottom-0 left-0 right-0 max-w-md mx-auto bg-white/95 backdrop-blur-lg border-t border-slate-100 px-4 py-2 flex justify-between items-center z-[90] safe-area-bottom">
        <button onclick="switchTab('home')" id="nav-btn-home" class="flex flex-col items-center gap-1 flex-1 text-indigo-600 transition-all">
            <span class="text-xl">📊</span>
            <span class="text-[10px] font-bold uppercase tracking-tight">Đấu trí</span>
        </button>
        <button onclick="switchTab('brand')" id="nav-btn-brand" class="flex flex-col items-center gap-1 flex-1 text-slate-400 transition-all">
            <span class="text-xl">🏢</span>
            <span class="text-[10px] font-bold uppercase tracking-tight">Brands</span>
        </button>
        <button onclick="switchTab('gacha')" id="nav-btn-gacha" class="flex flex-col items-center gap-1 flex-1 text-slate-400 transition-all -translate-y-4">
            <div class="w-14 h-14 gradient-brand rounded-full flex items-center justify-center text-white shadow-xl shadow-indigo-300 border-4 border-white">
                <span class="text-2xl">🎁</span>
            </div>
        </button>
        <button onclick="switchTab('guild')" id="nav-btn-guild" class="flex flex-col items-center gap-1 flex-1 text-slate-400 transition-all">
            <span class="text-xl">🛡️</span>
            <span class="text-[10px] font-bold uppercase tracking-tight">Bang</span>
        </button>
        <button onclick="switchTab('profile')" id="nav-btn-profile" class="flex flex-col items-center gap-1 flex-1 text-slate-400 transition-all">
            <span class="text-xl">👤</span>
            <span class="text-[10px] font-bold uppercase tracking-tight">Ví</span>
        </button>
    </nav>

    <!-- Scripts -->
    <script>
        let userFP = 2450;
        let profileChart = null;

        // Tab Navigation
        function switchTab(tabId) {
            // Hide all tabs
            document.querySelectorAll('.tab-content').forEach(tab => tab.classList.remove('active'));
            // Show target tab
            document.getElementById('tab-' + tabId).classList.add('active');

            // Reset Nav Icons
            document.querySelectorAll('nav button').forEach(btn => {
                btn.classList.replace('text-indigo-600', 'text-slate-400');
            });
            // Set Active Icon
            document.getElementById('nav-btn-' + tabId).classList.replace('text-slate-400', 'text-indigo-600');

            // Special init for Profile
            if (tabId === 'profile') {
                initChart();
            }
        }

        // Global FP Update
        function updateFP(amount) {
            userFP += amount;
            document.getElementById('global-fp').innerText = userFP.toLocaleString();
            
            // Visual feedback on points
            const fpDisplay = document.getElementById('global-fp').parentElement;
            fpDisplay.classList.add('scale-110');
            setTimeout(() => fpDisplay.classList.remove('scale-110'), 200);
        }

        // Prediction Logic
        function openPredictModal(title, option, roi) {
            document.getElementById('modal-title').innerText = title;
            document.getElementById('modal-option').innerText = option;
            document.getElementById('modal-roi').innerText = roi;
            document.getElementById('predict-modal').classList.remove('hidden');
        }

        function setInputVal(val) {
            document.getElementById('predict-amount').value = val;
        }

        function confirmPrediction() {
            const amount = parseInt(document.getElementById('predict-amount').value);
            if (amount > userFP) {
                showSimpleMessage('Bạn không đủ FP. Hãy cày thêm tại Brand Zone!');
                return;
            }
            updateFP(-amount);
            closeModal('predict-modal');
            showSimpleMessage('Đã ghi nhận nhận định! Nhớ check kết quả nhé.');
        }

        // Gacha Logic
        function spinGacha() {
            if (userFP < 500) {
                showSimpleMessage('Cần ít nhất 500 FP để mở hộp quà!');
                return;
            }

            const btn = document.getElementById('btn-spin');
            const box = document.getElementById('gacha-box');
            
            btn.disabled = true;
            updateFP(-500);

            // Start animation
            box.classList.add('gacha-shake');
            btn.innerText = "ĐANG MỞ...";

            setTimeout(() => {
                box.classList.remove('gacha-shake');
                btn.disabled = false;
                btn.innerText = "MỞ 1 LẦN (500 FP)";

                // Weighted Random Logic
                const rand = Math.random();
                if (rand > 0.4) {
                    showGachaResult('VOUCHER', 'Voucher Highlands 50k', 'HL-8291-FZ', '🎆');
                } else {
                    showGachaResult('HOÀN VỐN', 'Bạn nhận lại 300 FP', 'AN ỦI', '🎈');
                    updateFP(300);
                }
            }, 2500);
        }

        function showGachaResult(title, desc, code, emoji) {
            document.getElementById('result-title').innerText = title;
            document.getElementById('result-desc').innerText = desc;
            document.getElementById('result-code').innerText = code;
            document.getElementById('result-emoji').innerText = emoji;
            
            const modal = document.getElementById('gacha-result-modal');
            const card = document.getElementById('gacha-result-card');
            
            modal.classList.remove('hidden');
            setTimeout(() => card.classList.replace('scale-0', 'scale-100'), 50);
        }

        // Survey Simulator
        function simulateSurvey(points) {
            showSimpleMessage('Đang thực hiện khảo sát... (Demo)');
            setTimeout(() => {
                updateFP(points);
                showSimpleMessage(`Chúc mừng! Bạn đã nhận ${points} FP`);
            }, 1500);
        }

        // Utility Modals
        function closeModal(id) {
            if (id === 'gacha-result-modal') {
                document.getElementById('gacha-result-card').classList.replace('scale-100', 'scale-0');
                setTimeout(() => document.getElementById(id).classList.add('hidden'), 300);
            } else {
                document.getElementById(id).classList.add('hidden');
            }
        }

        function showSimpleMessage(msg) {
            const toast = document.createElement('div');
            toast.className = 'fixed top-20 left-1/2 -translate-x-1/2 bg-slate-900 text-white px-6 py-3 rounded-2xl text-xs font-bold z-[200] shadow-2xl animate-fade-in whitespace-nowrap';
            toast.innerText = msg;
            document.body.appendChild(toast);
            setTimeout(() => toast.remove(), 2500);
        }

        // Chart.js Init
        function initChart() {
            if (profileChart) return;
            const ctx = document.getElementById('profileChart').getContext('2d');
            profileChart = new Chart(ctx, {
                type: 'line',
                data: {
                    labels: ['T2', 'T3', 'T4', 'T5', 'T6', 'T7', 'CN'],
                    datasets: [{
                        label: 'FP Kiếm được',
                        data: [1200, 1900, 1500, 2400, 1800, 3200, 2450],
                        borderColor: '#4f46e5',
                        backgroundColor: 'rgba(79, 70, 229, 0.1)',
                        tension: 0.4,
                        fill: true,
                        pointRadius: 0
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: { legend: { display: false } },
                    scales: {
                        y: { display: false },
                        x: { grid: { display: false }, ticks: { font: { size: 10 } } }
                    }
                }
            });
        }
    </script>
</body>
</html>
