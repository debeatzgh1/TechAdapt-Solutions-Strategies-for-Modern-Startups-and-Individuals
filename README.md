
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title> | AI Tech Hub</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        :root {
            --bg: #0d1117;
            --banner-bg: rgba(22, 27, 34, 0.8);
            --text: #c9d1d9;
            --accent: #58a6ff;
            --cyber-cyan: #00f2ff;
            --glass-border: rgba(255, 255, 255, 0.1);
        }

        [data-theme="light"] {
            --bg: #f8fafc;
            --banner-bg: rgba(255, 255, 255, 0.8);
            --text: #1e293b;
            --accent: #2563eb;
            --cyber-cyan: #0ea5e9;
            --glass-border: rgba(0, 0, 0, 0.1);
        }

        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Plus Jakarta Sans', sans-serif; }
        body { background: var(--bg); color: var(--text); transition: background 0.4s, color 0.4s; overflow-x: hidden; min-height: 200vh; }

        /* --- 1. TOP FLOATING BANNER --- */
        .top-banner {
            position: fixed; top: 15px; left: 50%; transform: translateX(-50%);
            width: 95%; max-width: 1200px; height: 65px;
            background: var(--banner-bg); backdrop-filter: blur(12px);
            border-radius: 20px; border: 1px solid var(--glass-border);
            display: flex; justify-content: space-between; align-items: center;
            padding: 0 25px; z-index: 1000;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
        }

        .brand-section { display: flex; align-items: center; gap: 12px; }
        .ai-pulse { width: 10px; height: 10px; background: var(--cyber-cyan); border-radius: 50%; box-shadow: 0 0 10px var(--cyber-cyan); animation: pulse 2s infinite; }
        @keyframes pulse { 0% { opacity: 1; } 50% { opacity: 0.3; } 100% { opacity: 1; } }

        .nav-icons { display: flex; gap: 20px; align-items: center; }
        .nav-link { color: var(--text); font-size: 18px; cursor: pointer; transition: 0.3s; }
        .nav-link:hover { color: var(--accent); transform: translateY(-2px); }

        /* --- 2. MODAL COMMANDS (Top-Left) --- */
        .modal-controls {
            position: fixed; top: 25px; left: 25px;
            display: none; flex-direction: row; gap: 10px; z-index: 10002;
            background: var(--banner-bg); padding: 8px; border-radius: 12px;
            border: 1px solid var(--cyber-cyan); backdrop-filter: blur(10px);
        }

        .modal-btn {
            background: transparent; color: var(--cyber-cyan); border: 1px solid rgba(0, 242, 255, 0.2);
            width: 35px; height: 35px; border-radius: 8px; cursor: pointer;
            display: flex; align-items: center; justify-content: center; transition: 0.3s;
        }
        .modal-btn:hover { background: var(--cyber-cyan); color: #000; box-shadow: 0 0 15px var(--cyber-cyan); }

        /* --- 3. BLOGGER FLOATING BUTTON --- */
        .floating-blogger {
            position: fixed; bottom: 30px; right: 30px;
            width: 60px; height: 60px; background: #ff5722; color: white;
            border-radius: 50%; display: flex; align-items: center; justify-content: center;
            font-size: 24px; cursor: pointer; z-index: 999;
            box-shadow: 0 10px 25px rgba(255, 87, 34, 0.4);
            animation: heartbeat 2s infinite; transition: 0.3s;
        }
        @keyframes heartbeat { 0% { transform: scale(1); } 10% { transform: scale(1.1); } 20% { transform: scale(1); } }
        .floating-blogger:hover { transform: scale(1.1) rotate(10deg); }

        /* --- 4. IFRAME MODAL --- */
        #iframe-modal {
            position: fixed; inset: 0; background: rgba(0,0,0,0.9);
            display: none; z-index: 10001; padding: 80px 20px 20px 20px;
            animation: fadeIn 0.4s ease;
        }
        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
        .iframe-container { 
            width: 100%; height: 100%; background: #fff; border-radius: 24px;
            overflow: hidden; border: 2px solid var(--cyber-cyan);
        }
        iframe { width: 100%; height: 100%; border: none; }

        /* --- 5. THEME SWITCH --- */
        .theme-toggle { background: transparent; border: none; color: var(--text); font-size: 20px; cursor: pointer; }
    </style>
</head>
<body>

    <nav class="top-banner">
        <div class="brand-section">
            <div class="ai-pulse"></div>
            <span style="font-weight: 800; letter-spacing: -0.5px; font-size: 1.1rem;">
                DEBEATZGH <span style="color: var(--accent)">AI_LAB</span>
            </span>
        </div>

        <div class="nav-icons">
            <i class="fas fa-home nav-link" title="Home"></i>
            <i class="fas fa-code nav-link" title="Projects"></i>
            <i class="fas fa-robot nav-link" title="AI Tools"></i>
            <div style="width: 1px; height: 20px; background: var(--glass-border); margin: 0 5px;"></div>
            <button class="theme-toggle" onclick="toggleTheme()" id="themeBtn">
                <i class="fas fa-moon"></i>
            </button>
        </div>
    </nav>

    <div class="modal-controls" id="mControls">
        <button class="modal-btn" onclick="closePortal()" title="Close"><i class="fas fa-times"></i></button>
        <button class="modal-btn" onclick="toggleFull()" title="Full Screen"><i class="fas fa-expand"></i></button>
    </div>

    <main style="padding-top: 120px; text-align: center;">
        <h1 style="font-size: 3rem; margin-bottom: 10px;">Future-Ready Platforms</h1>
        <p style="opacity: 0.6; max-width: 600px; margin: auto;">Integrating Ghanaian Tech Context with Global AI Standards.</p>
    </main>

    <div class="floating-blogger" onclick="openPortal('https://appdategh1.blogspot.com/')">
        <i class="fab fa-blogger-b"></i>
    </div>

    <div id="iframe-modal">
        <div class="iframe-container" id="iframeWrap">
            <iframe id="portal-frame" src=""></iframe>
        </div>
    </div>

    <script>
        // --- Theme Switcher ---
        function toggleTheme() {
            const body = document.body;
            const btn = document.getElementById('themeBtn');
            const current = body.getAttribute('data-theme');
            
            if (current === 'light') {
                body.setAttribute('data-theme', 'dark');
                btn.innerHTML = '<i class="fas fa-moon"></i>';
            } else {
                body.setAttribute('data-theme', 'light');
                btn.innerHTML = '<i class="fas fa-sun"></i>';
            }
        }

        // --- Iframe Logic ---
        function openPortal(url) {
            const modal = document.getElementById('iframe-modal');
            const frame = document.getElementById('portal-frame');
            const controls = document.getElementById('mControls');
            
            frame.src = url;
            modal.style.display = 'block';
            controls.style.display = 'flex';
            document.body.style.overflow = 'hidden';
        }

        function closePortal() {
            document.getElementById('iframe-modal').style.display = 'none';
            document.getElementById('mControls').style.display = 'none';
            document.getElementById('portal-frame').src = "";
            document.body.style.overflow = 'auto';
        }

        function toggleFull() {
            const wrap = document.getElementById('iframeWrap');
            if (!document.fullscreenElement) {
                wrap.requestFullscreen();
            } else {
                document.exitFullscreen();
            }
        }
    </script>
</body>
</html>




<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        :root {
            --notify-red: #ff3e3e;
            --gist-blue: #58a6ff;
            --glass-dark: rgba(13, 17, 23, 0.95);
            --cyber-cyan: #00f2ff;
        }

        body { background: #0d1117; margin: 0; font-family: 'Plus Jakarta Sans', sans-serif; }

        /* --- 1. COMMAND CONTROLS (Top-Left) --- */
        .modal-controls {
            position: fixed;
            top: 20px;
            left: 20px;
            display: none; /* Shows when iframe is active */
            flex-direction: row;
            gap: 10px;
            z-index: 10001;
            padding: 8px;
            background: rgba(13, 17, 23, 0.8);
            border: 1px solid var(--cyber-cyan);
            border-radius: 12px;
            backdrop-filter: blur(10px);
        }

        .modal-btn {
            background: transparent;
            color: var(--cyber-cyan);
            border: 1px solid rgba(0, 242, 255, 0.2);
            width: 38px;
            height: 38px;
            border-radius: 8px;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: 0.3s;
        }

        .modal-btn:hover {
            background: var(--cyber-cyan);
            color: #000;
            box-shadow: 0 0 15px var(--cyber-cyan);
        }

        /* --- 2. THIN NAVIGATION INDICATORS --- */
        .nav-indicators {
            position: fixed;
            right: 25px;
            top: 50%;
            transform: translateY(-50%);
            display: flex;
            flex-direction: column;
            gap: 20px;
            z-index: 9000;
        }

        .nav-arrow {
            font-size: 10px;
            color: rgba(255, 255, 255, 0.2);
            transition: 0.5s;
            text-align: center;
            font-weight: 900;
            letter-spacing: 1px;
        }

        .nav-arrow.active {
            color: var(--cyber-cyan);
            text-shadow: 0 0 10px var(--cyber-cyan);
            transform: scale(1.2);
        }

        /* --- 3. NOTIFICATION & TYPEWRITER --- */
        #notification-wrapper {
            position: fixed;
            bottom: 30px;
            right: 30px;
            display: flex;
            align-items: center;
            z-index: 9999;
        }

        #gist-notifier {
            width: 60px; height: 60px; background: var(--glass-dark);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 50%; display: flex; align-items: center; justify-content: center;
            cursor: pointer; box-shadow: 0 10px 40px rgba(0,0,0,0.6); position: relative;
        }

        #notify-bubble {
            background: white; color: #0d1117; padding: 12px 20px;
            border-radius: 14px; margin-right: 15px; font-size: 13px;
            font-weight: 800; opacity: 0; transform: translateX(20px);
            transition: 0.4s ease; white-space: nowrap;
            box-shadow: 0 5px 15px rgba(0,0,0,0.3); min-width: 180px;
        }
        #notify-bubble.show { opacity: 1; transform: translateX(0); }

        /* --- 4. IFRAME OVERLAY --- */
        #gist-overlay {
            position: fixed; inset: 0; background: rgba(0,0,0,0.92);
            display: none; z-index: 10000; padding: 60px 20px 20px 20px;
        }
        .modal-container { 
            width: 100%; height: 100%; background: #fff; 
            border-radius: 20px; overflow: hidden; border: 2px solid var(--cyber-cyan);
        }
        iframe { width: 100%; height: 100%; border: none; }

        @keyframes bell-shake {
            0%, 100% { transform: rotate(0); }
            25% { transform: rotate(15deg); }
            75% { transform: rotate(-15deg); }
        }
        .shake { animation: bell-shake 0.4s ease-in-out infinite; }
    </style>
</head>
<body>

    <div class="modal-controls" id="mControls">
        <button class="modal-btn" onclick="closeGist()"><i class="fas fa-times"></i></button>
        <button class="modal-btn" onclick="toggleFullScreen()"><i class="fas fa-expand"></i></button>
    </div>

    <div class="nav-indicators">
        <div id="arrow-up" class="nav-arrow"><i class="fas fa-chevron-up"></i><br>SLIDE</div>
        <div id="arrow-down" class="nav-arrow">AUTO<br><i class="fas fa-chevron-down"></i></div>
    </div>

    <div id="notification-wrapper">
        <div id="notify-bubble">
            <span id="type-text"></span>
        </div>
        <div id="gist-notifier" onclick="handleEngagement()">
            <span id="comment-badge" style="position:absolute; top:-5px; right:-5px; background:var(--notify-red); color:white; font-size:9px; padding:3px 6px; border-radius:5px; font-weight:bold; display:none;">NEW</span>
            <svg width="26" height="26" viewBox="0 0 24 24" fill="none" stroke="#58a6ff" stroke-width="2.5"><path d="M18 8A6 6 0 0 0 6 8c0 7-3 9-3 9h18s-3-2-3-9"></path><path d="M13.73 21a2 2 0 0 1-3.46 0"></path></svg>
        </div>
    </div>

    <div id="gist-overlay">
        <div class="modal-container" id="mContainer">
            <iframe id="gist-frame"></iframe>
        </div>
    </div>

    <script>
        const bubble = document.getElementById('notify-bubble');
        const badge = document.getElementById('comment-badge');
        const notifier = document.getElementById('gist-notifier');
        const typeTarget = document.getElementById('type-text');
        const mControls = document.getElementById('mControls');

        // 1. Auto-Slide Indicator Logic (Every 3s)
        let toggle = true;
        setInterval(() => {
            document.getElementById('arrow-up').classList.toggle('active', toggle);
            document.getElementById('arrow-down').classList.toggle('active', !toggle);
            toggle = !toggle;
        }, 3000);

        // 2. Typewriter Logic
        function typeWriter(text, i = 0) {
            if (i < text.length) {
                typeTarget.innerHTML += text.charAt(i);
                setTimeout(() => typeWriter(text, i + 1), 50);
            }
        }

        // 3. Notification Trigger
        window.onload = () => {
            setTimeout(() => {
                bubble.classList.add('show');
                badge.style.display = 'block';
                notifier.classList.add('shake');
                typeWriter("System: New Gist update detected...");
                setTimeout(() => { 
                    bubble.classList.remove('show');
                    notifier.classList.remove('shake');
                }, 7000);
            }, 2500);
        };

        // 4. Portal Control
        function handleEngagement() {
            const frame = document.getElementById('gist-frame');
            frame.src = "https://appdategh1.blogspot.com/";
            document.getElementById('gist-overlay').style.display = 'block';
            mControls.style.display = 'flex';
        }

        function closeGist() {
            document.getElementById('gist-overlay').style.display = 'none';
            mControls.style.display = 'none';
            document.getElementById('gist-frame').src = "";
        }

        function toggleFullScreen() {
            const container = document.getElementById('mContainer');
            if (!document.fullscreenElement) {
                container.requestFullscreen();
            } else {
                document.exitFullscreen();
            }
        }
    </script>
</body>
</html>



# 🌐 Web App Resource Hub

![Status](https://img.shields.io/badge/Status-Active-success?style=for-the-badge&logo=github)
![Platform](https://img.shields.io/badge/Platform-Blogger%20%7C%20WordPress-blue?style=for-the-badge&logo=googlechrome)
![Category](https://img.shields.io/badge/Category-Web%20Apps%20%7C%20AI%20Tools-purple?style=for-the-badge&logo=appveyor)
![Made with ❤️](https://img.shields.io/badge/Made%20with-%E2%9D%A4-red?style=for-the-badge)

[![🚀 Explore All Projects](https://img.shields.io/badge/🚀%20Explore-All%20Projects-black?style=for-the-badge&logo=firefox)](https://debeatzgh.wordpress.com/)

Welcome to the **Web App Resource Hub**, a curated collection of tools, scripts, AI prompts, and components designed for developers, bloggers, startups, and productivity enthusiasts.  
This repository brings together useful resources with interactive previews, tutorials, and integration guides.

---

## 🚀 Featured Projects

### 1. Frontend Components
[![Frontend Components](https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/createamodernandcleanthumbnailforawebdevelopmentproducttitledmodernhomepagestylingtemplatewithtailwindcss3420170625469385526.jpg)](https://beatzde4.blogspot.com/p/firebase-curated-front-end-components.html)  
**Build modern UIs** with curated Firebase and frontend components for faster development.  
[![Open Project](https://img.shields.io/badge/🔗%20Open-Frontend%20Components-brightgreen?style=for-the-badge)](https://beatzde4.blogspot.com/p/firebase-curated-front-end-components.html)

---

### 2. Join Ads-Free Premium Classroom
[![Join Ads Free](https://debeatzgh.wordpress.com/wp-content/uploads/2025/09/asleekandmoderngoogleclassroombannerfortechaihubfeaturingfuturisticdigitalelements261807892942313727.jpg)](https://beatzde4.blogspot.com/p/join-our-premium-classroom-ads-free.html)  
Upgrade your learning experience with an **ads-free tech classroom** featuring exclusive tutorials and resources.  
[![Open Project](https://img.shields.io/badge/🔗%20Open-Ads%20Free%20Classroom-blue?style=for-the-badge)](https://beatzde4.blogspot.com/p/join-our-premium-classroom-ads-free.html)

---

### 3. Frontend & GitHub Widgets
[![Widgets for GitHub](https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/amodernuidashboardonalaptopscreenshowingastylishfloatinggreenbuttonlabeledaddservicecard8118683982414859133.jpg)](https://beatzde4.blogspot.com/p/patreon-blog-github-dock-styles.html)  
Enhance your GitHub pages with **modern widgets, floating buttons, and interactive scripts**.  
[![Open Project](https://img.shields.io/badge/🔗%20Open-Widgets%20for%20GitHub-orange?style=for-the-badge)](https://beatzde4.blogspot.com/p/patreon-blog-github-dock-styles.html)

---

### 4. Flashcards Learning App
[![Flashcards App](https://debeatzgh.wordpress.com/wp-content/uploads/2025/07/screenshot_20250731-172746_12073168234250614551.png)](https://beatzde4.blogspot.com/p/open-debeatzgh.html)  
A **flashcards-based learning script** to boost study habits and productivity.  
[![Open Project](https://img.shields.io/badge/🔗%20Open-Flashcards%20App-yellow?style=for-the-badge)](https://beatzde4.blogspot.com/p/open-debeatzgh.html)

---

### 5. Subscribe for Updates
[![Subscribe Updates](https://debeatzgh.wordpress.com/wp-content/uploads/2025/07/amodern3dillustrationofasignupbuttonglowingingreenonadigitalwebpagewithabstractbloggerinterfaceelementsinthebackground1809112666648032664.jpg)](https://beatzde4.blogspot.com/p/animation-for-button-fade-slide-in.html)  
Stay connected! Subscribe for the **latest updates, tutorials, and resources.**  
[![Open Project](https://img.shields.io/badge/🔗%20Open-Subscribe%20Updates-red?style=for-the-badge)](https://beatzde4.blogspot.com/p/animation-for-button-fade-slide-in.html)

---

### 6. AI Prompts for Startups
[![AI for Startups](https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/designacleanmodernthumbnailforabloggerproductscarouseltool1711994558720457535.jpg)](https://beatzde4.blogspot.com/p/ai-prompts-for-startups-carousel-box.html)  
Kickstart your **startup journey** with practical AI prompts designed for entrepreneurs and innovators.  
[![Open Project](https://img.shields.io/badge/🔗%20Open-AI%20Prompts%20for%20Startups-purple?style=for-the-badge)](https://beatzde4.blogspot.com/p/ai-prompts-for-startups-carousel-box.html)

---

### 7. Blogger Iframe Embed Generator
[![Blogger Embed Generator](https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/createacleanandmodernflat-stylethumbnailforaweb-basedtoolcalledhtmlpagegeneratorforblogger322282329178022614.jpg)](https://beatzde4.blogspot.com/p/debeatzgh-floating-buttons-v1.html)  
Easily **embed Blogger posts** into websites using iframes and styled cards.  
[![Open Project](https://img.shields.io/badge/🔗%20Open-Blogger%20Embed%20Generator-lightgrey?style=for-the-badge)](https://beatzde4.blogspot.com/p/debeatzgh-floating-buttons-v1.html)

---

### 8. AI Tools Library
[![AI Tools](https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/generateamobile-firstresponsivebloggertemplatewithcustomizablecolorsfontsandsections1576324612066211977.jpg)](https://beatzde4.blogspot.com/p/debeatzgh-ai-tools-library-ai-tools.html)  
Access a curated **library of AI tools** for creators, developers, and businesses.  
[![Open Project](https://img.shields.io/badge/🔗%20Open-AI%20Tools%20Library-green?style=for-the-badge)](https://beatzde4.blogspot.com/p/debeatzgh-ai-tools-library-ai-tools.html)

---

### 9. Blog Post Menu
[![Blog Menu](https://debeatzgh.wordpress.com/wp-content/uploads/2025/07/splitscreenleft-bloggerpostlistright-carouselbloguiwithsmoothscroll7271084210508251192.jpg)](https://beatzde4.blogspot.com/p/blog-post-menu.html)  
Organize your **blog posts into interactive menus** and carousels.  
[![Open Project](https://img.shields.io/badge/🔗%20Open-Blog%20Post%20Menu-blue?style=for-the-badge)](https://beatzde4.blogspot.com/p/blog-post-menu.html)

---

### 10. AI & Productivity Tools
[![AI Productivity](https://debeatzgh.wordpress.com/wp-content/uploads/2025/07/splitscreenleft-bloggerpostlistright-carouselbloguiwithsmoothscroll281293129661303566411426.jpg)](https://beatzde4.blogspot.com/p/get-20-cashback-on-every-products.html)  
Boost productivity with **AI-powered apps and cashback tools.**  
[![Open Project](https://img.shields.io/badge/🔗%20Open-AI%20%26%20Productivity-orange?style=for-the-badge)](https://beatzde4.blogspot.com/p/get-20-cashback-on-every-products.html)

---

### 11. Decode Artificial Intelligence
[![Decode AI](https://debeatzgh.wordpress.com/wp-content/uploads/2025/07/screenshot_20250731-171923_1221954168989747148.png)](https://msha.ke/debeatzgh)  
Explore guides and resources to **understand and apply AI effectively.**  
[![Open Project](https://img.shields.io/badge/🔗%20Open-Decode%20AI-grey?style=for-the-badge)](https://msha.ke/debeatzgh)

---

### 12. Official Website
[![Website](https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/designamodernminimalisticlogoforadigitaltoolcalledall-in-onefloatinginfomenuforblogger5444122951694103302.jpg)](https://debeatzgh.wordpress.com/)  
Visit the **official website** for tutorials, tools, and more resources.  
[![Open Project](https://img.shields.io/badge/🔗%20Open-Official%20Website-black?style=for-the-badge)](https://debeatzgh.wordpress.com/)

---

## 📌 How to Use
1. Browse the resource cards above.  
2. Click on a thumbnail, title, or **Open Project button**.  
3. Explore scripts, tools, and guides directly from the hosted pages.  

---

## 🤝 Contributing
We welcome contributions! You can:  
- Suggest new resources  
- Share improvements for existing scripts  
- Submit pull requests with new ideas  

---

## 📬 Stay Connected
🔗 [Subscribe for updates](https://beatzde4.blogspot.com/p/animation-for-button-fade-slide-in.html)  
🌍 [Official Website](https://msha.ke/debeatzgh)  
📖 [Decode Artificial Intelligence](https://msha.ke/debeatzgh)  

---

### ⭐ If you find this repository useful, don’t forget to **star** it!
