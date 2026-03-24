<!doctype html>


    <style>
        :root {
            --notify-red: #ff3e3e;
            --gist-blue: #58a6ff;
            --glass-dark: rgba(13, 17, 23, 0.95);
        }

        /* 1. FLOATING WRAPPER */
        #notification-wrapper {
            position: fixed;
            bottom: 30px;
            right: 30px;
            display: flex;
            align-items: center;
            z-index: 9999;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        /* Shake Animation */
        @keyframes bell-shake {
            0%, 100% { transform: rotate(0); }
            15% { transform: rotate(15deg); }
            30% { transform: rotate(-15deg); }
            45% { transform: rotate(10deg); }
            60% { transform: rotate(-10deg); }
        }
        .shake { animation: bell-shake 0.6s ease-in-out; }

        #gist-notifier {
            width: 60px;
            height: 60px;
            background: var(--glass-dark);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            box-shadow: 0 10px 40px rgba(0,0,0,0.6);
            order: 2;
            position: relative;
        }

        /* 2. TYPEWRITER BUBBLE */
        #notify-bubble {
            background: white;
            color: #0d1117;
            padding: 12px 20px;
            border-radius: 14px;
            margin-right: 15px;
            font-size: 13px;
            font-weight: 800;
            opacity: 0;
            transform: translateX(20px);
            transition: opacity 0.4s ease;
            white-space: nowrap;
            order: 1;
            box-shadow: 0 5px 15px rgba(0,0,0,0.3);
            min-width: 180px;
        }
        #notify-bubble.show { opacity: 1; transform: translateX(0); }
        
        /* Cursor effect */
        #type-text::after {
            content: "|";
            animation: blink 0.7s infinite;
            margin-left: 2px;
            color: var(--gist-blue);
        }
        @keyframes blink { 50% { opacity: 0; } }

        /* 3. PERMANENT LAUNCHER */
        #hub-launcher {
            position: fixed;
            bottom: 25px;
            right: 25px;
            background: var(--glass-dark);
            color: #fff;
            padding: 12px 22px;
            border-radius: 50px;
            font-size: 10px;
            font-weight: 900;
            letter-spacing: 1.5px;
            text-transform: uppercase;
            border: 1px solid rgba(255,255,255,0.1);
            cursor: pointer;
            display: none; 
            z-index: 9998;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(0,0,0,0.4);
        }
        #hub-launcher:hover { border-color: var(--gist-blue); color: var(--gist-blue); transform: translateY(-2px); }

        #comment-badge {
            position: absolute;
            top: -2px; right: -2px;
            background: var(--notify-red);
            padding: 4px 7px;
            border-radius: 8px;
            font-size: 9px;
            color: #fff;
            display: none;
            font-weight: 900;
        }

        /* MODAL OVERLAY */
        #gist-overlay {
            position: fixed;
            inset: 0;
            background: rgba(0,0,0,0.92);
            backdrop-filter: blur(8px);
            display: none;
            z-index: 10000;
            justify-content: center;
            align-items: center;
        }
        .modal-container { width: 95%; max-width: 900px; height: 85vh; background: #0d1117; border-radius: 20px; overflow: hidden; display: flex; flex-direction: column; border: 1px solid #30363d;}
        iframe { width: 100%; flex-grow: 1; border: none; }
    </style>



    <audio id="notify-sound" src="https://debeatzgh1.github.io/blogs/"></audio>

    <div id="notification-wrapper">
        <div id="notify-bubble">
            <span id="type-text"></span>
        </div>
        <div id="gist-notifier" onclick="handleEngagement()">
            <span id="comment-badge">UPDATE</span>
            <svg width="26" height="26" viewbox="0 0 24 24" fill="none" stroke="#58a6ff" stroke-width="2.5"><path d="M18 8A6 6 0 0 0 6 8c0 7-3 9-3 9h18s-3-2-3-9"></path><path d="M13.73 21a2 2 0 0 1-3.46 0"></path></svg>
        </div>
    </div>

    <button id="hub-launcher" onclick="restoreFloatingButton()">
        FAQS
    </button>

    <div id="gist-overlay">
        <div class="modal-container">
            <div class="modal-header" style="padding:15px 25px; color:#8b949e; display:flex; justify-content:space-between; background:#161b22; font-size: 11px; font-weight: bold; border-bottom: 1px solid #30363d;">
                <span><i class="fab fa-github"></i> GIST_DISCUSSION_PORTAL & FAQS</span>
                <button onclick="closeGist()" style="color:white; background:none; border:none; cursor:pointer; font-size:22px;">&times;</button>
            </div>
            <iframe id="gist-frame"></iframe>
        </div>
    </div>

    <script>
        const wrapper = document.getElementById('notification-wrapper');
        const bubble = document.getElementById('notify-bubble');
        const badge = document.getElementById('comment-badge');
        const launcher = document.getElementById('hub-launcher');
        const notifier = document.getElementById('gist-notifier');
        const sound = document.getElementById('notify-sound');
        const typeTarget = document.getElementById('type-text');

        const message = "System: New Gist comment detected...";

        function typeWriter(text, i = 0) {
            if (i < text.length) {
                typeTarget.innerHTML += text.charAt(i);
                setTimeout(() => typeWriter(text, i + 1), 50);
            }
        }

        function checkNotification() {
            const hasSeen = localStorage.getItem('gist_final_engaged');
            if (!hasSeen) {
                // Initial delay before alert
                setTimeout(() => {
                    bubble.classList.add('show');
                    badge.style.display = 'block';
                    notifier.classList.add('shake');
                    typeWriter(message);
                    
                    // Unlock sound on first interaction
                    document.addEventListener('mouseover', () => { sound.play().catch(()=>{}) }, {once: true});

                    // Auto-hide bubble after 7s
                    setTimeout(() => { 
                        bubble.classList.remove('show');
                        notifier.classList.remove('shake');
                    }, 7000);
                }, 2500);
            } else {
                wrapper.style.display = 'none';
                launcher.style.display = 'block';
            }
        }

        function handleEngagement() {
            localStorage.setItem('gist_final_engaged', 'true');
            document.getElementById('gist-frame').src = "https://mailchi.mp/dda1a453c7bd/ai-decoder";
            document.getElementById('gist-overlay').style.display = 'flex';
            
            // Vanish animation
            wrapper.style.opacity = '0';
            wrapper.style.transform = 'translateY(20px)';
            setTimeout(() => {
                wrapper.style.display = 'none';
                launcher.style.display = 'block'; 
            }, 500);
        }

        function restoreFloatingButton() {
            document.getElementById('gist-frame').src = "https://debeatzgh1.github.io/Html-code-for-portfolio-/";
            document.getElementById('gist-overlay').style.display = 'flex';
        }

        function closeGist() {
            document.getElementById('gist-overlay').style.display = 'none';
            document.getElementById('gist-frame').src = "";
        }

        window.onload = checkNotification;
    </script>

</!doctype>




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
