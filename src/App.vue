<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue'

// ==========================================
// EDITABLE CONTENT
// ==========================================
const profile = ref({
  name: "Kenneth Lico",
  role: "BSIT Student | Frontend Dev",
  description: "Documenting my Bachelor of Science in Information Technology journey through clean code, minimalist design, and continuous learning.",
  pictureUrl: new URL('/public/images/me.jpg', import.meta.url).href,  
  email: "licokenneth11@gmail.com",
  github: "https://github.com/YuKennnn",
  linkedin: "https://www.linkedin.com/in/kenneth-lico-696165369/",
  facebook: "https://www.facebook.com/kenneth.lico.92/"
})

const skills = ref([
  'HTML5', 'CSS3', 'JavaScript', 'Vue.js', 'FastAPI', 'PHP', 'MySQL', 'Laravel', 'Dart', 'Firebase',
  'Node.js', 'Python', 'Git', 'Figma', 'UI/UX Design'
])

const projects = ref([
  // --- 1ST YEAR PROJECTS (7 items) ---
  {
    id: 1,
    year: '1st Year',
    title: 'Into the Woods',
    description: 'Short Film',
    image: new URL('../public/images/first-year/into-the-woods.jfif', import.meta.url).href,
    link: '#'
  },
  {
    id: 2,
    year: '1st Year',
    title: 'Hatid Sundo by Gimme 5',
    description: 'MTV Spoof',
    image: new URL('../public/images/first-year/hatid-sundo.jfif', import.meta.url).href,
    link: '#'
  },
  {
    id: 3,
    year: '1st Year',
    title: 'Photo Collage',
    description: 'Series Photography',
    image: new URL('../public/images/first-year/series-photography.png', import.meta.url).href,  
    link: '#'
  },
  {
    id: 4,
    year: '1st Year',
    title: 'CRUD Presentation',
    description: 'Operations for Money Laundering Tracker System',
    tech: ['Java'],
    image: new URL('../public/images/first-year/crud-gui.png', import.meta.url).href,
    link: '#'
  },
  {
    id: 5,
    year: '1st Year',
    title: 'Lifting GUI | CRUD Presentation',
    description: 'A Java Swing application with a clean interface to manage gym workout routines, demonstrating Create, Read, Update, Delete operations for exercise tracking.',
    tech: ['Java', 'Swing'],
    image: new URL('../public/images/first-year/lifting-gui.png', import.meta.url).href,
    link: '#'
  },
  {
    id: 6,
    year: '1st Year',
    title: 'Hotel-Motel GUI | CRUD Presentation',
    description: 'A Java Swing application designed to manage hotel reservations, featuring a user-friendly interface for creating, reading, updating, and deleting booking records.',
    tech: ['Java', 'Swing'],
    image: new URL('../public/images/first-year/hotel-motel-gui.png', import.meta.url).href,
    link: '#'
  },
  {
    id: 7,
    year: '1st Year',
    title: 'DNSC Shop Management System | CRUD Presentation',
    description: 'A Java Swing Final Project application that showcases a simple shop management system for Davao del Norte State College, allowing users to perform CRUD operations on products, customers, and orders through an intuitive graphical interface.',
    tech: ['Java', 'Swing'],
    image: new URL('../public/images/first-year/dsms-gui.png', import.meta.url).href,
    link: 'https://github.com/YuKennnn/DNSC_SMS'
  },

  // --- 2ND YEAR PROJECTS (3 items) ---
  {
    id: 8,
    year: '2nd Year',
    title: 'Honey Dias Website',
    description: 'A responsive e-commerce website built for a local honey business, featuring product listings, shopping cart functionality, and a clean user interface.',
    tech: ['HTML', 'CSS', 'JavaScript', 'Bootstrap'],
    image: new URL('../public/images/second-year/honey-dias-group.jpg', import.meta.url).href,
    link: 'https://panzerweb.github.io/HoneyDias/'
  },
  {
    id: 9,
    year: '2nd Year',
    title: 'Locker Management System | ZakkSpace Team',
    description: 'A Laravel-based web application designed to manage locker rentals for Davao del Norte State College, featuring user authentication, locker availability tracking, and an admin dashboard for managing reservations.',
    tech: ['PHP', 'MySQL', 'Laravel', 'Bootstrap', 'JavaScript'],
    image: new URL('../public/images/second-year/zakkspace-locker.jpg', import.meta.url).href,
    link: 'https://github.com/YuKennnn/ZakkSpace-LMS-Updated'
  },
  {
    id: 10,
    year: '2nd Year',
    title: 'Peasy Builder Website',
    description: 'A website for computer hardware assembly services, showcasing a catalog of components, a custom PC builder tool, and an order form for customers to request builds based on their preferences.',
    tech: ['JavaScript', 'CSS', 'HTML', 'PHP', 'MySQL'],
    image: new URL('../public/images/second-year/peasy-system.jfif', import.meta.url).href,
    link: 'https://github.com/YuKennnn/PeasyShopBuilder'
  },

  // --- 3RD YEAR PROJECTS (5 items) ---
  {
    id: 11,
    year: '3rd Year',
    title: 'Attendance Tracker Application',
    description: 'A flutter-based mobile application designed to streamline attendance management for educational institutions, featuring QR code scanning, real-time attendance updates, and a user-friendly interface for both students and teachers.',
    tech: ['Flutter', 'Dart', 'Firebase'],
    image: new URL('../public/images/third-year/atansdance-app.jfif', import.meta.url).href,
    link: 'https://github.com/YuKennnn/AtansDanceApp'
  },
  {
    id: 12,
    year: '3rd Year',
    title: 'Intrusion Detection IoT-Based System',
    description: 'A real-time monitoring system utilizing IoT sensors to detect intrusions for farmers, sending alerts through sms notifications with a secure hardware-software integrated approach.',
    tech: ['IoT', 'Arduino', 'Arduino IDE'],
    image: new URL('../public/images/third-year/IoT-intruder-detection-system.jpg', import.meta.url).href,
    link: '#'
  },
  {
    id: 13,
    year: '3rd Year',
    title: 'Lakbay+',
    description: 'Lakbay+ is your interactive travel canvas. We analyze commute costs, split expenses among friends, and calculate your daily savings target automatically.',
    tech: ['Vue Native', 'Tailwind', 'Capacitor'],
    image: new URL('../public/images/third-year/lakbay-plus.jfif', import.meta.url).href,
    link: 'https://github.com/YuKennnn/lakbay-web'
  },
  {
    id: 14,
    year: '3rd Year',
    title: 'Secure System|Cyber Security Final Project',
    description: 'A Hosted Cyber Security project focused on building a secure API Gateway and login system implementing Hash, Salt and Pepper techniques for password security, along with JSON Web Tokens for session management and authentication.',
    tech: ['Vue.js', 'FastAPI', 'bcrypt', 'Render', 'Vercel'],
    image: new URL('../public/images/third-year/cyber-final-project.jfif', import.meta.url).href,
    link: 'https://cyber-security-final-project-fronte.vercel.app/'
  },
  {
    id: 15,
    year: '3rd Year',
    title: 'CyberMorph | Capstone Project',
    description: 'A Cyber Security Game designed to teach users about common vulnerabilities and attack vectors through interactive challenges, utilizing a secure API Gateway and login system with Dashboard analytics to track user progress and performance.',
    tech: ['Vue.js', 'FastAPI', 'bcrypt', 'Render', 'Vercel', 'Godot Engine', 'Aseprite', 'Figma', 'Canva'],
    image: new URL('../public/images/third-year/capstone-project.jfif', import.meta.url).href,
    link: 'https://cyber-morph-portal.vercel.app/portal/educator'
  },
])

// ==========================================
// FORM STATE LOGIC
// ==========================================
const formState = ref({
  name: '',
  email: '',
  message: ''
})

const handleFormSubmit = (e) => {
  e.preventDefault();
  alert(`Thanks for reaching out, ${formState.value.name}! I will get back to you soon.`);
  formState.value = { name: '', email: '', message: '' };
}

// ==========================================
// TAB LOGIC & FILTERING
// ==========================================
const tabs = ['All', '1st Year', '2nd Year', '3rd Year', '4th Year']
const activeTab = ref('All')

const filteredProjects = computed(() => {
  if (activeTab.value === 'All') {
    return projects.value
  }
  return projects.value.filter(project => project.year === activeTab.value)
})

// ==========================================
// JS ANIMATIONS & LOGIC
// ==========================================

// 1. Dynamic Scroll Progress & Nav Behavior
const scrollProgress = ref(0)
const isNavScrolled = ref(false)

const handleScroll = () => {
  const scrollTop = window.scrollY || document.documentElement.scrollTop;
  const docHeight = document.documentElement.scrollHeight - document.documentElement.clientHeight;
  
  // Calculate Window Progress Line Width
  scrollProgress.value = docHeight > 0 ? (scrollTop / docHeight) * 100 : 0;
  
  // Shrink/Blur Nav state
  isNavScrolled.value = scrollTop > 60;
}

// 2. Interactive 3D Card Perspective Tilt Effect
const handleTilt = (e) => {
  const el = e.currentTarget;
  const rect = el.getBoundingClientRect();
  const x = e.clientX - rect.left; 
  const y = e.clientY - rect.top;  
  
  const centerX = rect.width / 2;
  const centerY = rect.height / 2;
  
  // Maximum rotation parameters
  const rotateX = ((y - centerY) / centerY) * -8;
  const rotateY = ((x - centerX) / centerX) * 8;
  
  el.style.setProperty('--rotate-x', `${rotateX}deg`);
  el.style.setProperty('--rotate-y', `${rotateY}deg`);
}

const resetTilt = (e) => {
  const el = e.currentTarget;
  el.style.setProperty('--rotate-x', `0deg`);
  el.style.setProperty('--rotate-y', `0deg`);
}

// 3. Automated JS Typewriter Array Logic
const displayedRole = ref('');
const fullRole = profile.value.role;

const scrollTo = (id) => {
  const element = document.getElementById(id)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll);

  // Trigger Typewriter execution logic after 800ms
  setTimeout(() => {
    let i = 0;
    const typeWriter = () => {
      if (i < fullRole.length) {
        displayedRole.value += fullRole.charAt(i);
        i++;
        setTimeout(typeWriter, 50); 
      }
    };
    typeWriter();
  }, 800);

  // Intersection Observer for slide reveal components
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting) {
        entry.target.classList.add('is-visible')
      }
    })
  }, { 
    threshold: 0.1, 
    rootMargin: "0px 0px -50px 0px" 
  })

  document.querySelectorAll('.animate-on-scroll').forEach((el) => {
    observer.observe(el)
  })
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll);
})
</script>

<template>
  <div class="portfolio-container fade-in-load">
    
    <div class="scroll-progress-bar" :style="{ width: scrollProgress + '%' }"></div>

    <nav class="navbar slide-down" :class="{ 'navbar-scrolled': isNavScrolled }">
      <div class="nav-content">
        <div class="logo">YuKen</div>
        <div class="nav-links">
          <button @click="scrollTo('home')">Home</button>
          <button @click="scrollTo('about')">About</button>
          <button @click="scrollTo('projects')">Projects</button>
          <button @click="scrollTo('contact')">Contact</button>
        </div>
      </div>
    </nav>

    <section id="home" class="hero">
      <div class="section-container hero-container">
        <div class="hero-text-content">
          <p class="greeting animate-on-scroll reveal-up" style="transition-delay: 0.1s">Hello, I'm</p>
          <h1 class="hero-name animate-on-scroll reveal-up" style="transition-delay: 0.2s">{{ profile.name }}</h1>
          
          <h2 class="hero-role animate-on-scroll reveal-up" style="transition-delay: 0.3s">
            {{ displayedRole }}<span class="blinking-cursor">|</span>
          </h2>
          
          <p class="hero-desc animate-on-scroll reveal-up" style="transition-delay: 0.4s">{{ profile.description }}</p>
          <div class="hero-actions animate-on-scroll reveal-up" style="transition-delay: 0.5s">
            <button class="btn-primary" @click="scrollTo('projects')">Explore Work</button>
            <button class="btn-secondary" @click="scrollTo('about')">About Me</button>
          </div>
        </div>
        
        <div 
          class="hero-image-container animate-on-scroll reveal-scale tilt-element" 
          style="transition-delay: 0.4s"
          @mousemove="handleTilt"
          @mouseleave="resetTilt"
        >
          <img :src="profile.pictureUrl" alt="Profile Picture" class="profile-pic" />
          <div class="hero-image-backdrop"></div>
        </div>
      </div>
    </section>

    <section id="about" class="about-section animate-on-scroll reveal-up">
      <div class="section-container">
        <h3 class="section-title animate-on-scroll reveal-up">My Journey</h3>
        <p class="about-text animate-on-scroll reveal-up">
          I am a passionate BSIT student. My journey started with a curiosity about how websites work, which quickly evolved into a love for frontend development. I believe in writing clean code and designing intuitive, user-centric interfaces. When I'm not coding for my classes, you can find me exploring new web frameworks or designing UI mockups.
        </p>
        
        <h4 class="skills-title animate-on-scroll reveal-up">Tech Stack</h4>
        <div class="skills-grid">
          <span 
            v-for="(skill, index) in skills" 
            :key="skill" 
            class="skill-pill animate-on-scroll reveal-up"
            :style="`transition-delay: ${index * 0.05}s`"
          >
            {{ skill }}
          </span>
        </div>
      </div>
    </section>

    <section id="projects" class="projects-section">
      <div class="section-container">
        <h3 class="section-title animate-on-scroll reveal-up">School Projects</h3>
        
        <div class="project-tabs animate-on-scroll reveal-up">
          <button 
            v-for="tab in tabs" 
            :key="tab"
            @click="activeTab = tab"
            :class="['tab-btn', { active: activeTab === tab }]"
          >
            {{ tab }}
          </button>
        </div>

        <TransitionGroup appear name="project-fade" tag="div" class="projects-grid">
          <div 
            v-for="project in filteredProjects" 
            :key="project.id" 
            class="project-card tilt-element"
            @mousemove="handleTilt"
            @mouseleave="resetTilt"
          >
            <div class="project-image">
              <img :src="project.image" :alt="project.title" />
              <span class="year-badge">{{ project.year }}</span>
            </div>
            <div class="project-content">
              <h4>{{ project.title }}</h4>
              <p>{{ project.description }}</p>
              <div class="tech-stack" v-if="project.tech">
                <span v-for="tech in project.tech" :key="tech" class="tech-tag">{{ tech }}</span>
              </div>
              <a :href="project.link" class="project-link">View Project &rarr;</a>
            </div>
          </div>
        </TransitionGroup>

        <div v-if="filteredProjects.length === 0" class="empty-state">
          <p>No projects documented for this year yet.</p>
        </div>
      </div>
    </section>

    <section id="contact" class="contact-section">
      <div class="section-container">
        <h3 class="section-title animate-on-scroll reveal-up">Let's Connect.</h3>
        <p class="contact-subtitle animate-on-scroll reveal-up">Currently open to internships, freelance opportunities, and collaborative projects. Reach out and let's talk code.</p>
        
        <div class="contact-grid">
          
          <div class="contact-form-container animate-on-scroll reveal-up" style="transition-delay: 0.1s">
            <form @submit="handleFormSubmit" class="contact-form">
              <div class="form-group">
                <label for="name">Your Name</label>
                <input type="text" id="name" v-model="formState.name" required placeholder="Bronny James">
              </div>
              
              <div class="form-group">
                <label for="email">Your Email</label>
                <input type="email" id="email" v-model="formState.email" required placeholder="bronny.james@gmail.com">
              </div>
              
              <div class="form-group">
                <label for="message">Message</label>
                <textarea id="message" v-model="formState.message" required rows="5" placeholder="How can we work together?"></textarea>
              </div>
              
              <button type="submit" class="submit-btn">Send Message &rarr;</button>
            </form>
          </div>

          <div class="contact-info-container animate-on-scroll reveal-up" style="transition-delay: 0.2s">
            <div class="info-block">
              <h4>Direct Email</h4>
              <a :href="'mailto:' + profile.email" class="direct-link">{{ profile.email }}</a>
            </div>
            
            <div class="info-block">
              <h4>Location</h4>
              <p>Panabo City, Davao Region, Philippines</p>
            </div>

            <div class="info-block">
              <h4>Social Profiles</h4>
              <div class="social-links-modern">
                <a :href="profile.github" target="_blank" rel="noopener noreferrer">GitHub</a>
                <a :href="profile.linkedin" target="_blank" rel="noopener noreferrer">LinkedIn</a>
              </div>
            </div>
          </div>
          
        </div>
      </div>
    </section>

    <footer class="footer">
      <div class="footer-content">
        <div class="footer-bottom">
          <p class="copyright">© 2026 {{ profile.name }}. All Rights Reserved.</p>
          <p class="craft-note"></p>
        </div>
      </div>
    </footer>
  </div>
</template>

<style>
/* Minimalist Theme Framework: Pink (Primary) & White (Secondary)
*/
:root {
  /* Core Pink Palettes */
  --primary-pink: #ff2a6d;
  --primary-pink-hover: #e0225e;
  --primary-pink-light: #fff0f4;
  
  /* White Architectural Ecosystem */
  --bg-color: #ffffff; 
  --bg-card: #fdfdfd;
  --bg-alt: #fcfcfc;
  
  /* Black Typographical Accents */
  --text-main: #1d1d1f; 
  --text-muted: #6e6e73;
  
  --border-light: #f2f2f7;
  --nav-bg: rgba(255, 255, 255, 0.85);
  
  /* Apple Easing Rules */
  --ease-spring: cubic-bezier(0.16, 1, 0.3, 1); 
  --ease-out: cubic-bezier(0.25, 1, 0.5, 1);
}

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: -apple-system, BlinkMacSystemFont, "SF Pro Display", "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
  background-color: var(--bg-color);
  color: var(--text-main);
  line-height: 1.5;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

/* ==========================================
   ANIMATION INTERACTION LAYER
   ========================================== */

/* JS Scroll Progress Tracking Bar */
.scroll-progress-bar {
  position: fixed;
  top: 0;
  left: 0;
  height: 3px;
  background-color: var(--primary-pink);
  z-index: 1000;
  transition: width 0.1s ease-out;
  box-shadow: 0 0 10px rgba(255, 42, 109, 0.5);
}

/* JS Automated Typewriter blinking cursor module */
.blinking-cursor {
  font-weight: 300;
  color: var(--primary-pink);
  animation: blink 1s step-end infinite;
}

@keyframes blink {
  from, to { opacity: 1; }
  50% { opacity: 0; }
}

.fade-in-load {
  animation: fadeIn 1s var(--ease-out) forwards;
}

.slide-down {
  animation: slideDown 0.8s var(--ease-spring) forwards;
}

.reveal-up {
  opacity: 0;
  transform: translateY(40px);
  transition: opacity 0.8s var(--ease-spring), transform 0.8s var(--ease-spring);
}

.reveal-scale {
  opacity: 0;
  transform: scale(0.9);
  transition: opacity 0.8s var(--ease-spring), transform 1s var(--ease-spring);
}

.is-visible.reveal-up {
  opacity: 1;
  transform: translateY(0);
}

.is-visible.reveal-scale {
  opacity: 1;
  transform: scale(1);
}

@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

@keyframes slideDown {
  from { transform: translateY(-100%); opacity: 0; }
  to { transform: translateY(0); opacity: 1; }
}

.project-fade-move,
.project-fade-enter-active,
.project-fade-leave-active {
  transition: all 0.5s var(--ease-spring);
}
.project-fade-enter-from,
.project-fade-leave-to {
  opacity: 0;
  transform: translateY(20px) scale(0.95);
}
.project-fade-leave-active {
  position: absolute;
}

/* JS Vector Matrix Tilt Element Rules */
.tilt-element {
  --rotate-x: 0deg;
  --rotate-y: 0deg;
  transform: perspective(1000px) rotateX(var(--rotate-x)) rotateY(var(--rotate-y));
  transition: transform 0.2s cubic-bezier(0.25, 1, 0.5, 1), box-shadow 0.3s ease, border-color 0.3s ease;
}

/* ==========================================
   LAYOUT DESIGN CORE
   ========================================== */
.portfolio-container {
  display: flex;
  flex-direction: column;
  overflow-x: hidden;
}

.section-title {
  font-size: 2.5rem;
  font-weight: 700;
  letter-spacing: -1px;
  margin-bottom: 2rem;
  text-align: center;
  color: var(--primary-pink); 
}

/* Navigation Framework */
.navbar {
  position: fixed;
  top: 0;
  width: 100%;
  background-color: transparent;
  z-index: 100;
  padding: 1.5rem 0;
  transition: padding 0.4s var(--ease-spring), background-color 0.4s var(--ease-out), border-bottom 0.4s ease;
}

.navbar-scrolled {
  background-color: var(--nav-bg);
  backdrop-filter: saturate(180%) blur(20px);
  -webkit-backdrop-filter: saturate(180%) blur(20px);
  border-bottom: 1px solid var(--border-light);
  padding: 1rem 0; 
}

.nav-content {
  max-width: 1100px;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 2rem;
}

.logo {
  font-weight: 800;
  font-size: 1.3rem;
  letter-spacing: -0.5px;
  color: var(--primary-pink);
}

.nav-links button {
  background: none;
  border: none;
  margin-left: 2rem;
  font-size: 0.9rem;
  font-weight: 600;
  color: var(--text-muted);
  cursor: pointer;
  transition: color 0.3s var(--ease-out);
}

.nav-links button:hover {
  color: var(--primary-pink);
}

section {
  padding: 8rem 2rem 5rem;
  display: flex;
  justify-content: center;
}

.section-container {
  max-width: 1100px;
  width: 100%;
}

/* Hero Elements */
.hero {
  min-height: 100vh;
  display: flex;
  align-items: center;
  background-color: var(--bg-alt);
}

.hero-container {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 4rem;
}

.hero-text-content {
  flex: 1;
}

.greeting {
  color: var(--primary-pink);
  font-weight: 700;
  font-size: 1rem;
  margin-bottom: 0.5rem;
  text-transform: uppercase;
  letter-spacing: 2px;
}

.hero-name {
  font-size: 4.5rem;
  font-weight: 800;
  letter-spacing: -2px;
  margin-bottom: 0.5rem;
  color: var(--text-main);
}

.hero-role {
  font-size: 2rem;
  color: var(--text-muted);
  font-weight: 500;
  letter-spacing: -0.5px;
  margin-bottom: 1.5rem;
  min-height: 2.5rem;
}

.hero-desc {
  font-size: 1.1rem;
  color: var(--text-main);
  opacity: 0.85;
  margin-bottom: 2.5rem;
  max-width: 500px;
  line-height: 1.6;
}

.hero-actions {
  display: flex;
  gap: 1rem;
}

.btn-primary, .btn-secondary {
  padding: 0.9rem 2rem;
  border-radius: 40px;
  font-size: 0.95rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.4s var(--ease-spring); 
}

.btn-primary {
  background-color: var(--primary-pink);
  color: white;
  border: 1px solid var(--primary-pink);
}

.btn-primary:hover {
  transform: translateY(-2px) scale(1.02);
  box-shadow: 0 10px 20px rgba(255, 42, 109, 0.2);
}

.btn-primary:active { transform: scale(0.98); }

.btn-secondary {
  background-color: transparent;
  color: var(--primary-pink);
  border: 1px solid var(--primary-pink);
}

.btn-secondary:hover {
  background-color: var(--primary-pink-light);
  transform: translateY(-2px);
}

.btn-secondary:active { transform: scale(0.98); }

.hero-image-container {
  flex: 1;
  display: flex;
  justify-content: center;
  position: relative;
}

.profile-pic {
  width: 320px;
  height: 320px;
  border-radius: 50%;
  object-fit: cover;
  z-index: 2;
  box-shadow: 0 20px 40px rgba(255, 42, 109, 0.1);
  border: 4px solid white;
}

.hero-image-backdrop {
  position: absolute;
  width: 320px;
  height: 320px;
  border-radius: 50%;
  background: linear-gradient(135deg, var(--primary-pink-light) 0%, var(--primary-pink) 100%);
  top: 15px;
  left: 50%;
  transform: translateX(-45%);
  z-index: 1;
  opacity: 0.6;
}

/* About Layout Modules */
.about-section {
  background-color: var(--bg-card);
}

.about-text {
  font-size: 1.2rem;
  color: var(--text-main);
  opacity: 0.9;
  text-align: center;
  max-width: 800px;
  margin: 0 auto 4rem;
  line-height: 1.8;
}

.skills-title {
  text-align: center;
  font-size: 1.2rem;
  font-weight: 700;
  color: var(--text-main);
  margin-bottom: 2rem;
}

.skills-grid {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 0.8rem;
}

.skill-pill {
  background-color: var(--bg-color);
  color: var(--primary-pink);
  padding: 0.6rem 1.4rem;
  border-radius: 20px;
  font-size: 0.95rem;
  font-weight: 600;
  border: 1px solid var(--primary-pink-light);
  transition: all 0.3s var(--ease-out);
}

.skill-pill:hover {
  border-color: var(--primary-pink);
  background-color: var(--primary-pink);
  color: white;
  transform: scale(1.05);
  box-shadow: 0 5px 15px rgba(255, 42, 109, 0.15);
}

/* Project Module Matrix */
.projects-section {
  background-color: var(--bg-alt);
}

.project-tabs {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 0.8rem;
  margin-bottom: 3.5rem;
}

.tab-btn {
  background: transparent;
  color: var(--text-muted);
  border: 1px solid var(--border-light);
  padding: 0.6rem 1.5rem;
  border-radius: 30px;
  font-size: 0.95rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s var(--ease-out);
}

.tab-btn:hover {
  color: var(--primary-pink);
  border-color: var(--primary-pink);
}

.tab-btn.active {
  background: var(--primary-pink);
  color: white;
  border-color: var(--primary-pink);
  box-shadow: 0 4px 10px rgba(255, 42, 109, 0.2);
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 2rem;
  position: relative; 
  min-height: 350px;
}

.project-card {
  background: linear-gradient(to bottom, var(--bg-card), #fffafc);
  border-radius: 20px;
  overflow: hidden;
  border: 1px solid rgba(255, 42, 109, 0.15);
  display: flex;
  flex-direction: column;
}

.project-card:hover {
  box-shadow: 0 30px 60px rgba(255, 42, 109, 0.1);
  border-color: var(--primary-pink);
  z-index: 10;
}

.project-image {
  position: relative;
  overflow: hidden; 
}

.project-image img {
  width: 100%;
  height: 220px;
  object-fit: cover;
  border-bottom: 1px solid var(--border-light);
  transition: transform 0.8s var(--ease-spring);
}

.year-badge {
  position: absolute;
  top: 1rem;
  left: 1rem;
  background-color: var(--primary-pink);
  color: white;
  padding: 0.4rem 1rem;
  border-radius: 20px;
  font-size: 0.75rem;
  font-weight: 700;
  box-shadow: 0 4px 10px rgba(255, 42, 109, 0.3);
  z-index: 2;
}

.project-content {
  padding: 2rem;
  display: flex;
  flex-direction: column;
  flex-grow: 1;
}

.project-content h4 {
  font-size: 1.3rem;
  font-weight: 700;
  color: var(--primary-pink); /* Pink title text */
  margin-bottom: 0.8rem;
  transition: color 0.3s var(--ease-out);
}

.project-card:hover .project-content h4 {
  color: var(--primary-pink-hover); 
}

.project-content p {
  color: var(--text-muted);
  font-size: 0.95rem;
  margin-bottom: 1.5rem;
  flex-grow: 1;
}

.tech-stack {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 1.5rem;
}

.tech-tag {
  font-size: 0.8rem;
  background-color: var(--primary-pink-light);
  padding: 0.3rem 0.8rem;
  border-radius: 12px;
  color: var(--primary-pink);
  font-weight: 600;
  border: 1px solid rgba(255, 42, 109, 0.2);
}

.project-link {
  text-decoration: none;
  color: var(--primary-pink);
  font-weight: 700;
  font-size: 0.95rem;
  align-self: flex-start;
  transition: transform 0.3s var(--ease-spring), opacity 0.3s var(--ease-out);
  display: inline-block;
}

.project-link:hover {
  opacity: 0.8;
  transform: translateX(4px); 
}

.empty-state { 
  text-align: center; 
  color: var(--text-muted); 
  padding: 3rem 0; 
  width: 100%; 
  grid-column: 1 / -1; 
}


/* ==========================================
   CONTACT SECTION STYLES
   ========================================== */
.contact-section {
  background-color: var(--bg-card);
  padding-bottom: 6rem;
}

.contact-subtitle {
  text-align: center;
  color: var(--text-muted);
  font-size: 1.1rem;
  max-width: 600px;
  margin: 0 auto 4rem;
}

.contact-grid {
  display: grid;
  grid-template-columns: 3fr 2fr;
  gap: 4rem;
  background-color: var(--bg-color);
  border-radius: 24px;
  padding: 3rem;
  border: 1px solid var(--border-light);
}

/* Contact Form */
.contact-form {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.form-group label {
  font-size: 0.9rem;
  font-weight: 600;
  color: var(--text-main);
}

.form-group input,
.form-group textarea {
  width: 100%;
  padding: 1rem;
  border-radius: 12px;
  border: 1px solid var(--border-light);
  background-color: var(--bg-card);
  color: var(--text-main);
  font-family: inherit;
  font-size: 1rem;
  transition: border-color 0.3s ease, box-shadow 0.3s ease;
}

.form-group input:focus,
.form-group textarea:focus {
  outline: none;
  border-color: var(--primary-pink);
  box-shadow: 0 0 0 3px var(--primary-pink-light);
}

.submit-btn {
  align-self: flex-start;
  padding: 1rem 2.5rem;
  background-color: var(--primary-pink);
  color: white;
  border: none;
  border-radius: 30px;
  font-weight: 600;
  font-size: 1rem;
  cursor: pointer;
  transition: transform 0.3s var(--ease-spring), box-shadow 0.3s var(--ease-out);
  margin-top: 1rem;
}

.submit-btn:hover {
  transform: translateY(-2px);
  background-color: var(--primary-pink-hover);
  box-shadow: 0 10px 20px rgba(255, 42, 109, 0.2);
}

/* Contact Info Side */
.contact-info-container {
  display: flex;
  flex-direction: column;
  gap: 2.5rem;
  padding-left: 2rem;
  border-left: 1px solid var(--border-light);
}

.info-block h4 {
  font-size: 0.9rem;
  color: var(--text-muted);
  text-transform: uppercase;
  letter-spacing: 1px;
  margin-bottom: 0.5rem;
}

.info-block p {
  font-size: 1.1rem;
  font-weight: 500;
  color: var(--text-main);
}

.direct-link {
  font-size: 1.2rem;
  font-weight: 700;
  color: var(--primary-pink);
  text-decoration: none;
  transition: opacity 0.2s ease;
}

.direct-link:hover {
  opacity: 0.7;
}

.social-links-modern {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.social-links-modern a {
  font-size: 1.1rem;
  font-weight: 500;
  color: var(--text-main);
  text-decoration: none;
  transition: color 0.2s ease, transform 0.2s ease;
  display: inline-block;
  width: fit-content;
}

.social-links-modern a:hover {
  color: var(--primary-pink);
  transform: translateX(4px);
}

/* Minimal Footer */
.footer {
  background-color: var(--bg-alt);
  padding: 3rem 2rem;
  border-top: 1px solid var(--border-light);
}

.footer-bottom {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 1100px;
  margin: 0 auto;
}

.copyright, .craft-note {
  font-size: 0.9rem;
  color: var(--text-muted);
  margin: 0;
}

/* Responsive Adjustments */
@media (max-width: 900px) {
  .hero-container {
    flex-direction: column-reverse;
    text-align: center;
    padding-top: 6rem;
  }
  
  .hero-actions {
    justify-content: center;
  }

  .hero-desc {
    margin: 0 auto 2.5rem;
  }

  .profile-pic, .hero-image-backdrop {
    width: 260px;
    height: 260px;
  }
  
  .contact-grid {
    grid-template-columns: 1fr;
    gap: 3rem;
    padding: 2rem;
  }
  
  .contact-info-container {
    padding-left: 0;
    border-left: none;
    border-top: 1px solid var(--border-light);
    padding-top: 3rem;
  }
}

@media (max-width: 768px) {
  .hero-name { font-size: 3rem; }
  .hero-role { font-size: 1.5rem; }
  .nav-links { display: none; }
  .section-title { font-size: 2rem; }
  .about-section, .contact-section { margin: 0 1rem; }
  .footer-bottom { flex-direction: column; gap: 1rem; text-align: center;}
}
</style>