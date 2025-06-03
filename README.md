<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>INSTANTWARE - Earn Money Bot</title>
    <style>
        :root {
            --primary-color: #0088cc;
            --secondary-color: #5f9ea0;
            --accent-color: #4CAF50;
            --danger-color: #f44336;
            --light-bg: #f5f5f5;
            --card-bg: #ffffff;
            --text-color: #333333;
            --text-light: #777777;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: var(--light-bg);
            color: var(--text-color);
            line-height: 1.6;
        }
        
        .telegram-container {
            max-width: 420px;
            margin: 20px auto;
            background-color: var(--card-bg);
            border-radius: 12px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            overflow: hidden;
        }
        
        .header {
            background-color: var(--primary-color);
            color: white;
            padding: 18px;
            text-align: center;
            font-size: 20px;
            font-weight: bold;
            position: relative;
        }
        
        .balance-display {
            background-color: rgba(255, 255, 255, 0.1);
            padding: 8px 15px;
            border-radius: 20px;
            font-size: 14px;
            margin-top: 8px;
            display: inline-block;
        }
        
        .content-area {
            padding: 20px;
            min-height: 500px;
        }
        
        .notification {
            background-color: #e3f2fd;
            padding: 15px;
            border-radius: 8px;
            margin-bottom: 20px;
            text-align: center;
            color: var(--primary-color);
            font-weight: 500;
        }
        
        .section {
            margin-bottom: 25px;
            background-color: var(--card-bg);
            border-radius: 10px;
            padding: 15px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.05);
        }
        
        .section-title {
            font-size: 16px;
            font-weight: 600;
            margin-bottom: 15px;
            color: var(--primary-color);
            display: flex;
            align-items: center;
            justify-content: space-between;
        }
        
        .section-title::after {
            content: "";
            flex: 1;
            margin-left: 10px;
            height: 1px;
            background-color: #eee;
        }
        
        .referral-link {
            background-color: #f8f9fa;
            border: 1px dashed #ccc;
            padding: 12px;
            border-radius: 8px;
            margin-bottom: 15px;
            word-break: break-all;
            font-size: 14px;
            color: var(--primary-color);
        }
        
        .btn {
            display: inline-block;
            padding: 10px 20px;
            background-color: var(--primary-color);
            color: white;
            border: none;
            border-radius: 6px;
            font-size: 14px;
            font-weight: 500;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s ease;
            text-decoration: none;
            margin-right: 10px;
            margin-bottom: 10px;
        }
        
        .btn:hover {
            opacity: 0.9;
            transform: translateY(-2px);
        }
        
        .btn-secondary {
            background-color: var(--secondary-color);
        }
        
        .btn-accent {
            background-color: var(--accent-color);
        }
        
        .btn-danger {
            background-color: var(--danger-color);
        }
        
        .btn-block {
            display: block;
            width: 100%;
            margin: 10px 0;
        }
        
        .stats-container {
            display: flex;
            justify-content: space-between;
            margin-bottom: 15px;
        }
        
        .stat-box {
            flex: 1;
            text-align: center;
            padding: 12px;
            background-color: #f8f9fa;
            border-radius: 8px;
            margin: 0 5px;
        }
        
        .stat-value {
            font-size: 18px;
            font-weight: bold;
            color: var(--primary-color);
        }
        
        .stat-label {
            font-size: 12px;
            color: var(--text-light);
        }
        
        .task-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 10px 0;
            border-bottom: 1px solid #eee;
        }
        
        .task-item:last-child {
            border-bottom: none;
        }
        
        .task-info {
            flex: 1;
        }
        
        .task-title {
            font-weight: 500;
            margin-bottom: 3px;
        }
        
        .task-reward {
            font-size: 12px;
            color: var(--accent-color);
        }
        
        .task-status {
            font-size: 12px;
            padding: 3px 8px;
            border-radius: 10px;
            background-color: #e8f5e9;
            color: var(--accent-color);
        }
        
        .nav-tabs {
            display: flex;
            background-color: var(--card-bg);
            border-top: 1px solid #eee;
        }
        
        .nav-tab {
            flex: 1;
            text-align: center;
            padding: 15px 0;
            color: var(--text-light);
            font-size: 14px;
            text-decoration: none;
            transition: all 0.3s ease;
        }
        
        .nav-tab.active {
            color: var(--primary-color);
            font-weight: 500;
            border-bottom: 2px solid var(--primary-color);
        }
        
        .nav-tab i {
            display: block;
            margin-bottom: 5px;
            font-size: 20px;
        }
        
        .hidden {
            display: none;
        }
        
        .withdraw-method {
            display: flex;
            align-items: center;
            padding: 10px;
            border: 1px solid #eee;
            border-radius: 8px;
            margin-bottom: 10px;
            cursor: pointer;
        }
        
        .withdraw-method.selected {
            border-color: var(--accent-color);
            background-color: #e8f5e9;
        }
        
        .withdraw-method-icon {
            width: 40px;
            height: 40px;
            background-color: #f0f0f0;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-right: 15px;
            color: var(--primary-color);
            font-size: 20px;
        }
        
        .form-group {
            margin-bottom: 15px;
        }
        
        .form-label {
            display: block;
            margin-bottom: 5px;
            font-size: 14px;
            color: var(--text-light);
        }
        
        .form-control {
            width: 100%;
            padding: 10px 15px;
            border: 1px solid #ddd;
            border-radius: 6px;
            font-size: 14px;
        }
        
        .emoji {
            font-size: 24px;
            margin-right: 5px;
            vertical-align: middle;
        }
    </style>
</head>
<body>
    <div class="telegram-container">
        <div class="header">
            INSTANTWARE
            <div class="balance-display">BDT1</div>
        </div>
        
        <div class="content-area">
            <div class="notification">
                Reward credited successfully!
            </div>
            
            <div id="earn-tab">
                <div class="section">
                    <div class="section-title">Today's Tasks</div>
                    <div class="stats-container">
                        <div class="stat-box">
                            <div class="stat-value">10</div>
                            <div class="stat-label">Total Tasks</div>
                        </div>
                        <div class="stat-box">
                            <div class="stat-value">0</div>
                            <div class="stat-label">Completed</div>
                        </div>
                        <div class="stat-box">
                            <div class="stat-value">10</div>
                            <div class="stat-label">Remaining</div>
                        </div>
                    </div>
                    <button class="btn btn-accent btn-block">Start Earning ►</button>
                </div>
                
                <div class="section">
                    <div class="section-title">Refer & Earn</div>
                    <div class="stats-container">
                        <div class="stat-box">
                            <div class="stat-value">0</div>
                            <div class="stat-label">Total Referrals</div>
                        </div>
                    </div>
                    <button class="btn btn-secondary btn-block">Invite Friends ➡️</button>
                </div>
            </div>
            
            <div id="referral-tab" class="hidden">
                <div class="section">
                    <div class="section-title">Your Referral Link</div>
                    <div class="referral-link">https://t.me/AdsToMoney_Bot?startapp=7001126563</div>
                    <p>Share your referral link and earn rewards for every friend who joins!</p>
                    <button class="btn"><span class="emoji">🔍</span> Share on Telegram</button>
                </div>
                
                <div class="section">
                    <div class="section-title">Total Referrals</div>
                    <div class="stats-container">
                        <div class="stat-box">
                            <div class="stat-value">0</div>
                            <div class="stat-label">Total Referrals</div>
                        </div>
                    </div>
                </div>
            </div>
            
            <div id="withdraw-tab" class="hidden">
                <div class="section">
                    <div class="section-title">Withdraw Funds</div>
                    <p>Available Balance: <strong>BDT1</strong></p>
                </div>
                
                <div class="section">
                    <div class="section-title">Request Withdrawal</div>
                    
                    <div class="form-group">
                        <label class="form-label">Withdrawal Method</label>
                        <div class="withdraw-method selected">
                            <div class="withdraw-method-icon">$</div>
                            <div>
                                <div style="font-weight: 500;">Select a method</div>
                                <div style="font-size: 12px; color: var(--text-light);">✔️ Verified</div>
                            </div>
                        </div>
                    </div>
                    
                    <div class="form-group">
                        <label class="form-label">Amount</label>
                        <input type="text" class="form-control" placeholder="Enter amount">
                    </div>
                    
                    <div class="form-group">
                        <label class="form-label">Withdrawal Address</label>
                        <input type="text" class="form-control" placeholder="Enter wallet address">
                    </div>
                    
                    <button class="btn btn-accent btn-block">Submit Withdrawal 😊</button>
                </div>
            </div>
            
            <div id="profile-tab" class="hidden">
                <div class="section">
                    <div class="section-title">User Profile</div>
                    <div style="text-align: center; margin-bottom: 20px;">
                        <div style="font-size: 24px; font-weight: bold;">INSTANTWARE</div>
                        <div style="color: var(--text-light);">@instantWares</div>
                    </div>
                    
                    <div class="stats-container">
                        <div class="stat-box">
                            <div class="stat-value">BDT1</div>
                            <div class="stat-label">Balance</div>
                        </div>
                    </div>
                </div>
                
                <div class="section">
                    <div class="section-title">Account Stats</div>
                    <div class="task-item">
                        <div class="task-info">
                            <div class="task-title">Total Earnings</div>
                        </div>
                        <div class="stat-value">BDT1</div>
                    </div>
                    <div class="task-item">
                        <div class="task-info">
                            <div class="task-title">Total Ads Watched</div>
                        </div>
                        <div class="stat-value">1</div>
                    </div>
                    <div class="task-item">
                        <div class="task-info">
                            <div class="task-title">Total Referrals</div>
                        </div>
                        <div class="stat-value">0</div>
                    </div>
                </div>
            </div>
        </div>
        
        <div class="nav-tabs">
            <a href="#" class="nav-tab active" onclick="showTab('earn-tab')">
                <span class="emoji">🏠</span> Home
            </a>
            <a href="#" class="nav-tab" onclick="showTab('referral-tab')">
                <span class="emoji">💰</span> Earn
            </a>
            <a href="#" class="nav-tab" onclick="showTab('withdraw-tab')">
                <span class="emoji">📤</span> Withdraw
            </a>
            <a href="#" class="nav-tab" onclick="showTab('profile-tab')">
                <span class="emoji">👤</span> Profile
            </a>
        </div>
    </div>
    
    <script>
        function showTab(tabId) {
            // Hide all tabs
            document.querySelectorAll('.content-area > div').forEach(tab => {
                tab.classList.add('hidden');
            });
            
            // Show selected tab
            document.getElementById(tabId).classList.remove('hidden');
            
            // Update active nav tab
            document.querySelectorAll('.nav-tab').forEach(tab => {
                tab.classList.remove('active');
            });
            event.currentTarget.classList.add('active');
        }
        
        // Initialize with earn tab visible
        document.addEventListener('DOMContentLoaded', function() {
            document.getElementById('earn-tab').classList.remove('hidden');
        });
    </script>
</body>
</html>
