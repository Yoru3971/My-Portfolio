# 🚀 Personal Web Portfolio

A modern, fast, and bilingual web portfolio built with **Angular 20**. Designed to showcase projects and skills, and to facilitate contact through a clean, responsive interface.

---

## ✨ Features

- 🌗 **Dark/Light Mode:** Natively implemented using CSS Variables and a custom `ThemeService`.
- 🌍 **Internationalization (i18n):** Dynamic bilingual support (English/Spanish) using `ngx-translate`.
- ✉️ **Contact Form:** Integrated with Formspree for serverless email management.
- 📱 **Responsive Design:** Mobile-first approach, featuring an Off-Canvas/Drawer menu and fluid navigation.
- ⚡ **Standalone Components:** Modern Angular architecture, bypassing traditional `NgModules` for a lighter, faster application.

---

## 🛠️ Tech Stack

- **Framework:** Angular 17+ (TypeScript)
- **Styling:** HTML5, pure CSS3 (Flexbox, Grid, CSS Variables)
- **Libraries:** `@ngx-translate/core`, `@angular/forms` (Reactive Forms)
- **Icons:** FontAwesome & Flag-icons

---

## 🚀 How to start your own portfolio

### 1️⃣ Create your repository

Click the **"Use this template"** button at the top right of this repository page (or "Create a new repository" from the dropdown) to generate a fresh repository in your GitHub account with all this code ready to go.

### 2️⃣ Clone your new repository

Open your terminal and clone the repository you just created (replace with your actual username and repo name):

```bash
git clone [https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git](https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git)
cd YOUR_REPO_NAME

```

### 3️⃣ Install dependencies

```bash
npm install

```

### 4️⃣ Start the development server

```bash
ng serve

```

### 5️⃣ Open your browser

Navigate to:

```text
http://localhost:4200/

```

---

## 🎨 How to Customize

This portfolio is built to be easily customizable. While the core text content is data-driven, you will need to tweak a few component files to truly make it yours.

### 📸 Update your Profile Picture

To change the hero image, replace the default picture with your own.
Save your photo exactly as `profile-photo.png` inside the following directory:
`/public/assets/images/`

### 📄 Update your Resume (CV) PDFs

The Navbar includes a button to download your CV depending on the currently selected language.

1. Place your own PDF files inside `/public/assets/docs/`.
2. Open the `NavBar` component (`nav-bar.ts`).
3. Update the `cvUrl` getter and the `downloadCV()` method to match your new filenames:

```typescript
  get cvUrl(): string {
    return this.languageService.isEnglish()
      ? 'assets/docs/YOUR_ENGLISH_CV.pdf'
      : 'assets/docs/YOUR_SPANISH_CV.pdf';
  }

```

### 📝 Modify Texts, Skills, and Projects

All the textual content is managed by `ngx-translate` through JSON files. To update your biography, skills, or portfolio items, edit the language files (usually located in `/public/assets/i18n/` or similar):

* `en.json` (English)
* `es.json` (Spanish)

**Adding a New Skill:**
Locate the `SKILLS.HARD` or `SKILLS.SOFT` array in both language files, and add a new object with your technology and its FontAwesome icon class:

```json
{ "name": "New Technology", "icon": "fa-brands fa-linux" }

```

**Adding a New Project:**
Locate the `PROJECTS.ITEMS` array. Add a new object following this structure. Remember to save your project's screenshot in `/public/assets/images/`:

```json
{
  "title": "Your New Project",
  "description": "A brief description of the architecture, goals, and your role.",
  "image": "assets/images/new-project-screenshot.png",
  "tech": ["Framework 1", "Database 2", "Cloud 3"],
  "githubFront": "[https://github.com/](https://github.com/)...",
  "githubBack": "[https://github.com/](https://github.com/)...",
  "demo": "https://..."
}

```

### 🌍 Add a New Language (Advanced)

The current portfolio is optimized for a binary language toggle (English/Spanish) using Angular Signals. Adding a third language requires a few structural changes:

1. **Create the translation file:** Duplicate `en.json`, rename it to the new language code (e.g., `fr.json`), and translate the content.
2. **Update `LanguageService`:** - Update `initLanguage()` to include the new language in the array: `this.translate.addLangs(['es', 'en', 'fr'])` and update the regex match: `/es|en|fr/`.
* The current `toggleLanguage()` method switches back and forth. You will need to replace this logic to handle multiple languages directly via `setLanguage(langCode)`.


3. **Update `NavBar` UI & Logic:** - Change the language toggle button in your HTML to a dropdown menu or multiple buttons.
* Update the `cvUrl` logic to handle the third language option instead of a simple boolean check.



---

## 📄 License

This project is licensed under the **MIT License**.

See the `LICENSE` file for details.

Feel free to use it as a template for your own portfolio ✨
