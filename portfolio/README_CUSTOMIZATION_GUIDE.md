# Portfolio Website Maintenance & Customization Guide

Welcome to your portfolio website guide! This document explains how you can easily **add**, **edit**, or **remove** content across every section of your portfolio located in [`portfolio/index.html`](file:///c:/Users/ASUS/Desktop/website/portfolio/index.html).

---

## 📑 Table of Contents
1. [General Tips & Safety Guidelines](#general-tips--safety-guidelines)
2. [Header & Navigation Menu](#1-header--navigation-menu)
3. [Hero Section](#2-hero-section)
4. [About Me Section & Technical Arsenal](#3-about-me-section--technical-arsenal)
5. [Skills Marquee (Continuous Loop)](#4-skills-marquee-continuous-loop)
6. [Featured Projects Section (Auto-Slider)](#5-featured-projects-section-auto-slider)
7. [Career & Experience Timeline](#6-career--experience-timeline)
8. [Testimonials & Recommendations](#7-testimonials--recommendations)
9. [Contact Section & Social Links](#8-contact-section--social-links)
10. [Footer](#9-footer)
11. [Saving, Testing & Pushing to GitHub](#10-saving-testing--pushing-to-github)

---

## General Tips & Safety Guidelines

- **File to Edit**: Open [`portfolio/index.html`](file:///c:/Users/ASUS/Desktop/website/portfolio/index.html) in your editor (Antigravity IDE / VS Code).
- **Find Sections Quickly**: Use `Ctrl + F` and search for the divider comments, e.g.:
  - `<!-- ═══════ HERO ═══════ -->`
  - `<!-- ═══════ ABOUT ═══════ -->`
  - `<!-- ═══════ SKILLS ═══════ -->`
  - `<!-- ═══════ PROJECTS ═══════ -->`
  - `<!-- ═══════ EXPERIENCE ═══════ -->`
  - `<!-- ═══════ TESTIMONIALS ═══════ -->`
  - `<!-- ═══════ CONTACT ═══════ -->`
- **Special Characters**:
  - For `&`, write `&amp;`
  - For `·` (middle dot separator), write `&middot;`
  - For `'` or quotes, plain characters are fine.

---

## 1. Header & Navigation Menu

Search for: `<!-- ═══════ NAVIGATION ═══════ -->` (~Line 1440)

### Edit Logo / Name:
Look for:
```html
<a href="#hero" class="nav-logo" aria-label="Fahad Sutary - Home">
  <span class="nav-logo-name">FAHAD SUTARY</span>
  <span class="nav-logo-sub">Robotics &amp; Automation</span>
</a>
```
- Change `FAHAD SUTARY` or the subtitle text as needed.

### Add / Edit / Remove Nav Links:
There are two places to update nav links (desktop menu and mobile dropdown):
1. **Desktop Menu (`.nav-links`)**:
   ```html
   <a href="#about" class="nav-link">About</a>
   <a href="#skills" class="nav-link">Skills</a>
   <a href="#projects" class="nav-link">Projects</a>
   <a href="#experience" class="nav-link">Experience</a>
   <a href="#testimonials" class="nav-link">Testimonials</a>
   <a href="#contact" class="nav-link">Contact</a>
   ```
2. **Mobile Menu (`#mobile-menu`)**:
   Find `#mobile-menu` and update the matching `<a>` tags.
- **To Remove**: Delete the `<a>` tag in both places.
- **To Add**: Duplicate an `<a>` line and update the `href="#section-id"` and text.

---

## 2. Hero Section

Search for: `<!-- ═══════ HERO ═══════ -->` (~Line 1490)

### Edit Text & Badges:
- **Status badge**: Look for `.status-dot` and edit:
  ```html
  <span class="status-dot"></span> Available for Select Projects
  ```
- **Headline / Title**:
  ```html
  <h1 class="hero-title">Robotics &amp; Automation Engineer</h1>
  ```
- **Hero Bio / Subtitle**: Edit text inside `<p class="hero-sub">...</p>`.

### Hero Portrait Photo:
Look for:
```html
<img src="../my photo.jpg" alt="Fahad Sutary - Robotics &amp; Automation Engineer" ... />
```
- To change the picture, replace `my photo.jpg` in the root folder or update the `src` attribute.

### Hero Stats Counters:
Look for `.hero-stat`:
```html
<div class="hero-stat-num" data-target="8">0</div>
<div class="hero-stat-label">Years of Engineering Experience</div>
```
- Edit `data-target="X"` (the target number the counter counts up to).
- Edit the label underneath.

---

## 3. About Me Section & Technical Arsenal

Search for: `<!-- ═══════ ABOUT ═══════ -->` (~Line 1550)

### Edit Bio Paragraphs:
Look inside `<div class="about-text">`:
- Edit paragraphs `<p>...</p>` detailing your background, leadership, and specializations.

### Edit Technical Arsenal Cards (Right Column):
Cards live inside `<div class="about-cards">`. Each card has this structure:
```html
<div class="about-card">
  <div class="about-card-icon">...SVG ICON...</div>
  <div>
    <div class="about-card-title">Robotics &amp; Kinematics</div>
    <div class="about-card-desc">KUKA KRC5, ABB IRC5, Fanuc, Dobot CR10A, ROS 2, MoveIt.</div>
  </div>
</div>
```
- **To Edit**: Change the title or description text.
- **To Add**: Copy one `.about-card` block and paste it inside `.about-cards`.
- **To Remove**: Delete that `.about-card` block.

---

## 4. Skills Marquee (Continuous Loop)

Search for: `<!-- ═══════ SKILLS MARQUEE ═══════ -->` (~Line 1600)

The skills banner runs in an infinite loop using two identical tracks (`.marquee-track`).
```html
<div class="marquee-track">
  <div class="marquee-item"><span class="m-icon">⚡</span> EPLAN Pro Panel</div>
  <div class="marquee-item"><span class="m-icon">🤖</span> Beckhoff TwinCAT 3</div>
  ...
</div>
<!-- Duplicate track for infinite loop -->
<div class="marquee-track" aria-hidden="true">
  ...
</div>
```
- **To Edit a Skill**: Change the emoji or text in **both** tracks.
- **To Add a Skill**: Add `<div class="marquee-item"><span class="m-icon">🎯</span> Skill Name</div>` to **both** tracks.
- **To Remove a Skill**: Delete the item from **both** tracks.

---

## 5. Featured Projects Section (Auto-Slider)

Search for: `<!-- ═══════ PROJECTS ═══════ -->` (~Line 1625)

The project carousel uses an automatic infinite loop: Cards 1, 2, and 3 are repeated as Cards 4, 5, and 6 to ensure smooth continuous scrolling.

### Card Structure:
```html
<article class="project-card" role="listitem" tabindex="0">
  <div class="proj-img-box">
    <img class="proj-img" src="IMAGE_URL_OR_PATH" alt="Project Name" loading="lazy" />
    <div class="proj-pill">Category / Tag</div>
  </div>
  <div class="proj-body">
    <div class="proj-meta">
      <span class="proj-cat">Category / Client</span>
      <span class="proj-year">2026</span>
    </div>
    <h3 class="proj-title">Project Title</h3>
    <p class="proj-desc">Detailed project description...</p>
    <div class="proj-footer">
      <a href="#contact" class="btn-ghost">View Details ...</a>
    </div>
  </div>
</article>
```

### How to Edit an Existing Project:
1. Find Card 1 (e.g. `MDP2`) and update the title, year, category, and description.
2. Update the duplicate Card 4 with the **exact same text** so the loop remains seamless.
3. Repeat the same for Card 2 & 5, or Card 3 & 6.

### How to Add a New Project:
1. Paste a new `<article class="project-card">` at the end of the first set (e.g., as Project 4).
2. Paste an identical duplicate at the end of the container (as Project 8) for the loop.

---

## 6. Career & Experience Timeline

Search for: `<!-- ═══════ EXPERIENCE ═══════ -->` (~Line 1820)

The timeline alternates between left (`odd`) and right (`even`) layouts.

### Structure of an Odd Entry (Year on left, Content on right):
```html
<div class="timeline-entry odd reveal" role="listitem">
  <div class="tl-left">
    <div class="tl-year">2026</div>
    <div class="tl-badge">Present</div> <!-- Optional badge -->
  </div>
  <div class="tl-center">
    <div class="tl-node" aria-hidden="true"></div>
  </div>
  <div class="tl-right">
    <div class="tl-role">Job Title</div>
    <div class="tl-org">Company Name &middot; Location</div>
    <p class="tl-desc">Detailed accomplishments and responsibilities...</p>
  </div>
</div>
```

### Structure of an Even Entry (Content on left, Year on right):
```html
<div class="timeline-entry even reveal" role="listitem">
  <div class="tl-left">
    <div class="tl-role">Job Title</div>
    <div class="tl-org" style="text-align:right;">Company Name &middot; Location</div>
    <p class="tl-desc" style="text-align:right;">Detailed accomplishments and responsibilities...</p>
  </div>
  <div class="tl-center">
    <div class="tl-node" aria-hidden="true"></div>
  </div>
  <div class="tl-right">
    <div class="tl-year">2025</div>
  </div>
</div>
```

### How to Edit:
- Simply change the text inside `.tl-role`, `.tl-org`, `.tl-year`, or `<p class="tl-desc">`.

### How to Add a New Job / Role:
1. Check whether the preceding item was `odd` or `even`.
2. Copy either the `odd` or `even` block above to maintain the alternating pattern.
3. Paste it in chronological order inside `<div class="timeline-wrap">`.

### How to Remove an Entry:
- Select the entire `<div class="timeline-entry ...">...</div>` block and delete it.
- If needed, adjust the remaining entries' classes (`odd`/`even`) so they alternate cleanly.

---

## 7. Testimonials & Recommendations

Search for: `<!-- ═══════ TESTIMONIALS ═══════ -->` (~Line 1920)

### Structure of a Testimonial Card:
```html
<div class="testi-card reveal d1">
  <img class="testi-avatar" src="AVATAR_IMAGE_URL" alt="Person's Name" loading="lazy" />
  <div class="testi-header">
    <div class="testi-name">Dr. James Hartley</div>
    <a href="https://www.linkedin.com/in/YOUR_TARGET_PROFILE" target="_blank" rel="noopener noreferrer" class="testi-linkedin" aria-label="LinkedIn profile">
      <!-- LinkedIn SVG Icon -->
    </a>
  </div>
  <div class="testi-role">Senior Robotics Researcher &middot; AMRC</div>
  <p class="testi-text">&ldquo;Quote text from recommendation...&rdquo;</p>
</div>
```

### How to Edit:
- **LinkedIn Link**: Change `href="https://www.linkedin.com/in/..."` to the person's real LinkedIn URL.
- **Name & Role**: Edit `.testi-name` and `.testi-role`.
- **Quote**: Edit text inside `<p class="testi-text">`.
- **Avatar Image**: Change `src="..."` to an image URL or local photo.

### How to Add / Remove:
- **To Remove**: Delete the entire `.testi-card` div.
- **To Add**: Duplicate any `.testi-card` block and update the details.

---

## 8. Contact Section & Social Links

Search for: `<!-- ═══════ CONTACT ═══════ -->` (~Line 2030)

### Contact Info (Left Column):
- **Email**: Update both `href="mailto:your.email@example.com"` and the visible email text.
- **Location**: Edit the city and country under `.contact-detail-val`.
- **Social Links**: Update `href="..."` for:
  - LinkedIn: `https://linkedin.com/in/YOUR_USERNAME`
  - GitHub: `https://github.com/YOUR_USERNAME`

### Contact Form (Right Column):
- Currently wired with client-side JavaScript validation.
- To connect it to an email service (like Formspree or EmailJS), update `<form id="contact-form" action="https://formspree.io/f/YOUR_FORM_ID" method="POST">`.

---

## 9. Footer

Search for: `<!-- ═══════ FOOTER ═══════ -->` (~Line 2150)
- Update copyright year or name:
  ```html
  <p class="footer-copy">&copy; 2026 Fahad Sutary. All rights reserved.</p>
  ```

---

## 10. Saving, Testing & Pushing to GitHub

### 1. Preview Changes Locally:
Run a local Python server in PowerShell:
```powershell
python -m http.server 8000
```
Open your browser to: `http://localhost:8000/portfolio/`

### 2. Commit & Push to GitHub:
Run these commands in PowerShell from the project root (`c:\Users\ASUS\Desktop\website`):

```powershell
# 1. Check changed files
& "C:\Program Files\Git\cmd\git.exe" status

# 2. Stage changes
& "C:\Program Files\Git\cmd\git.exe" add portfolio/index.html

# 3. Commit with a message
& "C:\Program Files\Git\cmd\git.exe" commit -m "Update portfolio content"

# 4. Push live to GitHub
& "C:\Program Files\Git\cmd\git.exe" push
```

*Tip: If you have Git added to your system PATH, you can simply type `git add .`, `git commit -m "..."`, and `git push`.*
