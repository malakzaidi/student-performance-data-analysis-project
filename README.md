# Student Performance Data Analysis Project 📊

Welcome to the **Student Performance Data Analysis Project**, a cutting-edge data science initiative designed to transform educational outcomes through advanced analytics. Conducted as part of the Digital Culture module in the Master's program in Distributed Systems and Artificial Intelligence (SDIA) at ENSET, University Hassan II, Casablanca, this project leverages **Python** 🐍 for robust data processing and predictive modeling, and **Power BI** 📈 for dynamic, interactive visualizations. The result is a comprehensive analysis that uncovers actionable insights into student academic performance, offering a blueprint for data-driven educational improvement.

This repository contains the complete codebase, dataset, visualizations, and a detailed report, analyzing engagement metrics, demographic factors, and academic outcomes. We identify key predictors of success, highlight disparities across gender, subjects, and academic periods, and propose evidence-based strategies to enhance teaching practices and student outcomes. This project is a valuable resource for educators, data scientists, and policymakers aiming to foster equitable and effective learning environments.

## Table of Contents 📋

- [Project Overview](#project-overview)
- [Dataset Description](#dataset-description)
- [Methodology](#methodology)
  - [Data Cleaning and Preparation](#data-cleaning-and-preparation)
  - [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
  - [Predictive Modeling](#predictive-modeling)
  - [Interactive Visualization](#interactive-visualization)
- [Key Findings](#key-findings)
- [Visualizations and Interpretations](#visualizations-and-interpretations)
  - [Python Visualizations](#python-visualizations)
  - [Power BI Visualizations](#power-bi-visualizations)
- [Recommendations](#recommendations)
- [How to Run the Project](#how-to-run-the-project)
- [Future Work](#future-work)
- [Acknowledgments](#acknowledgments)
- [Contact](#contact)

## Project Overview

The **Student Performance Data Analysis Project** analyzes a dataset of 480 student records with 17 variables to understand the dynamics of academic success in a real-world educational context. By combining descriptive analytics, predictive modeling, and interactive visualizations, we address critical challenges such as student engagement, gender disparities, and subject-specific performance gaps. Our mission is to empower educational institutions with insights that drive meaningful change.

### Objectives 🎯

- **Identify Key Drivers**: Pinpoint factors (e.g., engagement, attendance, parental involvement) that significantly impact student performance.
- **Analyze Disparities**: Explore performance differences by gender, subject, academic period, and nationality to address inequities.
- **Predict Outcomes**: Build a machine learning model to forecast student performance and identify at-risk students.
- **Visualize Insights**: Create interactive dashboards for intuitive exploration and decision-making.
- **Propose Interventions**: Recommend practical, data-driven strategies to improve student success and teaching effectiveness.

### Tools and Technologies 🛠️

- **Python** 🐍: Data cleaning, exploratory data analysis (EDA), and predictive modeling.
  - Libraries: `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`.
- **Power BI** 📈: Interactive dashboards and visualizations.
- **Jupyter Notebook** 📓: Interactive development and documentation.
- **Dataset Format**: CSV (`student-dataset.csv`).

## Dataset Description

The dataset, sourced from [Kaggle's xAPI-Edu-Data](https://www.kaggle.com/datasets/aljarah/xAPI-Edu-Data/data), comprises 480 observations and 17 variables, providing a rich foundation for analysis:

- **Demographic Variables**: `gender`, `NationalITy`, `PlaceofBirth`.
- **Academic Variables**: `StageID`, `GradeID`, `SectionID`, `Topic`, `Semester`, `Class` (target variable: `L` = Low, `M` = Medium, `H` = High, representing academic performance levels).
- **Engagement Metrics**: `raisedhands` (class participation), `VisITedResources` (resource usage), `AnnouncementsView` (engagement with announcements), `Discussion` (participation in discussions).
- **Contextual Variables**: `Relation`, `ParentAnsweringSurvey`, `ParentschoolSatisfaction`, `StudentAbsenceDays` (categorized as `Under-7` or `Above-7`).

The dataset was clean, with no missing values, and was enriched with derived features to enhance analysis:

- `ClassNumeric`: Numerical mapping of `Class` (`L=0`, `M=1`, `H=2`).
- `Failed`: Binary indicator for failure (`Yes` for `L`, `No` otherwise).
- `EngagementScore`: Average of engagement metrics (`raisedhands`, `VisITedResources`, `AnnouncementsView`, `Discussion`).
- `Period`: Combined `StageID` and `Semester` (e.g., `HighSchool_F`) for temporal analysis.

## Methodology

The project follows a rigorous data science pipeline to ensure robust analysis and actionable outcomes.

### Data Cleaning and Preparation

- **Tools**: Python (`pandas`, `numpy`).
- **Steps**:
  - Loaded the dataset and verified no missing values using `df.isnull().sum()`.
  - Removed 2 duplicate records, resulting in 478 unique observations.
  - Standardized categorical variables (e.g., `gender` to uppercase, `NationalITy` capitalized) for consistency.
  - Applied the Interquartile Range (IQR) method to detect outliers in numerical columns (`raisedhands`, `VisITedResources`, `AnnouncementsView`, `Discussion`); no significant outliers were found.
  - Created derived features:
    - `ClassNumeric` for quantitative analysis.
    - `Failed` for failure-focused visualizations.
    - `EngagementScore` as a composite engagement metric.
    - `Period` for temporal trends.
  - Saved cleaned and enriched datasets as `student_data_cleaned.csv` and `student_data_enriched.csv`.

### Exploratory Data Analysis (EDA)

- **Tools**: Python (`matplotlib`, `seaborn`).
- **Purpose**: Uncover relationships between engagement, demographics, and performance through visualizations.
- **Visualizations**: Detailed in the [Python Visualizations](#python-visualizations) subsection below.

### Predictive Modeling

- **Algorithm**: Random Forest Classifier (`scikit-learn`).
- **Features**: `raisedhands`, `VisITedResources`, `AnnouncementsView`, `Discussion`, `StudentAbsenceDays`, `ParentAnsweringSurvey`, `ParentschoolSatisfaction`.
- **Target**: `ClassNumeric`.
- **Steps**:
  - One-hot encoded categorical variables using `pd.get_dummies`.
  - Split data: 70% training, 30% testing (`train_test_split`).
  - Trained a Random Forest model with 100 estimators.
  - Evaluated performance using precision, recall, F1-score, and confusion matrix.
  - Saved feature importance to `feature_importance.csv` and predictions to `student_data_enriched.csv`.

### Interactive Visualization

- **Tool**: Power BI.
- **Steps**:
  - Imported `student_data_enriched.csv` into Power BI.
  - Defined DAX measures (e.g., `AtRiskPercentage`, `SuccessRate`, `AverageEngagementScore`) and calculated columns (e.g., `ParentalParticipationIndex` by semester).
  - Created interactive dashboards with filters for `Semester`, `Gender`, `Topic`, `NationalITy`.
  - Visualizations included bar charts, stacked bars, violin plots, and KPI cards.
  - Optimized DAX queries for performance and published dashboards to Power BI Service ([Power BI Report](https://app.powerbi.com/groups/me/reports/6f971c6e-b5fc-4af1-ac68-f50bd214014e?ctid=2ec11419-847c-4e29-8815-7f5b2fed9339&pbi_source=linkShare)).

## Key Findings

The analysis delivers profound insights into student performance, validated through Python visualizations, Power BI dashboards, and predictive modeling:

1. **Engagement is the Cornerstone of Success** 💡:
   - Students with `EngagementScore` > 70 are almost exclusively in the `H` (High) class, while those with scores < 30 are predominantly in the `L` (Low) class.
   - Random Forest feature importance confirms engagement metrics as top predictors: `VisITedResources` (24.2%), `raisedhands` (20.9%), `AnnouncementsView` (18.4%), and `Discussion` (14.5%).
   - **Implication**: Engagement is a modifiable factor that schools can target through interactive teaching, digital resources, and active learning strategies.

2. **Gender Disparities Highlight Inequities** ⚖️:
   - Girls outperform boys, with a failure rate of 12% (20/170) compared to 32% (90/280) for boys, and higher representation in the `H` class (35% vs. 21%).
   - Boys with low engagement and frequent absences are particularly at risk, suggesting motivational, behavioral, or external challenges.
   - **Implication**: Gender-specific interventions, such as mentorship for boys and STEM encouragement for girls, can address these gaps.

3. **Subject-Specific Engagement Varies Widely** 📚:
   - **High Engagement Subjects**:
     - Biology: 75.8% in `H`, but only 6.6% in `L`, showing a 69.2-point gap.
     - Science: 74.8% in `H`, indicating strong student interest.
     - History: 71.1% in `M`, suggesting effective teaching methods for mid-tier students.
   - **Low Engagement Subjects**:
     - Math, IT, and French show consistently low engagement, especially in `L` (e.g., Math at 10%, IT at 15%).
     - These subjects may suffer from abstract content, lack of practical applications, or unengaging pedagogy.
   - **Implication**: Subjects like Biology and History offer pedagogical models that can be applied to struggling disciplines.

4. **Temporal Trends Reveal Critical Periods** ⏰:
   - Performance improves in the second semester (`S`) across all levels, with a peak in `HighSchool_S` (mean `ClassNumeric` = 1.4, between `M` and `H`).
   - A significant dip occurs in `MiddleSchool_F` (mean `ClassNumeric` ~ 0.9, close to `L`), likely due to the challenging transition to middle school.
   - **Implication**: Targeted support during the first semester, especially in middle school, can prevent early setbacks.

5. **Absences are a Major Risk Factor** 🚨:
   - Students with `Above-7` absences are significantly more likely to fail, particularly when combined with low engagement (`EngagementScore` < 30).
   - Absences have a stronger impact in the second semester, possibly due to cumulative effects or missed critical content.
   - **Implication**: Early absence monitoring and intervention can mitigate risks.

6. **Nationality Influences Performance** 🌍:
   - Kuwaiti students exhibit higher average performance, while students from Egypt and Jordan lag, potentially due to linguistic, cultural, or resource access barriers.
   - Girls outperform boys across most nationalities, except in Iraq and Syria, where performance gaps are narrower.
   - **Implication**: Tailored support for underperforming nationalities can promote equity.

7. **Predictive Model Performance is Robust** ✅:
   - The Random Forest model achieved:
     - `L` class: Precision 0.84, Recall 0.86, F1-score 0.85 (critical for identifying at-risk students).
     - `M` class: Precision 0.73, Recall 0.73, F1-score 0.73 (most errors due to overlap with `L` and `H`).
     - `H` class: Precision 0.73, Recall 0.71, F1-score 0.72.
   - Confusion matrix: 37, 46, and 27 correct predictions for `L`, `M`, and `H`, respectively.
   - **Implication**: The model is effective for early identification of at-risk students but can be refined for `M` class accuracy.

## Visualizations and Interpretations

Below are all visualizations, separated into **Python Visualizations** and **Power BI Visualizations** for clarity. Each visualization includes a detailed description, observations, interpretations, and implications for education. Screenshots are embedded from provided GitHub links and will be added to the `visualizations/` folder.

### Python Visualizations

1. **Distribution of Raised Hands by Failure Status** 📈
   ![Image](https://github.com/user-attachments/assets/4225fa2e-52cd-44b0-a683-de937c21e472)
   - **Type**: FacetGrid (Seaborn).
   - **Description**: Displays the kernel density estimate of `raisedhands` for failing (`Class=L`, orange) vs. successful (`Class=M` or `H`, blue) students.
   - **Observations**:
     - Failing students show a sharp peak at 10-20 `raisedhands`, indicating minimal class participation.
     - Successful students have a broader distribution, peaking at 50-70, reflecting active engagement.
     - Overlap at 20-50 suggests moderate participation is not sufficient for success.
   - **Interpretation**: Low participation is a strong indicator of academic struggle, likely reflecting lack of interest, confidence, or understanding. The overlap indicates that other factors (e.g., resource usage, attendance) are critical for success. The distinct peaks suggest participation thresholds that differentiate failing and successful students.
   - **Implication**: Implement interactive teaching methods (e.g., group discussions, quizzes, polls) to boost participation, especially for boys, who show lower engagement in failing groups. Regular feedback on participation can motivate students to engage more actively.

2. **Class Distribution by Gender** 👥
   ![Image](https://github.com/user-attachments/assets/0a5a1e2a-7003-4216-9f9c-78b57724b7a4)
   - **Type**: Countplot (Seaborn).
   - **Description**: Shows the number of students in each class (`L`, `M`, `H`) by gender (`M`, `F`).
   - **Observations**:
     - Boys: 130 in `M`, 90 in `L`, 60 in `H` (total 280).
     - Girls: 90 in `M`, 60 in `H`, 20 in `L` (total 170).
     - Girls have a lower failure rate (12% vs. 32%) and higher `H` representation (35% vs. 21%).
   - **Interpretation**: Girls demonstrate stronger academic performance, possibly due to better study habits, time management, or intrinsic motivation. Boys' higher failure rate suggests they face unique challenges, particularly in engagement and attendance, which may be influenced by behavioral or external factors. The skewed distribution highlights a need for gender-focused interventions.
   - **Implication**: Offer targeted support for boys (e.g., mentorship, motivational workshops, behavioral counseling) and encourage girls to pursue high-achieving paths, such as STEM careers or leadership roles. Analyze underlying factors (e.g., peer influence, parental expectations) contributing to gender disparities.

3. **Engagement Score by Subject and Class** 📚
   ![Image](https://github.com/user-attachments/assets/7171eb65-5840-4305-a65a-46dddd671f04)
   - **Type**: Boxplot (Seaborn).
   - **Description**: Displays `EngagementScore` across subjects (`Topic`) and classes (`L`, `M`, `H`).
   - **Observations**:
     - `H` class: High engagement (median 60-80), e.g., Biology (80, IQR 70-90), Geology (75, IQR 65-85).
     - `L` class: Low engagement (median 10-20), e.g., Math (10, IQR 5-15), IT (15, IQR 10-20).
     - `M` class: Moderate engagement (median 40-60), with History at 65 (IQR 55-75).
     - Biology shows the largest gap (69.2 points between `H` and `L`).
   - **Interpretation**: Engagement strongly correlates with performance, with `H` students showing consistent involvement across subjects. Low engagement in Math, IT, and French for `L` students suggests these subjects may be perceived as difficult, abstract, or unengaging. Biology and History's success indicates effective pedagogical approaches, likely involving hands-on activities (e.g., labs) or discussion-based methods. The large gap in Biology highlights its potential as a model for engaging high-performing students.
   - **Implication**: Introduce interactive elements (e.g., coding projects for IT, real-world applications for Math, conversational practice for French) to boost engagement in struggling subjects. Share best practices from Biology and History, such as experiential learning, across the curriculum. Conduct teacher training to enhance engagement-focused pedagogy.

4. **Engagement vs. Performance by Gender and Absences** 📉
   ![Image](https://github.com/user-attachments/assets/ab3f911f-96aa-4ebe-88e6-90ef7a06e345)
   - **Type**: Scatter Plot (Seaborn).
   - **Description**: Plots `EngagementScore` (x-axis) vs. `ClassNumeric` (y-axis), colored by gender (`M`, `F`) and sized by absence level (`Under-7`, `Above-7`).
   - **Observations**:
     - High engagement (>70) predicts `H` class, regardless of gender or absences.
     - `Above-7` absences (larger points) and low engagement (<30) strongly predict `L` class.
     - Girls maintain `M` or `H` performance at moderate engagement (30-50), while boys are overrepresented in `L` at similar levels.
     - `Under-7` absences are associated with `M` or `H` classes.
   - **Interpretation**: Engagement and attendance are critical predictors of success, with clear thresholds separating performance levels. Girls' resilience at moderate engagement suggests better learning strategies, adaptability, or motivation. Boys with frequent absences and low engagement are at high risk, indicating potential behavioral issues, lack of motivation, or external challenges (e.g., family responsibilities). The strong correlation between absences and failure underscores attendance as a modifiable risk factor.
   - **Implication**: Implement real-time absence tracking systems and engagement-focused interventions (e.g., peer mentoring, gamified learning) for boys. Encourage consistent attendance through parent communication and school policies. Develop targeted support for students with moderate engagement to push them toward `H` performance.

5. **Performance Evolution by Period** 📅
   ![Image](https://github.com/user-attachments/assets/dde08180-d070-4aad-bf6f-426ea950ecaa)
   - **Type**: Line Plot (Seaborn).
   - **Description**: Shows average `ClassNumeric` across academic periods (e.g., `LowerLevel_F`, `MiddleSchool_S`).
   - **Observations**:
     - Peak in `HighSchool_S` (mean 1.4, between `M` and `H`).
     - Dip in `MiddleSchool_F` (mean ~0.9, close to `L`).
     - Second semesters (`S`) consistently show higher performance (e.g., `LowerLevel_S` at 1.2, `MiddleSchool_S` at 1.1).
   - **Interpretation**: Second-semester improvements suggest students adapt to academic demands over time, possibly due to better study habits, teacher feedback, or exam preparation. The `MiddleSchool_F` dip indicates a challenging transition, potentially due to increased academic rigor, new teaching methods, or social adjustments. High performance in `HighSchool_S` reflects student maturity, targeted preparation for exams, or effective teaching strategies. The consistent semester trend suggests systemic factors that can be leveraged.
   - **Implication**: Provide transition support (e.g., orientation programs, study skills workshops, peer mentoring) for MiddleSchool students in the first semester. Analyze `HighSchool_S` success factors (e.g., curriculum design, teacher training) for broader application. Implement early-semester interventions to mitigate performance dips.

6. **Confusion Matrix** 🧮
   ![Image](https://github.com/user-attachments/assets/f1752cd1-b28a-4ee0-856e-c11ab1637b8f)
   - **Type**: Heatmap (Seaborn).
   - **Description**: Displays Random Forest predictions vs. actual classes (`L`, `M`, `H`).
   - **Observations**:
     - Correct predictions: 37 (`L`), 46 (`M`), 27 (`H`).
     - Errors: 6 `L` misclassified as `M`, 7 `M` as `L`, 10 `M` as `H`, 11 `H` as `M`.
     - `L` class is best predicted; `M` has the most errors due to overlap.
   - **Interpretation**: The model excels at identifying at-risk students (`L`), which is critical for early intervention, with high precision and recall. Errors in `M` reflect its intermediate nature, making it harder to distinguish from `L` or `H` due to overlapping characteristics (e.g., moderate engagement). The model's performance is satisfactory but indicates room for improvement, particularly for mid-tier students. The high accuracy for `L` suggests reliable identification of students needing urgent support.
   - **Implication**: Enhance the model by including additional features (e.g., `Topic`, `NationalITy`, `GradeID`) to reduce `M` class errors. Deploy the model in a real-time monitoring system to flag at-risk students early. Use misclassification insights to refine intervention strategies for `M` students.

7. **Heatmap of Engagement by Subject and Class** 🌡️
   ![Image](https://github.com/user-attachments/assets/c1abe3f9-2da2-494e-b20f-186d67fc899d)
   - **Type**: Heatmap (Seaborn).
   - **Description**: Shows average `EngagementScore` by subject (`Topic`) and class (`L`, `M`, `H`).
   - **Observations**:
     - `H` class: High engagement (60-70%), e.g., Biology (75.8%), Science (74.8%), Quran (73.2%).
     - `L` class: Low engagement (10-30%), e.g., Biology (6.6%), Math (10%), IT (15%).
     - `M` class: Moderate engagement (36-71%), with History at 71.1%.
     - Geology lacks data for `L`, limiting analysis.
   - **Interpretation**: The stark contrast in engagement between classes underscores its role as a primary driver of performance. Biology's success in `H` suggests engaging content (e.g., labs, experiments) or effective teaching methods. History's strength in `M` indicates potential for mid-tier students to improve with targeted engagement strategies. Low engagement in Math and IT across all classes points to pedagogical challenges, such as abstract content or lack of interactive methods. The missing Geology data for `L` suggests a need for further data collection.
   - **Implication**: Replicate Biology's hands-on methods (e.g., practical experiments) in Math and IT (e.g., coding challenges, real-world applications). Develop targeted interventions for `L` students in low-engagement subjects, such as Math tutoring or IT workshops. Collect additional data for Geology to complete the analysis.

### Power BI Visualizations

1. **Tableau de Bord Global** 🌐
   ![Image](https://github.com/user-attachments/assets/8445db31-2448-44f5-86ec-b05b098d0e90)
   - **Description**: Overview dashboard with KPIs: `AtRiskPercentage`, `SuccessRate`, `AverageEngagementScore`, `TotalStudents`, `ParentalParticipationIndex`.
   - **Observations**:
     - `AtRiskPercentage`: 24% of students are at risk (`L` class).
     - `SuccessRate`: 74% achieve `M` or `H`.
     - `AverageEngagementScore`: 44.54/100, indicating moderate engagement.
     - `TotalStudents`: 478.
     - `ParentalParticipationIndex`: 47/100, suggesting moderate parental involvement.
   - **Interpretation**: The 24% at-risk rate highlights a significant group needing immediate intervention, representing a critical opportunity for improvement. The 74% success rate is promising but masks disparities (e.g., gender, nationality). Moderate engagement and parental involvement indicate untapped potential, as both are modifiable factors. The dashboard's high-level metrics provide a snapshot for stakeholders to prioritize resources.
   - **Implication**: Prioritize at-risk students with personalized support (e.g., tutoring, counseling). Engage parents through workshops or communication campaigns to boost participation. Use the dashboard to monitor progress and adjust strategies.

2. **Performance by Nationality** 🌍
   ![Image](https://github.com/user-attachments/assets/5bf6d02e-117d-46c9-b9c9-3950f8917300)
   - **Description**: Bar chart showing average performance (`ClassNumeric`) by nationality, split by gender.
   - **Observations**:
     - Kuwaiti students lead (mean `ClassNumeric` 1.5), followed by Lebanese (1.3).
     - Egyptian and Jordanian students lag (mean ~0.8-1.0).
     - Girls outperform boys in most nationalities, except Iraq and Syria, where gaps are narrower.
   - **Interpretation**: Performance disparities may stem from cultural, linguistic, or resource access differences, with Kuwaiti students benefiting from better educational infrastructure. Girls' consistent outperformance suggests gender-specific strengths, such as study habits or motivation. The narrower gaps in Iraq and Syria may reflect unique cultural or educational contexts, warranting further investigation.
   - **Implication**: Offer language and cultural support for Egyptian and Jordanian students (e.g., bilingual resources, cultural integration programs). Analyze Iraq/Syria data to understand performance patterns. Promote gender equity by leveraging girls' strengths in leadership roles.

3. **Factors of Influence** 🔑
   ![Image](https://github.com/user-attachments/assets/3f3c7ab7-fe8b-4b97-ab34-af5d355b7670)
   - **Description**: Stacked bar chart highlighting key performance factors based on Random Forest feature importance.
   - **Observations**:
     - `EngagementScore` (68%), `VisITedResources` (67%), `raisedhands` (65%) are top influencers.
     - `Discussion` (30%) and `AnnouncementsView` (53%) have lower impact.
     - `StudentAbsenceDays` (60%) and `ParentAnsweringSurvey` (55%) are moderate influencers.
   - **Interpretation**: Engagement metrics dominate performance prediction, confirming their centrality to academic success. The lower impact of `Discussion` suggests discussions may not be structured to maximize learning (e.g., lack of guided questions or participation incentives). Absences and parental involvement are significant but secondary, indicating their role as supporting factors.
   - **Implication**: Enhance discussion formats (e.g., structured debates, peer-led discussions) and promote announcement engagement through digital platforms. Strengthen attendance policies and parental engagement initiatives to complement engagement-focused strategies.

4. **Filtres Interactifs** 🎛️
   ![Image](https://github.com/user-attachments/assets/17dd60d3-46e7-4644-9a43-039f2e5eeda0)
   - **Description**: Interactive filters for `Semester`, `Gender`, `Topic`, `Class`, `NationalITy`, `StageID`, enabling granular analysis.
   - **Observations**:
     - Filtering by `Topic` reveals Math's challenges (70% of `L` students have `EngagementScore` < 20).
     - Gender filters highlight boys' higher failure rates (32% vs. 12%).
     - `Semester` filters show improved performance in `S` (e.g., `HighSchool_S` at 1.4).
   - **Interpretation**: Filters enable stakeholders to drill down into specific groups or subjects, pinpointing areas of concern. Math's persistent low engagement underscores the need for pedagogical reform. Gender and semester trends reinforce earlier findings, providing actionable context for interventions.
   - **Implication**: Use filters to identify at-risk subgroups (e.g., boys in Math, first-semester MiddleSchool students) and tailor interventions (e.g., Math workshops, transition programs). Train educators to use the dashboard for data-driven decision-making.

5. **Analyse des Modèles d'Engagement** 📊
   ![Image](https://github.com/user-attachments/assets/7910311b-821a-4ca2-be67-4115168237fe)
   - **Description**: Visualizes `EngagementScore` vs. `ClassNumeric` by gender, with trend lines for clarity.
   - **Observations**:
     - `EngagementScore` > 70 predicts `H`; < 30 predicts `L`.
     - Girls maintain `M` or `H` at moderate engagement (30-50); boys fail more often at similar levels (32% in `L`).
     - Trend lines show steeper improvement for girls as engagement increases.
   - **Interpretation**: Engagement thresholds are clear predictors of performance, with distinct cutoffs for success and failure. Girls' resilience at moderate engagement suggests better coping mechanisms, study habits, or motivation. Boys' higher failure rate at similar engagement levels indicates a need for targeted motivational strategies.
   - **Implication**: Develop gender-specific engagement strategies, focusing on boys' early intervention (e.g., gamified learning, peer support). Encourage girls to maintain high engagement through advanced opportunities (e.g., STEM projects).

6. **Analyse de Performance vs. Absence** 🕰️
   ![Image](https://github.com/user-attachments/assets/e2211c71-f7c8-42ce-87df-eda2ed2bd6f8)
   - **Description**: Analyzes absence impact (`Under-7`, `Above-7`) on performance (`ClassNumeric`) by semester.
   - **Observations**:
     - `Above-7` absences lower performance (mean `ClassNumeric` ~0.7), especially in second semester.
     - First semester has higher absences (30% `Above-7`) but improving performance in `S` (mean 1.2).
     - `Under-7` absences correlate with `M` or `H` (mean 1.3).
   - **Interpretation**: Absences compound over time, with greater impact in the second semester due to missed critical content or cumulative effects. First-semester absences may reflect adjustment issues, while second-semester improvements suggest recovery efforts (e.g., catch-up programs). Attendance is a key lever for performance improvement.
   - **Implication**: Implement real-time absence tracking and early interventions (e.g., parent notifications, attendance incentives). Expand recovery programs in the second semester to sustain performance gains.

7. **Impact de l'Absence sur la Performance** 🚨
   ![Image](https://github.com/user-attachments/assets/180e6eae-ccf2-4392-8bc0-6b5df9ef3c93)
   - **Description**: Visualizes absence trends (`Under-7`, `Above-7`) and their impact on performance by class and semester.
   - **Observations**:
     - `Above-7` absences strongly correlate with `L` class (80% of `L` students), especially in `S`.
     - Performance improves in `S` despite absences (mean `ClassNumeric` 1.1 vs. 0.9 in `F`).
     - `Under-7` absences align with `M` or `H` (90% of `H` students).
   - **Interpretation**: Absences are a modifiable risk factor, with a clear link to failure. Second-semester improvements indicate effective interventions or student resilience. The strong correlation between low absences and success underscores the importance of consistent attendance.
   - **Implication**: Strengthen absence policies (e.g., mandatory counseling after 7 absences) and support recovery programs (e.g., make-up assignments). Promote attendance through positive reinforcement (e.g., recognition programs).

8. **Tableau de Bord d'Engagement Ajusté** ⚙️
   ![Image](https://github.com/user-attachments/assets/696b16f3-dad4-4968-8577-9fb1405f63da)
   - **Description**: Shows adjusted engagement metrics (`EngagementScore` normalized by subject and semester) and recommendations.
   - **Observations**:
     - Adjusted engagement: 48.99/100, indicating potential for growth.
     - Low `EngagementScore` students (<30) are flagged for interactive activities.
     - High `EngagementScore` students (>70) are recommended for advanced roles.
   - **Interpretation**: The adjusted engagement score accounts for subject difficulty and semester variations, providing a fair benchmark. Moderate engagement suggests significant room for improvement through targeted strategies. Flagging low-engagement students enables proactive intervention.
   - **Implication**: Use adjusted engagement as a benchmark to evaluate intervention effectiveness. Implement recommended activities (e.g., group projects for low scorers, leadership roles for high scorers) to optimize engagement.

9. **Tableau de Recommandations d'Engagement** 💡
   ![Image](https://github.com/user-attachments/assets/f0881a81-afb1-430e-b986-2bd1cab08022)
   - **Description**: Lists personalized engagement recommendations based on `EngagementScore` ranges.
   - **Observations**:
     - Low scores (<30): "Engage more in discussions and access online resources."
     - Moderate scores (30-70): "Participate actively in class and review announcements."
     - High scores (>70): "Good work! Consider leadership roles or peer tutoring."
   - **Interpretation**: Personalized recommendations provide actionable steps for students and teachers, aligning interventions with engagement levels. The tiered approach ensures relevance for all performance levels, fostering a tailored educational experience.
   - **Implication**: Integrate recommendations into student feedback systems (e.g., report cards, parent-teacher meetings). Train teachers to use recommendations to guide classroom strategies, enhancing student engagement.

10. **Report's QR Code** 🔗
    ![Image](https://github.com/user-attachments/assets/1143b71b-fb51-4683-a421-bb24739065a9)
    - **Description**: QR code linking to the Power BI report for interactive exploration of the dashboards.
    - **Link**: [Power BI Report](https://app.powerbi.com/groups/me/reports/6f971c6e-b5fc-4af1-ac68-f50bd214014e?ctid=2ec11419-847c-4e29-8815-7f5b2fed9339&pbi_source=linkShare)
    - **Observations**: Provides direct access to the published Power BI report, enabling stakeholders to interact with visualizations and filters.
    - **Interpretation**: The QR code facilitates easy access to the interactive dashboards, enhancing stakeholder engagement with the analysis.
    - **Implication**: Encourage educators and policymakers to scan the QR code to explore the dashboards and derive actionable insights for decision-making.

## Recommendations 💡

Based on the findings, we propose the following evidence-based strategies to improve student performance:

1. **Targeted Support for At-Risk Students** 🎯:
   - Use predictive model outputs to identify students with low `EngagementScore`, `Above-7` absences, or male gender early in the semester.
   - Offer personalized tutoring, mentorship, and counseling to address academic and behavioral challenges.
   - Implement absence alerts after 7 days via automated systems (e.g., SMS notifications to parents).

2. **Interactive Pedagogical Methods** 🧑‍🏫:
   - Introduce gamification (e.g., quizzes, leaderboards), coding projects, and real-world applications in Math, IT, and French to boost engagement.
   - Replicate Biology and History's hands-on and discussion-based methods (e.g., labs, debates) across subjects.
   - Conduct teacher training on interactive pedagogy to enhance classroom engagement.

3. **First-Semester Focus** 📅:
   - Develop transition programs for MiddleSchool students in the first semester, including study skills workshops, peer mentoring, and orientation sessions.
   - Investigate Math and IT challenges in `MiddleSchool_F` (e.g., curriculum complexity, teaching methods) through focus groups or surveys.

4. **Encourage Female Excellence** 🚀:
   - Leverage girls' strong performance to promote STEM participation through scholarships, clubs, and leadership programs.
   - Ensure equitable opportunities for high-achieving girls to maintain their trajectory.

5. **Enhance Engagement** 🌟:
   - Incentivize `raisedhands` and `VisITedResources` through rewards (e.g., badges, certificates, recognition).
   - Promote active learning environments with group projects, flipped classrooms, and interactive discussions.

6. **Address Nationality Gaps** 🌍:
   - Provide language and cultural support for Jordanian and Egyptian students through bilingual resources, tutoring, and cultural integration programs.
   - Analyze Iraq/Syria performance anomalies to identify specific needs (e.g., curriculum adjustments, counseling).

7. **Refine Predictive Model** ⚙️:
   - Incorporate additional features (e.g., `Topic`, `NationalITy`, `GradeID`) to improve `M` class accuracy.
   - Test alternative algorithms (e.g., Gradient Boosting, XGBoost) for better performance.
   - Deploy the model in a real-time monitoring system integrated with school databases.

## How to Run the Project 🚀

1. **Clone the Repository** 📥:
   ```bash
   git clone https://github.com/malakzaidi/student-performance-data-analysis-project.git
   cd student-performance-data-analysis-project
   ```

2. **Set Up Environment** ⚙️:
   - Install Python 3.8+ and dependencies:
     ```bash
     pip install pandas numpy matplotlib seaborn scikit-learn
     ```
   - Install Power BI Desktop.

3. **Run Jupyter Notebook** 📓:
   - Open `notebooks/student_performance_analysis.ipynb` in Jupyter Notebook.
   - Execute cells to reproduce data cleaning, EDA, modeling, and visualizations.

4. **Explore Power BI Dashboards** 📊:
   - Open `powerbi/student_performance_report.pbix` in Power BI Desktop.
   - Access the published report: [Power BI Report](https://app.powerbi.com/groups/me/reports/6f971c6e-b5fc-4af1-ac68-f50bd214014e?ctid=2ec11419-847c-4e29-8815-7f5b2fed9339&pbi_source=linkShare).
   - Use filters to interact with visualizations and explore insights.

5. **Access Dataset** 📂:
   - Original: `data/student-dataset.csv` (Kaggle xAPI-Edu-Data).
   - Cleaned/Enriched: `data/student_data_cleaned.csv`, `data/student_data_enriched.csv`.

## Future Work 🔮

1. **Incorporate Additional Variables** 📊:
   - Include parental education, socioeconomic status, or teacher effectiveness to deepen analysis.

2. **Test Interventions** 🧪:
   - Implement and evaluate recommended strategies (e.g., gamification in Math, absence alerts) to measure impact.

3. **Advanced Modeling** 🤖:
   - Experiment with Gradient Boosting, XGBoost, or Neural Networks to enhance prediction accuracy.

4. **Real-Time Dashboards** ⚡:
   - Integrate live data feeds into Power BI for continuous monitoring of student performance.

5. **Longitudinal Analysis** 📈:
   - Track student performance over multiple years to identify long-term trends and intervention efficacy.

## Acknowledgments 🙏

- **Institution**: ENSET, University Hassan II, Casablanca.
- **Data Source**: Kaggle xAPI-Edu-Data.
- **Tools**: Gratitude to the open-source community for pandas, scikit-learn, seaborn, and Microsoft for Power BI.

## Contact 📬

- Malak Zaidi: [GitHub Profile](https://github.com/malakzaidi)
- Repository: [Student Performance Data Analysis Project](https://github.com/malakzaidi/student-performance-data-analysis-project)
- Email: [malakzaidi815@gmail.com]

This project exemplifies the transformative potential of data science in education, offering a robust framework for institutions to optimize teaching and learning through analytics. We invite educators, data scientists, and stakeholders to explore the repository, replicate the analysis, and build upon our findings to drive educational excellence.

     
