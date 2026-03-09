<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Forely - Community Forecasting</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        body { background-color: #0f172a; color: #f8fafc; }
        .market-card { background-color: #1e293b; border: 1px solid #334155; transition: 0.3s; }
        .market-card:hover { border-color: #3b82f6; }
    </style>
</head>
<body class="p-6">

    <header class="max-w-6xl mx-auto flex justify-between items-center mb-10">
        <h1 class="text-3xl font-bold text-blue-500">FORELY</h1>
        <div id="user-wallet" class="bg-blue-900/30 border border-blue-500 p-2 rounded-lg text-sm">
            Số dư: <span id="balance">10,000</span> FP
        </div>
    </header>

    <main class="max-w-6xl mx-auto">
        <h2 class="text-xl mb-6 font-medium text-gray-400">Các sự kiện đang diễn ra</h2>
        <div id="market-list" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
            <p class="text-gray-500">Đang tải dữ liệu từ Xano...</p>
        </div>
    </main>

    <script>
        // Đường link API bạn đã cung cấp
        const API_URL = "https://x8ki-letl-twmt.n7.xano.io/api:j6vjWKEW/market";

        async function fetchMarkets() {
            try {
                const response = await fetch(API_URL);
                const markets = await response.json();
                renderMarkets(markets);
            } catch (error) {
                console.error("Lỗi khi lấy dữ liệu:", error);
                document.getElementById('market-list').innerHTML = "Không thể kết nối với Xano.";
            }
        }

        function renderMarkets(markets) {
            const container = document.getElementById('market-list');
            container.innerHTML = ""; // Xóa nội dung cũ

            markets.forEach(item => {
                // Dựa trên các cột: question, category, image_url, total_yes, total_no
                const card = `
                    <div class="market-card rounded-2xl overflow-hidden shadow-lg">
                        <img src="${item.image_url}" class="w-full h-44 object-cover">
                        <div class="p-5">
                            <span class="text-xs font-bold text-blue-400 uppercase">${item.category}</span>
                            <h3 class="text-lg font-semibold mt-2 mb-4 leading-tight">${item.question}</h3>
                            
                            <div class="grid grid-cols-2 gap-4">
                                <button onclick="bet('YES', ${item.id})" class="bg-green-600/20 text-green-500 border border-green-600 font-bold py-2 rounded-xl hover:bg-green-600 hover:text-white transition">
                                    CÓ (${item.total_yes})
                                </button>
                                <button onclick="bet('NO', ${item.id})" class="bg-red-600/20 text-red-500 border border-red-600 font-bold py-2 rounded-xl hover:bg-red-600 hover:text-white transition">
                                    KHÔNG (${item.total_no})
                                </button>
                            </div>
                        </div>
                    </div>
                `;
                container.innerHTML += card;
            });
        }

        function bet(side, marketId) {
            alert(`Bạn đã chọn ${side} cho dự báo số ${marketId}. Tính năng đặt cược đang được kết nối...`);
        }

        // Chạy hàm lấy dữ liệu khi trang web mở ra
        fetchMarkets();
    </script>
</body>
</html>
