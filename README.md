argin-bottom: 24px;
                    background: linear-gradient(45deg, var(--dbz-text-main), var(--dbz-text-muted));
                    -webkit-background-clip: text;
                    -webkit-text-fill-color: transparent;
                    letter-spacing: -0.5px;
                }

                /* Swipeable Mobile Category Bar */
                #dbz-faq-hub .category-slider {
                    display: flex;
                    gap: 10px;
                    overflow-x: auto;
                    scroll-snap-type: x mandatory;
                    scrollbar-width: none; /* Hide scrollbar for Firefox */
                    -webkit-overflow-scrolling: touch;
                    padding-bottom: 16px;
                    margin-bottom: 20px;
                    border-bottom: 1px solid var(--dbz-card-border);
                }

                #dbz-faq-hub .category-slider::-webkit-scrollbar {
                    display: none; /* Hide scrollbar for Chrome/Safari */
                }

                #dbz-faq-hub .cat-btn {
                    flex: 0 0 auto;
                    scroll-snap-align: start;
                    background: rgba(255, 255, 255, 0.03);
                    border: 1px solid var(--dbz-card-border);
                    color: var(--dbz-text-muted);
                    padding: 8px 18px;
                    border-radius: 20px;
                    font-size: 0.85rem;
                    font-weight: 600;
                    cursor: pointer;
                    transition: all 0.25s cubic-bezier(0.4, 0, 0.2, 1);
                }

                #dbz-faq-hub .cat-btn.active {
                    background: linear-gradient(135deg, var(--dbz-accent-neon) 0%, var(--dbz-accent-blue) 100%);
                    color: #ffffff;
                    border-color: transparent;
                    box-shadow: 0 4px 15px rgba(217, 70, 239, 0.25);
                }

                /* Lazy Load Accordion Layout */
                #dbz-faq-hub .faq-wrapper {
                    display: none;
                    flex-direction: column;
                    gap: 12px;
                }

                #dbz-faq-hub .faq-wrapper.active {
                    display: flex;
                    animation: dbzFadeIn 0.35s ease;
                }

                #dbz-faq-hub .faq-item {
                    background: var(--dbz-panel-bg);
                    border: 1px solid var(--dbz-card-border);
                    border-radius: 14px;
                    overflow: hidden;
                    transition: border-color 0.2s ease;
                }

                #dbz-faq-hub .faq-trigger {
                    width: 100%;
                    padding: 16px 20px;
                    text-align: left;
                    background: transparent;
                    border: none;
                    color: var(--dbz-text-main);
                    font-size: 0.95rem;
                    font-weight: 700;
                    cursor: pointer;
                    display: flex;
                    justify-content: space-between;
                    align-items: center;
                    gap: 15px;
                }

                #dbz-faq-hub .faq-icon {
                    font-size: 0.75rem;
                    color: var(--dbz-text-muted);
                    transition: transform 0.3s cubic-bezier(0.4, 0, 0.2, 1);
                    flex-shrink: 0;
                }

                #dbz-faq-hub .faq-item.open {
                    border-color: rgba(217, 70, 239, 0.25);
                }

                #dbz-faq-hub .faq-item.open .faq-icon {
                    transform: rotate(180deg);
                    color: var(--dbz-accent-neon);
                }

                #dbz-faq-hub .faq-content {
                    max-height: 0;
                    overflow: hidden;
                    transition: max-height 0.3s cubic-bezier(0.4, 0, 0.2, 1);
                    background: rgba(0, 0, 0, 0.15);
                }

                #dbz-faq-hub .faq-content-inner {
                    padding: 16px 20px;
                    font-size: 0.88rem;
                    line-height: 1.5;
                    color: var(--dbz-text-muted);
                    border-top: 1px solid rgba(255, 255, 255, 0.02);
                }

                @keyframes dbzFadeIn {
                    from { opacity: 0; transform: translateY(6px); }
                    to { opacity: 1; transform: translateY(0); }
                }
            </style>

            <h2>Frequently Asked Questions</h2>

            <div class="category-slider" id="dbz-faq-cats">
                <button class="cat-btn active" onclick="switchFaqCategory('general')">General Portal</button>
                <button class="cat-btn" onclick="switchFaqCategory('ehub')">Ehub Streaming</button>
                <button class="cat-btn" onclick="switchFaqCategory('resources')">Creative Assets</button>
            </div>

            <div class="faq-wrapper active" id="faq-general">
                <div class="faq-item">
                    <button class="faq-trigger" onclick="toggleFaqAccordion(this, 'What is the DeBeatzGH workspace hub?')">
                        <span>What is the DeBeatzGH workspace hub?</span>
                        <span class="faq-icon">▼</span>
                    </button>
                    <div class="faq-content"><div class="faq-content-inner"></div></div>
                </div>
                <div class="faq-item">
                    <button class="faq-trigger" onclick="toggleFaqAccordion(this, 'How do I submit forms via GitHub pages safely?')">
                        <span>How do I submit forms via GitHub pages safely?</span>
                        <span class="faq-icon">▼</span>
                    </button>
                    <div class="faq-content"><div class="faq-content-inner"></div></div>
                </div>
            </div>

            <div class="faq-wrapper" id="faq-ehub">
                <div class="faq-item">
                    <button class="faq-trigger" onclick="toggleFaqAccordion(this, 'Where can I find the official music countdown charts?')">
                        <span>Where can I find the official music countdown charts?</span>
                        <span class="faq-icon">▼</span>
                    </button>
                    <div class="faq-content"><div class="faq-content-inner"></div></div>
                </div>
                <div class="faq-item">
                    <button class="faq-trigger" onclick="toggleFaqAccordion(this, 'Can I integrate the floating Ehub widget into my blog?')">
                        <span>Can I integrate the floating Ehub widget into my blog?</span>
                        <span class="faq-icon">▼</span>
                    </button>
                    <div class="faq-content"><div class="faq-content-inner"></div></div>
                </div>
            </div>

            <div class="faq-wrapper" id="faq-resources">
                <div class="faq-item">
                    <button class="faq-trigger" onclick="toggleFaqAccordion(this, 'Are the blogger templates free to modify?')">
                        <span>Are the blogger templates free to modify?</span>
                        <span class="faq-icon">▼</span>
                    </button>
                    <div class="faq-content"><div class="faq-content-inner"></div></div>
                </div>
            </div>

            <script>
                // Tab Switch Engine
                function switchFaqCategory(catId) {
                    document.querySelectorAll('#dbz-faq-hub .faq-wrapper').forEach(wrapper => {
                        wrapper.classList.remove('active');
                    });
                    document.querySelectorAll('#dbz-faq-hub .cat-btn').forEach(btn => {
                        btn.classList.remove('active');
                    });

                    document.getElementById(`faq-${catId}`).classList.add('active');
                    
                    const activeBtn = Array.from(document.querySelectorAll('#dbz-faq-hub .cat-btn')).find(btn => {
                        return btn.getAttribute('onclick').includes(catId);
                    });
                    if (activeBtn) {
                        activeBtn.classList.add('active');
                        activeBtn.scrollIntoView({ behavior: 'smooth', block: 'nearest', inline: 'center' });
                    }
                }

                // Lazy-Loading Accordion Logic Engine
                function toggleFaqAccordion(triggerElement, questionText) {
                    const faqItem = triggerElement.parentElement;
                    const contentPane = faqItem.querySelector('.faq-content');
                    const innerTextNode = faqItem.querySelector('.faq-content-inner');

                    if (!innerTextNode.innerHTML || innerTextNode.innerHTML.trim() === "") {
                        innerTextNode.innerHTML = fetchLazyFaqData(questionText);
                    }

                    const currentWrapper = faqItem.parentElement;
                    currentWrapper.querySelectorAll('.faq-item').forEach(item => {
                        if (item !== faqItem) {
                            item.classList.remove('open');
                            item.querySelector('.faq-content').style.maxHeight = null;
                        }
                    });

                    if (faqItem.classList.contains('open')) {
                        faqItem.classList.remove('open');
                        contentPane.style.maxHeight = null;
                    } else {
                        faqItem.classList.add('open');
                        contentPane.style.maxHeight = contentPane.scrollHeight + "px";
                    }
                }

                function fetchLazyFaqData(question) {
                    const dictionary = {
                        "What is the DeBeatzGH workspace hub?": "The DeBeatzGH workspace hub is a unified dashboard designed to catalog tools, widgets, entertainment pipelines, and custom API interfaces for creators, developers, and platform managers.",
                        "How do I submit forms via GitHub pages safely?": "Our system integrates lightweight sandboxed oembed environments. Your form fields render lazily inside designated sandboxes, bypassing raw infrastructure processing for maximum data compliance.",
                        "Where can I find the official music countdown charts?": "All digital entertainment updates are broadcast live inside the Ehub portal stream. Simply deploy the layout toggle widget or launch our system carousel overlays to view updated ranks.",
                        "Can I integrate the floating Ehub widget into my</script></div></div></!doctype>



<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Business Tools FAQ Hub</title>

<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">

<style>
*{
  margin:0;
  padding:0;
  box-sizing:border-box;
}

body{
  font-family:'Poppins',sans-serif;
  background:#07111f;
  color:#fff;
  overflow-x:hidden;
}

/* HERO */
.hero{
  padding:70px 20px 50px;
  text-align:center;
  background:
  linear-gradient(rgba(4,9,20,.8),rgba(4,9,20,.9)),
  url('https://images.unsplash.com/photo-1520607162513-77705c0f0d4a?q=80&w=1200&auto=format&fit=crop') center/cover;
}

.hero h1{
  font-size:2.4rem;
  line-height:1.2;
  margin-bottom:18px;
}

.hero p{
  max-width:900px;
  margin:auto;
  color:#d7d7d7;
  line-height:1.8;
}

.hero-btns{
  margin-top:28px;
  display:flex;
  gap:15px;
  justify-content:center;
  flex-wrap:wrap;
}

.hero-btns a{
  text-decoration:none;
  padding:14px 22px;
  border-radius:50px;
  font-weight:600;
  transition:.3s;
}

.btn-primary{
  background:#00d4ff;
  color:#07111f;
}

.btn-secondary{
  border:1px solid #00d4ff;
  color:#00d4ff;
}

.hero-btns a:hover{
  transform:translateY(-4px);
}

/* SEARCH */
.search-wrap{
  padding:25px 20px;
  max-width:1100px;
  margin:auto;
}

.search-box{
  width:100%;
  padding:16px 20px;
  border:none;
  border-radius:18px;
  background:#111d2f;
  color:#fff;
  font-size:1rem;
  outline:none;
}

/* FAQ */
.container{
  max-width:1100px;
  margin:auto;
  padding:20px;
}

.section-title{
  font-size:1.6rem;
  margin-bottom:20px;
  color:#00d4ff;
}

.faq{
  display:grid;
  gap:18px;
}

.faq-item{
  background:#101a2c;
  border-radius:18px;
  overflow:hidden;
  border:1px solid rgba(255,255,255,.05);
  transition:.3s;
}

.faq-item:hover{
  transform:translateY(-4px);
}

.faq-question{
  width:100%;
  background:none;
  border:none;
  color:#fff;
  padding:22px;
  text-align:left;
  font-size:1rem;
  font-weight:600;
  cursor:pointer;
  display:flex;
  justify-content:space-between;
  align-items:center;
}

.faq-question span{
  color:#00d4ff;
  font-size:1.4rem;
}

.faq-answer{
  max-height:0;
  overflow:hidden;
  transition:max-height .4s ease;
  padding:0 22px;
}

.faq-answer-content{
  padding-bottom:22px;
  color:#d7d7d7;
  line-height:1.9;
}

.faq-answer ul{
  margin-top:10px;
  padding-left:20px;
}

.faq-answer li{
  margin-bottom:12px;
}

/* TOOL CARDS */
.tool-grid{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(220px,1fr));
  gap:18px;
  margin-top:30px;
}

.tool-card{
  background:#101a2c;
  padding:22px;
  border-radius:18px;
  border:1px solid rgba(255,255,255,.06);
  transition:.3s;
}

.tool-card:hover{
  transform:translateY(-6px);
}

.tool-card h3{
  margin-bottom:10px;
  color:#00d4ff;
}

.tool-card p{
  color:#d5d5d5;
  line-height:1.7;
  font-size:.95rem;
}

/* CTA */
.cta{
  margin:70px 20px;
  padding:40px 25px;
  border-radius:24px;
  background:linear-gradient(135deg,#00d4ff,#3a47d5);
  text-align:center;
}

.cta h2{
  margin-bottom:15px;
  color:#fff;
}

.cta p{
  max-width:900px;
  margin:auto;
  line-height:1.8;
}

.cta a{
  margin-top:22px;
  display:inline-block;
  background:#fff;
  color:#111;
  padding:14px 22px;
  border-radius:50px;
  text-decoration:none;
  font-weight:600;
}

/* FOOTER */
footer{
  text-align:center;
  padding:30px 20px;
  color:#a7a7a7;
}

/* LAZY LOAD */
.lazy-section{
  opacity:0;
  transform:translateY(40px);
  transition:1s;
}

.lazy-section.show{
  opacity:1;
  transform:translateY(0);
}

/* MOBILE */
@media(max-width:768px){

.hero h1{
  font-size:1.8rem;
}

.section-title{
  font-size:1.3rem;
}

}
</style>
</head>

<body>

<!-- HERO -->
<section class="hero">
  <h1>Best Business Tools & Productivity Resources</h1>

  <p>
    Discover powerful business tools, productivity apps, collaboration platforms,
    marketing solutions, HR systems, AI tools, automation resources, and startup ideas
    designed to help businesses grow faster and improve customer experience.
  </p>

  <div class="hero-btns">
    <a href="#faq" class="btn-primary">Browse Tools</a>
    <a href="#startup" class="btn-secondary">Get Started</a>
  </div>
</section>

<!-- SEARCH -->
<div class="search-wrap">
  <input type="text" id="searchInput" class="search-box"
  placeholder="Search FAQ, tools, startups, CRM, productivity..." />
</div>

<!-- FAQ -->
<div class="container">

  <h2 class="section-title">Frequently Asked Questions</h2>

  <div class="faq" id="faq">

    <!-- ITEM -->
    <div class="faq-item lazy-section">
      <button class="faq-question">
        What are productivity tools?
        <span>+</span>
      </button>

      <div class="faq-answer">
        <div class="faq-answer-content">
          Productivity tools are software applications designed to help individuals and teams organise tasks, manage time, and increase efficiency in work or personal life.

          <br><br>

          These apps streamline workflows, improve collaboration, optimise resource usage, and enhance customer service experiences for startups and businesses.
        </div>
      </div>
    </div>

    <!-- ITEM -->
    <div class="faq-item lazy-section">
      <button class="faq-question">
        Best Task Management Tools
        <span>+</span>
      </button>

      <div class="faq-answer">
        <div class="faq-answer-content">

          <ul>
            <li><strong>Todoist</strong> — Organise tasks and priorities efficiently.</li>
            <li><strong>Trello</strong> — Visual project boards and workflow tracking.</li>
            <li><strong>Asana</strong> — Team collaboration and project management.</li>
            <li><strong>Notion</strong> — Workspace for notes, tasks, and databases.</li>
            <li><strong>Monday.com</strong> — Workflow automation and project planning.</li>
          </ul>

        </div>
      </div>
    </div>

    <!-- ITEM -->
    <div class="faq-item lazy-section">
      <button class="faq-question">
        Best Communication & Collaboration Tools
        <span>+</span>
      </button>

      <div class="faq-answer">
        <div class="faq-answer-content">

          <ul>
            <li><strong>Slack</strong> — Real-time team messaging.</li>
            <li><strong>Microsoft Teams</strong> — Meetings and workplace collaboration.</li>
            <li><strong>Zoom</strong> — Video conferencing and webinars.</li>
            <li><strong>Google Workspace</strong> — Docs, Drive, Meet, and productivity tools.</li>
            <li><strong>Discord</strong> — Community and business communication platform.</li>
          </ul>

        </div>
      </div>
    </div>

    <!-- ITEM -->
    <div class="faq-item lazy-section">
      <button class="faq-question">
        Best Marketing & Sales Tools
        <span>+</span>
      </button>

      <div class="faq-answer">
        <div class="faq-answer-content">

          <ul>
            <li><strong>HubSpot</strong> — CRM and marketing automation.</li>
            <li><strong>Salesforce</strong> — Enterprise customer management system.</li>
            <li><strong>MailChimp</strong> — Email marketing campaigns.</li>
            <li><strong>SEMrush</strong> — SEO and keyword optimisation.</li>
            <li><strong>Hootsuite</strong> — Social media scheduling and analytics.</li>
          </ul>

        </div>
      </div>
    </div>

    <!-- ITEM -->
    <div class="faq-item lazy-section">
      <button class="faq-question">
        Accounting & Financial Tools
        <span>+</span>
      </button>

      <div class="faq-answer">
        <div class="faq-answer-content">

          <ul>
            <li><strong>QuickBooks</strong> — Business accounting software.</li>
            <li><strong>Xero</strong> — Cloud accounting and bookkeeping.</li>
            <li><strong>FreshBooks</strong> — Invoicing and expense tracking.</li>
            <li><strong>Expensify</strong> — Expense management platform.</li>
            <li><strong>Harvest</strong> — Time tracking and invoicing.</li>
          </ul>

        </div>
      </div>
    </div>

    <!-- ITEM -->
    <div class="faq-item lazy-section">
      <button class="faq-question">
        HR & Employee Management Tools
        <span>+</span>
      </button>

      <div class="faq-answer">
        <div class="faq-answer-content">

          <ul>
            <li><strong>BambooHR</strong> — Employee onboarding and HR.</li>
            <li><strong>Workday</strong> — HR and workforce management.</li>
            <li><strong>Greenhouse</strong> — Recruitment management.</li>
            <li><strong>15Five</strong> — Performance reviews and feedback.</li>
            <li><strong>Zenefits</strong> — HR automation and benefits.</li>
          </ul>

        </div>
      </div>
    </div>

    <!-- ITEM -->
    <div class="faq-item lazy-section">
      <button class="faq-question">
        Data Analysis & Visualisation Tools
        <span>+</span>
      </button>

      <div class="faq-answer">
        <div class="faq-answer-content">

          <ul>
            <li><strong>Power BI</strong> — Business intelligence dashboards.</li>
            <li><strong>Tableau</strong> — Interactive visual analytics.</li>
            <li><strong>Google Data Studio</strong> — Free reporting dashboards.</li>
            <li><strong>Excel</strong> — Spreadsheet analysis and calculations.</li>
            <li><strong>Plotly</strong> — Interactive chart creation.</li>
          </ul>

        </div>
      </div>
    </div>

    <!-- ITEM -->
    <div class="faq-item lazy-section">
      <button class="faq-question">
        AI Startup Ideas & Automation
        <span>+</span>
      </button>

      <div class="faq-answer">
        <div class="faq-answer-content">

          Tired of cookie-cutter startups? Build your own empire with AI tools and automation.

          <br><br>

          Create:
          <ul>
            <li>AI-powered eCommerce websites</li>
            <li>Android and Web Apps</li>
            <li>Customer service chatbots</li>
            <li>AI business assistants</li>
            <li>Automated marketing systems</li>
          </ul>

          You no longer need advanced coding skills to launch powerful online businesses.
        </div>
      </div>
    </div>

  </div>

  <!-- TOOL CARDS -->
  <div class="tool-grid lazy-section">

    <div class="tool-card">
      <h3>Hosting & Domains</h3>
      <p>
        Domain registration, cloud hosting, VPS servers,
        WordPress hosting, and website deployment tools.
      </p>
    </div>

    <div class="tool-card">
      <h3>E-commerce Tools</h3>
      <p>
        Astra, Ecwid, Take App, and dropshipping solutions
        for launching online stores quickly.
      </p>
    </div>

    <div class="tool-card">
      <h3>Affiliate Platforms</h3>
      <p>
        Adsterra, Spocket, Fiverr affiliate tools,
        CPM management, and monetisation systems.
      </p>
    </div>

    <div class="tool-card">
      <h3>Customer Service</h3>
      <p>
        LiveChat, WhatsApp commerce, CRM systems,
        and customer engagement widgets.
      </p>
    </div>

    <div class="tool-card">
      <h3>Creative Tools</h3>
      <p>
        Canva, Stylesi AI, Elfsight, and modern
        design platforms for business branding.
      </p>
    </div>

    <div class="tool-card">
      <h3>Business Forms & CRM</h3>
      <p>
        Jotform CRM, Viquote Canvas,
        automation forms, and workflow systems.
      </p>
    </div>

  </div>

</div>

<!-- CTA -->
<section class="cta lazy-section" id="startup">

  <h2>Build Your Startup With AI</h2>

  <p>
    AI is transforming businesses worldwide. Launch smarter startups,
    automate customer service, improve productivity, and create scalable
    digital products with powerful business tools and automation systems.
  </p>

  <a href="#">Browse Tools & Resources</a>

</section>

<!-- FOOTER -->
<footer>
  © 2026 Business Tools Hub • Productivity • AI • Startups • Automation
</footer>

<script>

/* FAQ TOGGLE */
document.querySelectorAll(".faq-question").forEach(btn => {

  btn.addEventListener("click", () => {

    const answer = btn.nextElementSibling;
    const icon = btn.querySelector("span");

    if(answer.style.maxHeight){
      answer.style.maxHeight = null;
      icon.textContent = "+";
    } else {
      answer.style.maxHeight = answer.scrollHeight + "px";
      icon.textContent = "−";
    }

  });

});

/* SEARCH FILTER */
const searchInput = document.getElementById("searchInput");

searchInput.addEventListener("keyup", function(){

  const filter = this.value.toLowerCase();
  const items = document.querySelectorAll(".faq-item");

  items.forEach(item => {

    const text = item.innerText.toLowerCase();

    if(text.includes(filter)){
      item.style.display = "block";
    } else {
      item.style.display = "none";
    }

  });

});

/* LAZY LOAD ANIMATION */
const lazySections = document.querySelectorAll(".lazy-section");

const observer = new IntersectionObserver(entries => {

  entries.forEach(entry => {

    if(entry.isIntersecting){
      entry.target.classList.add("show");
    }

  });

}, {
  threshold:0.1
});

lazySections.forEach(section => {
  observer.observe(section);
});

</script>

</body>
</html>





<style>
/* 1. RESET & VARIABLES */
:root {
  --dd-bg: #1a1c1e; /* Deep Dark */
  --dd-text: #f0f6fc;
  --dd-accent: #1877F2; /* Facebook Blue */
  --dd-border: rgba(240, 246, 252, 0.1);
  --dd-font: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
}

/* 2. MAIN CONTAINER (SLIM-FIT & FLOATING) */
.dd-banner-container {
  position: fixed;
  bottom: 10px; /* Slight offset for modern float */
  left: 50%;
  transform: translateX(-50%);
  width: 92%;
  max-width: 900px;
  height: 40px; /* Slim height */
  background-color: var(--dd-bg);
  background-image: radial-gradient(at 10% 10%, rgba(24, 119, 242, 0.15) 0px, transparent 50%),
                    radial-gradient(at 90% 90%, rgba(240, 246, 252, 0.05) 0px, transparent 50%);
  border: 1px solid var(--dd-border);
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 10px 0 15px;
  z-index: 999999; /* Ensure topmost */
  box-shadow: 0 10px 25px rgba(0,0,0,0.4);
  overflow: hidden;
  transition: all 0.3s ease;
  font-family: var(--dd-font);
}

.dd-banner-container:hover {
  border-color: var(--dd-accent);
  box-shadow: 0 10px 30px rgba(24, 119, 242, 0.2);
  transform: translateX(-50%) translateY(-2px);
}

/* 3. LEFT SECTION (BRAND & SLIDER) */
.dd-left {
  display: flex;
  align-items: center;
  gap: 12px;
  flex: 1;
  overflow: hidden;
}

.dd-brand {
  color: var(--dd-accent);
  font-size: 16px;
  display: flex;
  align-items: center;
}

/* AUTO-SLIDE TEXT LOGIC */
.dd-slider-box {
  flex: 1;
  height: 20px;
  overflow: hidden;
  position: relative;
}

.dd-slider-content {
  display: flex;
  flex-direction: column;
  animation: ddTextSlide 12s cubic-bezier(0.645, 0.045, 0.355, 1) infinite;
}

.dd-slider-content span {
  height: 20px;
  font-size: 11px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 1px;
  color: var(--dd-text);
  display: flex;
  align-items: center;
  white-space: nowrap;
}

.dd-highlight { color: var(--dd-accent); font-weight: 800; }

@keyframes ddTextSlide {
  0%, 20% { transform: translateY(0); }             /* Intro */
  25%, 45% { transform: translateY(-20px); }        /* Recommend 1 */
  50%, 70% { transform: translateY(-40px); }        /* Recommend 2 */
  75%, 95% { transform: translateY(-60px); }        /* Action */
  100% { transform: translateY(0); }                /* Reset loop */
}

/* 4. RIGHT SECTION (ACTION BUTTON) */
.dd-right {
  display: flex;
  align-items: center;
}

.dd-join-btn {
  background-color: var(--dd-accent);
  color: #ffffff;
  border: none;
  padding: 5px 12px;
  border-radius: 6px;
  font-size: 10px;
  font-weight: 800;
  text-transform: uppercase;
  letter-spacing: 1px;
  cursor: pointer;
  transition: all 0.2s ease;
  display: flex;
  align-items: center;
  gap: 6px;
  text-decoration: none;
}

.dd-join-btn:hover {
  background-color: #ffffff;
  color: #1877F2;
  transform: scale(1.05);
}

/* 5. MOBILE OPTIMIZATION */
@media (max-width: 600px) {
  .dd-banner-container { width: 96%; top: 5px; height: 36px; padding: 0 8px; }
  .dd-brand { font-size: 14px; }
  .dd-slider-content span { font-size: 9px; }
  .dd-join-btn { padding: 4px 8px; font-size: 9px; }
  .dd-btn-text { display: none; } /* Show only icon on mobile */
  .dd-join-btn i { font-size: 12px; margin: 0; }
}
</style>

<div class='dd-banner-container'>
  <div class='dd-left'>
    <div class='dd-brand'>
      <i class='fab fa-facebook-square'></i>
    </div>
    <div class='dd-slider-box'>
      <div class='dd-slider-content'>
        <span>Official Community: <strong class='dd-highlight'>&quot;Digital Dynamo&quot;</strong></span>
        <span>Recommended: A High-Performance Portal for AI Automation, ..</span>
        <span>Software Development, and Digital Strategy: Join the <strong class='dd-highlight'>Dynamo</strong> network.</span>
        <span>Action Required: Tap &#39;Chat with AI Bot &#39; to deepen Research.</span>
      </div>
    </div>
  </div>
  <div class='dd-right'>
    <a class='dd-join-btn' href='https://debeatzgh1.github.io/sales/' target='_blank'>
      <i class='fas fa-users'></i> <span class='dd-btn-text'>Contact support</span>
    </a>
  </div>
</div>

<script src='https://kit.fontawesome.com/0f6c123a31.js' crossorigin='anonymous'></script>





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
