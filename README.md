# 🎓 Student Study Planner (StudyMate)

A complete, modern, responsive academic productivity web application and AI-assisted learning companion designed for college and university students.

![Student Study Planner Dashboard Preview](screenshots/dashboard.png)

---

## 📌 1. Project Overview & Problem Statement

### The Problem
College students consistently manage complex academic workloads spanning 4–6 rigorous courses with disparate problem sets, coding assignments, reading lists, midterms, and capstone deadlines. In practice, students coordinate these requirements across fragmented tools: paper planners, phone notes, calendar apps, and disjointed messaging groups.

This fragmentation leads to:
* **Missed or misprioritized deadlines** due to scattered schedules.
* **Unrealistic study planning** without tracking *actual* time spent studying vs. planned time.
* **Scheduling collisions** where overlapping study sessions cause friction and drop-off.
* **Unassisted learning barriers** when encountering difficult theoretical concepts during independent study.

### The Solution: StudyMate
**Student Study Planner** brings all core academic workflows together into a unified, privacy-first, responsive web application:
1. **Academic Task Manager:** Tracks deadlines, priorities, durations, and statuses with dynamic filtering.
2. **Intelligent Study Planner:** Allows scheduling study blocks with real-time **Schedule Overlap Warnings** and a **Persistent Focus Study Timer** (Pomodoro & Stopwatch).
3. **Subject & Course Portfolio:** Organizes credit hours, weekly study targets, course codes, and notes.
4. **AI Academic Tutor:** Delivers step-by-step conceptual breakdowns, practice exam quizzes, and custom revision schedules via Google Gemini API, with an automatic, transparent fallback to an interactive **Offline Demo Simulation**.
5. **Academic Calendar & Visual Progress:** Maps assignments onto a 42-cell monthly grid and renders empirical analytics distinguishing recorded focus time from planned estimates.

---

## 📸 2. Application Screenshots

| View | Screenshot Preview | Key Capabilities |
| :--- | :--- | :--- |
| **Dashboard** | ![Dashboard](screenshots/dashboard.png) | Personalized greeting, 4 dynamic metric cards, today's schedule, upcoming deadlines, 7-day study activity chart, quick actions. |
| **My Tasks** | ![Tasks](screenshots/tasks.png) | Multi-criteria filtering (status, subject, priority), sorting (due date, priority, duration), title/desc search, overdue alerts. |
| **Study Planner** | ![Study Planner](screenshots/study-planner.png) | Pomodoro timer (25/50/90m), custom blocks, conflict detection warning, background persistence, verified session logging. |
| **Subjects** | ![Subjects](screenshots/subjects.png) | Course codes, custom color swatches, weekly study target progress bars, assignment counts, safe cascade deletion. |
| **AI Academic Tutor** | ![AI Tutor](screenshots/ai-tutor.png) | Live Gemini model generation (`gemini-flash-lite-latest`) & offline simulation, suggested prompts, formatted markdown, copy notes. |
| **Academic Calendar** | ![Calendar](screenshots/calendar.png) | 42-cell monthly grid, previous/next navigation, assignment & session badges, interactive day schedule popover modal. |
| **Progress Analytics** | ![Progress](screenshots/progress.png) | Completion rate %, recorded study hours vs weekly target, subject-wise distribution, 7-day activity histogram, metric clarity. |
| **Settings** | ![Settings](screenshots/settings.png) | Profile name, credit hour goals, light/dark theme switch, timer presets, JSON export/import backup, reset demo data. |

---

## 🛠️ 3. Technology Stack

* **Frontend Framework:** React 18 with modern functional components and custom React hooks (`useStudy`).
* **Build Tool & Bundler:** Vite 5 with Hot Module Replacement (HMR) and optimized rollup production bundling.
* **Styling & Design System:** Custom semantic CSS with CSS Variables, modern SaaS typography (Inter), rounded card surfaces, elevation shadows, fluid responsive layouts, and native Dark Mode.
* **Icons & Micro-Interactions:** Lucide React icons & Canvas Confetti for celebratory milestone completion.
* **Client-Side Persistence:** HTML5 LocalStorage with defensive JSON parsing, schema fallbacks, and full JSON data backup export/import.
* **Backend API Proxy:** Node.js & Express 4 server for secure server-side Google Gemini API requests without exposing credentials.
* **AI Engine:** Google Generative AI SDK (`@google/generative-ai`) utilizing `gemini-flash-lite-latest` with candidate fallback models and an offline educational simulation engine.
* **Testing:** Vitest automated unit testing suite.

---

## 📁 4. Project Structure

```
student-study-planner/
├── index.html                   # HTML5 root template with Inter font
├── package.json                 # Dependencies, npm scripts, and metadata
├── vite.config.js               # Vite config with backend proxy and Vitest
├── .env.example                 # Environment configuration template
├── .env                         # Server environment configuration (GEMINI_API_KEY)
├── .gitignore                   # Ignored files (node_modules, dist, .env)
├── public/
│   └── logo.svg                 # Application graduation cap logo
├── server/
│   └── server.js                # Express API backend for secure Gemini integration
├── src/
│   ├── main.jsx                 # React root mount
│   ├── App.jsx                  # Main router, navigation layout, and modal controllers
│   ├── components/
│   │   ├── Header.jsx           # Top header bar (date, breadcrumbs, theme toggle)
│   │   ├── Sidebar.jsx          # Responsive collapsible navigation sidebar
│   │   ├── GlobalTimerBar.jsx   # Floating active study timer pill
│   │   ├── Toast.jsx            # Toast alert notifications
│   │   ├── TaskModal.jsx        # Assignment creation and editing dialog
│   │   ├── SubjectModal.jsx     # Course creation and editing dialog
│   │   └── SessionModal.jsx     # Study session scheduler with conflict detection
│   ├── context/
│   │   └── StudyContext.jsx     # Central React Context for state and LocalStorage sync
│   ├── pages/
│   │   ├── Dashboard.jsx        # Dashboard overview and daily pulse
│   │   ├── Tasks.jsx            # Assignment management and filtering
│   │   ├── StudyPlanner.jsx     # Study schedule, focus timer, and history
│   │   ├── Subjects.jsx         # Course cards, credit hour goals, safe delete
│   │   ├── AiTutor.jsx          # AI academic tutor chat and study assistant
│   │   ├── CalendarView.jsx     # 42-cell monthly calendar with event badges
│   │   ├── ProgressView.jsx     # Empirical study analytics and visual charts
│   │   └── SettingsView.jsx     # Preferences, theme, and data export/import
│   ├── styles/
│   │   └── index.css            # Complete design system and responsive styles
│   └── utils/
│       ├── storage.js           # LocalStorage wrapper with error handling
│       ├── sampleData.js        # Realistic initial college dataset
│       ├── dateHelpers.js       # Overlap detection, overdue checks, formatting
│       └── aiDemoEngine.js      # Offline educational simulation engine
├── tests/
│   ├── dateHelpers.test.js      # Scheduling overlap and date math unit tests
│   ├── aiDemoEngine.test.js     # Offline AI simulation response tests
│   └── progressView.test.jsx    # React server rendering verification test
├── docs/                        # Complete capstone documentation suite
│   ├── README.md                # Documentation table of contents
│   ├── project-overview.md      # Problem statement, scope, target audience
│   ├── research-summary.md      # Competitive analysis & planned usability plan
│   ├── information-architecture.md # Hierarchy, components, entity schema
│   ├── user-flows.md            # Interaction maps for primary student journeys
│   ├── design-system.md         # Color tokens, typography, component standards
│   ├── ai-integration-log.md    # Model verification records & prompt engineering
│   ├── usability-testing.md     # Usability testing protocol and SUS criteria
│   ├── handoff-guide.md         # Developer handoff and technical instructions
│   ├── asset-inventory.md       # Capstone digital asset index
│   └── final-capstone-summary.md # 7-slide presentation deck summary
└── screenshots/                 # Application visual screenshots (8 views)
```

---

## 🚀 5. Installation & Local Development Instructions

### Prerequisites
* **Node.js:** v18.0.0 or later (v24.19.0 verified).
* **npm:** v9.0.0 or later (v11.17.0 verified).

### Quick Start (3 Steps)

1. **Clone or Navigate to the Project:**
   ```bash
   cd c:\project\flyrank
   ```

2. **Install Dependencies:**
   ```bash
   npm install
   ```

3. **Start Client and Backend Concurrently:**
   ```bash
   npm run dev
   ```
   * Open your browser and navigate to: **[http://localhost:5173](http://localhost:5173)**.
   * The backend API server starts concurrently on `http://localhost:5000`.

---

## 🤖 6. AI Configuration & Transparent Demo Mode

### Configuring Live Google Gemini AI
1. Obtain an API key from [Google AI Studio](https://aistudio.google.com/).
2. Add your key to `.env` in the project root:
   ```env
   PORT=5000
   GEMINI_API_KEY=your_gemini_api_key_here
   ```
3. Restart the server (`npm run dev`). The AI Tutor will automatically connect to Gemini (`gemini-flash-lite-latest`) through the secure backend proxy.

### Interactive Offline Demo Mode
If you do not configure an API key or if quota limits are reached:
* **The application never breaks or exposes errors.**
* The AI Tutor seamlessly switches to a clearly labeled **Offline Demo Mode**.
* It provides realistic college-level explanations on Algorithms (Dijkstra, Dynamic Programming), Machine Learning (Overfitting, L1/L2 Regularization), Operating Systems (Virtual Memory, Paging Quiz), Database Systems (ACID Transactions), and 3-Day Exam Revision Strategies.
* Every simulated response is clearly flagged with an `(Offline Demo Simulation)` badge to maintain complete academic transparency.

---

## 🔒 7. Data Storage & Privacy

* **100% Client-Side:** All tasks, subjects, scheduled sessions, and timer logs are stored in the user's browser using HTML5 `localStorage`.
* **Zero Tracking:** No personal academic data or assignment contents are transmitted to third-party databases.
* **Data Sovereignty:**
  * **Export Backup (JSON):** Download your complete academic record as a structured `.json` file at any time from the Settings page.
  * **Import Backup (JSON):** Restore your planner state on another browser or machine with one click.
  * **Reset Demo Data:** Easily restore the sample college dataset (5 subjects, assignments, and study logs).
  * **Permanent Wipe:** Clear all local application records with a confirmation dialog.

---

## 🧪 8. Testing Instructions

Run the automated Vitest test suite:
```bash
npm test
```

### Verified Test Coverage (9 Passing Tests):
* **Date & Scheduling Utilities:**
  * Detects overlapping time blocks on the same date.
  * Detects schedule collisions in arrays of study sessions.
  * Accurately calculates days remaining and overdue task statuses.
  * Formats duration into friendly hours/minutes strings.
* **AI Simulation Engine:**
  * Validates conceptual explanations, quiz generation with answer keys, and revision plans.
* **Component Rendering Verification:**
  * Tests error-free rendering of complex analytical views (`ProgressView`).

---

## 🎨 9. Figma Capstone Reference

* **Reference Project:** [Figma Community Student Study Planner](https://www.figma.com/design/8A9ohoZV5Btsg3DfNoL5Ec/Student-Study-Planner?node-id=1-2&p=f)
* The visual design tokens, sidebar structure, color palette, and component cards implement the specifications established in the capstone design reference.

---

## ⚠️ 10. Known Limitations & Future Roadmap

### Current Limitations
1. **Device-Specific Storage:** Data persists indefinitely in the current browser, but does not automatically synchronize across separate computers without exporting/importing JSON.
2. **Manual Task Entry:** Assignments are created manually by the student rather than ingested via university LMS APIs.

### Future Roadmap
* **Cloud Multi-Device Sync:** Optional Firebase / Supabase cloud database synchronization with university SSO.
* **LMS Feed Integration:** Ingest assignment deadlines via standard Canvas, Blackboard, or Google Classroom `.ics` calendar feeds.
* **Progressive Web App (PWA):** Offline service worker and web manifest for mobile home screen installation.
* **Spaced Repetition Flashcards:** Automated Leitner-box review drills for memorizing definitions and formulas.
