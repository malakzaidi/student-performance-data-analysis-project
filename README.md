# 📊 Student Performance Data Analysis Project


<div align="center">
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=power-bi&logoColor=black" alt="Power BI">
  <img src="https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white" alt="Jupyter">
  <img src="https://img.shields.io/badge/pandas-150458?style=for-the-badge&logo=pandas&logoColor=white" alt="Pandas">
  <img src="https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white" alt="Scikit-learn">
  <img src="https://img.shields.io/badge/Seaborn-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Seaborn">
</div>

<div align="center">
  <h3>🔍 Transforming Education Through Data Science</h3>
</div>

---

## ✨ Project Overview

Welcome to the **Student Performance Data Analysis Project**, a cutting-edge data science initiative that transforms educational outcomes through advanced analytics. Conducted as part of the Digital Culture module in the Master's program in Distributed Systems and Artificial Intelligence (SDIA) at ENSET, University Hassan II, Casablanca, this project leverages the power of **Python** 🐍 and **Power BI** 📈 to deliver actionable insights into student performance.

<div align="center">
  <img src="https://github.com/user-attachments/assets/c8f542d7-1c82-4f5e-a5bf-3ba6c8e91e5c" width="700px" alt="Tech Stack">
</div>

By analyzing a comprehensive dataset of student records, we identify key factors influencing academic success, uncover hidden patterns in performance metrics, and provide evidence-based recommendations for educational enhancement. Our innovative approach combines:

- 🧠 **Advanced Machine Learning** techniques for predictive modeling
- 📊 **Interactive Visualizations** for intuitive data exploration
- 🔍 **In-depth Statistical Analysis** for robust insights
- 💡 **Strategic Recommendations** for educational improvement

## 📋 Table of Contents

- [Project Overview](#-project-overview)
- [Dataset Description](#-dataset-description)
- [Methodology](#-methodology)
  - [Data Cleaning and Preparation](#data-cleaning-and-preparation)
  - [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
  - [Predictive Modeling](#predictive-modeling)
  - [Interactive Visualization](#interactive-visualization)
- [Key Findings](#-key-findings)
- [Visualizations and Interpretations](#-visualizations-and-interpretations)
  - [Python Visualizations](#python-visualizations)
  - [Power BI Visualizations](#power-bi-visualizations)
- [Recommendations](#-recommendations)
- [How to Run the Project](#-how-to-run-the-project)
- [Future Work](#-future-work)
- [Acknowledgments](#-acknowledgments)
- [Contact](#-contact)

## 📊 Dataset Description

The dataset, sourced from [Kaggle's xAPI-Edu-Data](https://www.kaggle.com/datasets/aljarah/xAPI-Edu-Data/data), comprises **480 student records** with **17 variables** across multiple dimensions:

### 👤 Demographic Variables
- `gender`: Student's gender (Male/Female)
- `NationalITy`: Student's nationality
- `PlaceofBirth`: Student's birthplace

### 📚 Academic Variables
- `StageID`: Educational level (LowerLevel, MiddleSchool, HighSchool)
- `GradeID`: Grade level
- `SectionID`: Section identifier
- `Topic`: Course subject
- `Semester`: Academic semester (First/Second)
- `Class`: Performance level (L=Low, M=Medium, H=High) - **Target Variable**

### 📱 Engagement Metrics
- `raisedhands`: Frequency of hand raising in class
- `VisITedResources`: Frequency of course resource visits
- `AnnouncementsView`: Frequency of checking course announcements
- `Discussion`: Frequency of participation in discussion groups

### 🏠 Contextual Variables
- `Relation`: Parent responsible for student (Mom/Dad)
- `ParentAnsweringSurvey`: Parent survey participation (Yes/No)
- `ParentschoolSatisfaction`: Parent satisfaction with school (Yes/No)
- `StudentAbsenceDays`: Student absence days (Under-7/Above-7)

### 📈 Derived Features
- `ClassNumeric`: Numerical mapping of `Class` (L=0, M=1, H=2)
- `Failed`: Binary indicator for failure (Yes for L, No otherwise)
- `EngagementScore`: Composite score of engagement metrics
- `Period`: Combined `StageID` and `Semester` for temporal analysis

## 🔬 Methodology

Our rigorous data science pipeline ensures robust analysis and actionable outcomes:

### Data Cleaning and Preparation

- **Tools**: Python (`pandas`, `numpy`)
- **Steps**:
  - Verified data integrity with no missing values
  - Removed 2 duplicate records
  - Standardized categorical variables
  - Applied IQR method for outlier detection
  - Created derived features for enhanced analysis
  - Generated cleaned datasets: `student_data_cleaned.csv` and `student_data_enriched.csv`

### Exploratory Data Analysis (EDA)

- **Tools**: Python (`matplotlib`, `seaborn`)
- **Purpose**: Uncover relationships between variables through visual exploration
- **Key Visualizations**:
  - Distribution plots for engagement metrics
  - Countplots for gender and performance relationships
  - Boxplots for subject-specific engagement patterns
  - Scatterplots for engagement vs. performance
  - Line plots for temporal performance trends

### Predictive Modeling

- **Algorithm**: Random Forest Classifier
- **Features**: Engagement metrics, absence days, parental involvement
- **Target**: Student performance level (`ClassNumeric`)
- **Process**:
  - One-hot encoded categorical variables
  - Split data: 70% training, 30% testing
  - Trained model with 100 estimators
  - Evaluated performance with precision, recall, F1-score
  - Saved feature importance and predictions

### Interactive Visualization

<div align="center">
  <img src="https://github.com/user-attachments/assets/4d8e9f1a-3a5d-42e9-8a4a-d2eb8e8befe6" width="150px" alt="Interactive Visualization">
</div>

- **Tool**: Power BI
- **Features**:
  - Interactive filters for dynamic data exploration
  - DAX measures for calculated metrics
  - Multi-dimensional visualizations
  - Published dashboards for stakeholder access

## 🔍 Key Findings

<div align="center">
  <img src="https://github.com/user-attachments/assets/e9c74b8e-9f4a-4eaa-9431-0ca5c7c2ab75" width="700px" alt="Key Findings">
</div>

Our analysis revealed several critical insights into student performance:

### 1. 💡 Engagement is the Cornerstone of Success

- Students with `EngagementScore` > 70 are almost exclusively in the `H` class
- `VisITedResources` (24.2%), `raisedhands` (20.9%), and `AnnouncementsView` (18.4%) are top predictors
- Clear thresholds separate performance levels (< 30 for `L`, > 70 for `H`)

### 2. ⚖️ Gender Disparities Highlight Inequities

- Girls outperform boys with lower failure rates (12% vs. 32%)
- Girls have higher representation in `H` class (35% vs. 21%)
- Boys with low engagement and frequent absences are particularly at risk

### 3. 📚 Subject-Specific Engagement Varies Widely

- **High Engagement**: Biology (75.8% in `H`), Science (74.8%), Quran (73.2%)
- **Low Engagement**: Math (10% in `L`), IT (15%), French (18%)
- Biology shows the largest engagement gap (69.2 points between `H` and `L`)

### 4. ⏰ Temporal Trends Reveal Critical Periods

- Performance improves in second semester across all levels
- Peak performance in `HighSchool_S` (mean `ClassNumeric` = 1.4)
- Significant dip in `MiddleSchool_F` (mean `ClassNumeric` ~ 0.9)

### 5. 🚨 Absences are a Major Risk Factor

- `Above-7` absences strongly predict failure, especially with low engagement
- Absences have stronger impact in second semester
- 80% of `L` class students have `Above-7` absences

### 6. 🌍 Nationality Influences Performance

- Kuwaiti students exhibit higher average performance (mean `ClassNumeric` 1.5)
- Egyptian and Jordanian students lag (mean ~0.8-1.0)
- Gender performance gaps vary by nationality

### 7. ✅ Predictive Model Performance is Robust

- `L` class: Precision 0.84, Recall 0.86, F1-score 0.85
- `M` class: Precision 0.73, Recall 0.73, F1-score 0.73
- `H` class: Precision 0.73, Recall 0.71, F1-score 0.72

## 📊 Visualizations and Interpretations

Our analysis is supported by comprehensive visualizations that reveal hidden patterns and relationships:

### Python Visualizations

<div align="center">
  <img src="https://github.com/user-attachments/assets/3fab89e3-c67e-4c5e-ae0e-5f51b2b3f75c" width="250px" alt="Python Viz">
</div>

1. **Distribution of Raised Hands by Failure Status** 📈
   ![Image](https://github.com/user-attachments/assets/4225fa2e-52cd-44b0-a683-de937c21e472)
   - Failing students show minimal class participation (peak at 10-20 `raisedhands`)
   - Successful students demonstrate active engagement (peak at 50-70)
   - Distinct participation thresholds differentiate performance levels

2. **Class Distribution by Gender** 👥
   ![Image](https://github.com/user-attachments/assets/0a5a1e2a-7003-4216-9f9c-78b57724b7a4)
   - Girls demonstrate stronger academic performance with lower failure rates
   - Boys face unique challenges, particularly in engagement and attendance
   - Gender-focused interventions are needed to address disparities

3. **Engagement Score by Subject and Class** 📚
   ![Image](https://github.com/user-attachments/assets/7171eb65-5840-4305-a65a-46dddd671f04)
   - Biology shows exceptional engagement in `H` class (median 80)
   - Math and IT struggle with engagement across all classes
   - Subject-specific pedagogical approaches significantly impact performance

4. **Engagement vs. Performance by Gender and Absences** 📉
   ![Image](https://github.com/user-attachments/assets/ab3f911f-96aa-4ebe-88e6-90ef7a06e345)
   - High engagement consistently predicts success regardless of other factors
   - Girls show resilience at moderate engagement levels
   - Frequent absences combined with low engagement create high failure risk

5. **Performance Evolution by Period** 📅
   ![Image](https://github.com/user-attachments/assets/dde08180-d070-4aad-bf6f-426ea950ecaa)
   - Performance consistently improves in second semesters
   - Middle school transition presents significant challenges
   - High school students demonstrate maturity and effective study habits

6. **Confusion Matrix** 🧮
   ![Image](https://github.com/user-attachments/assets/f1752cd1-b28a-4ee0-856e-c11ab1637b8f)
   - Model excels at identifying at-risk students for early intervention
   - Most errors occur in the `M` class due to overlap with `L` and `H`
   - High accuracy for critical `L` class enables targeted support

7. **Heatmap of Engagement by Subject and Class** 🌡️
   ![Image](https://github.com/user-attachments/assets/c1abe3f9-2da2-494e-b20f-186d67fc899d)
   - Stark contrast in engagement between performance levels
   - Biology and Science show highest engagement in `H` class
   - Math and IT face consistent engagement challenges across all classes

### Power BI Visualizations

<div align="center">
  <img src="https://github.com/user-attachments/assets/7b8c4d9e-5f3a-4d2e-a321-d98c5e4f6a8d" width="250px" alt="Power BI Viz">
</div>

1. **Global Dashboard** 🌐
   ![Image](https://github.com/user-attachments/assets/8445db31-2448-44f5-86ec-b05b098d0e90)
   - 24% of students are at risk (`L` class)
   - 74% achieve success (`M` or `H` class)
   - Moderate engagement (44.54/100) indicates improvement potential

2. **Performance by Nationality** 🌍
   ![Image](https://github.com/user-attachments/assets/5bf6d02e-117d-46c9-b9c9-3950f8917300)
   - Kuwaiti students lead with highest performance metrics
   - Cultural and educational factors influence national performance patterns
   - Gender performance gaps vary by nationality

3. **Factors of Influence** 🔑
   ![Image](https://github.com/user-attachments/assets/3f3c7ab7-fe8b-4b97-ab34-af5d355b7670)
   - Engagement metrics dominate performance prediction
   - Resource visits and hand-raising are top influencers
   - Absences and parental involvement are significant secondary factors

4. **Interactive Filters** 🎛️
   ![Image](https://github.com/user-attachments/assets/17dd60d3-46e7-4644-9a43-039f2e5eeda0)
   - Granular analysis through dynamic filtering
   - Subject-specific performance patterns emerge
   - Temporal and demographic trends provide actionable context

5. **Engagement Pattern Analysis** 📊
   ![Image](https://github.com/user-attachments/assets/7910311b-821a-4ca2-be67-4115168237fe)
   - Clear engagement thresholds predict performance levels
   - Gender-specific engagement patterns highlight differing needs
   - Trend lines show steeper improvement for girls with increasing engagement

6. **Performance vs. Absence Analysis** 🕰️
   ![Image](https://github.com/user-attachments/assets/e2211c71-f7c8-42ce-87df-eda2ed2bd6f8)
   - Absences compound over time with greater second-semester impact
   - Attendance is a key modifiable factor for performance improvement
   - First-semester absences may reflect adjustment challenges

7. **Absence Impact Dashboard** 🚨
   ![Image](https://github.com/user-attachments/assets/180e6eae-ccf2-4392-8bc0-6b5df9ef3c93)
   - Strong correlation between absences and failure
   - Consistent attendance aligns with success
   - Second-semester improvements indicate effective interventions

8. **Adjusted Engagement Dashboard** ⚙️
   ![Image](https://github.com/user-attachments/assets/696b16f3-dad4-4968-8577-9fb1405f63da)
   - Normalized engagement metrics provide fair comparison
   - Risk flagging enables proactive intervention
   - Significant room for engagement improvement (48.99/100)

9. **Engagement Recommendations** 💡
   ![Image](https://github.com/user-attachments/assets/f0881a81-afb1-430e-b986-2bd1cab08022)
   - Personalized, actionable recommendations by engagement level
   - Tiered approach ensures relevance for all students
   - Integrated guidance for educators and students

10. **Report's QR Code** 🔗
    ![Image](https://github.com/user-attachments/assets/1143b71b-fb51-4683-a421-bb24739065a9)
    - Direct access to interactive Power BI dashboards
    - Enables stakeholder exploration and decision-making
    - Available at [Power BI Report](https://app.powerbi.com/groups/me/reports/6f971c6e-b5fc-4af1-ac68-f50bd214014e?ctid=2ec11419-847c-4e29-8815-7f5b2fed9339&pbi_source=linkShare)

## 💡 Recommendations

<div align="center">
  <img src="https://github.com/user-attachments/assets/8cde4f7a-6b9b-4a23-9a35-a2f6d8e3f8b5" width="700px" alt="Recommendations">
</div>

Based on our findings, we propose these evidence-based strategies to enhance student performance:

### 1. 🎯 Targeted Support for At-Risk Students
- Identify high-risk profiles early (low engagement, frequent absences)
- Implement personalized tutoring and mentorship programs
- Deploy automated absence alerts after 7 days

### 2. 🧑‍🏫 Interactive Pedagogical Methods
- Introduce gamification elements in challenging subjects
- Replicate successful teaching methods from Biology and History
- Conduct teacher training on engagement-focused pedagogy

### 3. 📅 First-Semester Focus
- Develop transition programs for MiddleSchool students
- Provide study skills workshops and orientation sessions
- Address curriculum complexity in challenging subjects

### 4. 🚀 Encourage Female Excellence
- Promote STEM participation through dedicated programs
- Leverage girls' strengths in peer mentoring initiatives
- Ensure equitable advancement opportunities

### 5. 🌟 Enhance Engagement Strategies
- Incentivize participation through recognition systems
- Promote active learning environments and group projects
- Implement flipped classroom approaches in challenging subjects

### 6. 🌍 Address Nationality Gaps
- Provide language and cultural support for underperforming groups
- Develop tailored interventions based on cultural learning styles
- Create inclusive classroom environments

### 7. ⚙️ Refine Predictive Models
- Incorporate additional features for improved accuracy
- Test alternative algorithms for better performance
- Deploy real-time monitoring systems for proactive intervention

## 🚀 How to Run the Project

<div align="center">
  <img src="https://github.com/user-attachments/assets/12ef6d8c-1b57-4a09-9c3e-d2e7fdb9e48c" width="700px" alt="Project Setup">
</div>

Get started with our analysis by following these steps:

### 1. 📥 Clone the Repository
```bash
git clone https://github.com/malakzaidi/student-performance-data-analysis-project.git
cd student-performance-data-analysis-project
```

### 2. ⚙️ Set Up Environment
- Install Python 3.8+ and dependencies:
  ```bash
  pip install pandas numpy matplotlib seaborn scikit-learn
  ```
- Install Power BI Desktop

### 3. 📓 Run Jupyter Notebook
- Open `notebooks/student_performance_analysis.ipynb`
- Execute cells sequentially to reproduce:
  - Data cleaning and preparation
  - Exploratory data analysis
  - Predictive modeling
  - Visualization generation

### 4. 📊 Explore Power BI Dashboards
- Open `powerbi/student_performance_report.pbix`
- Access the published report: [Power BI Report](https://app.powerbi.com/groups/me/reports/6f971c6e-b5fc-4af1-ac68-f50bd214014e?ctid=2ec11419-847c-4e29-8815-7f5b2fed9339&pbi_source=linkShare)
- Use interactive filters to explore insights

### 5. 📂 Access Dataset
- Original: `data/student-dataset.csv`
- Cleaned: `data/student_data_cleaned.csv`
- Enriched: `data/student_data_enriched.csv`

## 🔮 Future Work

<div align="center">
  <img src="https://github.com/user-attachments/assets/9ed28f5a-b3e5-4a8c-b1f7-d2e4a7c6f9d3" width="700px" alt="Future Work">
</div>

We envision several directions to expand this research:

### 1. 📊 Incorporate Additional Variables
- Parental education and socioeconomic status
- Teacher effectiveness metrics
- School infrastructure and resources

### 2. 🧪 Test Interventions
- Implement recommended strategies in real educational settings
- Measure impact through controlled studies
- Refine approaches based on outcome data

### 3. 🤖 Advanced Modeling
- Experiment with Gradient Boosting and Neural Networks
- Develop time-series forecasting for performance trends
- Implement ensemble methods for improved accuracy

### 4. ⚡ Real-Time Analytics
- Create live dashboards with continuous data integration
- Develop early warning systems for at-risk students
- Enable automated intervention recommendations

### 5. 📈 Longitudinal Analysis
- Track cohorts over multiple academic years
- Identify long-term patterns and intervention efficacy
- Measure sustained impact of educational strategies

## 🙏 Acknowledgments

<div align="center">
  <img src="https://github.com/user-attachments/assets/6e9d3f1c-5a8b-4e2d-b7fa-f1d9c4a8e0b7" width="300px" alt="Acknowledgments">
</div>

We extend our sincere gratitude to:

- **ENSET, University Hassan II, Casablanca** for institutional support
- **Kaggle** for providing the xAPI-Edu-Data dataset
- The **open-source community** for pandas, scikit-learn, and seaborn
- **Microsoft** for Power BI's powerful visualization capabilities

## 📬 Contact

<div align="center">
  <img src="https://github.com/user-attachments/assets/3a9c2d8e-1f5b-4e7a-b8ef-d4e8c7f6b09a" width="300px" alt="Contact">
</div>

Have questions or want to collaborate? Reach out to us:

- **Creator**: Malak Zaidi
- **GitHub**: [malakzaidi](https://github.com/malakzaidi)
- **Repository**: [Student Performance Data Analysis Project](https://github.com/malakzaidi/student-performance-data-analysis-project)
- **Email**: [malakzaidi815@gmail.com](mailto:malakzaidi815@gmail.com)

---

<div align="center">
  <p>This project exemplifies the transformative potential of data science in education, offering a robust framework for institutions to optimize teaching and learning through analytics.</p>
  
  <h3>🌟 Transform Education Through Data 🌟</h3>
</div>
