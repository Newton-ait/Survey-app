# MoveUganda – Long-Distance Travel Survey App 🇺🇬🚌

This is a **self-contained, mobile-optimized web application** for collecting
transportation research data in Uganda. It presents two distinct survey flows
(Passenger & Driver) with multi‑step forms, progress tracking, validation, and
anonymous submission via **Formspree**.

Designed for a university research project, the app explores travel habits,
frustrations, interest in ride‑sharing, and safety preferences among people
making long‑distance trips (e.g., Kampala–Gulu, Mbarara, Mbale).

---

## ✨ Features

- **Two survey tracks** – one for passengers, one for drivers.
- **Step‑by‑step forms** with clear progress bar.
- **Smart skipping** – drivers who don’t own a car or never drive long trips are
  thanked and exited early.
- **Client‑side validation** – ensures required questions are answered before
  proceeding.
- **Formspree integration** – each survey sends data to a separate endpoint
  (passenger / driver).
- **Fully responsive** – works on phones, tablets, and desktops.
- **“Take another survey”** – reset and reuse without refreshing.
- **Anonymous & confidential** – no identifying information is collected.

---

## 🚀 Live demo / usage

1. Open `index.html` in any modern browser (Chrome, Firefox, Safari, Edge).
2. Read the welcome message and choose **Passenger** or **Driver**.
3. Answer each question – the “Next” button will only work when all required
   fields on the current step are filled.
4. After submission, a thank‑you screen appears and the data is sent to
   Formspree.
5. Click **“Take another survey”** to start over with the other role.

> **Note:** Form submissions are sent to Formspree. For testing you can use
> fake data; Formspree will ask for email confirmation on the first real
> submission. To change the destination, update the `action` URL in each
> `<form>` tag.

---

## 📁 Project structure

The entire application is a **single HTML file** – no build step, no
dependencies (except Font Awesome for icons). All styles and JavaScript are
embedded.

```

index.html
│
├── <head> – fonts, icons, global styles (CSS)
├── <body>
│   ├── app-header
│   ├── homeScreen (welcome + survey cards)
│   ├── passengerForm (5 steps)
│   ├── driverForm   (7 steps, with filtering)
│   ├── thankYouScreen
│   └── footer
└── <script> – all navigation, validation, progress, reset logic

```

---

## 🧠 How the driver filter works

The driver form includes two early “gate” questions:

1. **“Do you currently drive on long-distance trips?”**  
   If `No` → user is sent directly to the thank‑you screen.

2. **“Do you own or have regular access to a private car?”**  
   If `No` → user is sent to the thank‑you screen.

This ensures that only people who actually drive and have access to a car
continue with the full driver survey.

---

## 🔧 Customisation

### Change Formspree endpoints

Look for these lines and replace the `action` URLs with your own Formspree
(or other form handler) addresses:

```html
<!-- passenger -->
<form id="passengerForm" action="https://formspree.io/f/xwpwvbde" ...>

<!-- driver -->
<form id="driverForm" action="https://formspree.io/f/meopekbv" ...>
```

Add / remove questions

· Each step is a <div class="form-step"> inside the respective form.
· To add a step, duplicate an existing step, update the id, and adjust the
  showPassengerStep / showDriverStep arrays and the total step count in the
  JavaScript (the progress bar width is calculated automatically).
· Remember to update the navigation button ids and event listeners.

Modify styling

The colour scheme uses CSS custom properties (variables) at the top of the
<style> block. Change --primary, --accent, etc. to match your
institution’s branding.

```css
:root {
  --primary: #0b3d5f;
  --accent: #f39c12;
  /* ... */
}
```

---

📱 Mobile behaviour

· Buttons are large and easy to tap.
· Form inputs stretch to full width.
· The rating scales wrap on small screens.
· No horizontal scrolling – everything fits inside the viewport.

---

🧪 Testing the validation

All Next buttons have validation listeners. If a required field is empty,
an alert message explains what is missing. This prevents incomplete submissions
and guides the respondent.

---

📄 License / use

Feel free to adapt this code for your own academic or non‑commercial research.
No attribution required, but it’s nice to leave the original comments.

---
