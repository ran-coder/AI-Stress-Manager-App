# AI-Stress-Manager-App

> **[One-line elevator pitch describing what your project does and the core problem it solves]**

---

## 🎥 Deliverables & Links

* 📹 **3–5 Min Pitch & Demo Video:** [Watch on YouTube (Unlisted)](https://youtube.com/watch?v=YOUR_VIDEO_ID)  
  * *Video Title format:* `[Team Name] - [Project Name] Hackathon Demo`
* 🎨 **Interactive Design Prototype:** [Figma Prototype / Canva Board](https://figma.com/file/YOUR_PROTOTYPE_LINK)
* 📊 **Presentation Slides:** [Google Slides / Canva Presentation](https://docs.google.com/presentation/d/YOUR_SLIDES_LINK)

---
## Project Overview 

### The Problem
University coursework is structured so that assignments and projects cluster heavily toward the end of the semester, while the first few weeks stay relatively light. This creates a sharp mismatch between workload and preparation time because when deadlines converge, students especially those balancing coursework with part-time jobs and student club activities are forced to split limited time and energy across multiple demanding tasks. The result is not just lower-quality work across the board, but significant anxiety from knowing they can't realistically do their best on everything at once, with universities and academic advisors ultimately absorbing the downstream effects through declining performance and burnout. 

Existing tools like [Todoist](https://www.todoist.com/) help with capturing and prioritizing tasks through a clean, fast interface, but they're built for general productivity rather than a personalized workload manager — there's no concept of workload intensity or energy capacity, no awareness of how a task is actually affecting the student beyond its due date, and no adaptive response when someone is clearly overwhelmed. Todoist optimizes for organization, not wellbeing, leaving the real stress of semester crunch entirely unaddressed.

### Our Solution
AI-powered workload stress manager built for university students who juggle mental, time, physical, social, and errand-based tasks with no system that reacts to how overwhelmed they actually are. Students log their tasks, and the AI continuously calculates a real-time workload percentage, escalating its response through staged interventions. Our system infers stress directly from behavior (task engagement, completion patterns, time-on-task) and responds proactively, including an agentic AI Task Coach that steps in the moment it detects a student struggling with a specific task. The result is a tool that manages workload and protects wellbeing at the same time, instead of treating productivity and mental health as separate problems.

- **NLP-based task inference** — estimate complexity and duration directly from task description text, removing manual input
- **Behavioral overwhelm pre-inference** — use engagement signals (opens, edits, ignores) to predict overwhelm before the student confirms it
- **Personalized workload thresholds** — calibrate each student's baseline over time instead of a fixed global threshold
- **Named forecasting method** — implement Burnout Trajectory Forecasting via a concrete lightweight model (e.g. moving average or linear regression)
- **Multi-step AI Task Coach pipeline** — classify the task's blocker type first, then generate a tailored breakdown, rather than a single LLM call


## 💡 Ideation & Thought Process
 
### Step 1 — Initial Ideation
Iteration 1 started simple: students log tasks, the app calculates a workload percentage, and produces a priority-based task list. No reactive response yet — purely a passive log.
 
### Step 2 — Identifying Weaknesses
Moving to Iteration 2, we added an AI reactive layer: a workload threshold that triggers a recommendation, AI task breakdown for flagged complex tasks, and an AI-generated visual long-term goal tracker. Reviewing this version surfaced clear weaknesses:
 
- A single on/off workload threshold treats mild and severe stress the same way, with no proportional response.
- The goal tracker's constant countdown creates anxiety by design and risks pushing students to work *more* — directly contradicting the app's purpose as a stress manager.
This also raised a broader question we hadn't yet answered: **"Implementing more AI? (NLP / CV / RAG / Agentic)"** — could a more AI-driven mechanism replace these weaker points and make the solution genuinely more novel?
 
Engagement and wellness extras (virtual study room, device time-out, mini-games) were also considered at this stage, but were deprioritized since their UI/UX build effort felt too heavy relative to their impact.
 
### Step 3 — Revisions Made
Working through that question, we refined the reactive layer and then integrated its pieces together:

<img width="1920" height="1080" alt="codenection dump (2)" src="https://github.com/user-attachments/assets/d8bcb3a9-1d44-4cb0-aafd-1e3af1d983f7" />
> **Diagram description:**
> Evolution from Iteration 1 (simple workload log) through Iteration 2 (added AI reactive layer), Iteration 3 (refining Iteration 2's features based on severity and reframing the goal tracker), to Iteration 4 (integrating the behavioral check-in with the AI Task Coach).
 
- **Iteration 3 →** Workload threshold recommendations and their frequency are now based on severity stage. The AI Task Coach became agentic, running a multi-step reasoning loop in a chatbot-style interface to generate an adaptive, personalized plan. The goal tracker was reframed into **Burnout Trajectory Forecasting** with an LLM explanation layer.
- **Iteration 4 →** Integrated the behavioral check-in with the AI Task Coach: the app passively tracks engagement signals (opens, edits, ignores) and asks "Looks like you might be overwhelmed by this one?" If confirmed, the AI Task Coach auto-generates a step-by-step breakdown personalized to current workload and mental state.

### Step 4 — Final Architecture
These revisions converged into a single connected system, structured around one central homepage hub that every feature branches from and returns to.

<img width="3713" height="2241" alt="Add text" src="https://github.com/user-attachments/assets/4bd78c2d-fce2-43ee-8626-aa758f1ef351" />
> **Diagram description:**
> This diagram maps the complete user journey from opening the app to completing a task, centered on the homepage as the main hub. Every feature — task logging, the AI Task Coach, and Burnout Forecasting — branches out from and returns to this central point.
 
---
## Feature: Task Logging & Check-Ins

* **V1:** Task logging + workload % calculation + basic plan output
* **Problem identified:** If a task passes its due date unmarked, the app has no way to tell whether the student forgot or genuinely overwhelmed -> false burnout signal.
* **V2 (ENHANCED):** Added a Check-In feature. When a task goes overdue unmarked, the app asks *"This one's overdue, what happened?"* with options (**Forgot about it** / **Still working on it** / **Too overwhelmed to start** / **Not a priority anymore**), classifying the cause before it affects the workload score.
* **V3 (INTEGRATE):**  Instead of check-ins,  app passively tracks engagement signals (how many times a task is opened, edited, or ignored) to detect early signs of overwhelm. It surfaces a soft check-in: "Looks like you might be overwhelmed by this one?" If confirmed, the AI Task Coach is triggered automatically, generating a step-by-step breakdown personalized to the student's current workload and mental state.

---

## Feature: Staged Workload Intervention

* **V1:** Soothing recommendations triggered by a single workload threshold.
* **Problem identified:** A single on/off threshold treats mild and severe stress the same way, with no proportional response.
* **V2 (REFINED):** A Staged Workload Intervention System. Workload severity broken into stages that escalate in both frequency and intervention type, culminating in a dedicated recovery mission mode at the most severe stage.

---

## Feature: Agentic AI Task Coach

* **V1:** A chatbot style AI that give breakdowns and helps with comprehension for complex tasks.
* **V2 (REFINED):** A single AI agent that runs a multi-step reasoning loop rather than a one-time LLM response: it analyzes the flagged task and current workload context, decides what kind of breakdown is needed, generates a personalized step-by-step plan, then checks back in later ("did you finish step 1?") to dynamically adjust the remaining steps. 

---

## Feature: Burnout Trajectory Forecasting

* **V1:** Visual long-term goal tracker showing consequences of not focusing (countdown/percentage toward the goal).
* **Problem identified:** A constant countdown creates **anxiety by design** and risks pushing students to work more → directly contradicting the app's stress-manager purpose.
* **V2 (REFRAMED):** Reframed as Burnout Trajectory Forecasting. Projects the student's stress trajectory from behavioral data (workload %, completion consistency, overdue backlog, time-on-task), paired with an LLM explanation layer that interprets the forecast honestly and suggests one specific, actionable adjustment.

---
### 4. Breadth of Exploration
We evaluated several core candidate concepts against feasibility and impact:

| Concept Considered | Pros | Cons |
| :--- | :--- | :--- |
| **Burnout Trajectory Forecasting + LLM Explanation** | <ul><li>Directly addresses the stated problem</li><li>Built entirely from data the app already collects (workload %, completion consistency, overdue backlog, time-on-task)</li></ul> | Slightly harder to build correctly (needs the explanation layer to avoid sounding alarmist) |
| **AI-Generated Visual Long-Term Goal Tracker** | <ul><li>Visually compelling concept</li><li>Clear tie to long-term motivation, which resonates with students</li></ul> | <ul><li>Weaker fit to problem stated because addresses motivation more than stress</li><li>Doesn't reduce workload or prevent burnout; it risks increasing pressure instead</li><li>Harder to make the AI generation reliably good in a short build window.</li></ul> |
| **Manual Prompt Check-Ins** | <ul><li>Zero False Positives: Intervention relies on explicit user confirmation</li><li>Preserves full user control and privacy | High Cognitive Load: Demands executive function and self-awareness from a student who is already overwhelmed.<br> |
| **System Activity Monitoring** | <ul><li>Proactive Detection:Continuously identifies silent task avoidance, procrastination, and paralysi</li><li>Zero User Friction:Operates quietly in the background| False Alarm Risk: May misidentify normal breaks or non-linear study habits as task overwhelm if thresholds are poorly tuned.|

System Activity Monitoring and Burnout Trajectory Forecasting are chosen because they are tightly coupled to the core problem statement and the realities of student burnout. On feasibility, this combination comes out ahead by reusing existing data and infrastructure (such as workload %, completion consistency, and interaction telemetry). In contrast, concepts like the AI-Generated Visual Goal Tracker add open-ended technical complexity and risk increasing pressure rather than relieving stress. Ultimately, System Activity Monitoring and Burnout Trajectory Forecasting align directly with the scoring criteria by delivering immediate, proactive intervention with minimal user friction.

---
### 5. Mentor Consultation & Feedback Integration

| Mentor / Role | Key Feedback Received | Action Taken & Changes Made |
| :--- | :--- | :--- |
| **Teh Ming En** | *"</li><li>Restructure the README.md contents so it looks more like a thought process ideation documentation rather than dumping everything there.</li><li>The UI/UX can make simple solutions stand out.</li><li>Place yourself in the target user's shoes and understand their pain points to deliver a good pitch presentation."* | </li><li>Reorganize README.md</li><li>Optimizing and priotizing UI/UX useability</li><li>Understand and draft a good pitch script. |

