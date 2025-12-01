# FapStreak
#this website has a feature to keep fap streak you can update your fab details in daily basis
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>No-Fap Streak Tracker</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        :root {
            --primary: #4a6fa5;
            --secondary: #166088;
            --accent: #fdbb2d;
            --success: #4CAF50;
            --danger: #e74c3c;
            --light: #f8f9fa;
            --dark: #343a40;
            --shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        
        body {
            background: linear-gradient(135deg, #1a2a6c, #b21f1f, #fdbb2d);
            color: var(--light);
            min-height: 100vh;
            padding: 20px;
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        
        .container {
            max-width: 800px;
            width: 100%;
            background-color: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 30px;
            box-shadow: var(--shadow);
            margin-top: 20px;
            border: 1px solid rgba(255, 255, 255, 0.2);
        }
        
        header {
            text-align: center;
            margin-bottom: 30px;
        }
        
        h1 {
            font-size: 2.8rem;
            margin-bottom: 10px;
            color: var(--accent);
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
        }
        
        .subtitle {
            font-size: 1.2rem;
            opacity: 0.9;
            margin-bottom: 10px;
        }
        
        .auth-container {
            display: flex;
            flex-direction: column;
            gap: 20px;
            margin-top: 20px;
        }
        
        .auth-form {
            background: rgba(255, 255, 255, 0.15);
            border-radius: 15px;
            padding: 25px;
        }
        
        .auth-form h3 {
            color: var(--accent);
            margin-bottom: 20px;
            text-align: center;
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 500;
            font-size: 1.1rem;
        }
        
        input, select, button {
            width: 100%;
            padding: 15px;
            border-radius: 10px;
            border: none;
            font-size: 1rem;
            transition: all 0.3s ease;
        }
        
        input {
            background-color: rgba(255, 255, 255, 0.9);
            color: var(--dark);
            border: 2px solid transparent;
        }
        
        input:focus, select:focus {
            outline: none;
            border: 2px solid var(--accent);
            box-shadow: 0 0 0 3px rgba(253, 187, 45, 0.3);
        }
        
        button {
            background: linear-gradient(to right, var(--accent), var(--danger));
            color: white;
            font-weight: bold;
            cursor: pointer;
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 10px;
            margin-top: 10px;
        }
        
        button:hover {
            transform: translateY(-3px);
            box-shadow: 0 7px 15px rgba(0, 0, 0, 0.3);
        }
        
        button:active {
            transform: translateY(1px);
        }
        
        .reset-btn {
            background: linear-gradient(to right, var(--danger), var(--secondary));
        }
        
        .auth-switch {
            text-align: center;
            margin-top: 20px;
        }
        
        .auth-switch a {
            color: var(--accent);
            text-decoration: none;
            font-weight: bold;
            cursor: pointer;
        }
        
        .auth-switch a:hover {
            text-decoration: underline;
        }
        
        .streak-display {
            text-align: center;
            background: rgba(255, 255, 255, 0.15);
            border-radius: 15px;
            padding: 25px;
            margin-bottom: 30px;
            position: relative;
            overflow: hidden;
            transition: transform 0.3s ease;
        }
        
        .streak-display:hover {
            transform: translateY(-5px);
        }
        
        .streak-display::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 5px;
            background: linear-gradient(to right, var(--accent), var(--danger));
        }
        
        .current-streak {
            font-size: 5rem;
            font-weight: bold;
            color: var(--accent);
            margin: 10px 0;
            text-shadow: 2px 2px 8px rgba(0, 0, 0, 0.3);
            transition: all 0.3s ease;
        }
        
        .streak-label {
            font-size: 1.3rem;
            opacity: 0.9;
            margin-bottom: 10px;
        }
        
        .progress-container {
            width: 100%;
            height: 12px;
            background-color: rgba(255, 255, 255, 0.2);
            border-radius: 10px;
            margin: 20px 0;
            overflow: hidden;
        }
        
        .progress-bar {
            height: 100%;
            background: linear-gradient(to right, var(--success), var(--accent));
            border-radius: 10px;
            width: 0%;
            transition: width 1s ease-in-out;
        }
        
        .yesterday-info {
            background: rgba(255, 255, 255, 0.15);
            border-radius: 15px;
            padding: 20px;
            margin-bottom: 30px;
            border-left: 5px solid var(--accent);
        }
        
        .yesterday-info h3 {
            color: var(--accent);
            margin-bottom: 10px;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .form-container {
            background: rgba(255, 255, 255, 0.15);
            border-radius: 15px;
            padding: 25px;
            margin-bottom: 20px;
        }
        
        .form-container h3 {
            color: var(--accent);
            margin-bottom: 20px;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .motivation {
            margin-top: 30px;
            text-align: center;
            font-style: italic;
            opacity: 0.9;
            padding: 15px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 10px;
            border-left: 4px solid var(--accent);
        }
        
        .history {
            margin-top: 30px;
        }
        
        .history h3 {
            color: var(--accent);
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .history-item {
            background: rgba(255, 255, 255, 0.1);
            border-radius: 10px;
            padding: 15px;
            margin-bottom: 10px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            transition: all 0.3s ease;
        }
        
        .history-item:hover {
            background: rgba(255, 255, 255, 0.15);
            transform: translateX(5px);
        }
        
        .status-badge {
            padding: 5px 12px;
            border-radius: 20px;
            font-size: 0.9rem;
            font-weight: bold;
        }
        
        .status-success {
            background-color: var(--success);
        }
        
        .status-reset {
            background-color: var(--danger);
        }
        
        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            padding: 15px 25px;
            border-radius: 10px;
            background: var(--success);
            color: white;
            box-shadow: var(--shadow);
            transform: translateX(150%);
            transition: transform 0.5s ease;
            z-index: 1000;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .notification.show {
            transform: translateX(0);
        }
        
        .notification.error {
            background: var(--danger);
        }
        
        .stats-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 15px;
            margin-bottom: 30px;
        }
        
        .stat-card {
            background: rgba(255, 255, 255, 0.15);
            border-radius: 10px;
            padding: 15px;
            text-align: center;
            transition: transform 0.3s ease;
        }
        
        .stat-card:hover {
            transform: translateY(-5px);
        }
        
        .stat-value {
            font-size: 2rem;
            font-weight: bold;
            color: var(--accent);
            margin: 5px 0;
        }
        
        .stat-label {
            font-size: 0.9rem;
            opacity: 0.8;
        }
        
        .user-info {
            position: absolute;
            top: 20px;
            right: 20px;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .logout-btn {
            background: rgba(255, 255, 255, 0.2);
            color: white;
            padding: 8px 15px;
            border-radius: 20px;
            font-size: 0.9rem;
            width: auto;
        }
        
        .hidden {
            display: none;
        }
        
        @media (max-width: 600px) {
            .container {
                padding: 20px;
            }
            
            h1 {
                font-size: 2.2rem;
            }
            
            .current-streak {
                font-size: 3.5rem;
            }
            
            .stats-container {
                grid-template-columns: 1fr 1fr;
            }
            
            .user-info {
                position: relative;
                top: 0;
                right: 0;
                justify-content: center;
                margin-bottom: 20px;
            }
        }
        
        .fire-animation {
            display: inline-block;
            animation: fire 1.5s infinite alternate;
        }
        
        @keyframes fire {
            0% { color: var(--accent); transform: scale(1); }
            100% { color: #ff4500; transform: scale(1.1); }
        }
        
        .pulse {
            animation: pulse 2s infinite;
        }
        
        @keyframes pulse {
            0% { box-shadow: 0 0 0 0 rgba(253, 187, 45, 0.7); }
            70% { box-shadow: 0 0 0 15px rgba(253, 187, 45, 0); }
            100% { box-shadow: 0 0 0 0 rgba(253, 187, 45, 0); }
        }
    </style>
</head>
<body>
    <div class="notification" id="notification">
        <i class="fas fa-check-circle"></i>
        <span id="notificationText">Streak updated successfully!</span>
    </div>
    
    <div class="container">
        <header>
            <h1><i class="fas fa-fire fire-animation"></i> No-Fap Streak Tracker</h1>
            <p class="subtitle">Track your progress and build better habits</p>
        </header>
        
        <!-- Authentication Section -->
        <div id="authSection">
            <div class="auth-container">
                <div class="auth-form" id="loginForm">
                    <h3><i class="fas fa-sign-in-alt"></i> Login to Your Account</h3>
                    <div class="form-group">
                        <label for="loginUsername">Username</label>
                        <input type="text" id="loginUsername" placeholder="Enter your username" required>
                    </div>
                    <div class="form-group">
                        <label for="loginPassword">Password</label>
                        <input type="password" id="loginPassword" placeholder="Enter your password" required>
                    </div>
                    <button type="button" id="loginBtn">
                        <i class="fas fa-sign-in-alt"></i> Login
                    </button>
                    <div class="auth-switch">
                        Don't have an account? <a id="showRegister">Sign up here</a>
                    </div>
                </div>
                
                <div class="auth-form hidden" id="registerForm">
                    <h3><i class="fas fa-user-plus"></i> Create New Account</h3>
                    <div class="form-group">
                        <label for="registerUsername">Username</label>
                        <input type="text" id="registerUsername" placeholder="Choose a username" required>
                    </div>
                    <div class="form-group">
                        <label for="registerPassword">Password</label>
                        <input type="password" id="registerPassword" placeholder="Choose a password" required>
                    </div>
                    <div class="form-group">
                        <label for="confirmPassword">Confirm Password</label>
                        <input type="password" id="confirmPassword" placeholder="Confirm your password" required>
                    </div>
                    <button type="button" id="registerBtn">
                        <i class="fas fa-user-plus"></i> Create Account
                    </button>
                    <div class="auth-switch">
                        Already have an account? <a id="showLogin">Login here</a>
                    </div>
                </div>
            </div>
        </div>
        
        <!-- Main App Section (hidden by default) -->
        <div id="appSection" class="hidden">
            <div class="user-info">
                <span>Welcome, <span id="usernameDisplay"></span>!</span>
                <button class="logout-btn" id="logoutBtn">
                    <i class="fas fa-sign-out-alt"></i> Logout
                </button>
            </div>
            
            <div class="stats-container">
                <div class="stat-card">
                    <div class="stat-label">Current Streak</div>
                    <div class="stat-value" id="currentStreakStat">0</div>
                    <div class="stat-label">days</div>
                </div>
                <div class="stat-card">
                    <div class="stat-label">Longest Streak</div>
                    <div class="stat-value" id="longestStreakStat">0</div>
                    <div class="stat-label">days</div>
                </div>
                <div class="stat-card">
                    <div class="stat-label">Success Rate</div>
                    <div class="stat-value" id="successRateStat">0%</div>
                    <div class="stat-label">this month</div>
                </div>
                <div class="stat-card">
                    <div class="stat-label">Total Days</div>
                    <div class="stat-value" id="totalDaysStat">0</div>
                    <div class="stat-label">tracked</div>
                </div>
            </div>
            
            <div class="streak-display pulse">
                <p class="streak-label">Your Current Streak</p>
                <div class="current-streak" id="currentStreak">0 days</div>
                <p class="streak-label" id="encouragement">Start your journey today!</p>
                
                <div class="progress-container">
                    <div class="progress-bar" id="progressBar"></div>
                </div>
                
                <p id="nextMilestone">Next milestone: 7 days</p>
            </div>
            
            <div class="yesterday-info">
                <h3><i class="fas fa-history"></i> Yesterday's Status</h3>
                <p id="yesterdayStatus">No data available yet</p>
            </div>
            
            <div class="form-container">
                <h3><i class="fas fa-edit"></i> Update Your Streak</h3>
                <form id="streakForm">
                    <div class="form-group">
                        <label for="todayStatus"><i class="fas fa-calendar-day"></i> How did you do today?</label>
                        <select id="todayStatus" required>
                            <option value="" disabled selected>Select your status</option>
                            <option value="success">Success - I maintained my streak</option>
                            <option value="reset">I need to reset my streak</option>
                        </select>
                    </div>
                    
                    <button type="submit" id="submitBtn">
                        <i class="fas fa-paper-plane"></i> Update Streak
                    </button>
                </form>
            </div>
            
            <button class="reset-btn" id="resetBtn">
                <i class="fas fa-redo"></i> Reset All Data
            </button>
            
            <div class="motivation">
                <p><i class="fas fa-quote-left"></i> The greatest glory in living lies not in never falling, but in rising every time we fall. <i class="fas fa-quote-right"></i> - Nelson Mandela</p>
            </div>
            
            <div class="history">
                <h3><i class="fas fa-chart-line"></i> Recent History</h3>
                <div id="historyList">
                    <!-- History items will be added here dynamically -->
                </div>
            </div>
        </div>
    </div>

    <script>
        // DOM Elements
        const authSection = document.getElementById('authSection');
        const appSection = document.getElementById('appSection');
        const loginForm = document.getElementById('loginForm');
        const registerForm = document.getElementById('registerForm');
        const loginBtn = document.getElementById('loginBtn');
        const registerBtn = document.getElementById('registerBtn');
        const showRegister = document.getElementById('showRegister');
        const showLogin = document.getElementById('showLogin');
        const logoutBtn = document.getElementById('logoutBtn');
        const usernameDisplay = document.getElementById('usernameDisplay');
        
        const currentStreakElement = document.getElementById('currentStreak');
        const currentStreakStat = document.getElementById('currentStreakStat');
        const longestStreakStat = document.getElementById('longestStreakStat');
        const successRateStat = document.getElementById('successRateStat');
        const totalDaysStat = document.getElementById('totalDaysStat');
        const yesterdayStatusElement = document.getElementById('yesterdayStatus');
        const streakForm = document.getElementById('streakForm');
        const todayStatusSelect = document.getElementById('todayStatus');
        const resetBtn = document.getElementById('resetBtn');
        const historyList = document.getElementById('historyList');
        const progressBar = document.getElementById('progressBar');
        const nextMilestoneElement = document.getElementById('nextMilestone');
        const encouragementElement = document.getElementById('encouragement');
        const notification = document.getElementById('notification');
        const notificationText = document.getElementById('notificationText');
        const submitBtn = document.getElementById('submitBtn');
        
        // User management
        let currentUser = null;
        let users = JSON.parse(localStorage.getItem('noFapUsers')) || {};
        
        // Show/hide auth forms
        showRegister.addEventListener('click', () => {
            loginForm.classList.add('hidden');
            registerForm.classList.remove('hidden');
        });
        
        showLogin.addEventListener('click', () => {
            registerForm.classList.add('hidden');
            loginForm.classList.remove('hidden');
        });
        
        // Register new user
        registerBtn.addEventListener('click', () => {
            const username = document.getElementById('registerUsername').value.trim();
            const password = document.getElementById('registerPassword').value;
            const confirmPassword = document.getElementById('confirmPassword').value;
            
            if (!username || !password) {
                showNotification("Please fill in all fields", true);
                return;
            }
            
            if (password !== confirmPassword) {
                showNotification("Passwords do not match", true);
                return;
            }
            
            if (users[username]) {
                showNotification("Username already exists", true);
                return;
            }
            
            // Create new user
            users[username] = {
                password: password, // In a real app, this would be hashed
                streakData: {
                    currentStreak: 0,
                    longestStreak: 0,
                    yesterdayStatus: 'No data available yet',
                    history: [],
                    totalDays: 0,
                    successDays: 0
                }
            };
            
            localStorage.setItem('noFapUsers', JSON.stringify(users));
            showNotification("Account created successfully! Please login.");
            
            // Switch to login form
            registerForm.classList.add('hidden');
            loginForm.classList.remove('hidden');
            
            // Clear form
            document.getElementById('registerUsername').value = '';
            document.getElementById('registerPassword').value = '';
            document.getElementById('confirmPassword').value = '';
        });
        
        // Login user
        loginBtn.addEventListener('click', () => {
            const username = document.getElementById('loginUsername').value.trim();
            const password = document.getElementById('loginPassword').value;
            
            if (!username || !password) {
                showNotification("Please enter username and password", true);
                return;
            }
            
            if (!users[username] || users[username].password !== password) {
                showNotification("Invalid username or password", true);
                return;
            }
            
            // Login successful
            currentUser = username;
            usernameDisplay.textContent = username;
            
            // Switch to app section
            authSection.classList.add('hidden');
            appSection.classList.remove('hidden');
            
            // Load user data and update display
            updateDisplay();
            
            // Clear form
            document.getElementById('loginUsername').value = '';
            document.getElementById('loginPassword').value = '';
            
            showNotification(`Welcome back, ${username}!`);
        });
        
        // Logout user
        logoutBtn.addEventListener('click', () => {
            currentUser = null;
            appSection.classList.add('hidden');
            authSection.classList.remove('hidden');
            showNotification("You have been logged out.");
        });
        
        // Get current user's streak data
        function getCurrentUserData() {
            return users[currentUser].streakData;
        }
        
        // Save current user's data
        function saveUserData() {
            users[currentUser].streakData = getCurrentUserData();
            localStorage.setItem('noFapUsers', JSON.stringify(users));
        }
        
        // Update the display with current data
        function updateDisplay() {
            const streakData = getCurrentUserData();
            
            currentStreakElement.textContent = `${streakData.currentStreak} ${streakData.currentStreak === 1 ? 'day' : 'days'}`;
            currentStreakStat.textContent = streakData.currentStreak;
            longestStreakStat.textContent = streakData.longestStreak;
            yesterdayStatusElement.textContent = streakData.yesterdayStatus;
            
            // Calculate success rate
            const successRate = streakData.totalDays > 0 
                ? Math.round((streakData.successDays / streakData.totalDays) * 100) 
                : 0;
            successRateStat.textContent = `${successRate}%`;
            
            totalDaysStat.textContent = streakData.totalDays;
            
            // Update progress bar based on current streak
            const milestone = getNextMilestone(streakData.currentStreak);
            const progress = (streakData.currentStreak / milestone) * 100;
            progressBar.style.width = `${Math.min(progress, 100)}%`;
            
            // Update next milestone text
            nextMilestoneElement.textContent = `Next milestone: ${milestone} days`;
            
            // Update encouragement text
            updateEncouragementText();
            
            // Update history list
            updateHistoryList();
            
            // Update longest streak if needed
            if (streakData.currentStreak > streakData.longestStreak) {
                streakData.longestStreak = streakData.currentStreak;
                saveUserData();
            }
        }
        
        // Get the next milestone based on current streak
        function getNextMilestone(streak) {
            const milestones = [7, 14, 30, 60, 90, 120, 180, 365];
            for (const milestone of milestones) {
                if (streak < milestone) return milestone;
            }
            return 365;
        }
        
        // Update encouragement text based on streak
        function updateEncouragementText() {
            const streakData = getCurrentUserData();
            const streak = streakData.currentStreak;
            let text = "Start your journey today!";
            
            if (streak === 0) {
                text = "Start your journey today!";
            } else if (streak < 7) {
                text = "You're building momentum! Keep going!";
            } else if (streak < 30) {
                text = "Amazing progress! You're building a solid habit!";
            } else if (streak < 90) {
                text = "Incredible! You're mastering self-control!";
            } else {
                text = "Legendary! You're an inspiration to others!";
            }
            
            encouragementElement.textContent = text;
        }
        
        // Update history list
        function updateHistoryList() {
            const streakData = getCurrentUserData();
            historyList.innerHTML = '';
            
            if (streakData.history.length === 0) {
                historyList.innerHTML = '<p>No history yet. Start tracking to see your progress!</p>';
                return;
            }
            
            // Show last 7 entries
            const recentHistory = streakData.history.slice(-7).reverse();
            
            recentHistory.forEach(entry => {
                const historyItem = document.createElement('div');
                historyItem.className = 'history-item';
                
                const date = new Date(entry.date);
                const formattedDate = date.toLocaleDateString('en-US', { 
                    weekday: 'short', 
                    month: 'short', 
                    day: 'numeric' 
                });
                
                const statusClass = entry.status === 'success' ? 'status-success' : 'status-reset';
                const statusText = entry.status === 'success' ? 'Maintained' : 'Reset';
                
                historyItem.innerHTML = `
                    <span><i class="far fa-calendar"></i> ${formattedDate}</span>
                    <span class="status-badge ${statusClass}">${statusText}</span>
                `;
                
                historyList.appendChild(historyItem);
            });
        }
        
        // Show notification
        function showNotification(message, isError = false) {
            notificationText.textContent = message;
            
            if (isError) {
                notification.classList.add('error');
            } else {
                notification.classList.remove('error');
            }
            
            notification.classList.add('show');
            
            setTimeout(() => {
                notification.classList.remove('show');
            }, 3000);
        }
        
        // Handle form submission
        streakForm.addEventListener('submit', function(e) {
            e.preventDefault();
            
            if (!currentUser) {
                showNotification("Please log in to update your streak", true);
                return;
            }
            
            const todayStatus = todayStatusSelect.value;
            
            if (!todayStatus) {
                showNotification("Please select your status for today", true);
                return;
            }
            
            // Disable button to prevent multiple submissions
            submitBtn.disabled = true;
            submitBtn.innerHTML = '<i class="fas fa-spinner fa-spin"></i> Updating...';
            
            // Simulate processing delay
            setTimeout(() => {
                const today = new Date();
                const streakData = getCurrentUserData();
                
                // Update streak based on user's selection
                if (todayStatus === 'success') {
                    streakData.currentStreak += 1;
                    streakData.successDays += 1;
                    streakData.yesterdayStatus = `You maintained your streak on ${today.toLocaleDateString()}`;
                    showNotification(`Awesome! Streak updated to ${streakData.currentStreak} days!`);
                } else {
                    streakData.currentStreak = 0;
                    streakData.yesterdayStatus = `You reset your streak on ${today.toLocaleDateString()}`;
                    showNotification("Streak reset. Every day is a new beginning!", true);
                }
                
                // Add to history
                streakData.history.push({
                    date: today.toISOString(),
                    status: todayStatus
                });
                
                streakData.totalDays += 1;
                
                // Keep only last 30 days of history
                if (streakData.history.length > 30) {
                    streakData.history = streakData.history.slice(-30);
                }
                
                // Save to localStorage
                saveUserData();
                
                // Update display
                updateDisplay();
                
                // Reset form
                streakForm.reset();
                
                // Re-enable button
                submitBtn.disabled = false;
                submitBtn.innerHTML = '<i class="fas fa-paper-plane"></i> Update Streak';
            }, 1000);
        });
        
        // Handle reset button
        resetBtn.addEventListener('click', function() {
            if (!currentUser) {
                showNotification("Please log in to reset data", true);
                return;
            }
            
            if (confirm('Are you sure you want to reset all data? This cannot be undone.')) {
                const streakData = getCurrentUserData();
                streakData.currentStreak = 0;
                streakData.longestStreak = 0;
                streakData.yesterdayStatus = 'No data available yet';
                streakData.history = [];
                streakData.totalDays = 0;
                streakData.successDays = 0;
                
                saveUserData();
                updateDisplay();
                showNotification("All data has been reset.");
            }
        });
        
        // Check if user is already logged in (for page refresh)
        function checkLoggedIn() {
            const loggedInUser = localStorage.getItem('noFapCurrentUser');
            if (loggedInUser && users[loggedInUser]) {
                currentUser = loggedInUser;
                usernameDisplay.textContent = currentUser;
                authSection.classList.add('hidden');
                appSection.classList.remove('hidden');
                updateDisplay();
            }
        }
        
        // Save current user on page unload
        window.addEventListener('beforeunload', () => {
            if (currentUser) {
                localStorage.setItem('noFapCurrentUser', currentUser);
            }
        });
        
        // Initialize the app
        checkLoggedIn();
    </script>
</body>
</html>
