<!DOCTYPE html>
<html lang="sw">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PakuaPro - Digital Downloads</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Material Icons -->
    <link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">
    <!-- Firebase SDK -->
    <script src="https://www.gstatic.com/firebasejs/9.6.0/firebase-app-compat.js"></script>
    <script src="https://www.gstatic.com/firebasejs/9.6.0/firebase-auth-compat.js"></script>
    <script src="https://www.gstatic.com/firebasejs/9.6.0/firebase-firestore-compat.js"></script>
    <script src="https://www.gstatic.com/firebasejs/9.6.0/firebase-storage-compat.js"></script>
    <style>
        /* Custom Styles */
        .product-card {
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        .product-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
        }
        .download-btn {
            transition: background-color 0.3s ease;
        }
        .download-btn:hover {
            background-color: #2563EB;
        }
        .nav-link.active {
            color: #3B82F6;
        }
        .smooth-transition {
            transition: all 0.3s ease;
        }
        /* Animation for notifications */
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        .fade-in {
            animation: fadeIn 0.3s ease-out;
        }
        /* Mobile-first responsive design */
        @media (min-width: 768px) {
            #app {
                max-width: 768px;
            }
        }
        /* Preview image styling */
        .image-preview {
            max-height: 200px;
            object-fit: contain;
        }
        /* Post content styling */
        .post-content {
            max-height: 100px;
            overflow: hidden;
            transition: max-height 0.5s ease;
        }
        .post-content.expanded {
            max-height: 1000px;
        }
    </style>
</head>
<body class="bg-gray-100 font-sans">
    <div id="app" class="max-w-md mx-auto bg-white min-h-screen relative pb-16">
        <!-- Main Content will be injected here -->
        <div id="main-content" class="pb-16"></div>
        
        <!-- Loading Spinner -->
        <div id="loading-spinner" class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50 hidden">
            <div class="animate-spin rounded-full h-16 w-16 border-t-4 border-b-4 border-blue-500"></div>
        </div>
        
        <!-- Navigation Bar -->
        <nav class="fixed bottom-0 w-full max-w-md bg-white shadow-lg flex justify-around items-center p-3 z-40">
            <a href="#" class="nav-link flex flex-col items-center smooth-transition" data-page="home">
                <span class="material-icons">home</span>
                <span class="text-xs mt-1">Nyumbani</span>
            </a>
            <a href="#" class="nav-link flex flex-col items-center smooth-transition" data-page="products">
                <span class="material-icons">apps</span>
                <span class="text-xs mt-1">Bidhaa</span>
            </a>
            <a href="#" class="nav-link flex flex-col items-center smooth-transition" data-page="notifications">
                <span class="material-icons">notifications</span>
                <span class="text-xs mt-1">Taarifa</span>
                <span id="notification-badge" class="absolute top-0 right-0 bg-red-500 text-white text-xs rounded-full h-4 w-4 flex items-center justify-center hidden"></span>
            </a>
            <a href="#" class="nav-link flex flex-col items-center smooth-transition" data-page="profile">
                <span class="material-icons">account_circle</span>
                <span class="text-xs mt-1">Akaunti</span>
            </a>
        </nav>
    </div>

    <script>
        // Firebase Configuration
        const firebaseConfig = {
            apiKey: "AIzaSyDJRv_zJlZq9UheyRYx2qurcEtGjkD5Mes",
            authDomain: "pakuapro-75bed.firebaseapp.com",
            projectId: "pakuapro-75bed",
            storageBucket: "pakuapro-75bed.appspot.com",
            messagingSenderId: "455099191044",
            appId: "1:455099191044:web:23db3e15d92935df100a51",
            measurementId: "G-937EEEVMGG"
        };

        // Initialize Firebase
        const app = firebase.initializeApp(firebaseConfig);
        const auth = firebase.auth();
        const db = firebase.firestore();
        const storage = firebase.storage();

        // Admin Email
        const ADMIN_EMAIL = "danieliemanueli039@gmail.com";

        // Main Application
        class PakuaProApp {
            constructor() {
                this.currentUser = null;
                this.isAdmin = false;
                this.deviceUID = localStorage.getItem('deviceUID') || this.generateUID();
                localStorage.setItem('deviceUID', this.deviceUID);
                this.unsubscribeAuth = null;
                this.unsubscribeNotifications = null;
                
                this.initAuth();
                this.initUI();
                this.setupEventListeners();
                this.checkConnection();
            }

            generateUID() {
                return 'xxxxxxxx-xxxx-4xxx-yxxx-xxxxxxxxxxxx'.replace(/[xy]/g, function(c) {
                    const r = Math.random() * 16 | 0, v = c == 'x' ? r : (r & 0x3 | 0x8);
                    return v.toString(16);
                });
            }

            checkConnection() {
                // Check online status
                window.addEventListener('online', () => this.showOnlineStatus());
                window.addEventListener('offline', () => this.showOfflineStatus());
                
                if (!navigator.onLine) {
                    this.showOfflineStatus();
                }
            }

            showOnlineStatus() {
                this.showToast("Uko online sasa", "bg-green-500");
            }

            showOfflineStatus() {
                this.showToast("Uko offline, tafadhali angalia muunganisho wa intaneti", "bg-red-500");
            }

            showToast(message, bgColor = "bg-blue-500") {
                const toast = document.createElement('div');
                toast.className = `${bgColor} text-white px-4 py-2 rounded-md fixed top-4 left-1/2 transform -translate-x-1/2 z-50 fade-in`;
                toast.textContent = message;
                document.body.appendChild(toast);
                
                setTimeout(() => {
                    toast.remove();
                }, 3000);
            }

            initAuth() {
                this.unsubscribeAuth = auth.onAuthStateChanged(async (user) => {
                    if (user) {
                        this.currentUser = user;
                        this.isAdmin = user.email === ADMIN_EMAIL;
                        
                        // Check if user account is active
                        try {
                            const userDoc = await db.collection('users').doc(user.uid).get();
                            if (userDoc.exists && !userDoc.data().isActive) {
                                this.showDisabledAccountPopup();
                                await auth.signOut();
                                return;
                            }
                            
                            // Record login activity
                            await db.collection('user_activities').add({
                                userId: user.uid,
                                activityType: 'login',
                                timestamp: firebase.firestore.FieldValue.serverTimestamp(),
                                deviceInfo: navigator.userAgent
                            });
                            
                            this.updateUIAfterAuth();
                            this.renderPage('home');
                            
                            // Subscribe to notifications if admin
                            if (this.isAdmin) {
                                this.subscribeToNotifications();
                            }
                        } catch (error) {
                            console.error("Error checking user status:", error);
                            this.showToast("Hitilafu ya kuhakiki hali ya akaunti", "bg-red-500");
                        }
                    } else {
                        this.currentUser = null;
                        this.isAdmin = false;
                        this.renderLoginPage();
                        
                        // Unsubscribe from notifications if not admin
                        if (this.unsubscribeNotifications) {
                            this.unsubscribeNotifications();
                            this.unsubscribeNotifications = null;
                        }
                    }
                });
            }

            subscribeToNotifications() {
                this.unsubscribeNotifications = db.collection('notifications')
                    .orderBy('timestamp', 'desc')
                    .limit(10)
                    .onSnapshot(snapshot => {
                        const unreadCount = snapshot.docs.filter(doc => !doc.data().read).length;
                        const badge = document.getElementById('notification-badge');
                        
                        if (unreadCount > 0) {
                            badge.textContent = unreadCount;
                            badge.classList.remove('hidden');
                        } else {
                            badge.classList.add('hidden');
                        }
                    });
            }

            initUI() {
                // Set active nav link
                document.querySelectorAll('.nav-link').forEach(link => {
                    link.addEventListener('click', (e) => {
                        e.preventDefault();
                        document.querySelectorAll('.nav-link').forEach(l => l.classList.remove('active'));
                        link.classList.add('active');
                    });
                });
            }

            setupEventListeners() {
                // Navigation
                document.querySelectorAll('.nav-link').forEach(link => {
                    link.addEventListener('click', (e) => {
                        e.preventDefault();
                        const page = link.getAttribute('data-page');
                        this.renderPage(page);
                    });
                });
            }

            showLoading(show) {
                const spinner = document.getElementById('loading-spinner');
                spinner.classList.toggle('hidden', !show);
            }

            async register(email, password, phone) {
                this.showLoading(true);
                try {
                    // Check if device already has an account
                    const deviceCheck = await db.collection('device_restrictions').doc(this.deviceUID).get();
                    if (deviceCheck.exists) {
                        throw new Error('Kifaa chako tayari kimejiandikisha. Kifaa kimoja hakiruhusiwi kuwa na akaunti zaidi ya moja.');
                    }

                    const userCredential = await auth.createUserWithEmailAndPassword(email, password);
                    await db.collection('users').doc(userCredential.user.uid).set({
                        email,
                        phone,
                        deviceUID: this.deviceUID,
                        isActive: true,
                        createdAt: firebase.firestore.FieldValue.serverTimestamp(),
                        lastLogin: firebase.firestore.FieldValue.serverTimestamp()
                    });

                    await db.collection('device_restrictions').doc(this.deviceUID).set({
                        userId: userCredential.user.uid
                    });

                    // Record signup activity
                    await db.collection('user_activities').add({
                        userId: userCredential.user.uid,
                        activityType: 'signup',
                        timestamp: firebase.firestore.FieldValue.serverTimestamp(),
                        deviceInfo: navigator.userAgent
                    });

                    this.showToast("Akaunti yako imeundwa kikamilifu!", "bg-green-500");
                    return userCredential.user;
                } catch (error) {
                    console.error("Registration error:", error);
                    throw error;
                } finally {
                    this.showLoading(false);
                }
            }

            async login(email, password) {
                this.showLoading(true);
                try {
                    const userCredential = await auth.signInWithEmailAndPassword(email, password);
                    const userDoc = await db.collection('users').doc(userCredential.user.uid).get();
                    
                    if (!userDoc.data().isActive) {
                        await auth.signOut();
                        throw new Error('disabled');
                    }

                    // Update last login time
                    await db.collection('users').doc(userCredential.user.uid).update({
                        lastLogin: firebase.firestore.FieldValue.serverTimestamp()
                    });

                    this.showToast("Umeingia kikamilifu!", "bg-green-500");
                    return userCredential.user;
                } catch (error) {
                    console.error("Login error:", error);
                    throw error;
                } finally {
                    this.showLoading(false);
                }
            }

            async logout() {
                try {
                    await auth.signOut();
                    this.showToast("Umeondoka kikamilifu", "bg-blue-500");
                } catch (error) {
                    console.error("Error signing out:", error);
                    this.showToast("Hitilafu ya kuondoka", "bg-red-500");
                }
            }

            showDisabledAccountPopup() {
                const popupHTML = `
                    <div class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50">
                        <div class="bg-white rounded-lg p-6 max-w-sm mx-4">
                            <h2 class="text-xl font-bold mb-4">Akaunti Imesimamishwa</h2>
                            <p class="mb-4">Akaunti yako imezimwa. Tafadhali lipia Tsh 2000 kupitia M-Pesa 0745720609 (Jina: Danieli Yohana) ili iweze kurudishwa.</p>
                            <button class="bg-blue-500 text-white px-4 py-2 rounded-md w-full" id="closePopup">Sawa</button>
                        </div>
                    </div>
                `;
                document.getElementById('app').insertAdjacentHTML('beforeend', popupHTML);
                document.getElementById('closePopup').addEventListener('click', () => {
                    document.getElementById('app').lastChild.remove();
                });
            }

            updateUIAfterAuth() {
                if (this.isAdmin) {
                    // Add admin badge to profile nav
                    const profileLink = document.querySelector('.nav-link[data-page="profile"]');
                    profileLink.innerHTML = `
                        <span class="material-icons">admin_panel_settings</span>
                        <span class="text-xs mt-1">Admin</span>
                    `;
                }
            }

            async renderPage(page) {
                const mainContent = document.getElementById('main-content');
                mainContent.innerHTML = '';
                
                switch(page) {
                    case 'home':
                        mainContent.innerHTML = `
                            <div class="p-4">
                                <h1 class="text-2xl font-bold mb-6 text-center">Karibu PakuaPro</h1>
                                <div class="bg-blue-50 p-4 rounded-lg mb-6">
                                    <h2 class="text-lg font-semibold mb-2">Bidhaa Mpya</h2>
                                    <p>Angalia bidhaa zote mpya zilizowekwa kwenye mfumo wetu.</p>
                                </div>
                                ${this.isAdmin ? `
                                <div class="bg-green-50 p-4 rounded-lg">
                                    <h2 class="text-lg font-semibold mb-2">Admin Panel</h2>
                                    <p>Unaweza kudhibiti mfumo kutoka hapa.</p>
                                    <button class="bg-green-500 text-white px-4 py-2 rounded-md mt-2" id="adminPanelBtn">Fungua Admin Panel</button>
                                </div>
                                ` : ''}
                            </div>
                        `;
                        
                        if (this.isAdmin) {
                            document.getElementById('adminPanelBtn').addEventListener('click', () => {
                                this.renderAdminPanel();
                            });
                        }
                        break;
                        
                    case 'products':
                        this.showLoading(true);
                        try {
                            const products = await this.getAllProducts();
                            let productsHTML = '<div class="p-4"><h1 class="text-2xl font-bold mb-6">Bidhaa Zote</h1>';
                            
                            if (products.length === 0) {
                                productsHTML += '<p class="text-center text-gray-500">Hakuna bidhaa zilizopatikana kwa sasa.</p>';
                            } else {
                                products.forEach(product => {
                                    productsHTML += this.renderProductCard(product);
                                });
                            }
                            
                            productsHTML += '</div>';
                            mainContent.innerHTML = productsHTML;
                            
                            // Add event listeners for expandable posts
                            document.querySelectorAll('.expand-post').forEach(btn => {
                                btn.addEventListener('click', (e) => {
                                    const postContent = e.target.closest('.post-container').querySelector('.post-content');
                                    postContent.classList.toggle('expanded');
                                    e.target.textContent = postContent.classList.contains('expanded') ? 'Funga' : 'Soma Zaidi';
                                });
                            });
                            
                            // Add like functionality
                            document.querySelectorAll('.like-btn').forEach(btn => {
                                btn.addEventListener('click', async (e) => {
                                    const postId = e.target.closest('.product-card').getAttribute('data-id');
                                    await this.handleLike(postId);
                                });
                            });
                        } catch (error) {
                            mainContent.innerHTML = `
                                <div class="p-4 text-red-500">
                                    <p>Kuna hitilafu katika kupakua bidhaa. Tafadhali jaribu tena baadaye.</p>
                                </div>
                            `;
                        } finally {
                            this.showLoading(false);
                        }
                        break;
                        
                    case 'notifications':
                        if (!this.currentUser) {
                            this.renderLoginPage();
                            return;
                        }
                        
                        this.showLoading(true);
                        try {
                            let notificationsHTML = '<div class="p-4"><h1 class="text-2xl font-bold mb-6">Taarifa</h1>';
                            
                            if (this.isAdmin) {
                                // Admin can create notifications
                                notificationsHTML += `
                                    <div class="mb-6 bg-white p-4 rounded-lg shadow">
                                        <h2 class="text-lg font-semibold mb-2">Tuma Taarifa Mpya</h2>
                                        <textarea id="newNotification" class="w-full border p-2 rounded mb-2" placeholder="Andika taarifa hapa..."></textarea>
                                        <button id="sendNotification" class="bg-blue-500 text-white px-4 py-2 rounded-md">Tuma</button>
                                    </div>
                                `;
                                
                                // Show all notifications
                                const notifications = await db.collection('notifications')
                                    .orderBy('timestamp', 'desc')
                                    .get();
                                
                                if (notifications.empty) {
                                    notificationsHTML += '<p class="text-gray-500">Hakuna taarifa zilizotumwa.</p>';
                                } else {
                                    notifications.forEach(doc => {
                                        const notification = doc.data();
                                        notificationsHTML += `
                                            <div class="bg-white p-4 rounded-lg shadow mb-4 ${!notification.read ? 'border-l-4 border-blue-500' : ''}">
                                                <p class="mb-2">${notification.message}</p>
                                                <p class="text-xs text-gray-500">${new Date(notification.timestamp.toDate()).toLocaleString()}</p>
                                                <p class="text-xs text-gray-500">Imesomwa na: ${notification.readBy?.length || 0} watu</p>
                                            </div>
                                        `;
                                    });
                                }
                            } else {
                                // Regular users can only view their notifications
                                const notifications = await db.collection('notifications')
                                    .orderBy('timestamp', 'desc')
                                    .get();
                                
                                if (notifications.empty) {
                                    notificationsHTML += '<p class="text-gray-500">Hakuna taarifa mpya.</p>';
                                } else {
                                    notifications.forEach(doc => {
                                        const notification = doc.data();
                                        notificationsHTML += `
                                            <div class="bg-white p-4 rounded-lg shadow mb-4">
                                                <p class="mb-2">${notification.message}</p>
                                                <p class="text-xs text-gray-500">${new Date(notification.timestamp.toDate()).toLocaleString()}</p>
                                            </div>
                                        `;
                                    });
                                    
                                    // Mark notifications as read
                                    await Promise.all(notifications.docs.map(doc => {
                                        if (!doc.data().readBy?.includes(this.currentUser.uid)) {
                                            return db.collection('notifications').doc(doc.id).update({
                                                readBy: firebase.firestore.FieldValue.arrayUnion(this.currentUser.uid)
                                            });
                                        }
                                    }));
                                }
                            }
                            
                            notificationsHTML += '</div>';
                            mainContent.innerHTML = notificationsHTML;
                            
                            if (this.isAdmin) {
                                document.getElementById('sendNotification').addEventListener('click', async () => {
                                    const message = document.getElementById('newNotification').value.trim();
                                    if (!message) return;
                                    
                                    try {
                                        await db.collection('notifications').add({
                                            message,
                                            timestamp: firebase.firestore.FieldValue.serverTimestamp(),
                                            readBy: [],
                                            sentBy: this.currentUser.uid
                                        });
                                        
                                        document.getElementById('newNotification').value = '';
                                        this.showToast("Taarifa imetumwa kikamilifu!", "bg-green-500");
                                        this.renderPage('notifications'); // Refresh the view
                                    } catch (error) {
                                        console.error("Error sending notification:", error);
                                        this.showToast("Hitilafu ya kutuma taarifa", "bg-red-500");
                                    }
                                });
                            }
                        } catch (error) {
                            console.error("Error loading notifications:", error);
                            mainContent.innerHTML = `
                                <div class="p-4 text-red-500">
                                    <p>Hitilafu ya kupakia taarifa. Tafadhali jaribu tena baadaye.</p>
                                </div>
                            `;
                        } finally {
                            this.showLoading(false);
                        }
                        break;
                        
                    case 'profile':
                        if (!this.currentUser) {
                            this.renderLoginPage();
                            return;
                        }
                        
                        try {
                            const userDoc = await db.collection('users').doc(this.currentUser.uid).get();
                            const userData = userDoc.data();
                            
                            // Get user activities
                            const activities = await db.collection('user_activities')
                                .where('userId', '==', this.currentUser.uid)
                                .orderBy('timestamp', 'desc')
                                .limit(5)
                                .get();
                            
                            let activitiesHTML = '';
                            activities.forEach(doc => {
                                const activity = doc.data();
                                activitiesHTML += `
                                    <div class="border-b pb-2 mb-2">
                                        <p class="text-sm">${activity.activityType === 'login' ? 'Ingia' : 'Usajili'}: ${new Date(activity.timestamp.toDate()).toLocaleString()}</p>
                                    </div>
                                `;
                            });
                            
                            mainContent.innerHTML = `
                                <div class="p-4">
                                    <h1 class="text-2xl font-bold mb-6">Akaunti Yangu</h1>
                                    <div class="bg-white shadow rounded-lg p-6">
                                        <div class="flex items-center mb-4">
                                            <span class="material-icons text-4xl mr-4">account_circle</span>
                                            <div>
                                                <h2 class="text-xl font-semibold">${userData.email}</h2>
                                                <p class="text-gray-600">${userData.phone || 'Hakuna namba ya simu'}</p>
                                            </div>
                                        </div>
                                        
                                        <div class="mb-4">
                                            <p class="font-semibold">Hali ya Akaunti:</p>
                                            <span class="inline-block px-3 py-1 rounded-full text-sm font-semibold ${userData.isActive ? 'bg-green-100 text-green-800' : 'bg-red-100 text-red-800'}">
                                                ${userData.isActive ? 'Aktivu' : 'Imezimwa'}
                                            </span>
                                        </div>
                                        
                                        <div class="mb-4">
                                            <p class="font-semibold">Shughuli Za Hivi Karibuni:</p>
                                            ${activitiesHTML || '<p class="text-sm text-gray-500">Hakuna shughuli zilizorekodiwa</p>'}
                                        </div>
                                        
                                        <button class="w-full bg-red-500 text-white py-2 rounded-md flex items-center justify-center mt-6" id="logoutBtn">
                                            <span class="material-icons mr-2">logout</span>
                                            Ondoka
                                        </button>
                                    </div>
                                </div>
                            `;
                            
                            document.getElementById('logoutBtn').addEventListener('click', () => {
                                this.logout();
                            });
                        } catch (error) {
                            console.error("Error loading profile:", error);
                            mainContent.innerHTML = `
                                <div class="p-4 text-red-500">
                                    <p>Hitilafu ya kupakia taarifa za akaunti. Tafadhali jaribu tena baadaye.</p>
                                </div>
                            `;
                        }
                        break;
                }
            }

            renderLoginPage() {
                document.getElementById('main-content').innerHTML = `
                    <div class="p-4 flex flex-col items-center justify-center min-h-[70vh]">
                        <div class="w-full max-w-sm">
                            <div class="text-center mb-8">
                                <h1 class="text-2xl font-bold mb-2">PakuaPro</h1>
                                <p class="text-gray-600">Pata programu, michezo na nyaraka kwa urahisi</p>
                            </div>
                            
                            <form id="loginForm" class="mb-6">
                                <div class="mb-4">
                                    <label class="block text-gray-700 mb-2" for="email">Barua Pepe</label>
                                    <input type="email" id="email" class="w-full px-4 py-2 border rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500" required>
                                </div>
                                <div class="mb-4">
                                    <label class="block text-gray-700 mb-2" for="password">Nenosiri</label>
                                    <input type="password" id="password" class="w-full px-4 py-2 border rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500" required>
                                </div>
                                <button type="submit" class="w-full bg-blue-500 text-white py-2 rounded-md hover:bg-blue-600 transition">
                                    Ingia
                                </button>
                            </form>
                            
                            <div class="text-center mb-6">
                                <p class="text-gray-600">Au</p>
                            </div>
                            
                            <div class="border-t pt-6">
                                <p class="text-center text-gray-600 mb-4">Huna akaunti?</p>
                                <button id="showRegisterBtn" class="w-full bg-green-500 text-white py-2 rounded-md hover:bg-green-600 transition">
                                    Jisajili Sasa
                                </button>
                            </div>
                        </div>
                    </div>
                `;
                
                document.getElementById('loginForm').addEventListener('submit', async (e) => {
                    e.preventDefault();
                    const email = document.getElementById('email').value;
                    const password = document.getElementById('password').value;
                    
                    try {
                        await this.login(email, password);
                    } catch (error) {
                        if (error.message === 'disabled') {
                            this.showDisabledAccountPopup();
                        } else {
                            this.showToast(`Hitilafu ya kuingia: ${error.message}`, "bg-red-500");
                        }
                    }
                });
                
                document.getElementById('showRegisterBtn').addEventListener('click', () => {
                    this.renderRegisterPage();
                });
            }

            renderRegisterPage() {
                document.getElementById('main-content').innerHTML = `
                    <div class="p-4 flex flex-col items-center justify-center min-h-[70vh]">
                        <div class="w-full max-w-sm">
                            <div class="text-center mb-8">
                                <h1 class="text-2xl font-bold mb-2">Jisajili</h1>
                                <p class="text-gray-600">Unda akaunti yako ya PakuaPro</p>
                            </div>
                            
                            <form id="registerForm">
                                <div class="mb-4">
                                    <label class="block text-gray-700 mb-2" for="regEmail">Barua Pepe</label>
                                    <input type="email" id="regEmail" class="w-full px-4 py-2 border rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500" required>
                                </div>
                                <div class="mb-4">
                                    <label class="block text-gray-700 mb-2" for="regPhone">Namba ya Simu</label>
                                    <input type="tel" id="regPhone" class="w-full px-4 py-2 border rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500" required>
                                </div>
                                <div class="mb-4">
                                    <label class="block text-gray-700 mb-2" for="regPassword">Nenosiri</label>
                                    <input type="password" id="regPassword" class="w-full px-4 py-2 border rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500" required>
                                </div>
                                <div class="mb-6">
                                    <label class="block text-gray-700 mb-2" for="regConfirmPassword">Thibitisha Nenosiri</label>
                                    <input type="password" id="regConfirmPassword" class="w-full px-4 py-2 border rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500" required>
                                </div>
                                <button type="submit" class="w-full bg-blue-500 text-white py-2 rounded-md hover:bg-blue-600 transition">
                                    Sajili
                                </button>
                            </form>
                            
                            <div class="text-center mt-6">
                                <button id="showLoginBtn" class="text-blue-500 hover:underline">
                                    Nina akaunti, ingia
                                </button>
                            </div>
                        </div>
                    </div>
                `;
                
                document.getElementById('registerForm').addEventListener('submit', async (e) => {
                    e.preventDefault();
                    const email = document.getElementById('regEmail').value;
                    const phone = document.getElementById('regPhone').value;
                    const password = document.getElementById('regPassword').value;
                    const confirmPassword = document.getElementById('regConfirmPassword').value;
                    
                    if (password !== confirmPassword) {
                        this.showToast("Nenosiri hazifanani!", "bg-red-500");
                        return;
                    }
                    
                    try {
                        await this.register(email, password, phone);
                        this.showToast("Akaunti yako imeundwa kikamilifu! Sasa unaweza kuingia.", "bg-green-500");
                        this.renderLoginPage();
                    } catch (error) {
                        this.showToast(`Hitilafu ya kusajili: ${error.message}`, "bg-red-500");
                    }
                });
                
                document.getElementById('showLoginBtn').addEventListener('click', () => {
                    this.renderLoginPage();
                });
            }

            async getAllProducts() {
                try {
                    const snapshot = await db.collection('products').orderBy('createdAt', 'desc').get();
                    const products = snapshot.docs.map(doc => ({ id: doc.id, ...doc.data() }));
                    
                    // Get likes count for each product
                    const productsWithLikes = await Promise.all(products.map(async product => {
                        const likesSnapshot = await db.collection('likes')
                            .where('postId', '==', product.id)
                            .get();
                        
                        const viewsSnapshot = await db.collection('views')
                            .where('postId', '==', product.id)
                            .get();
                            
                        // Record view if user is logged in
                        if (this.currentUser) {
                            await db.collection('views').add({
                                postId: product.id,
                                userId: this.currentUser.uid,
                                timestamp: firebase.firestore.FieldValue.serverTimestamp()
                            });
                        }
                        
                        return {
                            ...product,
                            likesCount: likesSnapshot.size,
                            viewsCount: viewsSnapshot.size,
                            likedByCurrentUser: this.currentUser ? 
                                !!(await db.collection('likes')
                                    .where('postId', '==', product.id)
                                    .where('userId', '==', this.currentUser.uid)
                                    .limit(1)
                                    .get()).docs.length : false
                        };
                    }));
                    
                    return productsWithLikes;
                } catch (error) {
                    console.error("Error fetching products:", error);
                    throw error;
                }
            }

            async handleLike(postId) {
                if (!this.currentUser) {
                    this.showToast("Lazima uwe umeingia kwa kwanza", "bg-red-500");
                    return;
                }
                
                try {
                    // Check if user already liked the post
                    const likeQuery = await db.collection('likes')
                        .where('postId', '==', postId)
                        .where('userId', '==', this.currentUser.uid)
                        .limit(1)
                        .get();
                    
                    if (likeQuery.empty) {
                        // Add like
                        await db.collection('likes').add({
                            postId,
                            userId: this.currentUser.uid,
                            timestamp: firebase.firestore.FieldValue.serverTimestamp()
                        });
                        this.showToast("Umeipenda post hii", "bg-blue-500");
                    } else {
                        // Remove like
                        await db.collection('likes').doc(likeQuery.docs[0].id).delete();
                        this.showToast("Umeondoa upendo kutoka kwenye post hii", "bg-blue-500");
                    }
                    
                    // Refresh the products view
                    this.renderPage('products');
                } catch (error) {
                    console.error("Error handling like:", error);
                    this.showToast("Hitilafu ya kuipenda post", "bg-red-500");
                }
            }

            renderProductCard(product) {
                const shortDescription = product.description.length > 100 ? 
                    product.description.substring(0, 100) + '...' : product.description;
                
                return `
                    <div class="product-card bg-white rounded-lg shadow-md overflow-hidden mb-6 border border-gray-200 post-container" data-id="${product.id}">
                        ${product.imageUrl ? `
                            <img src="${product.imageUrl}" alt="${product.title}" class="w-full h-48 object-cover">
                        ` : ''}
                        <div class="p-4">
                            <h3 class="text-lg font-semibold mb-2">${product.title}</h3>
                            <div class="post-content mb-4">
                                <p class="text-gray-600">${product.description}</p>
                            </div>
                            ${product.description.length > 100 ? `
                                <button class="expand-post text-blue-500 text-sm mb-4">Soma Zaidi</button>
                            ` : ''}
                            
                            <div class="flex justify-between items-center mb-4">
                                <div class="flex items-center text-gray-500 text-sm">
                                    <span class="material-icons text-sm mr-1">thumb_up</span>
                                    <span>${product.likesCount || 0}</span>
                                </div>
                                <div class="flex items-center text-gray-500 text-sm">
                                    <span class="material-icons text-sm mr-1">visibility</span>
                                    <span>${product.viewsCount || 0}</span>
                                </div>
                            </div>
                            
                            <div class="flex space-x-2">
                                <button class="like-btn flex-1 ${product.likedByCurrentUser ? 'bg-blue-500 text-white' : 'bg-gray-200 text-gray-800'} px-3 py-1 rounded-md flex items-center justify-center">
                                    <span class="material-icons text-sm mr-1">thumb_up</span>
                                    ${product.likedByCurrentUser ? 'Umependa' : 'Penda'}
                                </button>
                                <a href="${product.downloadUrl}" class="download-btn flex-1 bg-blue-500 text-white px-3 py-1 rounded-md flex items-center justify-center hover:bg-blue-600">
                                    <span class="material-icons text-sm mr-1">file_download</span>
                                    Pakua
                                </a>
                            </div>
                        </div>
                    </div>
                `;
            }

            async renderAdminPanel() {
                this.showLoading(true);
                try {
                    const users = await this.getAllUsers();
                    
                    let usersHTML = '';
                    users.forEach(user => {
                        usersHTML += `
                            <div class="bg-white shadow rounded-lg p-4 mb-4">
                                <div class="flex justify-between items-center mb-2">
                                    <div>
                                        <h3 class="font-semibold">${user.email}</h3>
                                        <p class="text-sm text-gray-600">${user.phone || 'Hakuna simu'}</p>
                                    </div>
                                    <span class="inline-block px-3 py-1 rounded-full text-xs font-semibold ${user.isActive ? 'bg-green-100 text-green-800' : 'bg-red-100 text-red-800'}">
                                        ${user.isActive ? 'Aktivu' : 'Imezimwa'}
                                    </span>
                                </div>
                                <div class="flex justify-between items-center">
                                    <span class="text-xs text-gray-500">${new Date(user.createdAt?.toDate()).toLocaleDateString()}</span>
                                    <button class="toggle-user-btn text-xs px-3 py-1 rounded ${user.isActive ? 'bg-red-100 text-red-800 hover:bg-red-200' : 'bg-green-100 text-green-800 hover:bg-green-200'}" data-uid="${user.id}">
                                        ${user.isActive ? 'Zima' : 'Washa'}
                                    </button>
                                </div>
                            </div>
                        `;
                    });
                    
                    document.getElementById('main-content').innerHTML = `
                        <div class="p-4">
                            <div class="flex justify-between items-center mb-6">
                                <h1 class="text-2xl font-bold">Admin Panel</h1>
                                <button id="closeAdminPanel" class="bg-gray-200 px-3 py-1 rounded-md">Funga</button>
                            </div>
                            
                            <div class="mb-6">
                                <h2 class="text-lg font-semibold mb-2">Watumiaji (${users.length})</h2>
                                ${users.length === 0 ? '<p class="text-gray-500">Hakuna watumiaji waliosajiliwa.</p>' : usersHTML}
                            </div>
                            
                            <div class="mb-6">
                                <h2 class="text-lg font-semibold mb-2">Ongeza Bidhaa</h2>
                                <form id="addProductForm" class="bg-white p-4 rounded-lg shadow">
                                    <div class="mb-4">
                                        <label class="block text-gray-700 mb-2">Jina la Bidhaa</label>
                                        <input type="text" id="productTitle" class="w-full px-4 py-2 border rounded-md" required>
                                    </div>
                                    <div class="mb-4">
                                        <label class="block text-gray-700 mb-2">Maelezo</label>
                                        <textarea id="productDescription" class="w-full px-4 py-2 border rounded-md" rows="3" required></textarea>
                                    </div>
                                    <div class="mb-4">
                                        <label class="block text-gray-700 mb-2">Picha ya Bidhaa</label>
                                        <input type="file" id="productImageFile" accept="image/*" class="w-full px-4 py-2 border rounded-md">
                                        <div class="mt-2 hidden" id="imagePreviewContainer">
                                            <img id="imagePreview" class="image-preview border rounded">
                                        </div>
                                    </div>
                                    <div class="mb-4">
                                        <label class="block text-gray-700 mb-2">Kiungo cha Kupakua</label>
                                        <input type="url" id="productDownload" class="w-full px-4 py-2 border rounded-md" required>
                                    </div>
                                    <button type="submit" class="w-full bg-blue-500 text-white py-2 rounded-md hover:bg-blue-600 transition">
                                        Hifadhi Bidhaa
                                    </button>
                                </form>
                            </div>
                        </div>
                    `;
                    
                    // Image preview functionality
                    document.getElementById('productImageFile').addEventListener('change', function(e) {
                        const file = e.target.files[0];
                        if (file) {
                            const reader = new FileReader();
                            reader.onload = function(event) {
                                const previewContainer = document.getElementById('imagePreviewContainer');
                                const preview = document.getElementById('imagePreview');
                                preview.src = event.target.result;
                                previewContainer.classList.remove('hidden');
                            };
                            reader.readAsDataURL(file);
                        }
                    });
                    
                    // Add event listeners for toggle buttons
                    document.querySelectorAll('.toggle-user-btn').forEach(btn => {
                        btn.addEventListener('click', async () => {
                            const userId = btn.getAttribute('data-uid');
                            const userDoc = await db.collection('users').doc(userId).get();
                            const currentStatus = userDoc.data().isActive;
                            
                            try {
                                await db.collection('users').doc(userId).update({
                                    isActive: !currentStatus
                                });
                                btn.textContent = currentStatus ? 'Washa' : 'Zima';
                                btn.classList.toggle('bg-red-100', !currentStatus);
                                btn.classList.toggle('text-red-800', !currentStatus);
                                btn.classList.toggle('bg-green-100', currentStatus);
                                btn.classList.toggle('text-green-800', currentStatus);
                                
                                // Update the status badge
                                const userCard = btn.closest('.bg-white');
                                const statusBadge = userCard.querySelector('.rounded-full');
                                statusBadge.textContent = currentStatus ? 'Imezimwa' : 'Aktivu';
                                statusBadge.classList.toggle('bg-green-100', !currentStatus);
                                statusBadge.classList.toggle('text-green-800', !currentStatus);
                                statusBadge.classList.toggle('bg-red-100', currentStatus);
                                statusBadge.classList.toggle('text-red-800', currentStatus);
                            } catch (error) {
                                console.error("Error updating user status:", error);
                                this.showToast("Hitilafu ya kubadili hali ya mtumiaji.", "bg-red-500");
                            }
                        });
                    });
                    
                    // Add product form
                    document.getElementById('addProductForm').addEventListener('submit', async (e) => {
                        e.preventDefault();
                        this.showLoading(true);
                        
                        const title = document.getElementById('productTitle').value;
                        const description = document.getElementById('productDescription').value;
                        const downloadUrl = document.getElementById('productDownload').value;
                        const imageFile = document.getElementById('productImageFile').files[0];
                        
                        try {
                            let imageUrl = '';
                            
                            // Upload image if provided
                            if (imageFile) {
                                const storageRef = storage.ref(`product_images/${Date.now()}_${imageFile.name}`);
                                const uploadTask = await storageRef.put(imageFile);
                                imageUrl = await uploadTask.ref.getDownloadURL();
                            }
                            
                            // Save product to Firestore
                            await db.collection('products').add({
                                title,
                                description,
                                imageUrl,
                                downloadUrl,
                                createdAt: firebase.firestore.FieldValue.serverTimestamp(),
                                createdBy: this.currentUser.uid
                            });
                            
                            this.showToast("Bidhaa imeongezwa kikamilifu!", "bg-green-500");
                            document.getElementById('addProductForm').reset();
                            document.getElementById('imagePreviewContainer').classList.add('hidden');
                            this.renderAdminPanel(); // Refresh the view
                        } catch (error) {
                            console.error("Error adding product:", error);
                            this.showToast("Hitilafu ya kuongeza bidhaa.", "bg-red-500");
                        } finally {
                            this.showLoading(false);
                        }
                    });
                    
                    // Close admin panel
                    document.getElementById('closeAdminPanel').addEventListener('click', () => {
                        this.renderPage('home');
                    });
                    
                } catch (error) {
                    console.error("Error loading admin panel:", error);
                    document.getElementById('main-content').innerHTML = `
                        <div class="p-4 text-red-500">
                            <p>Hitilafu ya kupakia paneli ya admin. Tafadhali jaribu tena baadaye.</p>
                        </div>
                    `;
                } finally {
                    this.showLoading(false);
                }
            }

            async getAllUsers() {
                try {
                    const snapshot = await db.collection('users').orderBy('createdAt', 'desc').get();
                    return snapshot.docs.map(doc => ({ id: doc.id, ...doc.data() }));
                } catch (error) {
                    console.error("Error fetching users:", error);
                    throw error;
                }
            }
        }

        // Initialize the app when the page loads
        document.addEventListener('DOMContentLoaded', () => {
            new PakuaProApp();
        });
    </script>
</body>
</html>
