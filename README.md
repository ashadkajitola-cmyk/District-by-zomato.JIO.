<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PhonePe Pro Max - Banking, Cricket Schedule & Betting Platform</title>
    <style>
        :root {
            --primary: #5f259f; /* PhonePe Purple */
            --secondary: #1293d4;
            --accent: #ff9800;
            --bg: #f0f2f5;
            --white: #ffffff;
            --text: #222222;
            --danger: #e74c3c;
            --success: #10b981;
            --border: #dcdcdc;
        }
        * { box-sizing: border-box; margin: 0; padding: 0; font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; }
        body { background-color: var(--bg); color: var(--text); padding-bottom: 60px; font-size: 16px; }
        
        header { background: linear-gradient(135deg, var(--primary), #3b1568); color: var(--white); padding: 18px 25px; display: flex; justify-content: space-between; align-items: center; box-shadow: 0 4px 20px rgba(0,0,0,0.2); }
        header h1 { font-size: 1.4rem; font-weight: 800; letter-spacing: 0.5px; display: flex; align-items: center; gap: 8px; }
        .user-info { display: flex; gap: 15px; align-items: center; font-size: 0.95rem; }
        .wallet-badge { background: #ffffff22; color: #fff; padding: 8px 16px; border-radius: 12px; border: 1px solid rgba(255,255,255,0.3); font-weight: bold; font-size: 1rem; display: flex; flex-direction: column; align-items: flex-end; }
        
        .container { max-width: 950px; margin: 20px auto; padding: 0 15px; display: flex; flex-direction: column; gap: 20px; }
        .card { background: var(--white); border-radius: 16px; padding: 22px; box-shadow: 0 6px 18px rgba(0,0,0,0.05); border: 1px solid #e5e7eb; }
        
        h2 { font-size: 1.4rem; margin-bottom: 12px; color: var(--primary); font-weight: 700; }
        h3 { font-size: 1.2rem; margin-bottom: 10px; color: #333; font-weight: 700; }
        
        .btn { background: var(--primary); color: var(--white); border: none; padding: 12px 20px; border-radius: 10px; cursor: pointer; font-weight: bold; font-size: 1rem; transition: 0.2s; box-shadow: 0 3px 6px rgba(0,0,0,0.1); width: 100%; text-align: center; display: inline-block; }
        .btn:hover { opacity: 0.92; transform: translateY(-1px); }
        .btn-danger { background: var(--danger); }
        .btn-success { background: var(--success); }
        .btn-warning { background: var(--accent); color: #000; }
        .btn-secondary { background: #4b5563; }
        
        input, select, textarea { width: 100%; padding: 12px 16px; margin: 8px 0 16px 0; border: 2px solid var(--border); border-radius: 10px; font-size: 1rem; background: #fff; }
        input:focus, select:focus { border-color: var(--primary); outline: none; }
        label { font-weight: 700; font-size: 0.9rem; color: #444; display: block; margin-top: 5px; }
        
        .tabs { display: flex; gap: 8px; margin-bottom: 10px; background: #e2e8f0; padding: 6px; border-radius: 12px; flex-wrap: wrap; }
        .tab-btn { flex: 1; min-width: 110px; padding: 10px; background: transparent; border: none; border-radius: 8px; cursor: pointer; font-weight: bold; color: #555; transition: 0.2s; font-size: 0.9rem; text-align: center; }
        .tab-btn.active { background: var(--white); color: var(--primary); box-shadow: 0 3px 8px rgba(0,0,0,0.1); }

        .bank-grid { display: grid; grid-template-columns: repeat(auto-fill, min-minmax(130px, 1fr)); gap: 12px; margin: 15px 0; }
        .bank-card-item { border: 2px solid var(--border); border-radius: 12px; padding: 15px; text-align: center; cursor: pointer; font-weight: bold; transition: 0.2s; background: #fff; }
        .bank-card-item:hover, .bank-card-item.selected { border-color: var(--primary); background: #f3e8ff; color: var(--primary); }

        /* Debit Card Realistic UI */
        .debit-card-graphic {
            background: linear-gradient(135deg, #1e1e2f, #3a3a5e);
            color: #fff; border-radius: 16px; padding: 20px; box-shadow: 0 8px 20px rgba(0,0,0,0.3);
            max-width: 380px; margin: 15px auto; position: relative; font-family: 'Courier New', Courier, monospace;
        }
        .debit-card-chip { width: 45px; height: 32px; background: linear-gradient(135deg, #ffe066, #f59f00); border-radius: 6px; margin-bottom: 15px; }
        .debit-card-number { font-size: 1.3rem; letter-spacing: 2px; margin-bottom: 15px; text-shadow: 1px 1px 2px #000; }
        .debit-card-expiry { display: flex; gap: 20px; font-size: 0.85rem; }

        .hidden { display: none !important; }
        .flex-row { display: flex; gap: 12px; }
        .flex-row > * { flex: 1; }

        .history-item { background: #fff; border: 1px solid #e5e7eb; border-left: 5px solid var(--success); border-radius: 10px; padding: 14px; margin-bottom: 10px; }
        .history-item.sent { border-left-color: var(--danger); }
        
        .modal { position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.7); display: flex; justify-content: center; align-items: center; z-index: 1000; overflow-y: auto; padding: 20px; }
        .modal-content { background: var(--white); padding: 25px; border-radius: 16px; width: 100%; max-width: 500px; position: relative; max-height: 90vh; overflow-y: auto; box-shadow: 0 10px 30px rgba(0,0,0,0.3); }
        .close-modal { position: absolute; top: 15px; right: 20px; font-size: 1.8rem; cursor: pointer; color: #666; font-weight: bold; }

        /* Blue Tick Success Screen */
        .success-checkmark { text-align: center; padding: 20px 0; }
        .check-icon { width: 80px; height: 80px; background: var(--success); color: #fff; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-size: 3rem; margin: 0 auto 15px auto; box-shadow: 0 4px 15px rgba(16,185,129,0.4); }
    </style>
</head>
<body>

    <header>
        <h1>🟣 PhonePe Digital Platform</h1>
        <div class="user-info">
            <span id="displayUserName" style="font-weight: 700;">Login करें</span>
            <div class="wallet-badge">
                <span>Wallet: ₹<span id="displayWallet">0</span></span>
                <span id="displayReceiveCode" style="font-size:0.8rem; color:#ffd700; margin-top:2px;">Code: ----</span>
            </div>
            <button class="btn btn-danger" id="logoutBtn" onclick="logout()" style="padding: 6px 12px; font-size: 0.85rem; width: auto; display:none;">Logout</button>
        </div>
    </header>

    <div class="container">

        <!-- Login Section -->
        <div id="loginSection" class="card">
            <h2>🔐 Mobile Login / Register</h2>
            <p style="font-size:0.95rem; color:#555; margin-bottom:15px;">PhonePe सेवाओं और वॉलेट का उपयोग करने के लिए लॉगिन करें।</p>
            
            <label>Full Name (आपका नाम):</label>
            <input type="text" id="loginNameInput" placeholder="Enter your full name">

            <label>Mobile Number (10-Digit):</label>
            <input type="text" id="loginMobileInput" maxlength="10" placeholder="Enter 10-digit mobile number">
            
            <button class="btn" onclick="handleLogin()">Proceed to PhonePe Dashboard</button>
        </div>

        <!-- Main Dashboard -->
        <div id="mainDashboard" class="hidden">

            <!-- Top PhonePe Action Grid -->
            <div class="card" style="background: linear-gradient(to right, #f3e8ff, #ffffff); border-left: 6px solid var(--primary);">
                <h3>📱 PhonePe Money Transfer & Payments</h3>
                <p style="font-size: 0.9rem; color: #555; margin-bottom: 15px;">
                    आपका Receive Code: <b id="myReceiveCodeBadge" style="color:var(--primary); font-size:1.1rem;">----</b> 
                    <span style="color:#d97706; font-size:0.85rem;">(आप पैसे प्राप्त कर सकते हैं, भेजने के लिए बैंक खाता और PIN आवश्यक है)</span>
                </p>
                <div class="flex-row">
                    <button class="btn" onclick="openSendMoneyModal()">💸 Send Money (Code से)</button>
                    <button class="btn btn-warning" onclick="openRechargeModal()">📱 Mobile Recharge</button>
                </div>
            </div>

            <!-- Bank Account & Debit Card Section -->
            <div class="card" style="border-left: 6px solid #1293d4;">
                <h3>🏦 PhonePe Bank Account & Debit Card Setup</h3>
                <div id="noBankAccountView">
                    <p style="font-size:0.95rem; color:#555;">अगर आप पैसे ट्रांसफर करना चाहते हैं, तो किसी भी बैंक में ऑनलाइन खाता खोलें:</p>
                    
                    <div class="bank-grid">
                        <div class="bank-card-item" onclick="selectBank(this, 'SBI Bank')">🏛️ SBI Bank</div>
                        <div class="bank-card-item" onclick="selectBank(this, 'HDFC Bank')">🏛️ HDFC Bank</div>
                        <div class="bank-card-item" onclick="selectBank(this, 'ICICI Bank')">🏛️ ICICI Bank</div>
                        <div class="bank-card-item" onclick="selectBank(this, 'Paytm Payments Bank')">🏛️ Paytm Bank</div>
                        <div class="bank-card-item" onclick="selectBank(this, 'Axis Bank')">🏛️ Axis Bank</div>
                    </div>
                    <button class="btn btn-success" onclick="openAccountInSelectedBank()">खाता खोलें (Open Account)</button>
                </div>

                <div id="bankAccountActiveView" class="hidden">
                    <div style="display:flex; justify-content:space-between; align-items:center;">
                        <div>
                            <h4 id="userBankNameDisplay" style="color:var(--primary); font-size:1.1rem;">SBI Bank Account Active</h4>
                            <p style="font-size:0.85rem; color:#666;">A/C No: XXXXXX4821 | Status: <span style="color:green; font-weight:bold;">Verified</span></p>
                        </div>
                        <div id="debitCardStatusBadge"></div>
                    </div>

                    <!-- Debit Card Apply Section -->
                    <div id="applyDebitCardBox" style="margin-top:15px; background:#f9fafb; padding:15px; border-radius:10px;">
                        <p style="font-size:0.9rem; color:#333; margin-bottom:10px;">UPI PIN सेट करने के लिए ATM / Debit Card की आवश्यकता है।</p>
                        <button class="btn btn-primary" onclick="applyDebitCard()">💳 Apply Debit Card</button>
                    </div>

                    <div id="debitCardProcessingBox" class="hidden" style="margin-top:15px; text-align:center; padding:15px; background:#fef3c7; border-radius:10px;">
                        <p style="font-weight:bold; color:#b45309;">⏳ Card Application Under Process...</p>
                        <p style="font-size:0.9rem;">आपका डेबिट कार्ड 2 घंटे में तैयार हो जाएगा।</p>
                        <p style="font-size:1.1rem; font-weight:bold; color:#d97706; margin-top:5px;" id="cardTimerDisplay">01:59:59</p>
                    </div>

                    <!-- Issued Debit Card Display -->
                    <div id="debitCardReadyBox" class="hidden">
                        <div class="debit-card-graphic">
                            <div style="display:flex; justify-content:space-between; font-size:0.8rem; font-weight:bold; letter-spacing:1px; margin-bottom:10px;">
                                <span id="cardBankLabel">BANK</span>
                                <span>DEBIT</span>
                            </div>
                            <div class="debit-card-chip"></div>
                            <div class="debit-card-number" id="cardNumberDisplay">XXXX XXXX XXXX</div>
                            <div class="debit-card-expiry">
                                <div>MM: <span id="cardMMDisplay">XX</span></div>
                                <div>YY: <span id="cardYYDisplay">XX</span></div>
                            </div>
                        </div>

                        <div style="text-align:center; margin-top:10px;">
                            <button class="btn btn-warning" style="width:auto; padding:10px 25px;" onclick="openSetPinModal()">🔑 Set / Reset UPI PIN</button>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Tabs Navigation -->
            <div class="tabs">
                <button class="tab-btn active" onclick="switchTab('history', event)">📜 History</button>
                <button class="tab-btn" onclick="switchTab('cricket', event)">🏏 Matches</button>
                <button class="tab-btn" onclick="switchTab('activeTickets', event)">🎟️ Tickets</button>
            </div>

            <!-- History Section -->
            <div id="historyTabContent" class="tab-content card">
                <h2>📜 Transaction & Passbook History</h2>
                <p style="font-size:0.9rem; color:#666; margin-bottom:15px;">किसने पैसे भेजे, कितने भेजे और किस बैंक खाते में ट्रांसफर हुए:</p>
                <div id="historyList"></div>
            </div>

            <!-- Cricket Schedule Section -->
            <div id="cricketTabContent" class="tab-content card hidden">
                <h2>🏏 Upcoming Cricket Matches</h2>
                <div id="matchesList">
                    <div style="border: 1px solid var(--border); padding: 15px; border-radius: 10px; margin-top: 10px;">
                        <h4>IND vs SA - 4th T20I</h4>
                        <p style="font-size:0.85rem; color:#666;">WED, 17 DEC | EKANA STADIUM, LUCKNOW</p>
                        <button class="btn btn-success" style="margin-top:10px; padding:8px;" onclick="buyMatchTicket('IND vs SA - 4th T20I', 250)">Buy Ticket (₹250 - PIN Required)</button>
                    </div>
                </div>
            </div>

            <!-- Active Tickets -->
            <div id="activeTicketsTabContent" class="tab-content card hidden">
                <h2>🎟️ My Booked Tickets</h2>
                <div id="myTicketsList">
                    <p style="font-size:0.9rem; color:#777;">कोई भी टिकट नहीं खरीदा गया है।</p>
                </div>
            </div>

        </div>
    </div>

    <!-- MODALS -->

    <!-- Send Money Modal -->
    <div id="sendMoneyModal" class="modal hidden">
        <div class="modal-content">
            <span class="close-modal" onclick="closeModal('sendMoneyModal')">&times;</span>
            <h3>💸 Send Money via 4-Digit Code</h3>
            
            <label>Receiver 4-Digit Code:</label>
            <input type="text" id="sendCodeInput" maxlength="4" placeholder="Enter 4-digit code" oninput="lookupReceiverName()">
            
            <div id="receiverInfoBox" class="hidden" style="background:#e0f2fe; padding:10px; border-radius:8px; margin-bottom:12px; font-weight:bold; color:#0369a1;">
                Paying To: <span id="receiverNameDisplay">---</span>
            </div>

            <label>Amount (₹):</label>
            <input type="number" id="sendAmountInput" placeholder="Enter amount">

            <button class="btn btn-success" onclick="proceedToPaymentPin()">Proceed to Pay</button>
        </div>
    </div>

    <!-- Enter PIN Modal -->
    <div id="pinModal" class="modal hidden">
        <div class="modal-content">
            <span class="close-modal" onclick="closeModal('pinModal')">&times;</span>
            <h3 style="text-align:center;">🔑 Enter 4-Digit UPI PIN</h3>
            <p style="text-align:center; font-size:0.9rem; color:#666; margin-bottom:15px;">सुरक्षा के लिए अपना 4-अंकों का PIN दर्ज करें</p>
            
            <input type="password" id="enterUpiPinInput" maxlength="4" style="text-align:center; font-size:1.8rem; letter-spacing:10px;" placeholder="****">
            
            <button class="btn" onclick="verifyAndExecuteTransaction()">PAY NOW</button>
        </div>
    </div>

    <!-- Success Receipt Modal (Blue Tick) -->
    <div id="successModal" class="modal hidden">
        <div class="modal-content" style="text-align:center;">
            <div class="success-checkmark">
                <div class="check-icon">✓</div>
                <h2 style="color:#10b981;">Payment Successful!</h2>
                <p style="font-size:1.8rem; font-weight:bold; color:#111; margin:10px 0;" id="successAmountDisplay">₹0</p>
                <p style="color:#555; font-weight:600;" id="successReceiverDisplay">To Receiver</p>
                <p style="font-size:0.8rem; color:#888; margin-top:15px;" id="successBankInfoDisplay">Debited from Bank Account</p>
            </div>
            <button class="btn" onclick="closeModal('successModal')">Done</button>
        </div>
    </div>

    <!-- Set PIN Modal -->
    <div id="setPinModal" class="modal hidden">
        <div class="modal-content">
            <span class="close-modal" onclick="closeModal('setPinModal')">&times;</span>
            <h3>🔑 Set UPI PIN</h3>
            
            <div id="setPinStep1">
                <p style="font-size:0.85rem; color:#555; margin-bottom:10px;">डेबिट कार्ड की जानकारी दर्ज करके पुष्टि करें:</p>
                
                <label>Last 6 Digits of Debit Card:</label>
                <input type="text" id="pinCardDigitsInput" maxlength="6" placeholder="123456">

                <div class="flex-row">
                    <div>
                        <label>MM (4-Digit):</label>
                        <input type="text" id="pinMMInput" maxlength="4" placeholder="0012">
                    </div>
                    <div>
                        <label>YY (4-Digit):</label>
                        <input type="text" id="pinYYInput" maxlength="4" placeholder="2028">
                    </div>
                </div>
                <button class="btn" onclick="verifyCardDetailsForPin()">Proceed</button>
            </div>

            <div id="setPinStep2" class="hidden">
                <label>Enter New 4-Digit PIN:</label>
                <input type="password" id="newPinInput1" maxlength="4" style="text-align:center; font-size:1.4rem;" placeholder="****">
                <button class="btn" onclick="proceedToReenterPin()">Proceed</button>
            </div>

            <div id="setPinStep3" class="hidden">
                <label>Re-enter 4-Digit PIN (दोबारा दर्ज करें):</label>
                <input type="password" id="newPinInput2" maxlength="4" style="text-align:center; font-size:1.4rem;" placeholder="****">
                <button class="btn btn-success" onclick="saveFinalPin()">Confirm & Set PIN</button>
            </div>
        </div>
    </div>

    <!-- Mobile Recharge Modal -->
    <div id="rechargeModal" class="modal hidden">
        <div class="modal-content">
            <span class="close-modal" onclick="closeModal('rechargeModal')">&times;</span>
            <h3>📱 Mobile Recharge</h3>
            
            <label>Mobile Number:</label>
            <input type="text" id="rechargeMobileInput" maxlength="10" placeholder="Enter mobile number">

            <label>Select Plan:</label>
            <select id="rechargePlanSelect">
                <option value="299">₹299 - 1.5GB/Day (28 Days)</option>
                <option value="666">₹666 - 1.5GB/Day (84 Days)</option>
                <option value="19">₹19 - 1GB Data Pack</option>
            </select>

            <button class="btn btn-success" onclick="proceedToRechargePin()">Pay & Recharge</button>
        </div>
    </div>

    <script>
        // Global App State
        let currentUser = null;
        let selectedBankTemp = null;
        let pendingAction = null; // Store transaction intent

        // Mock Database of users by Receive Code
        const mockUsers = {
            "1001": { name: "Rahul Sharma", bank: "SBI Bank" },
            "1002": { name: "Priya Singh", bank: "HDFC Bank" },
            "1003": { name: "Amit Kumar", bank: "Paytm Payments Bank" }
        };

        // Initialize Application
        window.onload = function() {
            const saved = localStorage.getItem('phonepe_user');
            if (saved) {
                currentUser = JSON.parse(saved);
                showDashboard();
            }
        };

        function handleLogin() {
            const name = document.getElementById('loginNameInput').value.trim();
            const mobile = document.getElementById('loginMobileInput').value.trim();

            if (!name || mobile.length !== 10) {
                alert('Kripya apna Naam aur 10-digit Mobile Number bharein.');
                return;
            }

            // Assign unique 4-digit receive code based on mobile
            const receiveCode = mobile.substring(6, 10);

            currentUser = {
                name: name,
                mobile: mobile,
                receiveCode: receiveCode,
                wallet: 500, // Initial Signup Bonus
                bank: null,
                debitCardStatus: 'NONE', // NONE, PROCESSING, READY
                cardDetails: null,
                upiPin: null,
                history: [],
                tickets: []
            };

            // Register in mock database
            mockUsers[receiveCode] = { name: name, bank: "Not Set" };

            saveUserData();
            showDashboard();
        }

        function saveUserData() {
            localStorage.setItem('phonepe_user', JSON.stringify(currentUser));
        }

        function showDashboard() {
            document.getElementById('loginSection').classList.add('hidden');
            document.getElementById('mainDashboard').classList.remove('hidden');
            document.getElementById('logoutBtn').style.display = 'block';

            document.getElementById('displayUserName').innerText = currentUser.name;
            document.getElementById('displayWallet').innerText = currentUser.wallet;
            document.getElementById('displayReceiveCode').innerText = "Code: " + currentUser.receiveCode;
            document.getElementById('myReceiveCodeBadge').innerText = currentUser.receiveCode;

            renderBankingUI();
            renderHistory();
        }

        function logout() {
            localStorage.removeItem('phonepe_user');
            location.reload();
        }

        // --- BANKING & DEBIT CARD LOGIC ---
        function selectBank(element, bankName) {
            document.querySelectorAll('.bank-card-item').forEach(el => el.classList.remove('selected'));
            element.classList.add('selected');
            selectedBankTemp = bankName;
        }

        function openAccountInSelectedBank() {
            if (!selectedBankTemp) {
                alert('Kripya koi ek Bank select karein!');
                return;
            }
            currentUser.bank = selectedBankTemp;
            mockUsers[currentUser.receiveCode].bank = selectedBankTemp;
            saveUserData();
            renderBankingUI();
            alert(selectedBankTemp + ' me aapka Khata khul gaya hai! Ab Debit Card apply karein.');
        }

        function renderBankingUI() {
            if (!currentUser.bank) {
                document.getElementById('noBankAccountView').classList.remove('hidden');
                document.getElementById('bankAccountActiveView').classList.add('hidden');
                return;
            }

            document.getElementById('noBankAccountView').classList.add('hidden');
            document.getElementById('bankAccountActiveView').classList.remove('hidden');
            document.getElementById('userBankNameDisplay').innerText = currentUser.bank + " Account Active";

            // Status Card
            if (currentUser.debitCardStatus === 'NONE') {
                document.getElementById('applyDebitCardBox').classList.remove('hidden');
                document.getElementById('debitCardProcessingBox').classList.add('hidden');
                document.getElementById('debitCardReadyBox').classList.add('hidden');
            } else if (currentUser.debitCardStatus === 'PROCESSING') {
                document.getElementById('applyDebitCardBox').classList.add('hidden');
                document.getElementById('debitCardProcessingBox').classList.remove('hidden');
                document.getElementById('debitCardReadyBox').classList.add('hidden');
            } else if (currentUser.debitCardStatus === 'READY') {
                document.getElementById('applyDebitCardBox').classList.add('hidden');
                document.getElementById('debitCardProcessingBox').classList.add('hidden');
                document.getElementById('debitCardReadyBox').classList.remove('hidden');

                document.getElementById('cardBankLabel').innerText = currentUser.bank.toUpperCase();
                document.getElementById('cardNumberDisplay').innerText = currentUser.cardDetails.number;
                document.getElementById('cardMMDisplay').innerText = currentUser.cardDetails.mm;
                document.getElementById('cardYYDisplay').innerText = currentUser.cardDetails.yy;
            }
        }

        function applyDebitCard() {
            currentUser.debitCardStatus = 'PROCESSING';
            saveUserData();
            renderBankingUI();

            // Simulate 2 hour countdown (Fast-forwarded for UI responsiveness)
            let secondsLeft = 7200; // 2 hours
            const timer = setInterval(() => {
                secondsLeft -= 60;
                let h = Math.floor(secondsLeft / 3600);
                let m = Math.floor((secondsLeft % 3600) / 60);
                document.getElementById('cardTimerDisplay').innerText = `0${h}:${m < 10 ? '0' : ''}${m}:00`;

                if (secondsLeft <= 0 || true) { // Auto-ready for user testing
                    clearInterval(timer);
                    generateDebitCard();
                }
            }, 1000);
        }

        function generateDebitCard() {
            // 12 digit card + 4 digit MM + 4 digit YY
            const random12 = Math.floor(100000000000 + Math.random() * 900000000000).toString();
            currentUser.debitCardStatus = 'READY';
            currentUser.cardDetails = {
                number: random12.match(/.{1,4}/g).join(" "),
                rawNumber: random12,
                last6: random12.substring(6, 12),
                mm: "0012",
                yy: "2028"
            };
            saveUserData();
            renderBankingUI();
        }

        // --- PIN SETTING LOGIC ---
        function openSetPinModal() {
            document.getElementById('setPinStep1').classList.remove('hidden');
            document.getElementById('setPinStep2').classList.add('hidden');
            document.getElementById('setPinStep3').classList.add('hidden');
            document.getElementById('setPinModal').classList.remove('hidden');
        }

        function verifyCardDetailsForPin() {
            const digits = document.getElementById('pinCardDigitsInput').value.trim();
            const mm = document.getElementById('pinMMInput').value.trim();
            const yy = document.getElementById('pinYYInput').value.trim();

            if (digits !== currentUser.cardDetails.last6 || mm !== currentUser.cardDetails.mm || yy !== currentUser.cardDetails.yy) {
                alert('Galat Number ya Expiry details! Kripya sahi Debit Card details bharein.');
                return;
            }

            document.getElementById('setPinStep1').classList.add('hidden');
            document.getElementById('setPinStep2').classList.remove('hidden');
        }

        let tempNewPin = "";
        function proceedToReenterPin() {
            const pin1 = document.getElementById('newPinInput1').value.trim();
            if (pin1.length !== 4) {
                alert('4-digit PIN dalein!');
                return;
            }
            tempNewPin = pin1;
            document.getElementById('setPinStep2').classList.add('hidden');
            document.getElementById('setPinStep3').classList.remove('hidden');
        }

        function saveFinalPin() {
            const pin2 = document.getElementById('newPinInput2').value.trim();
            if (pin2 !== tempNewPin) {
                alert('PIN match nahi huya! Doshara koshish karein.');
                return;
            }
            currentUser.upiPin = pin2;
            saveUserData();
            closeModal('setPinModal');
            alert('UPI PIN Set Ho Gaya Hai Successfully!');
        }

        // --- MONEY TRANSFER LOGIC ---
        function openSendMoneyModal() {
            if (!currentUser.bank || !currentUser.upiPin) {
                alert('Paiise bhejne ke liye Pehle Bank me Khata khol kar Debit Card se PIN set karein!');
                return;
            }
            document.getElementById('sendMoneyModal').classList.remove('hidden');
        }

        function lookupReceiverName() {
            const code = document.getElementById('sendCodeInput').value.trim();
            if (code.length === 4) {
                if (mockUsers[code]) {
                    document.getElementById('receiverNameDisplay').innerText = mockUsers[code].name;
                    document.getElementById('receiverInfoBox').classList.remove('hidden');
                } else {
                    document.getElementById('receiverNameDisplay').innerText = "User Not Found";
                    document.getElementById('receiverInfoBox').classList.remove('hidden');
                }
            } else {
                document.getElementById('receiverInfoBox').classList.add('hidden');
            }
        }

        function proceedToPaymentPin() {
            const code = document.getElementById('sendCodeInput').value.trim();
            const amount = parseFloat(document.getElementById('sendAmountInput').value);

            if (!mockUsers[code]) {
                alert('Sahi 4-Digit Code dalein!');
                return;
            }
            if (isNaN(amount) || amount <= 0 || amount > currentUser.wallet) {
                alert('Sahi Amount dalein ya Wallet balance check karein!');
                return;
            }

            pendingAction = {
                type: 'SEND_MONEY',
                code: code,
                receiverName: mockUsers[code].name,
                receiverBank: mockUsers[code].bank || 'SBI Bank',
                amount: amount
            };

            closeModal('sendMoneyModal');
            document.getElementById('pinModal').classList.remove('hidden');
        }

        function verifyAndExecuteTransaction() {
            const enteredPin = document.getElementById('enterUpiPinInput').value.trim();

            if (enteredPin !== currentUser.upiPin) {
                alert('Galat PIN! Kripya sahi PIN dalein.');
                return;
            }

            closeModal('pinModal');
            document.getElementById('enterUpiPinInput').value = '';

            if (pendingAction.type === 'SEND_MONEY') {
                currentUser.wallet -= pendingAction.amount;
                
                // Add to History
                currentUser.history.unshift({
                    type: 'SENT',
                    name: pendingAction.receiverName,
                    bank: pendingAction.receiverBank,
                    amount: pendingAction.amount,
                    date: new Date().toLocaleTimeString()
                });

                saveUserData();
                showDashboard();

                // Show Blue Tick Success Receipt
                document.getElementById('successAmountDisplay').innerText = '₹' + pendingAction.amount;
                document.getElementById('successReceiverDisplay').innerText = 'Paid to ' + pendingAction.receiverName;
                document.getElementById('successBankInfoDisplay').innerText = 'Debited from ' + currentUser.bank;
                document.getElementById('successModal').classList.remove('hidden');
            } else if (pendingAction.type === 'RECHARGE') {
                currentUser.wallet -= pendingAction.amount;
                currentUser.history.unshift({
                    type: 'RECHARGE',
                    name: 'Mobile Recharge (' + pendingAction.mobile + ')',
                    bank: currentUser.bank,
                    amount: pendingAction.amount,
                    date: new Date().toLocaleTimeString()
                });
                saveUserData();
                showDashboard();

                document.getElementById('successAmountDisplay').innerText = '₹' + pendingAction.amount;
                document.getElementById('successReceiverDisplay').innerText = 'Recharge for ' + pendingAction.mobile;
                document.getElementById('successBankInfoDisplay').innerText = 'Debited from ' + currentUser.bank;
                document.getElementById('successModal').classList.remove('hidden');
            } else if (pendingAction.type === 'TICKET') {
                currentUser.wallet -= pendingAction.amount;
                currentUser.tickets.push(pendingAction.matchName);
                currentUser.history.unshift({
                    type: 'TICKET',
                    name: pendingAction.matchName,
                    bank: currentUser.bank,
                    amount: pendingAction.amount,
                    date: new Date().toLocaleTimeString()
                });
                saveUserData();
                showDashboard();

                document.getElementById('successAmountDisplay').innerText = '₹' + pendingAction.amount;
                document.getElementById('successReceiverDisplay').innerText = 'Ticket: ' + pendingAction.matchName;
                document.getElementById('successBankInfoDisplay').innerText = 'Debited from ' + currentUser.bank;
                document.getElementById('successModal').classList.remove('hidden');
            }
        }

        // --- RECHARGE LOGIC ---
        function openRechargeModal() {
            if (!currentUser.bank || !currentUser.upiPin) {
                alert('Recharge karne ke liye Bank me Khata aur PIN set hona zaruri hai!');
                return;
            }
            document.getElementById('rechargeModal').classList.remove('hidden');
        }

        function proceedToRechargePin() {
            const mobile = document.getElementById('rechargeMobileInput').value.trim();
            const amount = parseFloat(document.getElementById('rechargePlanSelect').value);

            if (mobile.length !== 10) {
                alert('Sahi Mobile Number bharein!');
                return;
            }

            pendingAction = {
                type: 'RECHARGE',
                mobile: mobile,
                amount: amount
            };

            closeModal('rechargeModal');
            document.getElementById('pinModal').classList.remove('hidden');
        }

        // --- TICKET BUY LOGIC ---
        function buyMatchTicket(matchName, amount) {
            if (!currentUser.bank || !currentUser.upiPin) {
                alert('Ticket khareedne ke liye UPI PIN hona zaruri hai!');
                return;
            }

            pendingAction = {
                type: 'TICKET',
                matchName: matchName,
                amount: amount
            };

            document.getElementById('pinModal').classList.remove('hidden');
        }

        // --- HISTORY RENDER ---
        function renderHistory() {
            const list = document.getElementById('historyList');
            if (currentUser.history.length === 0) {
                list.innerHTML = '<p style="color:#888; font-size:0.9rem;">Koi transaction history nahi hai.</p>';
                return;
            }

            let html = '';
            currentUser.history.forEach(item => {
                html += `
                    <div class="history-item ${item.type === 'SENT' ? 'sent' : ''}">
                        <div style="display:flex; justify-content:space-between; font-weight:bold;">
                            <span>${item.name}</span>
                            <span style="color:${item.type === 'SENT' ? 'red' : 'green'}">${item.type === 'SENT' ? '-' : ''}₹${item.amount}</span>
                        </div>
                        <div style="font-size:0.8rem; color:#666; margin-top:4px; display:flex; justify-content:space-between;">
                            <span>Bank Account: ${item.bank}</span>
                            <span>${item.date}</span>
                        </div>
                    </div>
                `;
            });
            list.innerHTML = html;
        }

        // Navigation Tabs
        function switchTab(tabName, event) {
            document.querySelectorAll('.tab-btn').forEach(btn => btn.classList.remove('active'));
            document.querySelectorAll('.tab-content').forEach(content => content.classList.add('hidden'));

            event.target.classList.add('active');
            document.getElementById(tabName + 'TabContent').classList.remove('hidden');
        }

        function closeModal(id) {
            document.getElementById(id).classList.add('hidden');
        }
    </script>
</body>
</html>


