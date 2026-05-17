# Part 4: AI Solution Design Report

## Task 1: Choose a Business Domain
* [cite_start]**Selected Domain:** Education [cite: 1]

---

## Task 2: Define the Business Problem
* [cite_start]**What problem is being solved?** Student dropout risk[cite: 1]. [cite_start]The system proactively identifies students who are at high risk of disengaging or withdrawing from their courses before they officially drop out[cite: 1].
* **Who are the users or stakeholders?** Academic advisors, university administrators, student success coaches, and department heads.
* **What is the current manual or traditional process?** Academic advisors manually monitor attendance logs, midterm deficiency reports, and grade books to flag struggling students.
* [cite_start]**Limitations of the current process?** Based on institutional baseline data, the manual approach has severe operational bottlenecks[cite: 3]:
  * [cite_start]**High Latency:** The average resolution time to identify and intervene in a student's case takes up to **44.7 hours**[cite: 3].
  * [cite_start]**Massive Operational Drain:** Administrative staff spend over **500 hours monthly** on purely manual processing and tracking[cite: 3].
  * [cite_start]**Inaccuracy:** High human error rates peaking at **11.16%** mean vulnerable students are frequently missed until it is too late for an intervention[cite: 3].

---

## Task 3: Identify the AI Task Type
* [cite_start]**AI Task Type:** Classification [cite: 1]
* [cite_start]**Why it is suitable:** The objective is to categorize students into distinct groups (e.g., *At-Risk* vs. *Not At-Risk*) based on behavioral patterns[cite: 1]. This binary classification approach allows the system to generate a highly accurate, actionable priority list for student success teams.

---

## Task 4: Data Requirement Plan
* [cite_start]**Type of data needed:** Attendance, assignment, and assessment data[cite: 1].
* [cite_start]**Structured or unstructured data:** Structured data extracted directly from university core databases[cite: 1].
* [cite_start]**Input features:** * *Academic Metrics:* Assignment submission rates, quiz scores, exam grades, and cumulative GPA trajectory[cite: 1].
  * [cite_start]*Behavioral Metrics:* LMS (Learning Management System) login frequencies and class attendance percentages[cite: 1].
* **Target variable or labels:** Binary risk status (`1` for dropped out, `0` for remained enrolled).
* **Data collection method:** Automated nightly ETL pipelines pulling direct logs from Student Information Systems (SIS) and LMS platforms (e.g., Canvas, Blackboard).
* **Data quality risks:** Missing records due to faculty delay in grade entries, sync errors between systems, and data drift due to changes in curriculum difficulty over different semesters.

---

## Task 5: Model Recommendation
* [cite_start]**Recommended Model/Architecture:** Feed-forward neural network [cite: 1]
* [cite_start]**Why it is appropriate:** Because the input data consists of structured, tabular metrics (such as grades and attendance percentages), a multi-layer Feed-forward Neural Network is ideal[cite: 1]. It efficiently processes non-linear interactions between disparate variables—such as a student maintaining passing grades but showing a sudden 40% drop in platform logins—capturing risk flags that traditional linear models miss.

---

## Task 6: Evaluation Plan
* [cite_start]**Technical Metrics:** * **Recall:** Maximizing recall is critical because a False Negative (missing a student who actually needs help) is far more damaging than a False Positive (checking in on a stable student)[cite: 1].
  * **F1-Score:** To maintain an optimal balance between precision and recall.
* [cite_start]**Business Metrics:** * **Reduction in Manual Processing Hours:** Cutting down historical administrative overhead from peak levels (>500 hours) by at least 50%[cite: 3].
  * [cite_start]**Resolution Time:** Accelerating case intervention routing from over 34 hours down to under 12 hours[cite: 3].
  * [cite_start]**Error Rate:** Dropping tracking errors significantly below the current baseline average[cite: 3].
* **Possible Failure Cases:** * *False Positive Fatigue:* Bombarding advisors with too many low-risk flags, causing them to disregard system notifications.
  * *Concept Drift:* The model becoming less accurate over time as teaching styles or student demographics change.
* **Human Review or Validation Process:** The AI system functions strictly as a decision-support tool. High-risk flags are routed to an advisor dashboard, allowing a human professional to review the student's holistic context before initiating an empathetic outreach plan.

---

## Task 7: Responsible AI Considerations
* [cite_start]**Bias in data:** Historical data might reflect systemic inequalities, leading the model to disproportionately flag specific student demographics[cite: 1].
* [cite_start]**Privacy concerns:** Over-monitoring digital footprints (like tracking every login time) can feel invasive to students[cite: 1].
* **Over-reliance on AI:** Advisors might rely entirely on automated scores and neglect students who are struggling emotionally but maintaining stable grades.
* **Mitigation Plan:** Demographics (such as gender, race, or zip code) are strictly excluded from training features to avoid label bias. Data collection is confined exclusively to on-platform academic interactions, and regular human oversight is maintained to review model behavior.

---

## Task 8: Final Solution Summary (The One-Pager)

| Section | Description |
| :--- | :--- |
| **Problem** | [cite_start]Manual student risk tracking is too slow (taking up to 44.7 hours) and error-prone (~11% error rate), causing vulnerable students to drop out before receiving help[cite: 3]. |
| **Proposed AI Solution** | [cite_start]An automated Classification system that analyzes daily LMS and attendance behavior to flag early-warning signs of student disengagement[cite: 1]. |
| **Required Data** | [cite_start]Structured attendance history, assignment submission timeliness, and continuous assessment scores[cite: 1]. |
| **Model Recommendation** | [cite_start]**Feed-forward Neural Network** optimized to identify complex risk patterns within tabular student data[cite: 1]. |
| **Expected Business Impact** | [cite_start]Reduce administrative case resolution delays by over 60%, lower manual data processing workloads, and systematically improve student retention rates[cite: 3]. |
| **Risks & Mitigation Plan** | [cite_start]*Risk:* Label bias leading to unfair demographic flagging[cite: 1]. <br> *Mitigation:* Exclude all sensitive demographic indicators from the data pipeline, training solely on behavioral performance metrics. |
