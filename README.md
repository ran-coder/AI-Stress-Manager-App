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

| Concept Considered | Pros | Cons | Decision & Rationale |
| :--- | :--- | :--- | :--- |
| **Concept A:** [Brief Name] | Easy technical setup | Low novelty & differentiation | ❌ Dropped due to lack of distinct impact |
| **Concept B:** [Brief Name] | High theoretical impact | Exceeds time & API rate limits | ❌ Dropped due to scope constraints |
| **Final Concept:** [Project Name] | Strong target fit & high viability | Requires focused UI scope | ✅ Selected for development |

---
### 3. Idea Evolution
<img width="1920" height="1080" alt="codenection dump (1)" src="https://github.com/user-attachments/assets/6ef17bc9-63a4-47e8-b1fa-46e7f3c02eb1" />

### 4. Feature Refinements & Iterations
Our core features progressed through several key iterations based on technical checks and user flow refinement:


## Feature: Task Logging & Check-Ins

* **V1:** Task logging + workload % calculation + basic plan output
* **Problem identified:** If a task passes its due date unmarked, the app has no way to tell whether the student simply forgot or is genuinely overwhelmed — treating both cases the same risks a false burnout signal.
* **V2 (ENHANCED):** Added a Check-In feature. When a task goes overdue unmarked, the app asks *"This one's overdue, what happened?"* with options (**Forgot about it** / **Still working on it** / **Too overwhelmed to start** / **Not a priority anymore**), classifying the cause before it affects the workload score.

---

## Feature: AI Task Coach & Staged Workload Intervention

* **V1:** Task breakdown for complex tasks + soothing recommendations triggered by a single workload threshold.
* **Problem identified:** A single on/off threshold treats mild and severe stress the same way, with no proportional response.
* **V2 (REFINED):** Expanded into an AI Task Coach (chatbot-style comprehension help for complex tasks) plus a Staged Workload Intervention System. Workload severity broken into stages that escalate in both frequency and intervention type, culminating in a dedicated recovery mission mode at the most severe stage.

---

## Feature: Time Tracking

* **V1:** Manual start/stop timer per task. The longer the time takes to complete a task, the higher the chance of burnout.
* **Problem identified:** Manual timing adds extra cognitive effort every time a user starts a task.
* **V2 (REFINED):** Dropped the manual timer. Change it to a rough proxy for time spent, starting when a task is logged and ending when marked done, requiring zero extra effort from the user.

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
