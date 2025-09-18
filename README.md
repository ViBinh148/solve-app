```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Web Giải Toán Thông Minh</title>
    <link rel="stylesheet" href="style.css">
    <!-- Tích hợp MathJax để hiển thị LaTeX -->
    <script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
    <script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
    <!-- Tích hợp thư viện giải toán Nerdamer -->
    <script src="https://cdn.jsdelivr.net/npm/nerdamer@1.1.13/nerdamer.core.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/nerdamer@1.1.13/Algebra.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/nerdamer@1.1.13/Calculus.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/nerdamer@1.1.13/Solve.js"></script>
</head>
<body>
    <header>
        <h1>Ứng Dụng Giải Toán Cao Cấp</h1>
        <p>Nhập bài toán của bạn bằng LaTeX và nhận lời giải chi tiết</p>
    </header>

    <main>
        <div class="solver-container">
            <h2>Nhập Bài Toán</h2>
            <textarea id="problem-input" placeholder="Ví dụ: 'tichphan(x^2, x)' để tính tích phân của x^2 hoặc 'daoham(x^3+2x, x)' để tính đạo hàm..."></textarea>
            <button id="solve-button">Giải</button>
            
            <div id="solution-output">
                <h3>Lời Giải Chi Tiết:</h3>
                <div id="solution-steps">
                    <!-- Các bước giải sẽ được hiển thị ở đây -->
                </div>
            </div>
        </div>

        <div class="ai-features">
            <div class="ai-suggestion">
                <h3><span class="ai-icon">💡</span> Gợi Ý Từ AI</h3>
                <div id="ai-hints">
                    <p>Nhập bài toán và nhấn "Giải" để nhận gợi ý.</p>
                </div>
            </div>

            <div class="chatbot-container">
                <h3><span class="ai-icon">🤖</span> Chat Bot 5.0</h3>
                <div id="chat-window">
                    <div class="bot-message">Chào bạn, tôi có thể giúp gì cho việc học của bạn?</div>
                </div>
                <div class="chat-input-area">
                    <input type="text" id="chat-input" placeholder="Hỏi tôi bất cứ điều gì...">
                    <button id="send-chat-button">Gửi</button>
                </div>
            </div>
        </div>
    </main>

    <footer>
        <p>&copy; 2025 - Lập trình bởi Web Developer Chuyên Nghiệp</p>
    </footer>

    <script src="script.js"></script>
</body>
</html>
```

#### **2. `style.css`**

```css
/* General Styling */
body {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
    line-height: 1.6;
    margin: 0;
    padding: 0;
    background-color: #f4f7f9;
    color: #333;
}

header {
    background-color: #007bff;
    color: #fff;
    text-align: center;
    padding: 2rem 1rem;
}

header h1 {
    margin: 0;
    font-size: 2.5rem;
}

main {
    max-width: 1200px;
    margin: 2rem auto;
    padding: 1rem;
    display: grid;
    grid-template-columns: 2fr 1fr;
    gap: 2rem;
}

/* Solver Section */
.solver-container {
    background: #fff;
    padding: 2rem;
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0,0,0,0.1);
}

#problem-input {
    width: 100%;
    height: 100px;
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 4px;
    font-size: 1rem;
    margin-bottom: 1rem;
}

#solve-button {
    display: block;
    width: 100%;
    padding: 1rem;
    background-color: #28a745;
    color: white;
    border: none;
    border-radius: 4px;
    font-size: 1.2rem;
    cursor: pointer;
    transition: background-color 0.3s;
}

#solve-button:hover {
    background-color: #218838;
}

#solution-output {
    margin-top: 2rem;
}

#solution-steps {
    background: #f8f9fa;
    padding: 1rem;
    border-radius: 4px;
    min-height: 50px;
    overflow-x: auto; /* For very long equations */
}

/* AI Features Section */
.ai-features {
    display: flex;
    flex-direction: column;
    gap: 2rem;
}

.ai-icon {
    margin-right: 8px;
}

.ai-suggestion, .chatbot-container {
    background: #fff;
    padding: 1.5rem;
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0,0,0,0.1);
}

/* Chatbot Styling */
.chatbot-container {
    display: flex;
    flex-direction: column;
}

#chat-window {
    height: 300px;
    overflow-y: auto;
    border: 1px solid #ddd;
    border-radius: 4px;
    padding: 10px;
    margin-bottom: 1rem;
    display: flex;
    flex-direction: column;
    gap: 10px;
}

.user-message, .bot-message {
    padding: 8px 12px;
    border-radius: 15px;
    max-width: 80%;
}

.user-message {
    background-color: #007bff;
    color: white;
    align-self: flex-end;
}

.bot-message {
    background-color: #e9ecef;
    color: #333;
    align-self: flex-start;
}

.chat-input-area {
    display: flex;
}

#chat-input {
    flex-grow: 1;
    border: 1px solid #ddd;
    padding: 8px;
    border-radius: 4px 0 0 4px;
}

#send-chat-button {
    padding: 8px 15px;
    border: none;
    background: #007bff;
    color: white;
    cursor: pointer;
    border-radius: 0 4px 4px 0;
}

footer {
    text-align: center;
    padding: 1rem;
    margin-top: 2rem;
    background-color: #343a40;
    color: #fff;
}

/* Responsive */
@media (max-width: 992px) {
    main {
        grid-template-columns: 1fr;
    }
}
```

#### **3. `script.js`**

```javascript
document.addEventListener('DOMContentLoaded', () => {

    const solveButton = document.getElementById('solve-button');
    const problemInput = document.getElementById('problem-input');
    const solutionSteps = document.getElementById('solution-steps');
    const aiHints = document.getElementById('ai-hints');

    const chatInput = document.getElementById('chat-input');
    const sendChatButton = document.getElementById('send-chat-button');
    const chatWindow = document.getElementById('chat-window');

    // --- XỬ LÝ GIẢI BÀI TOÁN ---
    solveButton.addEventListener('click', () => {
        const problem = problemInput.value.trim();
        if (!problem) {
            solutionSteps.innerHTML = '<p>Vui lòng nhập bài toán.</p>';
            return;
        }

        solveProblem(problem);
        getAIHints(problem);
    });

    function solveProblem(problem) {
        solutionSteps.innerHTML = '<p>Đang xử lý...</p>';
        try {
            // Sử dụng Nerdamer để giải bài toán
            // Hàm này cần được mở rộng để xử lý nhiều loại bài toán hơn
            let result;
            if (problem.startsWith('tichphan')) {
                const expression = problem.match(/\((.*),(.*)\)/);
                result = nerdamer.integrate(expression[1].trim(), expression[2].trim());
                displaySolution(`\\int ${nerdamer(expression[1].trim()).toTeX()} \\,d${expression[2].trim()} = ${result.toTeX()} + C`);
            } else if (problem.startsWith('daoham')) {
                const expression = problem.match(/\((.*),(.*)\)/);
                result = nerdamer.diff(expression[1].trim(), expression[2].trim());
                displaySolution(`\\frac{d}{d${expression[2].trim()}}\\left(${nerdamer(expression[1].trim()).toTeX()}\\right) = ${result.toTeX()}`);
            } else if (problem.startsWith('giaipt')) {
                const expression = problem.match(/\((.*)\)/)[1];
                result = nerdamer.solve(expression, 'x'); // Mặc định giải theo biến x
                 displaySolution(`Giải phương trình: ${nerdamer(expression).toTeX()} = 0 \\\\ Nghiệm: x = ${result.toTeX()}`);
            }
            else {
                // Thử tính toán biểu thức trực tiếp
                result = nerdamer(problem);
                displaySolution(`${result.toTeX()}`);
            }

        } catch (error) {
            displaySolution(`<p style="color: red;">Lỗi: Không thể giải bài toán này. Vui lòng kiểm tra lại cú pháp. Lỗi chi tiết: ${error.message}</p>`);
        }
    }

    function displaySolution(latexString) {
        // Hiển thị kết quả dạng LaTeX và yêu cầu MathJax render lại
        solutionSteps.innerHTML = `$$${latexString}$$`;
        MathJax.typesetPromise([solutionSteps]);
    }

    // --- TÍNH NĂNG GỢI Ý CỦA AI (MÔ PHỎNG) ---
    async function getAIHints(problem) {
        aiHints.innerHTML = '<p>AI đang phân tích bài toán...</p>';

        // *** PHẦN TÍCH HỢP API THẬT SẼ NẰM Ở ĐÂY ***
        // Bạn sẽ gọi API của OpenAI hoặc một mô hình AI khác.
        // Ví dụ: const response = await fetch('https://api.openai.com/v1/completions', { ... });
        
        // Dưới đây là dữ liệu mô phỏng
        setTimeout(() => {
            let hint = "Không có gợi ý cụ thể cho bài toán này.";
            if (problem.includes('tichphan')) {
                hint = "Đây là bài toán tính tích phân. Hãy xem xét các phương pháp như: tích phân từng phần, đổi biến số, hoặc sử dụng bảng công thức nguyên hàm cơ bản.";
            } else if (problem.includes('daoham')) {
                hint = "Để tính đạo hàm, bạn cần áp dụng các quy tắc đạo hàm của tổng, hiệu, tích, thương và đạo hàm của các hàm số cơ bản (lũy thừa, lượng giác, loga...).";
            } else if (problem.includes('giaipt')) {
                hint = "Đây là một phương trình. Tùy thuộc vào bậc của phương trình, bạn có thể sử dụng công thức nghiệm, phân tích thành nhân tử, hoặc các phương pháp giải gần đúng.";
            }
            aiHints.innerHTML = `<p>${hint}</p>`;
        }, 1500); // Giả lập thời gian chờ AI phản hồi
    }

    // --- CHATBOT (MÔ PHỎNG) ---
    sendChatButton.addEventListener('click', handleChat);
    chatInput.addEventListener('keypress', (e) => {
        if (e.key === 'Enter') {
            handleChat();
        }
    });

    function handleChat() {
        const userMessage = chatInput.value.trim();
        if (!userMessage) return;

        appendMessage(userMessage, 'user');
        chatInput.value = '';

        // Mô phỏng chatbot trả lời
        getBotResponse(userMessage);
    }
    
    function appendMessage(message, sender) {
        const messageDiv = document.createElement('div');
        messageDiv.classList.add(sender === 'user' ? 'user-message' : 'bot-message');
        messageDiv.textContent = message;
        chatWindow.appendChild(messageDiv);
        chatWindow.scrollTop = chatWindow.scrollHeight; // Tự động cuộn xuống tin nhắn mới nhất
    }
    
    async function getBotResponse(userMessage) {
         // *** PHẦN TÍCH HỢP API THẬT SẼ NẰM Ở ĐÂY ***
        // Giống như gợi ý AI, bạn sẽ gửi userMessage đến API của chatbot
        
        // Dữ liệu mô phỏng
        setTimeout(() => {
            let botReply = "Tôi chưa hiểu câu hỏi của bạn. Bạn có thể hỏi về các khái niệm toán học như 'đạo hàm là gì?', 'tích phân là gì?'.";
            if (userMessage.toLowerCase().includes('đạo hàm')) {
                botReply = "Đạo hàm của một hàm số là một đại lượng mô tả sự biến thiên của hàm tại một điểm nào đó. Nó cho biết tốc độ thay đổi của hàm số.";
            } else if (userMessage.toLowerCase().includes('tích phân')) {
                botReply = "Tích phân có hai loại chính: tích phân không xác định (nguyên hàm) và tích phân xác định (tính diện tích dưới đồ thị).";
            }
            appendMessage(botReply, 'bot');
        }, 1000);
    }
});
