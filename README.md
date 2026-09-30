<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cricket Schedule & Betting Platform Pro Max</title>
    <style>
        :root {
            --primary: #1e3c72;
            --secondary: #2a5298;
            --accent: #ff9800;
            --bg: #f0f4f8;
            --white: #ffffff;
            --text: #222222;
            --danger: #e74c3c;
            --success: #2ecc71;
            --border: #dcdcdc;
        }
        * { box-sizing: border-box; margin: 0; padding: 0; font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; }
        body { background-color: var(--bg); color: var(--text); padding-bottom: 60px; font-size: 16px; }
        
        header { background: linear-gradient(135deg, var(--primary), var(--secondary)); color: var(--white); padding: 20px 25px; display: flex; justify-content: space-between; align-items: center; box-shadow: 0 4px 20px rgba(0,0,0,0.2); }
        header h1 { font-size: 1.5rem; font-weight: 800; letter-spacing: 0.5px; }
        .user-info { display: flex; gap: 15px; align-items: center; font-size: 1rem; }
        .wallet-badge { background: var(--accent); color: #000; padding: 8px 16px; border-radius: 30px; font-weight: bold; font-size: 1.05rem; box-shadow: 0 3px 6px rgba(0,0,0,0.15); display: flex; flex-direction: column; align-items: center; }
        
        .container { max-width: 950px; margin: 25px auto; padding: 0 15px; display: flex; flex-direction: column; gap: 20px; }
        .card { background: var(--white); border-radius: 14px; padding: 25px; box-shadow: 0 6px 18px rgba(0,0,0,0.06); }
        
        h2 { font-size: 1.5rem; margin-bottom: 12px; color: var(--primary); font-weight: 700; }
        h3 { font-size: 1.25rem; margin-bottom: 10px; color: #333; font-weight: 700; }
        
        .btn { background: var(--secondary); color: var(--white); border: none; padding: 14px 20px; border-radius: 8px; cursor: pointer; font-weight: bold; font-size: 1.05rem; transition: 0.2s; box-shadow: 0 3px 6px rgba(0,0,0,0.1); width: 100%; text-align: center; display: inline-block; }
        .btn:hover { opacity: 0.92; transform: translateY(-2px); }
        .btn-danger { background: var(--danger); }
        .btn-success { background: var(--success); }
        .btn-warning { background: var(--accent); color: #000; }
        .btn-primary { background: var(--secondary); color: var(--white); }
        
        input, select, textarea { width: 100%; padding: 14px 16px; margin: 8px 0 18px 0; border: 2px solid var(--border); border-radius: 8px; font-size: 1.05rem; background: #fff; }
        input:focus, select:focus { border-color: var(--secondary); outline: none; }
        label { font-weight: 700; font-size: 0.95rem; color: #444; display: block; margin-top: 5px; }
        
        .tabs { display: flex; gap: 8px; margin-bottom: 15px; background: #e2e8f0; padding: 6px; border-radius: 10px; flex-wrap: wrap; }
        .tab-btn { flex: 1; min-width: 120px; padding: 12px; background: transparent; border: none; border-radius: 8px; cursor: pointer; font-weight: bold; color: #555; transition: 0.2s; font-size: 0.95rem; text-align: center; }
        .tab-btn.active { background: var(--white); color: var(--primary); box-shadow: 0 3px 8px rgba(0,0,0,0.1); }
        
        .match-card { border: 2px solid var(--border); border-radius: 12px; padding: 20px; margin-bottom: 18px; background: var(--white); box-shadow: 0 3px 8px rgba(0,0,0,0.03); }
        .series-title-bar { background: #e8f4fd; color: #1a5276; padding: 10px 15px; border-radius: 8px; font-weight: bold; font-size: 1.05rem; margin-bottom: 15px; display: flex; justify-content: space-between; align-items: center; }
        .match-row { display: flex; justify-content: space-between; align-items: center; margin: 15px 0; }
        .team-box { font-size: 1.25rem; font-weight: 800; display: flex; align-items: center; gap: 10px; color: var(--primary); }
        .match-format-green { background: var(--success); color: #fff; padding: 3px 10px; border-radius: 20px; font-size: 0.8rem; font-weight: bold; letter-spacing: 0.5px; }

        .plan-card-item {
            background: #fff; border: 2px solid var(--border); border-radius: 12px;
            padding: 16px 20px; display: flex; justify-content: space-between; align-items: center;
            margin-bottom: 12px; box-shadow: 0 2px 6px rgba(0,0,0,0.03); transition: 0.2s; flex-wrap: wrap; gap: 15px;
        }
        .plan-card-item:hover { border-color: var(--secondary); }
        .plan-info-group { display: flex; gap: 25px; align-items: center; flex-wrap: wrap; }
        .plan-price-tag { font-size: 1.6rem; font-weight: 900; color: var(--primary); letter-spacing: -0.5px; }
        .plan-meta-col { display: flex; flex-direction: column; }
        .plan-meta-label { font-size: 0.75rem; color: #777; font-weight: bold; letter-spacing: 0.5px; }
        .plan-meta-val { font-size: 1.05rem; color: #333; font-weight: 700; line-height: 1.5; }

        .message-item {
            background: #fff; border: 2px solid var(--border); border-radius: 10px;
            padding: 16px; margin-bottom: 12px; cursor: pointer; transition: 0.2s; box-shadow: 0 2px 5px rgba(0,0,0,0.03);
        }
        .message-item:hover { border-color: var(--primary); background: #f8fafc; }
        .message-header-bar { display: flex; justify-content: space-between; align-items: center; font-weight: bold; color: var(--primary); font-size: 1.1rem; }

        .hidden { display: none !important; }
        .flex-row { display: flex; gap: 12px; }
        .flex-row > * { flex: 1; }
        
        .modal { position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.7); display: flex; justify-content: center; align-items: center; z-index: 1000; overflow-y: auto; padding: 20px; }
        .modal-content { background: var(--white); padding: 30px; border-radius: 16px; width: 100%; max-width: 650px; position: relative; max-height: 90vh; overflow-y: auto; box-shadow: 0 10px 30px rgba(0,0,0,0.3); }
        .close-modal { position: absolute; top: 15px; right: 20px; font-size: 1.8rem; cursor: pointer; color: #666; font-weight: bold; }
    </style>
</head>
<body>

    <header>
        <h1>🏏 Cricket Schedule & Betting Pro</h1>
        <div class="user-info">
            <span id="displayNumber" style="font-weight: 700;">Login करें</span>
            <div class="wallet-badge">
                <span>Wallet: ₹<span id="displayWallet">0</span></span>
                <span id="displayUpiPin" style="font-size:0.8rem; color:#000; font-weight:600; margin-top:2px;">PIN: ------</span>
            </div>
            <button class="btn btn-danger" onclick="logout()" style="padding: 8px 16px; font-size: 0.9rem; width: auto;">Logout</button>
        </div>
    </header>

    <div class="container">
        <!-- Login Section -->
        <div id="loginSection" class="card">
            <h2>🔐 Login / Register</h2>
            <p id="deviceLimitInfo" style="font-size:0.95rem; color:#555; margin-bottom:15px;"></p>
            <label>Mobile Number:</label>
            <input type="text" id="loginMobileInput" placeholder="Enter 10-digit mobile number" oninput="checkExistingPinForLogin()">
            <label id="upiPinLabel">6-Digit UPI PIN:</label>
            <input type="password" id="loginUpiPinInput" maxlength="6" placeholder="Enter 6-digit UPI PIN">
            <button class="btn" onclick="handleLogin()">Login to Dashboard</button>
        </div>

        <!-- Main Dashboard -->
        <div id="mainDashboard" class="hidden">
            
            <div id="activeSubStatusBox" class="card" style="border-left: 6px solid var(--primary); background: #f8fafc;">
                <h3>✨ Active Subscription & Data Status</h3>
                <div id="subStatusContent" style="margin-top: 10px; font-size: 1.05rem; font-weight: 600; color: #1e3c72;">No Plan</div>
            </div>

            <!-- Subscription Plans Hub -->
            <div class="card" style="border-left: 6px solid var(--accent); background: #fffbeb;">
                <h3>📦 Subscription Plans & Data Hub</h3>
                <p style="font-size: 0.95rem; color: #555; margin-bottom: 15px;">Ticket buy karne ke liye active Data/MB subscription ya Data pack hona zaroori hai. Niche diye gaye plans mein se select karein:</p>
                <div id="subPlansList" style="margin-bottom: 5px;"></div>
            </div>

            <div class="card" style="border-left: 6px solid var(--success);">
                <h3>💳 Instant Wallet Recharge (Transaction ID / UTR)</h3>
                <p style="font-size: 0.95rem; color: #555; margin-bottom: 12px;">Payment ki Transaction ID / UTR number yahan dalein. <b>(Note: Sim card par active mobile recharge hona zaroori hai, Wi-Fi users allow nahi hain).</b></p>
                <label>Full Transaction ID / UTR:</label>
                <input type="text" id="txFullInput" placeholder="Enter transaction reference ID">
                <button class="btn btn-success" onclick="submitInstantRecharge()">Confirm & Get ₹210 Instantly</button>
            </div>

            <div class="card" style="border-left: 6px solid var(--secondary);">
                <h3>📂 Creator & Schedule Panel</h3>
                <p style="font-size: 0.95rem; color: #555; margin-bottom: 12px;">Apna match schedule create karne ke liye panel open karein (Active subscription zaroori hai).</p>
                <button class="btn" onclick="openCreatorDashboard()">Open Creator Panel</button>
            </div>

            <div id="adminMainControlCard" class="card hidden" style="border-left: 6px solid var(--danger); background: #fdfefe;">
                <h3 style="color: var(--danger);">👑 Master Website Admin Control Center</h3>
                <p style="font-size: 0.95rem; color: #555; margin-bottom: 15px;">Yahan se aap saare matches, tickets, subscription plans aur Data/MB settings manage kar sakte hain.</p>
                <div>
                    <button class="btn btn-danger" style="width: 100%;" onclick="openMasterAdminPanel()">⚙️ Manage Matches, Data & Plans</button>
                </div>
            </div>

            <div class="card">
                <h3>🔍 6-Digit Code Verification</h3>
                <div class="flex-row">
                    <input type="text" id="verifyCodeInput" maxlength="6" placeholder="Enter 6-digit match code">
                    <button class="btn" onclick="verifyMatchCode()" style="height: 52px; margin-top: 8px;">Check Code</button>
                </div>
                <div id="verifyResult" style="margin-top: 12px;"></div>
            </div>

            <!-- Top Navigation Tabs -->
            <div class="tabs">
                <button class="tab-btn active" onclick="switchTab('international', event)">🌍 Matches</button>
                <button class="tab-btn" onclick="switchTab('apna', event)">👤 Apna</button>
                <button class="tab-btn" onclick="switchTab('activeTickets', event)">🎟️ Tickets & Betting</button>
                <button class="tab-btn" onclick="switchTab('myPurchased', event)">📦 History</button>
                <button class="tab-btn" onclick="switchTab('messages', event)">📥 Messages</button>
            </div>

            <!-- Tab Content Sections -->
            <div id="internationalTabContent" class="tab-content card">
                <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 15px; flex-wrap: wrap; gap: 10px;">
                    <h2>International Matches</h2>
                    <button id="adminCreateMatchBtn" class="btn btn-success hidden" style="width: auto;" onclick="openInternationalMatchModal()">+ Create Match</button>
                </div>
                <div id="internationalMatchesList" style="margin-top: 15px;"></div>
            </div>

            <div id="apnaTabContent" class="tab-content card hidden">
                <h2>Apna Schedule (User Created)</h2>
                <div id="apnaMatchesList" style="margin-top: 15px;"></div>
            </div>

            <div id="activeTicketsTabContent" class="tab-content card hidden">
                <h2>Active Ticket District & Store</h2>
                <div id="activeTicketsList" style="margin-top: 15px;"></div>
            </div>

            <div id="myPurchasedTabContent" class="tab-content card hidden">
                <h2>All Purchased Tickets & Betting Store</h2>
                <div id="myPurchasedList" style="margin-top: 15px;"></div>
            </div>

            <div id="messagesTabContent" class="tab-content card hidden">
                <h2>📥 Messages Inbox</h2>
                <p style="font-size:0.95rem; color:#555; margin-bottom:15px;">Yahan aapke subscription recharges aur Data/MB packs ke messages dikhenge.</p>
                <div id="messagesInboxList"></div>
            </div>

        </div>
    </div>

    <!-- Checkout Modal -->
    <div id="jioCheckoutModal" class="modal hidden">
        <div class="modal-content" style="max-width: 480px; padding: 25px;">
            <span class="close-modal" onclick="closeJioModal()">&times;</span>
            <div style="display:flex; justify-content:space-between; align-items:center; border-bottom:1px solid #eee; padding-bottom:12px; margin-bottom:15px;">
                <h3 style="color:#111; font-size:1.3rem;">Recharge & Data Pack</h3>
                <span id="jioModalMobile" style="color:#666; font-weight:bold;"></span>
            </div>
            <div style="font-size: 2.2rem; font-weight: 900; color: #111; margin-bottom: 4px;" id="jioModalPrice">₹0</div>
            <div style="background: var(--accent); color: #fff; padding: 4px 10px; border-radius: 6px; font-weight: bold; font-size: 0.85rem; display: inline-block; margin-bottom: 20px;" id="jioModalTag">DATA PACK</div>

            <div style="background:#f8fafc; border:1px solid var(--border); border-radius:12px; padding:15px; margin-bottom:20px;">
                <h4 style="font-size: 1.05rem; color: #333; margin-bottom: 12px; border-bottom:1px solid #ddd; padding-bottom:6px;">Plan details</h4>
                <div style="display:flex; justify-content:space-between; margin-bottom:10px; font-size:0.95rem;">
                    <span style="color:#666;">Pack validity</span>
                    <strong id="jioModalValidity" style="color:#222;">30 Days</strong>
                </div>
                <div style="display:flex; justify-content:space-between; margin-bottom:10px; font-size:0.95rem;">
                    <span style="color:#666;">Total Data / MB</span>
                    <strong id="jioModalTotalData" style="color:#222;">0 GB</strong>
                </div>
                <div style="display:flex; justify-content:space-between; margin-bottom:10px; font-size:0.95rem;">
                    <span style="color:#666;">Daily Data / MB</span>
                    <strong id="jioModalDailyData" style="color:#222;">0 GB / Day</strong>
                </div>
            </div>

            <div id="jioPinContainer" class="hidden">
                <label>Enter 6-Digit UPI PIN:</label>
                <input type="password" id="jioUpiPinInput" maxlength="6" placeholder="Enter 6-digit UPI PIN">
            </div>

            <button class="btn btn-primary" style="background:#1932ff; border-radius:30px; font-size:1.1rem; padding:16px; margin-top:10px;" id="jioPayBtn" onclick="handleJioPayClick()">Pay ₹0</button>
        </div>
    </div>

    <!-- Modals -->
    <div id="creatorModal" class="modal hidden">
        <div class="modal-content">
            <span class="close-modal" onclick="closeCreatorModal()">&times;</span>
            <div id="subscriptionRequiredView">
                <h3 style="color: var(--danger);">📢 Subscription & Data Required</h3>
                <p style="font-size:0.95rem; color:#555; margin-bottom:15px;">Apna match schedule create karne ke liye active subscription ya Data pack hona zaroori hai.</p>
            </div>
            <div id="creatorActionView" class="hidden">
                <h3 style="color: var(--success);">👤 Creator Panel (Schedule Only)</h3>
                <p style="font-size: 1rem; color: #333; margin-bottom: 15px; font-weight: bold;">✔ Aapke paas active subscription/data hai. Aap match schedule create kar sakte hain:</p>
                <button class="btn" onclick="openMatchModal()">🏏 Create Match Schedule Only</button>
            </div>
        </div>
    </div>

    <div id="matchModal" class="modal hidden">
        <div class="modal-content">
            <span class="close-modal" onclick="closeMatchModal()">&times;</span>
            <h2 id="matchModalTitle">🏏 Create Match Schedule</h2>
            <input type="hidden" id="editingMatchId" value="">
            
            <label>Series Type:</label>
            <select id="matchSeriesType" onchange="toggleSeriesInput('match')">
                <option value="existing">Existing Series (Auto-select)</option>
                <option value="new">New Series (Enter Name)</option>
            </select>

            <div id="matchExistingSeriesContainer">
                <label>Select Existing Series:</label>
                <select id="matchExistingSeriesSelect"></select>
            </div>

            <div id="matchNewSeriesContainer" class="hidden">
                <label>New Series Name:</label>
                <input type="text" id="matchSeriesName" placeholder="e.g., Local League 2026">
            </div>

            <div class="flex-row">
                <div><label>Team 1 Name:</label><input type="text" id="matchTeam1" placeholder="Team A" oninput="updateTossTeamDropdowns('match')"></div>
                <div><label>Team 2 Name:</label><input type="text" id="matchTeam2" placeholder="Team B" oninput="updateTossTeamDropdowns('match')"></div>
            </div>

            <div class="flex-row">
                <div><label>Match Format:</label><input type="text" id="matchFormat" placeholder="4TH T20I"></div>
                <div><label>Date & Time:</label><input type="text" id="matchDateTime" placeholder="WED, 17 DEC, 2026 | 7 PM"></div>
            </div>

            <label>Venue (Stadium Name):</label>
            <input type="text" id="matchVenue" placeholder="EKANA STADIUM, LUCKNOW">

            <label>Gate Open Time:</label>
            <input type="text" id="matchGateTime" placeholder="Gate Opens: 2 Hours Before">

            <label>6-Digit Security Code:</label>
            <input type="text" id="matchCode6" maxlength="6" placeholder="6 digit code">

            <button class="btn btn-success" style="margin-top:10px;" onclick="saveMatchSchedule(false)">Save & Publish Match</button>
        </div>
    </div>

    <div id="internationalMatchModal" class="modal hidden">
        <div class="modal-content">
            <span class="close-modal" onclick="closeInternationalMatchModal()">&times;</span>
            <h2 id="intModalTitle">🌍 Create International Match (Admin Only)</h2>
            <input type="hidden" id="editingIntMatchId" value="">
            
            <label>Series Type:</label>
            <select id="intSeriesType" onchange="toggleSeriesInput('int')">
                <option value="existing">Existing Series (Auto-select)</option>
                <option value="new">New Series (Enter Name)</option>
            </select>

            <div id="intExistingSeriesContainer">
                <label>Select Existing Series:</label>
                <select id="intExistingSeriesSelect"></select>
            </div>

            <div id="intNewSeriesContainer" class="hidden">
                <label>New Series Name:</label>
                <input type="text" id="intSeriesName" placeholder="IND vs SA Series">
            </div>

            <div class="flex-row">
                <div><label>Team 1:</label><input type="text" id="intTeam1" placeholder="IND" oninput="updateTossTeamDropdowns('int')"></div>
                <div><label>Team 2:</label><input type="text" id="intTeam2" placeholder="SA" oninput="updateTossTeamDropdowns('int')"></div>
            </div>

            <div class="flex-row">
                <div><label>Match Format:</label><input type="text" id="intFormat" placeholder="4TH T20I"></div>
                <div><label>Date & Time:</label><input type="text" id="intDateTime" placeholder="WED, 17 DEC, 2026 | 7 PM"></div>
            </div>

            <label>Venue:</label>
            <input type="text" id="intVenue" placeholder="Stadium Name">

            <label>Gate Open Time:</label>
            <input type="text" id="intGateTime" placeholder="Gate Opens info">

            <div class="flex-row">
                <div><label>Ticket Price (₹):</label><input type="number" id="intPrice" placeholder="200"></div>
                <div><label>Ticket Limit:</label><input type="number" id="intLimit" placeholder="100"></div>
            </div>

            <label>6-Digit Security Code:</label>
            <input type="text" id="intCode6" maxlength="6" placeholder="6 digit code">

            <button class="btn btn-success" style="margin-top:10px;" onclick="saveMatchSchedule(true)">Publish International Match</button>
        </div>
    </div>

    <!-- Message Detail Modal -->
    <div id="messageDetailModal" class="modal hidden">
        <div class="modal-content">
            <span class="close-modal" onclick="closeMessageDetailModal()">&times;</span>
            <h3 style="color: var(--success); margin-bottom: 15px;">✅ Recharge & Data Pack Safal Raha</h3>
            <div id="messageDetailContent" style="font-size: 1.05rem; line-height: 1.6; color: #333;"></div>
            <button class="btn btn-danger" style="margin-top: 20px;" id="deleteMsgModalBtn">Delete Message</button>
        </div>
    </div>

    <!-- Master Admin Panel -->
    <div id="masterAdminModal" class="modal hidden">
        <div class="modal-content" style="max-width: 750px;">
            <span class="close-modal" onclick="closeMasterAdminPanel()">&times;</span>
            <h2>⚙️ Master Admin Panel</h2>
            
            <div class="tabs" style="margin-bottom:15px;">
                <button class="tab-btn active" onclick="switchAdminSubTab('matches', event)">Matches</button>
                <button class="tab-btn" onclick="switchAdminSubTab('tickets', event)">All Tickets & Bets</button>
                <button class="tab-btn" onclick="switchAdminSubTab('plans', event)">Subscriptions & Data</button>
            </div>

            <div id="adminTabMatches" class="admin-sub-tab"><div id="adminAllMatchesList"></div></div>
            <div id="adminTabTickets" class="admin-sub-tab hidden"><div id="adminAllTicketsList"></div></div>
            <div id="adminTabPlans" class="admin-sub-tab hidden">
                <div id="adminPlansList" style="margin-bottom: 15px;"></div>
                <hr style="margin: 15px 0;">
                <h3>Add New Subscription / Data Plan</h3>
                <label>Plan ID:</label><input type="text" id="newPlanId" placeholder="e.g., data_pro_28gb">
                <label>Plan Name:</label><input type="text" id="newPlanName" placeholder="e.g., 28 GB Data Pack">
                <div class="flex-row">
                    <div><label>Price (₹):</label><input type="number" id="newPlanPrice" placeholder="299"></div>
                    <div><label>Duration Days:</label><input type="number" id="newPlanDays" placeholder="28"></div>
                </div>
                <div class="flex-row">
                    <div><label>Total Data (GB/MB):</label><input type="text" id="newPlanTotalData" placeholder="e.g., 28 GB"></div>
                    <div><label>Daily Data (GB/MB):</label><input type="text" id="newPlanDailyData" placeholder="e.g., 2 GB / Day"></div>
                </div>
                <button class="btn btn-success" onclick="addNewSubscriptionPlan()">Add New Plan</button>
            </div>
        </div>
    </div>

    <script>
        const DEFAULT_ADMIN = "7355055313";
        
        let db = JSON.parse(localStorage.getItem('cricket_pro_db')) || {
            users: {},
            matches: [],
            tickets: [],
            bets: [],
            messages: [],
            usedTransactions: [],
            userRechargeTimestamps: {}, 
            settings: {
                adminNumber: DEFAULT_ADMIN,
                maxDevices: 15,
                plans: [
                    { id: 'data_28gb_plan', name: '28 GB Monthly Data Pack', price: 299, durationDays: 28, totalData: '28 GB', dailyData: '2 GB / Day' }
                ]
            },
            deviceSessions: {}
        };

        db.settings.adminNumber = DEFAULT_ADMIN;
        db.settings.maxDevices = 15;
        if (!db.userRechargeTimestamps) db.userRechargeTimestamps = {};
        if (!db.messages) db.messages = [];
        if (!db.bets) db.bets = [];

        let currentMobile = localStorage.getItem('cricket_pro_current_mobile') || null;
        let deviceId = localStorage.getItem('cricket_pro_device_id') || 'dev_' + Math.random().toString(36).substring(2,9);
        localStorage.setItem('cricket_pro_device_id', deviceId);

        let pendingCheckoutPlanId = null;

        function saveDB() {
            localStorage.setItem('cricket_pro_db', JSON.stringify(db));
        }

        window.onload = function() {
            if (!db.users[db.settings.adminNumber]) {
                db.users[db.settings.adminNumber] = { wallet: 0, subscription: null, upiPin: "123456" };
            }
            checkAndConsumeDailyData();
            if (currentMobile && db.users[currentMobile]) {
                showDashboard();
            } else {
                currentMobile = null;
                showLogin();
            }
        };

        function checkAndConsumeDailyData() {
            let todayStr = new Date().toDateString();
            for (let mob in db.users) {
                let user = db.users[mob];
                if (user && user.subscription) {
                    if (user.subscription.lastConsumedDate !== todayStr) {
                        user.subscription.lastConsumedDate = todayStr;
                        // Simulating daily data deduction or tracking reset
                    }
                }
            }
            saveDB();
        }

        function showLogin() {
            document.getElementById('loginSection').classList.remove('hidden');
            document.getElementById('mainDashboard').classList.add('hidden');
            let infoEl = document.getElementById('deviceLimitInfo');
            if(infoEl) infoEl.innerText = `(Max ${db.settings.maxDevices} numbers allowed per device)`;
            checkExistingPinForLogin();
        }

        function checkExistingPinForLogin() {
            let mobile = document.getElementById('loginMobileInput').value.trim();
            let pinInput = document.getElementById('loginUpiPinInput');
            let pinLabel = document.getElementById('upiPinLabel');
            
            if (mobile && db.users[mobile] && db.users[mobile].upiPin) {
                pinInput.value = db.users[mobile].upiPin;
                pinInput.disabled = true;
                pinLabel.innerText = "6-Digit UPI PIN (Already Set for this number):";
            } else {
                pinInput.disabled = false;
                if(db.users[mobile] && !db.users[mobile].upiPin) {
                    pinInput.value = '';
                }
                pinLabel.innerText = "6-Digit UPI PIN:";
            }
        }

        function showDashboard() {
            document.getElementById('loginSection').classList.add('hidden');
            document.getElementById('mainDashboard').classList.remove('hidden');
            
            let isAdmin = (currentMobile === db.settings.adminNumber);
            if (isAdmin) {
                document.getElementById('adminCreateMatchBtn').classList.remove('hidden');
                document.getElementById('adminMainControlCard').classList.remove('hidden');
            } else {
                document.getElementById('adminCreateMatchBtn').classList.add('hidden');
                document.getElementById('adminMainControlCard').classList.add('hidden');
            }

            updateHeader();
            renderSubscriptionStatusBox();
            renderSubscriptionPlansHub();
            renderMatches();
            renderActiveTickets();
            renderMyPurchasedTickets();
            renderMessagesInbox();
        }

        function handleLogin() {
            let mobile = document.getElementById('loginMobileInput').value.trim();
            let upiPin = document.getElementById('loginUpiPinInput').value.trim();

            if (!mobile || mobile.length < 10) { alert("Kripya sahi 10-digit mobile number enter karein!"); return; }
            if (!upiPin || upiPin.length !== 6) { alert("Kripya 6-digit ka valid UPI PIN enter karein!"); return; }

            if (!db.deviceSessions[deviceId]) db.deviceSessions[deviceId] = [];
            let activeNumbers = db.deviceSessions[deviceId];
            
            if (!activeNumbers.includes(mobile)) {
                if (activeNumbers.length >= db.settings.maxDevices) {
                    alert(`Is device par maximum ${db.settings.maxDevices} numbers hi allow hain!`);
                    return;
                }
                activeNumbers.push(mobile);
            }

            if (!db.users[mobile]) {
                let initialWallet = (mobile === db.settings.adminNumber) ? 0 : 200;
                db.users[mobile] = { wallet: initialWallet, subscription: null, upiPin: upiPin };
            } else {
                if (!db.users[mobile].upiPin) {
                    db.users[mobile].upiPin = upiPin;
                } else if (db.users[mobile].upiPin !== upiPin) {
                    alert("Galat UPI PIN! Kripya sahi UPI PIN enter karein.");
                    return;
                }
            }

            currentMobile = mobile;
            localStorage.setItem('cricket_pro_current_mobile', currentMobile);
            saveDB();
            showDashboard();
        }

        function logout() {
            currentMobile = null;
            localStorage.removeItem('cricket_pro_current_mobile');
            showLogin();
        }

        function updateHeader() {
            document.getElementById('displayNumber').innerText = currentMobile;
            let user = db.users[currentMobile];
            document.getElementById('displayWallet').innerText = user ? user.wallet : 0;
            document.getElementById('displayUpiPin').innerText = `PIN: ${user && user.upiPin ? user.upiPin : '------'}`;
        }

        function submitInstantRecharge() {
            let txInput = document.getElementById('txFullInput').value.trim();
            if (!txInput || txInput.length < 6) { alert("Kripya valid Transaction ID / UTR enter karein!"); return; }

            let hasCarrierRecharge = confirm("System verification check: Kya aapke is mobile number (" + currentMobile + ") par sim card mein active mobile recharge maujood hai? (OK = Haan, Cancel = Nahi / Wi-Fi user)");
            if (!hasCarrierRecharge) {
                alert("Recharge failed! Aapka mobile number active carrier recharge ke bina verified nahi ho saka.");
                return;
            }

            if (!db.usedTransactions) db.usedTransactions = [];
            if (db.usedTransactions.includes(txInput)) { alert("Yeh Transaction ID pehle hi use ki ja chuki hai!"); return; }

            let now = new Date().getTime();
            let lastRechargeTime = db.userRechargeTimestamps[currentMobile] || 0;
            let twentyNineDaysInMs = 29 * 24 * 60 * 60 * 1000;

            if (now - lastRechargeTime < twentyNineDaysInMs) {
                let remainingDays = Math.ceil((twentyNineDaysInMs - (now - lastRechargeTime)) / (1000 * 60 * 60 * 24));
                alert(`Aap pichle 29 dino me recharge kar chuke hain. Aap agla recharge ${remainingDays} dino ke baad kar sakte hain.`);
                return;
            }

            db.usedTransactions.push(txInput);
            db.userRechargeTimestamps[currentMobile] = now;

            if (!db.users[currentMobile]) db.users[currentMobile] = { wallet: 0, subscription: null };
            db.users[currentMobile].wallet += 210;

            saveDB();
            updateHeader();
            document.getElementById('txFullInput').value = '';
            alert("Transaction successfully confirm ho gayi! Aapke wallet mein ₹210 turant add kar diye gaye hain.");
        }

        function checkUserHasActiveSubOrData() {
            let isAdmin = (currentMobile === db.settings.adminNumber);
            if (isAdmin) return true;
            let user = db.users[currentMobile];
            if (user && user.subscription) {
                return new Date().getTime() < user.subscription.expiresAt;
            }
            return false;
        }

        function renderSubscriptionStatusBox() {
            let content = document.getElementById('subStatusContent');
            let user = db.users[currentMobile];
            let isAdmin = (currentMobile === db.settings.adminNumber);

            if (isAdmin) {
                content.innerHTML = `Role: Master Website Admin (Full Unlimited Access with Data)`;
                return;
            }

            if (user && user.subscription && checkUserHasActiveSubOrData()) {
                let sub = user.subscription;
                let now = new Date().getTime();
                let diffMs = sub.expiresAt - now;
                let diffHrs = Math.floor(diffMs / (1000 * 60 * 60));
                let diffDays = Math.floor(diffHrs / 24);
                
                let timeLeftText = diffDays > 0 ? `${diffDays} Days` : `${diffHrs} Hours`;
                content.innerHTML = `Plan: <b>${sub.planName}</b> (₹${sub.planPrice}) &nbsp;|&nbsp; Validity: <b>${timeLeftText}</b><br>Data: Total <b>${sub.totalData || '0 GB'}</b> | Daily: <b>${sub.dailyData || '0 GB / Day'}</b>`;
            } else {
                content.innerHTML = `<span style="color:var(--danger);">No Active Subscription or Data Pack! (Ticket buying ke liye Data pack zaroori hai)</span>`;
            }
        }

        function renderSubscriptionPlansHub() {
            let listHTML = '';
            db.settings.plans.forEach((plan) => {
                let validityText = plan.durationDays ? `${plan.durationDays} Days` : 'Active';
                listHTML += `
                    <div class="plan-card-item">
                        <div class="plan-info-group">
                            <div class="plan-price-tag">₹${plan.price}</div>
                            <div class="plan-meta-col">
                                <span class="plan-meta-label">Plan Name & Data</span>
                                <span class="plan-meta-val">${plan.name}<br><span style="color:var(--primary); font-size:0.95rem;">Total Data: <b>${plan.totalData || '0 GB'}</b> | Daily: <b>${plan.dailyData || '0 GB / Day'}</b></span></span>
                            </div>
                            <div class="plan-meta-col">
                                <span class="plan-meta-label">Validity</span>
                                <span class="plan-meta-val">${validityText}</span>
                            </div>
                        </div>
                        <button class="btn btn-primary" style="width: auto; padding: 10px 24px; font-size: 1rem;" onclick="openJioCheckoutModal('${plan.id}')">Buy</button>
                    </div>
                `;
            });
            document.getElementById('subPlansList').innerHTML = listHTML;
        }

        function openJioCheckoutModal(planId) {
            let planObj = db.settings.plans.find(p => p.id === planId);
            if (!planObj) return;
            pendingCheckoutPlanId = planId;

            document.getElementById('jioModalMobile').innerText = currentMobile;
            document.getElementById('jioModalPrice').innerText = `₹${planObj.price}`;
            document.getElementById('jioModalValidity').innerText = `${planObj.durationDays || 30} Days`;
            document.getElementById('jioModalTotalData').innerText = planObj.totalData || '0 GB';
            document.getElementById('jioModalDailyData').innerText = planObj.dailyData || '0 GB / Day';
            document.getElementById('jioModalTag').innerText = planObj.name.toUpperCase();

            document.getElementById('jioPinContainer').classList.add('hidden');
            document.getElementById('jioUpiPinInput').value = '';
            document.getElementById('jioPayBtn').innerText = `Pay ₹${planObj.price}`;
            document.getElementById('jioCheckoutModal').classList.remove('hidden');
        }

        function closeJioModal() {
            document.getElementById('jioCheckoutModal').classList.add('hidden');
            pendingCheckoutPlanId = null;
        }

        function handleJioPayClick() {
            let pinContainer = document.getElementById('jioPinContainer');
            if (pinContainer.classList.contains('hidden')) {
                pinContainer.classList.remove('hidden');
                document.getElementById('jioPayBtn').innerText = `Confirm & Pay`;
                return;
            }

            let pinInput = document.getElementById('jioUpiPinInput').value.trim();
            if (!pinInput || pinInput.length !== 6) { alert("Kripya 6-digit UPI PIN enter karein!"); return; }

            let user = db.users[currentMobile];
            if (user.upiPin && user.upiPin !== pinInput) { alert("Galat UPI PIN enter kiya gaya hai!"); return; }

            let planObj = db.settings.plans.find(p => p.id === pendingCheckoutPlanId);
            if (!planObj) { closeJioModal(); return; }

            if (user.wallet < planObj.price) { alert("Wallet me balance kam hai! Pehle Transaction ID daal kar ₹210 add karein."); return; }

            user.wallet -= planObj.price;
            let adminMob = db.settings.adminNumber;
            if (!db.users[adminMob]) db.users[adminMob] = { wallet: 0, subscription: null };
            db.users[adminMob].wallet += planObj.price;

            let now = new Date().getTime();
            let durationDays = planObj.durationDays || 30;
            let expiresAt = now + (durationDays * 24 * 3600 * 1000);

            user.subscription = {
                planId: planObj.id,
                planName: planObj.name,
                planPrice: planObj.price,
                expiresAt: expiresAt,
                totalData: planObj.totalData || '0 GB',
                dailyData: planObj.dailyData || '0 GB / Day',
                lastConsumedDate: new Date().toDateString()
            };

            let passId = generate12DigitPassId();
            let purchaseDateStr = new Date(now).toLocaleString();
            let expiryDateStr = new Date(expiresAt).toLocaleString();

            let msgObj = {
                id: 'msg_' + Date.now(),
                mobile: currentMobile,
                price: planObj.price,
                planName: planObj.name,
                validityDays: durationDays,
                totalData: planObj.totalData || '0 GB',
                dailyData: planObj.dailyData || '0 GB / Day',
                passId: passId,
                purchaseDate: purchaseDateStr,
                expiryDate: expiryDateStr
            };

            if (!db.messages) db.messages = [];
            db.messages.unshift(msgObj);

            saveDB();
            updateHeader();
            renderSubscriptionStatusBox();
            renderMessagesInbox();
            closeJioModal();
            alert("UPI PIN Verified! Subscription & Data Pack successfully activate ho gaya aur message inbox mein bhej diya gaya hai.");
        }

        function generate12DigitPassId() {
            let chars = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789';
            let res = '';
            for (let i = 0; i < 12; i++) {
                res += chars.charAt(Math.floor(Math.random() * chars.length));
            }
            return res;
        }

        function renderMessagesInbox() {
            let inboxListEl = document.getElementById('messagesInboxList');
            if (!db.messages) db.messages = [];
            let userMsgs = db.messages.filter(m => m.mobile === currentMobile);

            if (userMsgs.length === 0) {
                inboxListEl.innerHTML = '<p style="color:#666;">Aapke paas koi message nahi hai.</p>';
                return;
            }

            let html = '';
            userMsgs.forEach(msg => {
                html += `
                    <div class="message-item" onclick="openMessageDetail('${msg.id}')">
                        <div class="message-header-bar">
                            <span>Data Pack Safal Raha (${msg.planName})</span>
                            <span style="font-size: 0.85rem; color: #666; font-weight: normal;">${msg.purchaseDate}</span>
                        </div>
                        <div style="font-size: 0.95rem; color: #555; margin-top: 5px;">Total Data: ${msg.totalData} | Daily: ${msg.dailyData} - Click to view...</div>
                    </div>
                `;
            });
            inboxListEl.innerHTML = html;
        }

        function openMessageDetail(msgId) {
            let msg = db.messages.find(m => m.id === msgId);
            if (!msg) return;

            let contentHTML = `
                <p><strong>Plan Name:</strong> ${msg.planName}</p>
                <p><strong>Plan Price:</strong> ₹${msg.price}</p>
                <p><strong>Mobile Number:</strong> ${msg.mobile}</p>
                <p><strong>Total Data / MB:</strong> <span style="color:var(--primary); font-weight:bold;">${msg.totalData}</span></p>
                <p><strong>Daily Data / MB:</strong> <span style="color:var(--success); font-weight:bold;">${msg.dailyData}</span></p>
                <p><strong>Pass ID (12-Digit):</strong> <span style="font-family: monospace; background:#e2e8f0; padding:2px 6px; border-radius:4px;">${msg.passId}</span></p>
                <p><strong>Validity:</strong> ${msg.validityDays} Days</p>
                <p><strong>Purchase Date:</strong> ${msg.purchaseDate}</p>
                <p><strong>Expiry Date:</strong> ${msg.expiryDate}</p>
            `;

            document.getElementById('messageDetailContent').innerHTML = contentHTML;
            document.getElementById('deleteMsgModalBtn').setAttribute('onclick', `deleteMessage('${msg.id}')`);
            document.getElementById('messageDetailModal').classList.remove('hidden');
        }

        function closeMessageDetailModal() {
            document.getElementById('messageDetailModal').classList.add('hidden');
        }

        function deleteMessage(msgId) {
            if (confirm("Kya aap is message ko delete karna chahte hain?")) {
                db.messages = db.messages.filter(m => m.id !== msgId);
                saveDB();
                closeMessageDetailModal();
                renderMessagesInbox();
                alert("Message successfully delete kar diya gaya hai!");
            }
        }

        function openCreatorDashboard() {
            let modal = document.getElementById('creatorModal');
            let reqView = document.getElementById('subscriptionRequiredView');
            let actView = document.getElementById('creatorActionView');

            if (checkUserHasActiveSubOrData()) {
                reqView.classList.add('hidden');
                actView.classList.remove('hidden');
            } else {
                reqView.classList.remove('hidden');
                actView.classList.add('hidden');
            }
            modal.classList.remove('hidden');
        }

        function closeCreatorModal() { document.getElementById('creatorModal').classList.add('hidden'); }
        
        function openMatchModal() { 
            if (!checkUserHasActiveSubOrData()) {
                alert("Bina active subscription ya Data pack ke aap match schedule create nahi kar sakte!");
                return;
            }
            closeCreatorModal(); 
            document.getElementById('matchModalTitle').innerText = "🏏 Create Match Schedule";
            document.getElementById('editingMatchId').value = "";
            document.getElementById('matchTeam1').value = "";
            document.getElementById('matchTeam2').value = "";
            document.getElementById('matchFormat').value = "";
            document.getElementById('matchDateTime').value = "";
            document.getElementById('matchVenue').value = "";
            document.getElementById('matchGateTime').value = "";
            document.getElementById('matchCode6').value = "";
            populateExistingSeriesDropdown('match');
            toggleSeriesInput('match');
            document.getElementById('matchModal').classList.remove('hidden'); 
        }
        function closeMatchModal() { document.getElementById('matchModal').classList.add('hidden'); }
        
        function openInternationalMatchModal() { 
            if (currentMobile !== db.settings.adminNumber) return;
            document.getElementById('intModalTitle').innerText = "🌍 Create International Match (Admin Only)";
            document.getElementById('editingIntMatchId').value = "";
            document.getElementById('intTeam1').value = "";
            document.getElementById('intTeam2').value = "";
            document.getElementById('intFormat').value = "";
            document.getElementById('intDateTime').value = "";
            document.getElementById('intVenue').value = "";
            document.getElementById('intGateTime').value = "";
            document.getElementById('intPrice').value = "";
            document.getElementById('intLimit').value = "";
            document.getElementById('intCode6').value = "";
            populateExistingSeriesDropdown('int');
            toggleSeriesInput('int');
            document.getElementById('internationalMatchModal').classList.remove('hidden'); 
        }
        function closeInternationalMatchModal() { document.getElementById('internationalMatchModal').classList.add('hidden'); }

        function toggleSeriesInput(prefix) {
            let type = document.getElementById(`${prefix}SeriesType`).value;
            let existingContainer = document.getElementById(`${prefix}ExistingSeriesContainer`);
            let newContainer = document.getElementById(`${prefix}NewSeriesContainer`);

            if (type === 'existing') {
                existingContainer.classList.remove('hidden');
                newContainer.classList.add('hidden');
            } else {
                existingContainer.classList.add('hidden');
                newContainer.classList.remove('hidden');
            }
        }

        function populateExistingSeriesDropdown(prefix) {
            let selectEl = document.getElementById(`${prefix}ExistingSeriesSelect`);
            let seriesList = [];
            db.matches.forEach(m => {
                if (m.seriesName && !seriesList.includes(m.seriesName)) {
                    seriesList.push(m.seriesName);
                }
            });

            if (seriesList.length === 0) {
                selectEl.innerHTML = '<option value="">Koi existing series nahi hai (New select karein)</option>';
                document.getElementById(`${prefix}SeriesType`).value = 'new';
                toggleSeriesInput(prefix);
            } else {
                let html = '';
                seriesList.forEach(s => {
                    html += `<option value="${s}">${s}</option>`;
                });
                selectEl.innerHTML = html;
            }
        }

        function saveMatchSchedule(isInternational) {
            if (isInternational && currentMobile !== db.settings.adminNumber) {
                alert("International match sirf Admin create kar sakta hai!");
                return;
            }

            let prefix = isInternational ? 'int' : 'match';
            let seriesType = document.getElementById(`${prefix}SeriesType`).value;
            let seriesName = seriesType === 'existing' ? document.getElementById(`${prefix}ExistingSeriesSelect`).value : document.getElementById(`${prefix}SeriesName`).value.trim();

            let matchObj = {
                id: 'match_' + Date.now(),
                creator: currentMobile,
                isInternational: isInternational,
                seriesName: seriesName,
                team1: document.getElementById(`${prefix}Team1`).value.trim(),
                team2: document.getElementById(`${prefix}Team2`).value.trim(),
                matchFormat: document.getElementById(`${prefix}Format`).value.trim() || "T20I",
                dateTime: document.getElementById(`${prefix}DateTime`).value.trim() || "WED, 17 DEC, 2026 | 7 PM",
                venue: document.getElementById(`${prefix}Venue`).value.trim() || "STADIUM, LUCKNOW",
                gateTime: document.getElementById(`${prefix}GateTime`).value.trim() || "Gate Opens: 2 Hours Before",
                price: isInternational ? (Number(document.getElementById(`${prefix}Price`).value) || 0) : 0,
                limit: isInternational ? (Number(document.getElementById(`${prefix}Limit`).value) || 0) : 0,
                soldCount: 0,
                code6: document.getElementById(`${prefix}Code6`).value.trim(),
                resultStatus: 'Upcoming'
            };

            db.matches.push(matchObj);
            saveDB();
            if (isInternational) closeInternationalMatchModal();
            else closeMatchModal();
            renderMatches();
            alert("Match successfully publish ho gaya!");
        }

        function verifyMatchCode() {
            let code = document.getElementById('verifyCodeInput').value.trim();
            let resDiv = document.getElementById('verifyResult');
            let match = db.matches.find(m => m.code6 === code);

            if (!match) {
                resDiv.innerHTML = `<span style="color:var(--danger); font-weight:bold;">❌ Invalid Code! Koi match nahi mila.</span>`;
                return;
            }

            resDiv.innerHTML = `<div style="background:#e8f4fd; padding:12px; border-radius:8px; color:var(--primary); font-weight:bold;">✔ Match Found: ${match.team1} vs ${match.team2} (${match.matchFormat}) - Venue: ${match.venue}</div>`;
        }

        function switchTab(tabName, event) {
            document.querySelectorAll('.tab-content').forEach(el => el.classList.add('hidden'));
            document.querySelectorAll('.tabs .tab-btn').forEach(el => el.classList.remove('active'));

            if (tabName === 'international') document.getElementById('internationalTabContent').classList.remove('hidden');
            if (tabName === 'apna') document.getElementById('apnaTabContent').classList.remove('hidden');
            if (tabName === 'activeTickets') document.getElementById('activeTicketsTabContent').classList.remove('hidden');
            if (tabName === 'myPurchased') document.getElementById('myPurchasedTabContent').classList.remove('hidden');
            if (tabName === 'messages') document.getElementById('messagesTabContent').classList.remove('hidden');

            if (event && event.target) event.target.classList.add('active');
        }

        function renderMatches() {
            let intList = document.getElementById('internationalMatchesList');
            let apnaList = document.getElementById('apnaMatchesList');

            let intHTML = '';
            let apnaHTML = '';

            db.matches.forEach(m => {
                let ticketBtn = m.isInternational ? `<button class="btn btn-warning" onclick="buyTicket('${m.id}')">Buy Ticket (₹${m.price})</button>` : '';
                let cardHTML = `
                    <div class="match-card">
                        <div class="series-title-bar">
                            <span>${m.seriesName || 'Series'}</span>
                            <span class="match-format-green">${m.matchFormat}</span>
                        </div>
                        <div class="match-row">
                            <div class="team-box">🏏 ${m.team1}</div>
                            <div class="vs-text"><span>VS</span><span style="font-size:0.8rem; color:#888;">${m.dateTime}</span></div>
                            <div class="team-box">${m.team2} 🏏</div>
                        </div>
                        <div style="font-size: 0.9rem; color: #555; margin-bottom: 12px;">📍 Venue: <b>${m.venue}</b> | ⏰ Gate: <b>${m.gateTime}</b></div>
                        ${ticketBtn}
                    </div>
                `;

                if (m.isInternational) intHTML += cardHTML;
                else apnaHTML += cardHTML;
            });

            intList.innerHTML = intHTML || '<p style="color:#666;">Koi International match available nahi hai.</p>';
            apnaList.innerHTML = apnaHTML || '<p style="color:#666;">Koi Apna schedule available nahi hai.</p>';
        }

        function buyTicket(matchId) {
            if (!checkUserHasActiveSubOrData()) {
                alert("Ticket buy karne ke liye active subscription ya Data pack hona zaroori hai! Pehle Data pack buy karein.");
                return;
            }

            let match = db.matches.find(m => m.id === matchId);
            if (!match) return;

            let user = db.users[currentMobile];
            if (user.wallet < match.price) {
                alert("Wallet mein balance kam hai! Pehle Transaction ID daal kar balance add karein.");
                return;
            }

            user.wallet -= match.price;
            match.soldCount++;

            let ticketObj = {
                id: 'tkt_' + Date.now(),
                matchId: match.id,
                mobile: currentMobile,
                team1: match.team1,
                team2: match.team2,
                matchFormat: match.matchFormat,
                dateTime: match.dateTime,
                venue: match.venue,
                price: match.price,
                code6: match.code6,
                purchasedAt: new Date().toLocaleString()
            };

            db.tickets.push(ticketObj);
            saveDB();
            updateHeader();
            renderActiveTickets();
            renderMyPurchasedTickets();
            alert("Ticket successfully buy ho gayi hai!");
        }

        function renderActiveTickets() {
            let container = document.getElementById('activeTicketsList');
            let userTickets = db.tickets.filter(t => t.mobile === currentMobile);

            if (userTickets.length === 0) {
                container.innerHTML = '<p style="color:#666;">Aapke paas koi active ticket nahi hai.</p>';
                return;
            }

            let html = '';
            userTickets.forEach(t => {
                html += `
                    <div style="background: linear-gradient(135deg, #1e3c72, #2a5298); color:#fff; border-radius:14px; padding:20px; margin-bottom:15px; box-shadow:0 4px 15px rgba(0,0,0,0.2);">
                        <div style="display:flex; justify-content:space-between; font-size:0.9rem; font-weight:bold; border-bottom:1px solid rgba(255,255,255,0.3); padding-bottom:8px; margin-bottom:10px;">
                            <span>TICKET PASS</span>
                            <span>${t.matchFormat}</span>
                        </div>
                        <div style="font-size:1.5rem; font-weight:900; text-align:center; margin:10px 0;">${t.team1} vs ${t.team2}</div>
                        <div style="font-size:0.95rem; margin-bottom:8px;">📍 ${t.venue}</div>
                        <div style="font-size:0.95rem; margin-bottom:12px;">⏰ ${t.dateTime}</div>
                        <div style="background:#fff; color:#333; padding:10px; border-radius:8px; display:flex; justify-content:space-between; font-weight:bold;">
                            <span>Security Code: <span style="color:var(--danger); font-family:monospace; font-size:1.1rem;">${t.code6 || 'N/A'}</span></span>
                            <span>Paid: ₹${t.price}</span>
                        </div>
                    </div>
                `;
            });
            container.innerHTML = html;
        }

        function renderMyPurchasedTickets() {
            let container = document.getElementById('myPurchasedList');
            let userTickets = db.tickets.filter(t => t.mobile === currentMobile);

            if (userTickets.length === 0) {
                container.innerHTML = '<p style="color:#666;">Aapne abhi tak koi ticket purchase nahi ki hai.</p>';
                return;
            }

            let html = '';
            userTickets.forEach(t => {
                html += `
                    <div class="match-card">
                        <h4>${t.team1} vs ${t.team2} (${t.matchFormat})</h4>
                        <p style="color:#666; font-size:0.9rem;">Purchased At: ${t.purchasedAt} | Price: ₹${t.price}</p>
                    </div>
                `;
            });
            container.innerHTML = html;
        }

        function openMasterAdminPanel() {
            if (currentMobile !== db.settings.adminNumber) return;
            renderAdminMatches();
            renderAdminTickets();
            renderAdminPlans();
            document.getElementById('masterAdminModal').classList.remove('hidden');
        }

        function closeMasterAdminPanel() {
            document.getElementById('masterAdminModal').classList.add('hidden');
        }

        function switchAdminSubTab(subTab, event) {
            document.querySelectorAll('.admin-sub-tab').forEach(el => el.classList.add('hidden'));
            if (subTab === 'matches') document.getElementById('adminTabMatches').classList.remove('hidden');
            if (subTab === 'tickets') document.getElementById('adminTabTickets').classList.remove('hidden');
            if (subTab === 'plans') document.getElementById('adminTabPlans').classList.remove('hidden');

            document.querySelectorAll('#masterAdminModal .tab-btn').forEach(el => el.classList.remove('active'));
            if (event && event.target) event.target.classList.add('active');
        }

        function renderAdminMatches() {
            let container = document.getElementById('adminAllMatchesList');
            if (db.matches.length === 0) {
                container.innerHTML = '<p>No matches available.</p>';
                return;
            }
            let html = '';
            db.matches.forEach(m => {
                html += `
                    <div style="background:#f8fafc; border:1px solid var(--border); padding:12px; border-radius:8px; margin-bottom:10px; display:flex; justify-content:space-between; align-items:center;">
                        <div>
                            <strong>${m.team1} vs ${m.team2}</strong> (${m.matchFormat})<br>
                            <span style="font-size:0.85rem; color:#666;">Series: ${m.seriesName} | Code: ${m.code6}</span>
                        </div>
                        <button class="btn btn-danger" style="width:auto; padding:6px 12px; font-size:0.85rem;" onclick="adminDeleteMatch('${m.id}')">Delete</button>
                    </div>
                `;
            });
            container.innerHTML = html;
        }

        function adminDeleteMatch(matchId) {
            if (confirm("Kya aap is match ko delete karna chahte hain?")) {
                db.matches = db.matches.filter(m => m.id !== matchId);
                saveDB();
                renderAdminMatches();
                renderMatches();
            }
        }

        function renderAdminTickets() {
            let container = document.getElementById('adminAllTicketsList');
            if (db.tickets.length === 0) {
                container.innerHTML = '<p>No tickets sold yet.</p>';
                return;
            }
            let html = '';
            db.tickets.forEach(t => {
                html += `
                    <div style="background:#f8fafc; border:1px solid var(--border); padding:10px; border-radius:8px; margin-bottom:8px; font-size:0.9rem;">
                        <strong>Mobile: ${t.mobile}</strong> | Match: ${t.team1} vs ${t.team2} | Paid: ₹${t.price}
                    </div>
                `;
            });
            container.innerHTML = html;
        }

        function renderAdminPlans() {
            let container = document.getElementById('adminPlansList');
            let html = '<h4>Existing Plans</h4>';
            db.settings.plans.forEach(p => {
                html += `
                    <div style="background:#f8fafc; border:1px solid var(--border); padding:10px; border-radius:8px; margin-bottom:8px; display:flex; justify-content:space-between; align-items:center;">
                        <div><strong>${p.name}</strong> - ₹${p.price} (${p.durationDays} Days)<br><span style="font-size:0.85rem; color:var(--primary);">Total: ${p.totalData} | Daily: ${p.dailyData}</span></div>
                        <button class="btn btn-danger" style="width:auto; padding:6px 10px; font-size:0.8rem;" onclick="adminDeletePlan('${p.id}')">Delete</button>
                    </div>
                `;
            });
            container.innerHTML = html;
        }

        function addNewSubscriptionPlan() {
            let id = document.getElementById('newPlanId').value.trim();
            let name = document.getElementById('newPlanName').value.trim();
            let price = Number(document.getElementById('newPlanPrice').value);
            let days = Number(document.getElementById('newPlanDays').value);
            let totalData = document.getElementById('newPlanTotalData').value.trim();
            let dailyData = document.getElementById('newPlanDailyData').value.trim();

            if (!id || !name || !price || !days || !totalData || !dailyData) {
                alert("Kripya sabhi fields sahi se bharein!");
                return;
            }

            db.settings.plans.push({
                id: id,
                name: name,
                price: price,
                durationDays: days,
                totalData: totalData,
                dailyData: dailyData
            });

            saveDB();
            renderAdminPlans();
            renderSubscriptionPlansHub();
            alert("Naya Data/Subscription plan successfully add ho gaya hai!");
        }

        function adminDeletePlan(planId) {
            if (confirm("Kya aap is plan ko delete karna chahte hain?")) {
                db.settings.plans = db.settings.plans.filter(p => p.id !== planId);
                saveDB();
                renderAdminPlans();
                renderSubscriptionPlansHub();
            }
        }
    </script>
</body>
</html>
