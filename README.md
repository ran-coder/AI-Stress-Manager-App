# AI-Stress-Manager-App

> **[One-line elevator pitch describing what your project does and the core problem it solves]**

---

## 🎥 Deliverables & Links

* 📹 **3–5 Min Pitch & Demo Video:** [Watch on YouTube (Unlisted)](https://youtube.com/watch?v=YOUR_VIDEO_ID)  
  * *Video Title format:* `[Team Name] - [Project Name] Hackathon Demo`
* 🎨 **Interactive Design Prototype:** [Figma Prototype / Canva Board](https://figma.com/file/YOUR_PROTOTYPE_LINK)
* 📊 **Presentation Slides:** [Google Slides / Canva Presentation](https://docs.google.com/presentation/d/YOUR_SLIDES_LINK)

---

## 💡 Ideation & Evolution

### 1. Mindmap & Visual Workflow
*Below is the structural mapping of our problem space, solution architecture, and primary user journey.*

![Ideation Mindmap & User Flow](assets/ideation-mindmap.png)

> **Diagram Description:**  
> *Briefly explain what the diagram above illustrates (e.g., "The mindmap above highlights the core problem branches identified, mapping user pain points directly to our target feature modules.")*

---

### 2. Breadth of Exploration
Before selecting our final approach, we evaluated multiple candidate concepts against feasibility and impact:

| Concept Considered | Pros | Cons |
| :--- | :--- | :--- |
| **Burnout Trajectory Forecasting + LLM Explanation** | <ul><li>Directly addresses the stated problem</li><li>Built entirely from data the app already collects (workload %, completion consistency, overdue backlog, time-on-task)</li></ul> | Slightly harder to build correctly (needs the explanation layer to avoid sounding alarmist) |
| **AI-Generated Visual Long-Term Goal Tracker** | <ul><li>Visually compelling concept</li><li>Clear tie to long-term motivation, which resonates with students</li></ul> | <ul><li>Weaker fit to problem stated because addresses motivation more than stress</li><li>Doesn't reduce workload or prevent burnout; it risks increasing pressure instead</li><li>Harder to make the AI generation reliably good in a short build window.</li></ul> |

Burnout Trajectory Forecasting is chosen as it's more tightly coupled to problem statement and target group On Feasibility, it also comes out ahead: it reuses data and infrastructure, whereas the goal tracker introduces extra, more open-ended technical and design work. The the goal tracker loses on nearly every axis judges will actually score.

---
### 3. Idea Evolution
<img width="1920" height="1080" alt="codenection dump (1)" src="https://github.com/user-attachments/assets/6ef17bc9-63a4-47e8-b1fa-46e7f3c02eb1" />

### 4. Feature Refinements & Iterations
Our core features progressed through several key iterations based on technical checks and user flow refinement:


## Feature: Task Logging & Check-Ins

* **V1:** Task logging + workload % calculation + basic plan output
* **Problem identified:** If a task passes its due date unmarked, the app has no way to tell whether the student forgot or genuinely overwhelmed -> false burnout signal.
* **V2 (ENHANCED):** Added a Check-In feature. When a task goes overdue unmarked, the app asks *"This one's overdue, what happened?"* with options (**Forgot about it** / **Still working on it** / **Too overwhelmed to start** / **Not a priority anymore**), classifying the cause before it affects the workload score.
* **V3 (INTEGRATE):**  Instead of check-ins,  app passively tracks engagement signals (how many times a task is opened, edited, or ignored) to detect early signs of overwhelm. It surfaces a soft check-in: "Looks like you might be overwhelmed by this one?" If confirmed, the AI Task Coach is triggered automatically, generating a step-by-step breakdown personalized to the student's current workload and mental state.

---

## Feature: AI Task Coach & Staged Workload Intervention

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

### 4. Mentor Consultation & Feedback Integration

| Mentor / Role | Key Feedback Received | Action Taken & Changes Made |
| :--- | :--- | :--- |
| **[Mentor Name / Role]** | *"The main workflow takes too many steps for the user to reach value."* | Redesigned the primary interface flow in Figma to reduce user actions from 4 screens down to 2. |
| **[Mentor Name / Role]** | *"Clarify how your solution differs from standard existing solutions."* | Highlighted our novel feature set and explicitly defined our target user constraints in the presentation slides. |
