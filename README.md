## At-Risk Student Profiling — School Bullying Clustering
Unsupervised Machine Learning project that identifies distinct student profiles based on bullying exposure, emotional well-being, and social behavior using K-Means clustering on a dataset of 56,981 students worldwide.

## Research Problem
Bullying in schools is a widespread issue with severe consequences on students' mental health, academic performance, and social development. Educational institutions often lack data-driven tools to identify which students are most at risk and what type of support they need.

This project addresses the question: **"Can we automatically identify groups of students with similar bullying-related profiles using unsupervised learning — without any predefined labels?"**

## Social Impact
- Early identification — detect at-risk students before problems escalate
- Targeted support — direct counseling and resources to the right groups
- Informed policy — help schools design evidence-based anti-bullying programs
- Pattern discovery — uncover hidden relationships between bullying, loneliness, and social support

## Project Overview
- DatasetBullying_2018.csv — 56,981 students, 18 features
- Final dataset 32,938 students, 13 features (after preprocessing)
- AlgorithmK-Means Clustering
- Optimal K3 clusters
- Silhouette Score0.246 (typical for social survey data)
- Dimensionality ReductionPCA — 7 components (64.5% variance explained)

## Key Steps
### 1. Data Preprocessing
- Handling missing values
- Removing redundant and duplicate columns:
    - Missed_classes_or_school_without_permission (binary duplicate of Miss_school_no_permission)
    - Most_of_the_time_or_always_felt_lonely (binary duplicate of Felt_lonely)
    - Were_obese (redundant with Were_overweight)
    - Were_underweight (near-zero variance — 95%+ were "No")
- Dropping rows with remaining missing values → 32,938 clean records
- Ordinal encoding for Likert-scale variables (preserving natural order):
    - felt_lonely: Never=0 → Always=4
    - students_kind, parents_understand: Never=0 → Always=4
    - physically_attacked, physical_fighting: 0 times=0 → 12+ times=12
    - missed_school: 0 days=0 → 10+ days=4
- Binary encoding: Yes/No columns → 1/0
- Age extraction: "14 years old" → 14 (integer)
- StandardScaler applied to all 13 features before modeling

### 2. Exploratory Data Analysis (EDA)
- Key findings:
    - ~22% of females and ~18% of males report being bullied at school
    - Peak risk age: 13–14 years old — risk decreases significantly after 16
    - Bullied students report significantly higher loneliness (median 2 vs 0)
    - Strong positive correlation between the three forms of bullying (0.29–0.36)
    - Strong negative correlation between felt_lonely and parents_understand (-0.30)

### Top 3 Factors Influencing Bullying
- bullied_outside +0.36 Bullying forms strongly co-occur
- cyber_bullied +0.29 Online and in-person bullying are linked
- felt_lonely +0.21 Bullied students feel significantly lonelier

### 3. Modeling
- Algorithm: K-Means Clustering
- Applied on PCA-reduced data (7 principal components, 64.5% variance explained).
- K selection methodology:
    - Elbow Method (KElbowVisualizer) → suggested K=7
    - Silhouette Score analysis (K=2 to 10) → highest score at K=2 (0.2361)
    - Final decision: K=3 — best balance between statistical quality and interpretability

### 4. Results — Cluster Profiles
- Cluster 1 — Well-Adjusted Students (67.6%)
  Not bullied across any dimension, emotionally stable, kind peers, supportive parents. Low-risk group representing the majority of students.
- Cluster 0 — Bullied & Isolated Students (28.4%)
  High bullying exposure across all forms (school: 0.85, outside: 0.92, cyber: 0.90). High loneliness (0.68), low parental support (-0.36), unkind peers (-0.38). These are the victims — highest priority for intervention.
- Cluster 2 — Violent & Disengaged Students (4.0%)
  Extremely high physical violence scores (attacked: 3.29, fighting: 3.47), high absenteeism (0.55), predominantly male. Likely the aggressors — require behavioral and disciplinary intervention.

### Key Findings
- 1 in 3 students falls into an at-risk category (bullied or violent)
- The "Bullied & Isolated" group (28.4%) is the most concerning — these students suffer in silence with minimal support from parents or peers
- Age 13–14 is the highest-risk window — preventive programs should prioritize this age group
- Parental involvement is a strong protective factor — students with understanding parents show significantly lower loneliness
- The "Violent & Disengaged" group (4%) is small but extreme — early intervention could prevent further escalation
- All three forms of bullying (school, outside, cyber) are strongly correlated — a student being bullied in one context is likely bullied in others
  

### Technologies Used
- pandas
- numpy
- matplotlib / seaborn
- plotly
- scikit-learn
- yellowbrick
