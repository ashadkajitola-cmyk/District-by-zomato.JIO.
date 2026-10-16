<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cricket Schedule & PhonePe Payment Platform</title>
    <style>
        :root {
            --primary: #1e3c72;
            --secondary: #2a5298;
            --phonepe: #5f259f;
            --accent: #ff9800;
            --bg: #f0f4f8;
            --white: #ffffff;
            --text: #222222;
            --danger: #e74c3c;
            --success: #2ecc71;
            --border: #dcdcdc;
        }
        * { box-sizing: border-box; margin: 0; padding: 0; font-family: 'Segoe UI', Roboto, sans-serif; }
        body { background-color: var(--bg); color: var(--text); padding-bottom: 60px; font-size: 16px; }
        
        header { background: linear-gradient(135deg, var(--primary), var(--secondary)); color: var(--white); padding: 18px 25px; display: flex; justify-content: space-between; align-items: center; box-shadow: 0 4px 20px rgba(0,0,0,0.2); }
        header h1 { font-size: 1.4rem; font-weight: 800; }
        .user-info { display: flex; gap: 12px; align-items: center; }
        .wallet-badge { background: var(--accent); color: #000; padding: 6px 14px; border-radius: 20px; font-weight: bold; font-size: 0.95rem; text-align: center; }
        
        .container { max-width: 950px; margin: 20px auto; padding: 0 15px; display: flex; flex-direction: column; gap: 20px; }
        .card { background: var(--white); border-radius: 14px; padding: 22px; box-shadow: 0 4px 15px rgba(0,0,0,0.05); }
        
        h2 { font-size: 1.4rem; margin-bottom: 12px; color: var(--primary); font-weight: 700; }
        h3 { font-size: 1.2rem; margin-bottom: 10px; color: #333; font-weight: 700; }
        
        .btn { background: var(--secondary); color: var(--white); border: none; padding: 12px 18px; border-radius: 8px; cursor: pointer; font-weight: bold; font-size: 1rem; transition: 0.2s; width: 100%; text-align: center; display: inline-block; }
        .btn:hover { opacity: 0.92; transform: translateY(-1px); }
        .btn-phonepe { background: var(--phonepe); color: #fff; }
        .btn-danger { background: var(--danger); }
        .btn-success { background: var(--success); }
        .btn-warning { background: var(--accent); color: #000; }
        
        input, select, textarea { width: 100%; padding: 12px 15px; margin: 6px 0 16px 0; border: 2px solid var(--border); border-radius: 8px; font-size: 1rem; background: #fff; }
        input:focus, select:focus { border-color: var(--phonepe); outline: none; }
        label { font-weight: 700; font-size: 0.9rem; color: #444; display: block; }
        
        .tabs { display: flex; gap: 8px; margin-bottom: 15px; background: #e2e8f0; padding: 6px; border-radius: 10px; flex-wrap: wrap; }
        .tab-btn { flex: 1; min-width: 100px; padding: 10px; background: transparent; border: none; border-radius: 8px; cursor: pointer; font-weight: bold; color: #555; transition: 0.2s; text-align: center; }
        .tab-btn.active { background: var(--white); color: var(--phonepe); box-shadow: 0 2px 6px rgba(0,0,0,0.1); }
        
        .match-card { border: 2px solid var(--border); border-radius: 12px; padding: 18px; margin-bottom: 15px; background: var(--white); }
        .series-title-bar { background: #e8f4fd; color: #1a5276; padding: 8px 12px; border-radius: 6px; font-weight: bold; margin-bottom: 12px; display: flex; justify-content: space-between; align-items: center; }
        .match-row { display: flex; justify-content: space-between; align-items: center; margin: 12px 0; }
        .team-box { font-size: 1.15rem; font-weight: 800; color: var(--primary); }

        /* Bank UI Grid Styles (From Reference Screenshots) */
        .popular-banks-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 15px; margin-top: 15px; }
        .bank-item { background: #fff; border: 1px solid #e0e0e0; border-radius: 12px; padding: 15px 10px; text-align: center; cursor: pointer; transition: 0.2s; display: flex; flex-direction: column; align-items: center; gap: 8px; }
        .bank-item:hover { border-color: var(--phonepe); box-shadow: 0 4px 10px rgba(95,37,159,0.15); }
        .bank-icon { width: 45px; height: 45px; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-weight: bold; color: white; font-size: 1.1rem; }
        .bank-name { font-size: 0.85rem; font-weight: 700; color: #333; line-height: 1.2; }

        /* Virtual Debit Card Style */
        .debit-card { background: linear-gradient(135deg, #2c3e50, #000000); color: #fff; border-radius: 14px; padding: 20px; box-shadow: 0 8px 20px rgba(0,0,0,0.3); position: relative; margin-top: 15px; }
        .debit-card .chip { width: 40px; height: 30px; background: #f1c40f; border-radius: 4px; margin-bottom: 15px; }
        .debit-card .card-num { font-size: 1.3rem; letter-spacing: 2px; font-family: monospace; font-weight: bold; margin-bottom: 15px; text-align: center; }
        .debit-card .card-expiry { display: flex; justify-content: space-between; font-size: 0.9rem; font-weight: 600; }

        /* Pay UI Box (From Screenshot 1000030254) */
        .pay-header-card { background: #fff; border-radius: 12px; padding: 15px; border: 1px solid #e2e8f0; margin-bottom: 15px; }
        .pay-user-row { display: flex; align-items: center; gap: 12px; }
        .avatar-circle { width: 48px; height: 48px; background: #8d6e63; color: white; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-size: 1.3rem; font-weight: bold; }
        .verified-badge { color: #2ecc71; font-weight: bold; display: inline-flex; align-items: center; gap: 3px; font-size: 0.9rem; }
        .amount-input-box { border: 2px solid var(--phonepe); border-radius: 8px; padding: 10px 15px; display: flex; align-items: center; margin-top: 15px; font-size: 1.8rem; font-weight: bold; color: #222; }
        .amount-input-box input { border: none; font-size: 1.8rem; font-weight: bold; margin: 0; padding: 0 0 0 10px; width: 100%; outline: none; }

        /* History List (From Screenshot 1000030253) */
        .history-item { display: flex; justify-content: space-between; align-items: center; padding: 15px; border-bottom: 1px solid #f0f0f0; background: #fff; border-radius: 8px; margin-bottom: 8px; }
        .history-icon { width: 40px; height: 40px; background: #f0f4f8; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-size: 1.2rem; }

        .hidden { display: none !important; }
        .flex-row { display: flex; gap: 10px; }
        .flex-row > * { flex: 1; }
        
        .modal { position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.7); display: flex; justify-content: center; align-items: center; z-index: 1000; padding: 20px; }
        .modal-content { background: var(--white); padding: 25px; border-radius: 16px; width: 100%; max-width: 500px; position: relative; max-height: 90vh; overflow-y: auto; }
        .close-modal { position: absolute; top: 15px; right: 20px; font-size: 1.8rem; cursor: pointer; color: #666; }
    </style>
</head>
<body>

    <header>
        <h1>🏏 Cricket & PhonePe Pro</h1>
        <div class="user-info">
            <span id="displayUser" style="font-weight: 700;">Login करें</span>
            <div class="wallet-badge">
                <span>Wallet: ₹<span id="displayWallet">0</span></span>
            </div>
            <button id="logoutBtn" class="btn btn-danger hidden" onclick="logout()" style="padding: 6px 12px; font-size: 0.85rem; width: auto;">Logout</button>
        </div>
    </header>

    <div class="container">
        <!-- Login Section -->
        <div id="loginSection" class="card">
            <h2>🔐 Login / Registration</h2>
            <p style="font-size:0.9rem; color:#666; margin-bottom:15px;">PhonePe system aur Cricket Match Schedule access karne ke liye login karein.</p>
            <label>Name (Aapka Naam):</label>
            <input type="text" id="loginNameInput" placeholder="Enter Full Name">
            <label>Mobile Number:</label>
            <input type="text" id="loginMobileInput" maxlength="10" placeholder="Enter 10-digit mobile number">
            <button class="btn btn-phonepe" onclick="handleLogin()">Proceed to Home</button>
        </div>

        <!-- Main Dashboard -->
        <div id="mainDashboard" class="hidden">
            
            <!-- User Transfer Code Box -->
            <div class="card" style="background: linear-gradient(135deg, #5f259f, #391263); color: white;">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <div>
                        <p style="font-size: 0.9rem; opacity: 0.9;">Aapka Transfer Code (Paise lene ke liye):</p>
                        <h1 id="userPayCodeDisplay" style="font-size: 2.2rem; letter-spacing: 3px; font-weight: 900; margin-top: 5px;">----</h1>
                    </div>
                    <div style="background: rgba(255,255,255,0.2); padding: 10px; border-radius: 8px; font-size: 0.8rem; text-align: right;">
                        <span>Bank Status:</span><br>
                        <strong id="bankStatusText">No Account</strong>
                    </div>
                </div>
            </div>

            <!-- Navigation Tabs -->
            <div class="tabs">
                <button class="tab-btn active" onclick="switchTab('matches', event)">🏏 Matches</button>
                <button class="tab-btn" onclick="switchTab('phonepe', event)">📱 PhonePe</button>
                <button class="tab-btn" onclick="switchTab('recharge', event)">⚡ Recharge</button>
                <button class="tab-btn" onclick="switchTab('history', event)">📜 History</button>
            </div>

            <!-- TAB 1: MATCHES -->
            <div id="matchesTabContent" class="tab-content">
                <div class="card">
                    <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 15px;">
                        <h2>Cricket Matches</h2>
                        <button class="btn btn-success" style="width: auto;" onclick="openCreateMatchModal()">+ Create Match</button>
                    </div>
                    <div id="matchesList"></div>
                </div>
            </div>

            <!-- TAB 2: PHONEPE SYSTEM -->
            <div id="phonepeTabContent" class="tab-content hidden">
                
                <!-- Section A: Bank Account Opening -->
                <div id="bankAccountSection" class="card">
                    <h3>🏦 Open Bank Account</h3>
                    <p style="font-size: 0.9rem; color: #555; margin-bottom: 15px;">Paise sent karne aur Debit Card ke liye Bank me khata khulwayein:</p>
                    <div class="popular-banks-grid">
                        <div class="bank-item" onclick="selectBankToOpen('State Bank of India', '#1a73e8')">
                            <div class="bank-icon" style="background: #1a73e8;">SBI</div>
                            <div class="bank-name">State Bank of India</div>
                        </div>
                        <div class="bank-item" onclick="selectBankToOpen('Punjab National Bank', '#f1c40f')">
                            <div class="bank-icon" style="background: #e67e22;">PNB</div>
                            <div class="bank-name">Punjab National Bank</div>
                        </div>
                        <div class="bank-item" onclick="selectBankToOpen('Bank Of Baroda', '#f39c12')">
                            <div class="bank-icon" style="background: #f39c12;">BOB</div>
                            <div class="bank-name">Bank Of Baroda</div>
                        </div>
                        <div class="bank-item" onclick="selectBankToOpen('Airtel Payments Bank', '#e74c3c')">
                            <div class="bank-icon" style="background: #e74c3c;">APB</div>
                            <div class="bank-name">Airtel Payments Bank</div>
                        </div>
                        <div class="bank-item" onclick="selectBankToOpen('India Post Payment Bank', '#8e44ad')">
                            <div class="bank-icon" style="background: #8e44ad;">IPPB</div>
                            <div class="bank-name">India Post Payment Bank</div>
                        </div>
                        <div class="bank-item" onclick="selectBankToOpen('Union Bank Of India', '#2980b9')">
                            <div class="bank-icon" style="background: #2980b9;">UBI</div>
                            <div class="bank-name">Union Bank Of India</div>
                        </div>
                        <div class="bank-item" onclick="selectBankToOpen('HDFC Bank', '#004c8f')">
                            <div class="bank-icon" style="background: #004c8f;">HDFC</div>
                            <div class="bank-name">HDFC Bank</div>
                        </div>
                        <div class="bank-item" onclick="selectBankToOpen('Canara Bank', '#16a085')">
                            <div class="bank-icon" style="background: #16a085;">CNB</div>
                            <div class="bank-name">Canara Bank</div>
                        </div>
                        <div class="bank-item" onclick="selectBankToOpen('Kotak Mahindra Bank', '#c0392b')">
                            <div class="bank-icon" style="background: #c0392b;">KOTAK</div>
                            <div class="bank-name">Kotak Mahindra</div>
                        </div>
                    </div>
                </div>

                <!-- Section B: Debit Card & PIN Setup -->
                <div id="debitCardSection" class="card hidden">
                    <h3>💳 Virtual Debit Card & UPI PIN</h3>
                    <div id="debitCardDisplayArea"></div>
                    <div style="margin-top: 15px;">
                        <button id="applyCardBtn" class="btn btn-phonepe" onclick="applyDebitCard()">Apply Debit Card</button>
                        <button id="setPinBtn" class="btn btn-warning hidden" onclick="openSetPinModal()">Set 4-Digit PIN</button>
                    </div>
                </div>

                <!-- Section C: Send Money via Code -->
                <div id="sendMoneySection" class="card" style="margin-top: 20px;">
                    <h3>💸 Send Money to Anyone</h3>
                    <p style="font-size: 0.9rem; color: #555; margin-bottom: 12px;">Receiver ka 4-Digit Code dalein:</p>
                    <label>Enter 4-Digit Recipient Code:</label>
                    <input type="text" id="targetCodeInput" maxlength="4" placeholder="Enter 4-digit code" oninput="lookupCodeName()">
                    
                    <div id="receiverPreviewCard" class="pay-header-card hidden">
                        <div class="pay-user-row">
                            <div class="avatar-circle" id="receiverAvatar">U</div>
                            <div>
                                <h4 id="receiverName" style="font-size: 1.1rem; color: #222;">User Name</h4>
                                <div class="verified-badge">Banking name verified <span style="background: #2ecc71; color: white; border-radius: 50%; padding: 0 4px; font-size: 0.7rem;">✓</span></div>
                                <div style="font-size: 0.8rem; color: #666;" id="receiverBankText">Bank: BOB</div>
                            </div>
                        </div>
                        <div class="amount-input-box">
                            ₹ <input type="number" id="sendAmountInput" placeholder="0">
                        </div>
                        <button class="btn btn-phonepe" style="margin-top: 15px; padding: 14px;" onclick="initiateMoneyTransfer()">Proceed To Pay</button>
                    </div>
                </div>

            </div>

            <!-- TAB 3: RECHARGE SYSTEM -->
            <div id="rechargeTabContent" class="tab-content hidden card">
                <h2>📱 Mobile Recharge</h2>
                <p style="font-size: 0.9rem; color: #555; margin-bottom: 15px;">Kisi ka bhi mobile recharge karein (UPI PIN zaroori hai):</p>
                <label>Mobile Number:</label>
                <input type="text" id="rechargeMobileInput" maxlength="10" placeholder="Enter 10-digit mobile number">
                <label>Select Recharge Amount:</label>
                <select id="rechargeAmountSelect">
                    <option value="239">₹239 - 1.5GB/Day (28 Days)</option>
                    <option value="299">₹299 - 2GB/Day (28 Days)</option>
                    <option value="666">₹666 - 1.5GB/Day (84 Days)</option>
                    <option value="19">₹19 - 1GB Data Pack</option>
                </select>
                <button class="btn btn-phonepe" onclick="processMobileRecharge()">Pay & Recharge</button>
            </div>

            <!-- TAB 4: HISTORY -->
            <div id="historyTabContent" class="tab-content hidden card">
                <h2>📜 Transaction History</h2>
                <p style="font-size: 0.9rem; color: #555; margin-bottom: 15px;">Aapki saari len-den aur receive kiye paise:</p>
                <div id="historyList"></div>
            </div>

        </div>
    </div>

    <!-- MODAL 1: OPEN BANK ACCOUNT -->
    <div id="openBankModal" class="modal hidden">
        <div class="modal-content">
            <span class="close-modal" onclick="closeModal('openBankModal')">&times;</span>
            <h3>🏦 Khata Kholne Ka Form</h3>
            <p id="selectedBankModalTitle" style="font-weight: bold; color: var(--phonepe); margin-bottom: 10px;"></p>
            <label>Mobile Number:</label>
            <input type="text" id="bankMobileInput" readonly>
            <label>Text / Details (Kuch bhi likhein):</label>
            <input type="text" id="bankTextDetails" placeholder="Jaise: Aadhar / Address / Name">
            <button class="btn btn-phonepe" onclick="confirmOpenAccount()">Khata Kholiye (Submit)</button>
        </div>
    </div>

    <!-- MODAL 2: SET UPI PIN -->
    <div id="setPinModal" class="modal hidden">
        <div class="modal-content">
            <span class="close-modal" onclick="closeModal('setPinModal')">&times;</span>
            <h3>🔐 Set UPI PIN</h3>
            <label>Debit Card Last 6 Digits:</label>
            <input type="text" id="pinCardDigits" maxlength="6" placeholder="Last 6 Digits">
            <div class="flex-row">
                <div><label>MM (4-digit):</label><input type="text" id="pinMM" maxlength="4" placeholder="e.g. 0528"></div>
                <div><label>YY (4-digit):</label><input type="text" id="pinYY" maxlength="4" placeholder="e.g. 2030"></div>
            </div>
            <button class="btn btn-phonepe" onclick="verifyCardForPin()">Proceed</button>
            
            <div id="pinEntryStep" class="hidden" style="margin-top: 15px; border-top: 1px solid #ddd; padding-top: 15px;">
                <label id="pinStepLabel">Enter 4-Digit New PIN:</label>
                <input type="password" id="pinInput1" maxlength="4" placeholder="****">
                <button class="btn btn-success" id="pinStepBtn" onclick="submitPinStep1()">Proceed</button>
            </div>
        </div>
    </div>

    <!-- MODAL 3: PAY PIN CONFIRMATION -->
    <div id="payPinModal" class="modal hidden">
        <div class="modal-content" style="text-align: center;">
            <span class="close-modal" onclick="closeModal('payPinModal')">&times;</span>
            <h3 style="color: var(--phonepe);">ENTER 4-DIGIT PIN</h3>
            <p id="payModalAmountText" style="font-size: 1.5rem; font-weight: bold; margin: 15px 0; color: #222;"></p>
            <input type="password" id="payPinAttempt" maxlength="4" style="font-size: 2rem; text-align: center; letter-spacing: 10px; width: 80%; margin: 0 auto 20px auto;">
            <button class="btn btn-phonepe" onclick="executePaymentWithPin()">PAY</button>
        </div>
    </div>

    <!-- MODAL 4: CREATE MATCH -->
    <div id="createMatchModal" class="modal hidden">
        <div class="modal-content">
            <span class="close-modal" onclick="closeModal('createMatchModal')">&times;</span>
            <h2>🏏 Create Cricket Match</h2>
            <label>Series Name:</label>
            <input type="text" id="matchSeries" placeholder="e.g. T20 World Series">
            <div class="flex-row">
                <div><label>Team 1:</label><input type="text" id="matchT1" placeholder="IND"></div>
                <div><label>Team 2:</label><input type="text" id="matchT2" placeholder="AUS"></div>
            </div>
            <label>Date & Time:</label>
            <input type="text" id="matchTime" placeholder="Today, 7:30 PM">
            <button class="btn btn-success" onclick="saveMatch()">Publish Match</button>
        </div>
    </div>

    <script>
        // Global App State (Stored in LocalStorage)
        let currentUser = null;
        let usersDB = JSON.parse(localStorage.getItem('cricket_phonepe_users') || '{}');
        let matchesDB = JSON.parse(localStorage.getItem('cricket_phonepe_matches') || '[]');
        let tempPendingPin = "";
        let pendingPaymentAction = null;

        // Default Match Setup
        if(matchesDB.length === 0) {
            matchesDB = [
                { id: 'm1', series: 'IND vs SA T20 Series', t1: 'India', t2: 'South Africa', time: 'Tonight, 7:00 PM' }
            ];
            localStorage.setItem('cricket_phonepe_matches', JSON.stringify(matchesDB));
        }

        function saveUsers() {
            localStorage.setItem('cricket_phonepe_users', JSON.stringify(usersDB));
        }

        // --- LOGIN SYSTEM ---
        function handleLogin() {
            const name = document.getElementById('loginNameInput').value.trim();
            const mobile = document.getElementById('loginMobileInput').value.trim();

            if(!name || mobile.length !== 10) {
                alert("Kripya apna sahi Naam aur 10 digit Mobile Number dalein!");
                return;
            }

            // ADMIN SPECIAL CASE: 7355055313
            if(mobile === "7355055313") {
                if(!usersDB[mobile]) {
                    usersDB[mobile] = {
                        name: name || "Admin",
                        mobile: mobile,
                        wallet: 50000,
                        code: "7355",
                        bankOpened: "Bank Of Baroda",
                        cardReady: true,
                        cardNum: "453289012345",
                        cardMM: "0828",
                        cardYY: "2030",
                        pin: "1234",
                        appliedTime: 0,
                        history: []
                    };
                } else {
                    usersDB[mobile].bankOpened = "Bank Of Baroda";
                    usersDB[mobile].cardReady = true;
                }
            } else if(!usersDB[mobile]) {
                // Generate unique 4-digit code
                let code = Math.floor(1000 + Math.random() * 9000).toString();
                usersDB[mobile] = {
                    name: name,
                    mobile: mobile,
                    wallet: 500,
                    code: code,
                    bankOpened: null,
                    cardReady: false,
                    cardNum: "",
                    cardMM: "",
                    cardYY: "",
                    pin: null,
                    appliedTime: null,
                    history: []
                };
            }

            currentUser = usersDB[mobile];
            saveUsers();
            
            document.getElementById('loginSection').classList.add('hidden');
            document.getElementById('mainDashboard').classList.remove('hidden');
            document.getElementById('logoutBtn').classList.remove('hidden');

            updateUI();
        }

        function logout() {
            currentUser = null;
            document.getElementById('mainDashboard').classList.add('hidden');
            document.getElementById('logoutBtn').classList.add('hidden');
            document.getElementById('loginSection').classList.remove('hidden');
        }

        // --- UI REFRESH ---
        function updateUI() {
            if(!currentUser) return;

            document.getElementById('displayUser').innerText = currentUser.name + " (" + currentUser.mobile + ")";
            document.getElementById('displayWallet').innerText = currentUser.wallet;
            document.getElementById('userPayCodeDisplay').innerText = currentUser.code;
            document.getElementById('bankStatusText').innerText = currentUser.bankOpened ? currentUser.bankOpened : "No Account";

            renderDebitCardSection();
            renderMatches();
            renderHistory();
        }

        // --- BANK ACCOUNT & DEBIT CARD LOGIC ---
        let selectedBankTemp = "";
        function selectBankToOpen(bankName) {
            selectedBankTemp = bankName;
            document.getElementById('selectedBankModalTitle').innerText = "Bank: " + bankName;
            document.getElementById('bankMobileInput').value = currentUser.mobile;
            document.getElementById('openBankModal').classList.remove('hidden');
        }

        function confirmOpenAccount() {
            currentUser.bankOpened = selectedBankTemp;
            saveUsers();
            closeModal('openBankModal');
            alert(selectedBankTemp + " me aapka khata safaltapurvak khul gaya hai!");
            updateUI();
        }

        function applyDebitCard() {
            if(!currentUser.bankOpened) {
                alert("Debit card apply karne ke liye pahle bank account kholna zaroori hai!");
                return;
            }

            if(currentUser.mobile === "7355055313") {
                currentUser.cardReady = true;
                currentUser.cardNum = "453289012345";
                currentUser.cardMM = "0828";
                currentUser.cardYY = "2030";
            } else {
                currentUser.appliedTime = Date.now();
                currentUser.cardNum = Math.floor(100000000000 + Math.random() * 900000000000).toString();
                currentUser.cardMM = "0528";
                currentUser.cardYY = "2030";
                currentUser.cardReady = false;
            }

            saveUsers();
            alert("Debit card apply ho gaya hai!");
            updateUI();
        }

        function renderDebitCardSection() {
            const cardSec = document.getElementById('debitCardSection');
            const displayArea = document.getElementById('debitCardDisplayArea');
            const applyBtn = document.getElementById('applyCardBtn');
            const setPinBtn = document.getElementById('setPinBtn');

            if(!currentUser.bankOpened) {
                cardSec.classList.add('hidden');
                return;
            }

            cardSec.classList.remove('hidden');

            if(!currentUser.cardNum) {
                displayArea.innerHTML = `<p style="color:#666;">Aapke paas koi active debit card nahi hai. Apply pe click karein.</p>`;
                applyBtn.classList.remove('hidden');
                setPinBtn.classList.add('hidden');
                return;
            }

            // Check 2 Hour Timer
            let hoursPassed = 0;
            if(currentUser.appliedTime) {
                hoursPassed = (Date.now() - currentUser.appliedTime) / (1000 * 60 * 60);
            }

            if(currentUser.cardReady || hoursPassed >= 2 || currentUser.mobile === "7355055313") {
                currentUser.cardReady = true;
                saveUsers();

                displayArea.innerHTML = `
                    <div class="debit-card">
                        <div style="font-size: 0.85rem; font-weight: bold; opacity: 0.8; text-transform: uppercase;">${currentUser.bankOpened}</div>
                        <div class="chip"></div>
                        <div class="card-num">${currentUser.cardNum.match(/.{1,4}/g).join(' ')}</div>
                        <div class="card-expiry">
                            <span>VALID THRU: ${currentUser.cardMM}/${currentUser.cardYY}</span>
                            <span>PIN: ${currentUser.pin ? '✓ SET' : 'NOT SET'}</span>
                        </div>
                    </div>
                `;
                applyBtn.classList.add('hidden');
                setPinBtn.classList.remove('hidden');
            } else {
                let timeLeftMinutes = Math.ceil((2 * 60) - ((Date.now() - currentUser.appliedTime) / (1000 * 60)));
                displayArea.innerHTML = `
                    <div style="background: #fff3cd; color: #856404; padding: 15px; border-radius: 8px; font-weight: bold;">
                        ⏳ Debit Card Process me hai. 2 Hours me ready ho jayega.<br>
                        Remaining time: Approx ${timeLeftMinutes} Minutes.
                    </div>
                `;
                applyBtn.classList.add('hidden');
                setPinBtn.classList.add('hidden');
            }
        }

        // --- SET PIN VERIFICATION ---
        function openSetPinModal() {
            document.getElementById('pinCardDigits').value = "";
            document.getElementById('pinMM').value = "";
            document.getElementById('pinYY').value = "";
            document.getElementById('pinEntryStep').classList.add('hidden');
            document.getElementById('setPinModal').classList.remove('hidden');
        }

        function verifyCardForPin() {
            const digits = document.getElementById('pinCardDigits').value.trim();
            const mm = document.getElementById('pinMM').value.trim();
            const yy = document.getElementById('pinYY').value.trim();

            const actualLast6 = currentUser.cardNum.slice(-6);

            if(digits === actualLast6 && mm === currentUser.cardMM && yy === currentUser.cardYY) {
                document.getElementById('pinEntryStep').classList.remove('hidden');
                document.getElementById('pinStepLabel').innerText = "Enter 4-Digit New PIN:";
                document.getElementById('pinInput1').value = "";
                tempPendingPin = "";
            } else {
                alert("Galat Number! Card details match nahi kar rahi hain.");
            }
        }

        function submitPinStep1() {
            const val = document.getElementById('pinInput1').value.trim();
            if(val.length !== 4) {
                alert("Kripya 4-digit PIN dalein!");
                return;
            }

            if(!tempPendingPin) {
                tempPendingPin = val;
                document.getElementById('pinInput1').value = "";
                document.getElementById('pinStepLabel').innerText = "Re-enter 4-Digit PIN (Dobara dalein):";
            } else {
                if(tempPendingPin === val) {
                    currentUser.pin = val;
                    saveUsers();
                    closeModal('setPinModal');
                    alert("PIN Safaltapurvak Set Ho Gaya Hai!");
                    updateUI();
                } else {
                    alert("PIN Match nahi hua! Dobara koshish karein.");
                    tempPendingPin = "";
                    document.getElementById('pinStepLabel').innerText = "Enter 4-Digit New PIN:";
                    document.getElementById('pinInput1').value = "";
                }
            }
        }

        // --- LOOKUP RECEIVER BY CODE ---
        let foundReceiver = null;
        function lookupCodeName() {
            const code = document.getElementById('targetCodeInput').value.trim();
            const card = document.getElementById('receiverPreviewCard');

            if(code.length === 4) {
                foundReceiver = Object.values(usersDB).find(u => u.code === code);
                if(foundReceiver) {
                    document.getElementById('receiverName').innerText = foundReceiver.name;
                    document.getElementById('receiverAvatar').innerText = foundReceiver.name.charAt(0).toUpperCase();
                    document.getElementById('receiverBankText').innerText = "Banking: " + (foundReceiver.bankOpened || "Wallet");
                    card.classList.remove('hidden');
                } else {
                    alert("Is Code ka koi user nahi mila!");
                    card.classList.add('hidden');
                }
            } else {
                card.classList.add('hidden');
            }
        }

        // --- PAY & TRANSFER LOGIC ---
        function initiateMoneyTransfer() {
            if(!currentUser.bankOpened || !currentUser.pin) {
                alert("Paise bhejne ke liye Khata khulwana aur Debit Card se PIN set hona zaroori hai!");
                return;
            }

            const amt = parseInt(document.getElementById('sendAmountInput').value);
            if(!amt || amt <= 0) {
                alert("Sahi amount dalein!");
                return;
            }

            if(currentUser.wallet < amt) {
                alert("Aapke paas paryapt balance nahi hai!");
                return;
            }

            pendingPaymentAction = {
                type: 'TRANSFER',
                amount: amt,
                receiver: foundReceiver
            };

            document.getElementById('payModalAmountText').innerText = "Pay ₹" + amt + " to " + foundReceiver.name;
            document.getElementById('payPinAttempt').value = "";
            document.getElementById('payPinModal').classList.remove('hidden');
        }

        function processMobileRecharge() {
            if(!currentUser.bankOpened || !currentUser.pin) {
                alert("Recharge karne ke liye Khata khulwana aur UPI PIN zaroori hai!");
                return;
            }

            const mob = document.getElementById('rechargeMobileInput').value.trim();
            const amt = parseInt(document.getElementById('rechargeAmountSelect').value);

            if(mob.length !== 10) {
                alert("10 digit mobile number dalein!");
                return;
            }

            if(currentUser.wallet < amt) {
                alert("Balance kam hai!");
                return;
            }

            pendingPaymentAction = {
                type: 'RECHARGE',
                amount: amt,
                mobile: mob
            };

            document.getElementById('payModalAmountText').innerText = "Recharge ₹" + amt + " for " + mob;
            document.getElementById('payPinAttempt').value = "";
            document.getElementById('payPinModal').classList.remove('hidden');
        }

        function executePaymentWithPin() {
            const enteredPin = document.getElementById('payPinAttempt').value.trim();

            if(enteredPin !== currentUser.pin) {
                alert("Galat PIN!");
                return;
            }

            closeModal('payPinModal');

            if(pendingPaymentAction.type === 'TRANSFER') {
                const amt = pendingPaymentAction.amount;
                const rec = pendingPaymentAction.receiver;

                currentUser.wallet -= amt;
                usersDB[rec.mobile].wallet += amt;

                // Add History for Sender
                currentUser.history.unshift({
                    type: 'Sent to ' + rec.name,
                    amount: '- ₹' + amt,
                    bank: rec.bankOpened || 'Wallet',
                    date: new Date().toLocaleDateString('en-GB')
                });

                // Add History for Receiver
                usersDB[rec.mobile].history.unshift({
                    type: 'Received from ' + currentUser.name,
                    amount: '+ ₹' + amt,
                    bank: currentUser.bankOpened || 'Wallet',
                    date: new Date().toLocaleDateString('en-GB')
                });

                saveUsers();
                alert("Payment Successful! ₹" + amt + " sent to " + rec.name);

            } else if(pendingPaymentAction.type === 'RECHARGE') {
                const amt = pendingPaymentAction.amount;
                currentUser.wallet -= amt;

                currentUser.history.unshift({
                    type: 'Mobile Recharge (' + pendingPaymentAction.mobile + ')',
                    amount: '- ₹' + amt,
                    bank: currentUser.bankOpened,
                    date: new Date().toLocaleDateString('en-GB')
                });

                saveUsers();
                alert("Recharge Successful for " + pendingPaymentAction.mobile + "!");
            }

            pendingPaymentAction = null;
            updateUI();
        }

        // --- RENDER HISTORY ---
        function renderHistory() {
            const container = document.getElementById('historyList');
            if(!currentUser.history || currentUser.history.length === 0) {
                container.innerHTML = `<p style="color:#777; text-align:center;">Koi transaction history nahi hai.</p>`;
                return;
            }

            container.innerHTML = currentUser.history.map(item => `
                <div class="history-item">
                    <div style="display:flex; align-items:center; gap:12px;">
                        <div class="history-icon">↙</div>
                        <div>
                            <div style="font-weight:bold; color:#222;">${item.type}</div>
                            <div style="font-size:0.8rem; color:#666;">Bank: ${item.bank} | ${item.date}</div>
                        </div>
                    </div>
                    <div style="font-weight:bold; font-size:1.1rem; color: ${item.amount.includes('+') ? '#2ecc71' : '#222'};">
                        ${item.amount}
                    </div>
                </div>
            `).join('');
        }

        // --- MATCH MANAGEMENT & ADMIN DELETE ---
        function renderMatches() {
            const container = document.getElementById('matchesList');
            container.innerHTML = matchesDB.map(m => `
                <div class="match-card">
                    <div class="series-title-bar">
                        <span>${m.series}</span>
                        ${currentUser && currentUser.mobile === "7355055313" ? `<button class="btn btn-danger" style="width:auto; padding:4px 8px; font-size:0.75rem;" onclick="deleteMatch('${m.id}')">Delete Match</button>` : ''}
                    </div>
                    <div class="match-row">
                        <div class="team-box">${m.t1}</div>
                        <div style="font-weight:bold; color:#e74c3c;">VS</div>
                        <div class="team-box">${m.t2}</div>
                    </div>
                    <div style="font-size:0.85rem; color:#555;">⏰ ${m.time}</div>
                </div>
            `).join('');
        }

        function openCreateMatchModal() {
            document.getElementById('createMatchModal').classList.remove('hidden');
        }

        function saveMatch() {
            const series = document.getElementById('matchSeries').value.trim();
            const t1 = document.getElementById('matchT1').value.trim();
            const t2 = document.getElementById('matchT2').value.trim();
            const time = document.getElementById('matchTime').value.trim();

            if(!series || !t1 || !t2) {
                alert("Sabhi details bharein!");
                return;
            }

            matchesDB.unshift({
                id: 'm_' + Date.now(),
                series: series,
                t1: t1,
                t2: t2,
                time: time || 'Upcoming'
            });

            localStorage.setItem('cricket_phonepe_matches', JSON.stringify(matchesDB));
            closeModal('createMatchModal');
            renderMatches();
        }

        function deleteMatch(id) {
            if(currentUser.mobile !== "7355055313") {
                alert("Keval Admin matches delete kar sakta hai!");
                return;
            }

            if(confirm("Kya aap is match ko delete karna chahte hain?")) {
                matchesDB = matchesDB.filter(m => m.id !== id);
                localStorage.setItem('cricket_phonepe_matches', JSON.stringify(matchesDB));
                renderMatches();
            }
        }

        // --- HELPER FUNCTIONS ---
        function switchTab(tabName, evt) {
            document.querySelectorAll('.tab-content').forEach(el => el.classList.add('hidden'));
            document.querySelectorAll('.tab-btn').forEach(el => el.classList.remove('active'));

            document.getElementById(tabName + 'TabContent').classList.remove('hidden');
            evt.target.classList.add('active');
        }

        function closeModal(modalId) {
            document.getElementById(modalId).classList.add('hidden');
        }
    </script>
</body>
</html>

