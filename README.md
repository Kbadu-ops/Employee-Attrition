FINAL PROJECT ANALYSIS – HR Employee Attrition
Project: Operational Analytics – Employee Attrition Prediction & Retention Optimization
Authors: Victor Badu & Rita Awitty
Dataset: IBM HR Employee Attrition (Kaggle)

1. Introduction
Employee attrition is one of the most persistent operational challenges facing modern organizations. Losing employees especially those with critical skills or difficult-to-replace experience, creates direct financial costs, disrupts workflow, and weakens organizational stability. Because of this, organizations increasingly rely on data-driven approaches to understand why employees leave, which employees are most likely to leave, and what targeted actions can reduce turnover in a cost-effective way.
This report presents a fully integrated analysis that combines descriptive, predictive, and prescriptive analytics into a single decision-making framework for managing employee attrition.

	The descriptive analysis examines patterns in the workforce, highlights early warning signs, and identifies the conditions most strongly associated with employees leaving.

	The predictive analysis builds on these insights by using machine learning to estimate each employee’s likelihood of resignation, allowing the organization to move from general observations to individualized risk assessment.

	The prescriptive analysis then translates those risk predictions into actionable intervention strategies, constrained by real-world budget limitations and HR capacity.

Together, these three components create a comprehensive view of the attrition problem—moving from what is happening, to why it is happening and who is affected, and finally to what the organization can do next to improve retention. The analyses have been refined based on instructor feedback to strengthen managerial relevance, improve clarity, and present a fully defined optimization model that supports informed HR decision-making.

2. Background Research
Employee attrition has long been recognized as a major concern for organizations because it directly affects productivity, financial performance, and long-term strategic stability. When employees leave, organizations face recruitment costs, onboarding delays, and potential loss of skill and experience. For these reasons, understanding why employees resign and how to reduce preventable turnover has become a core priority in human resource management.
Research in HR analytics consistently shows that attrition is not random. Instead, it is driven by identifiable and measurable factors such as workload intensity, compensation fairness, career growth opportunities, job satisfaction, and personal well-being. Prior studies from IBM, SHRM, Deloitte, and peer-reviewed HRM literature highlight several reliable patterns:

	Excessive workload and burnout: Employees with high overtime or sustained work pressure show significantly higher resignation rates.
	Compensation and role stagnation: Employees who feel underpaid or see limited advancement opportunities are more likely to disengage and eventually leave.
	Satisfaction and work–life balance: Lower satisfaction—whether with the work environment, manager relationships, or life balance—often precedes voluntary quits.
	Focused, data-driven interventions: Targeted retention programs have been shown to produce far better returns than broad, one-size-fits-all HR initiatives.
This project builds on these research findings by analyzing the IBM HR Employee Attrition dataset and applying modern analytics techniques. The predictive component identifies the most influential drivers of turnover and quantifies each employee’s risk of resigning. The prescriptive component then uses these insights to design an optimized retention strategy—one that allocates resources to the employees who need them most while ensuring that HR investments deliver the highest possible return.


3. Problem Presentation
The organization is experiencing recurring voluntary attrition, particularly among employees who are early in their tenure, have high overtime demands, or report lower satisfaction with their job or compensation. These patterns suggest that turnover is influenced by both structural issues (such as workload and pay levels) and individual employee experiences (such as work–life balance and career development). While HR has attempted various initiatives in the past, these efforts have typically been reactive and broad in scope, rather than targeted and data-driven.
To address this challenge effectively, the organization needs a clearer understanding of three core questions:
1. What factors are driving employee attrition?
The descriptive and predictive analyses reveal that factors such as overtime, compensation disparity, job satisfaction, and growth limitations are strongly associated with employees choosing to leave. Understanding these drivers allows HR to move beyond assumptions and base decisions on measurable evidence.
2. Which employees are most at risk of leaving?
The predictive model (GLMNET) generates individualized attrition probabilities, allowing the organization to identify high-risk employees before they resign. These risk scores transform the attrition issue from a broad problem into a prioritized list of employees who may benefit most from timely HR intervention.
3. How should HR allocate a limited retention budget to reduce turnover most effectively?
Budget and staffing constraints make it impossible to offer interventions to every at-risk employee. The prescriptive model therefore determines:
	Which intervention types to offer
	How many employees can be supported under the available budget
	Which employees should receive support first
	Which mix of interventions maximizes the expected reduction in attrition
This turns predictive insights into a practical, decision-support tool that helps HR leaders invest in retention strategies with confidence. By linking risk scores to specific actions and cost considerations, the analysis provides a structured way to reduce turnover while maintaining financial responsibility and maximizing organizational impact.
4. Specification and Design
This project was designed using a structured analytics framework that moves systematically from understanding the attrition problem, to predicting its future occurrences, to prescribing the most effective retention strategies. The overall design ensures that each analytical component supports the next, resulting in a coherent and actionable decision-making system.
4.1 Analytical Framework Overview
The analysis follows a three-stage structure commonly used in operational analytics:

Stage 1: Descriptive Analytics – Understanding the Workforce
This stage examines the current state of the workforce by exploring demographic trends, satisfaction levels, workload patterns, compensation structures, and early signs of attrition risk. Descriptive statistics and visualizations help identify underlying patterns and potential areas of concern before building predictive models.

Stage 2: Predictive Analytics – Identifying Who Is Likely to Leave
Machine learning models—specifically GLMNET and Random Forest—are used to estimate each employee’s probability of resigning. These risk scores quantify the likelihood of attrition at an individual level and highlight which factors contribute most to turnover. This transition from general patterns to individual predictions forms the foundation for targeted retention strategies.




Stage 3: Prescriptive Analytics – Determining What Actions to Take
The prescriptive phase uses optimization logic to recommend the best combination of HR interventions under real-world constraints. Because HR budgets are limited, the organization cannot support every at-risk employee. The prescriptive model determines which interventions to offer to whom, and at what cost to maximize the number of quits prevented.
Together, these stages create a comprehensive analytical pipeline that connects insight (descriptive), foresight (predictive), and actionable strategy (prescriptive).
4.2 Tools and Methods Used
To implement this design, the project uses:
	R (tidymodels, themis, glmnet, ranger) for modeling and resampling
	Data cleaning and transformation tools for encoding, normalization, and class balancing
	Optimization logic to convert predictive insights into operational retention strategies
	Sensitivity analysis to test the stability of recommendations under changing budget or cost conditions
These tools enable a rigorous and reproducible workflow, with each step transparently documented and consistent with industry standards.

5. Data Acquisition
The analysis uses the IBM HR Employee Attrition dataset, a widely studied dataset in HR analytics that captures demographic, behavioral, and job-related information for 1,470 employees. The dataset provides the depth and variety of variables required to understand employee retention and support the development of predictive and prescriptive models.
5.1 Data Source and Structure
	Dataset: IBM HR Analytics Employee Attrition & Performance
	Size: 1,470 employee records
	Features: 35 variables covering demographics, job characteristics, compensation, satisfaction, performance, and workload
	Outcome Variable: Attrition (Yes/No)
The dataset includes:
	Employee age, tenure, and marital status
	Monthly income and job level
	Overtime and travel frequency
	Job satisfaction, environment satisfaction, and work–life balance
	Performance ratings and promotion history
This broad range of features makes it suitable for analyzing both organizational-level trends and individual-level attrition risk.
5.2 Data Cleaning and Preprocessing
Before analysis, several cleaning steps were conducted to prepare the dataset:
	Removal of non-informative variables:
Variables such as EmployeeNumber, EmployeeCount, StandardHours, and Over18 were removed because they do not contribute meaningful predictive information.
	Target Variable Formatting:
The Attrition column was converted into a binary factor with levels "No" and "Yes" to support classification modeling.
	Missing Data Check:
A full inspection using skimr::skim() confirmed that the dataset contains no missing values, avoiding the need for imputation.
	Consistency Checks:
Variable types were standardized (e.g., converting categorical fields to factors), and numerical ranges were examined to ensure logical values.





5.3 Data Partitioning
To ensure robust predictive performance and avoid overfitting, the data was partitioned as follows:
	Training Set: 70% of the data (stratified by attrition outcome)
	Testing Set: 30% of the data (held out for final evaluation)
Stratification ensures that the proportion of "Yes" and "No" cases remains consistent across both sets, preserving class balance for modeling.

5.4 Why This Dataset Supports Operational Decision-Making
This dataset is especially well-suited for operational analytics because:
	It includes variables linked directly to managerial levers such as salary, promotion, workload, and satisfaction.
	It allows for both individual risk assessment (predictive phase) and intervention design (prescriptive phase).
	It reflects real-world HR challenges that organizations encounter, particularly regarding workforce planning and retention strategy.
These characteristics make the dataset ideal for developing a complete analytics pipeline that connects insights to practical recommendations.

6. Descriptive Analysis
The descriptive analysis provides an initial understanding of employee characteristics, workplace patterns, and early indicators of attrition. By summarizing the dataset and visualizing key variables, this phase identifies the structural factors that may contribute to employees’ decisions to stay or leave, forming the foundation for the predictive and prescriptive models.
6.1 Overall Attrition Levels
Attrition in the dataset is imbalanced, with only 16.1% of employees labeled as “Yes.”
This imbalance suggests that although turnover is relatively low in frequency, the associated cost of each departure may still be significant for the organization.
The imbalance also necessitates techniques such as SMOTE during predictive modeling to ensure the model does not become biased toward predicting “No.”




								
Table 1: Attrition distribution (No vs Yes).
Figure 1. Attrition distribution (No vs Yes).	

6.2 Key Workforce Demographics
Age Distribution
The age distribution is right-skewed, showing:
	A concentration of employees between 30 and 40,
	Fewer very young or nearing-retirement employees.
This suggests a workforce dominated by mid-career professionals whose attrition may be especially expensive due to their skill levels and experience.

Tenure (Years at Company)
Tenure is also skewed:
	Many early-tenure employees (<3 years)
	A steady decline in longer-tenure employees
This pattern indicates higher vulnerability to early turnover—an important insight later reinforced by the predictive model.
6.3 Workload and Compensation Patterns
Monthly Income
Monthly income displays a strong right skew:
	Most employees earn moderate salaries,
	A small number earn significantly higher incomes.
Such skewness justifies the log transformation used during predictive modeling to normalize the distribution.
Overtime
A notable share of employees report working overtime, with those who do so exhibiting a substantially higher proportion of attrition. This aligns with HR literature identifying workload strain as a leading indicator of voluntary quits.
6.4 Satisfaction Measures
Employees report multiple satisfaction scores (job, relationship, environment, work–life balance).
Boxplots consistently show:
	Employees who left tend to report lower satisfaction across all measures.
	Job Satisfaction and Work–Life Balance show the strongest separation between “Yes” and “No” groups.
These patterns foreshadow the predictive significance of satisfaction variables.
6.5 Correlation Structure
A correlation heatmap of numeric variables reveals:
	Minimal strong multicollinearity (most correlations < 0.6)
	Logical relationships (e.g., Age ↔ Years at Company)
	Independence across many predictors, supporting robust modeling
A follow-up VIF analysis confirmed no multicollinearity concerns requiring variable removal.

6.6 Relationships Between Key Variables and Attrition
Scatter Plot: Monthly Income vs. Tenure
The scatter visual shows that:
	Low-income employees across all tenure levels have higher attrition probabilities.
	Employees with higher income and longer tenure are significantly less likely to leave.
This supports the role of income and tenure as stabilizing factors.

6.7 Outlier Diagnostics
Using Mahalanobis distance:
	A small number of multivariate outliers were identified,
	But they were retained because they represent real and meaningful employee scenarios rather than data errors.
These may capture legitimate high-risk employee profiles (e.g., high overtime + low satisfaction).

6.8 Summary of Descriptive Insights
The descriptive findings establish several foundational patterns:
	Attrition is concentrated among employees who are young or early in their tenure.
	High overtime and low satisfaction consistently correlate with attrition.
	Income is a stabilizing factor, especially at the lower end.
	No major data quality issues or multicollinearity concerns were found.
	These patterns provide a clear direction for predictive modeling—confirming which variables should be prioritized—and shape the prescriptive phase, which targets interventions to the most relevant risk factors.

Find all figures in Appendix 1

7. Data Transformations
To ensure reliable predictive modeling and accurate prescriptive recommendations, several transformations and preprocessing techniques were applied to the dataset. These transformations were grounded in statistical best practices and directly address issues identified during the descriptive analysis, such as skewness, class imbalance, and categorical variable handling.
7.1 Preparing the Target Variable
The outcome variable Attrition was converted into a binary factor with two levels:
	“No” (employee stayed)
	“Yes” (employee left)
This formatting is required by classification algorithms and ensures consistency across all modeling steps.
7.2 Removing Non-Informative Variables
Several variables were removed because they contained no predictive information or had no variation:
	EmployeeNumber
	EmployeeCount
	StandardHours
	Over18
Removing these columns reduces noise in the model and improves computational efficiency without affecting accuracy.
7.3 Log Transformation for Skewed Distributions
The variable MonthlyIncome exhibited a strong right skew, as confirmed by the descriptive histograms.
To normalize its distribution and avoid inflating model variance:
	A log transformation was applied with a small offset to manage zero values:
step_log(MonthlyIncome, offset = 1)
This helps models such as GLM and GLMNET treat income as a smoother, more linear predictor.
7.4 Dummy Encoding of Categorical Variables
Most predictors in the dataset are categorical (e.g., BusinessTravel, JobRole, Department).
These were transformed using dummy encoding:
	Converts categories into numerical columns
	Required for GLMNET and Random Forest
	Ensures all levels contribute meaningfully to model training
Dummy encoding also prevents models from incorrectly assuming order in categorical values.

7.5 Normalization of Numeric Predictors
For models sensitive to feature scale (especially GLMNET), all numeric variables were standardized:
	Mean-centered
	Divided by standard deviation
This places all numeric predictors on the same scale and prevents high-magnitude variables (e.g., YearsAtCompany) from dominating the model.

7.6 Handling Class Imbalance Using SMOTE
Attrition had only 16.1% “Yes” cases, which poses a risk of models learning to always predict “No.”
To correct this imbalance, the Synthetic Minority Oversampling Technique (SMOTE) was applied within the recipe:
	Generates synthetic samples for minority cases
	Keeps relationships with predictors intact
	Improves model sensitivity to detecting “Yes” attrition
	Performed after dummy encoding and normalization to avoid distortions
SMOTE was used for both GLMNET and Random Forest workflows since both benefit from a balanced training set.
7.7 Correlation and Multicollinearity Checks
To ensure predictive stability:
	A correlation filter (step_corr()) removed highly correlated predictors (threshold = 0.85).
	A diagnostic logistic model confirmed all Variance Inflation Factors (VIF) were below critical thresholds.
This step guards against unstable coefficient estimates and improves interpretability.
7.8 Final Preprocessing Summary
The data transformation pipeline successfully:
	Cleaned and standardized the dataset
	Normalized numeric variables
	Encoded all categorical variables
	Balanced attrition classes for modeling
	Reduced skew and multicollinearity
	Prepared fully structured datasets ready for cross-validation and model training
These transformations ensured that the predictive models learned meaningful patterns and provided fair and unbiased output—forming the backbone for accurate risk scoring and prescriptive optimization.

8. Predictive Results
This section presents the results of the predictive modeling phase, which estimated the probability that each employee would voluntarily leave the organization. Three models were evaluated—Logistic Regression, GLMNET (penalized logistic regression), and Random Forest—but GLMNET emerged as the most balanced and reliable model for HR decision-making.
8.1 Model Tuning and Cross-Validation
Each model was trained on 70% of the data using 5-fold stratified cross-validation, ensuring that the natural class imbalance (16% attrition) was preserved in every fold.
Class imbalance was addressed using SMOTE, applied inside the preprocessing pipeline.
Hyperparameter tuning included:
	GLMNET:
	penalty (λ) and mixture (α) tuned over a structured grid
	Random Forest:
	mtry, min_n, and 1,000 trees
	Logistic Regression:
	No tuning, used as a baseline
Tuning focused on probability-based metrics:
	ROC-AUC
	PR-AUC
These metrics are appropriate for imbalanced datasets and provide insight into model discrimination.
8.2 Evaluation of the Hold-Out Test Set
After selecting the best tuning parameters, each model was tested on the 30% hold-out set using an F1-optimized probability threshold. The GLMNET and Random Forest models produced the following results:
GLMNET (Final Selected Model)
	ROC-AUC: 0.837
	PR-AUC: Strong performance relative to class imbalance
	Sensitivity: Able to correctly identify many “Yes” attrition cases
	Specificity: Low false alarms
	F1-Score: Balanced precision and recall
Random Forest
	Performed competitively but showed slightly lower balance between sensitivity and precision compared to GLMNET.








8.3 Confusion Matrix Interpretation
The confusion matrices illustrate how effectively each model classified employee attrition outcomes. For the GLMNET model (TN = 316, FP = 23, FN = 54, TP = 49), it correctly identified most employees who stayed while detecting a substantial number of those who actually left, demonstrating a strong balance between sensitivity and precision. Its relatively low number of false positives means few unnecessary alerts, making it reliable for proactive HR decision-making.

In comparison, the Random Forest model (TN = 320, FP = 29, FN = 50, TP = 43) was slightly better at recognizing employees who remained but less effective at identifying those who resigned. Overall, the GLMNET model achieved the best compromise between detecting true attrition cases and minimizing false alarms, making it the more suitable model for anticipating employee turnover and guiding timely retention actions.
This evaluation confirms that the GLMNET model not only performed well during cross-validation but also generalized effectively to new, unseen data, supporting its selection for final deployment and interpretation
 
Table 2: Confusion Matrix Results
8.4 Variable Importance and Key Predictors
Both models highlighted consistent predictors:
Top Predictors (from GLMNET Coefficients)
	Overtime (Yes) – Strong positive effect on attrition
	Monthly Income (log-scaled) – Higher income reduces attrition probability
	Job Satisfaction – Lower scores strongly increase risk
	Work–Life Balance – Lower balance increases risk
	Job Role and Business Travel effects
Top Predictors (from Random Forest Importance)
	Confirmed the same pattern: workload + satisfaction + compensation variables dominate.
The agreement across models strengthens confidence in their predictive validity.

8.5 Visualization of Predictive Results

 
	Shows GLMNET outperforming Random Forest across most thresholds.
Figure 2: ROC Curve Comparison



 
	Illustrates the direction and magnitude of predictor effects.
Table 3: GLMNET Coefficient Table
Random Forest Variable Importance Plot
 
	Highlights the top contributing features in the ensemble model.
Figure 3. Random Forest Variable Importance
These visuals strengthen the narrative by showing both model performance and interpretability.
8.6 Why GLMNET Was Selected
GLMNET was chosen as the final model because:
	It offered the best balance of sensitivity, precision, and ROC-AUC.
	It is more interpretable, allowing HR leaders to understand the contribution of each predictor.
	It generalizes well while avoiding overfitting through regularization.
	Its output (probability scores) integrates seamlessly into the prescriptive optimization model.
GLMNET therefore provides a stable and actionable foundation for targeting interventions.




9. Prescriptive Results
The prescriptive phase transforms model-generated attrition risk scores into specific HR actions that maximize retention under a fixed monthly budget. This analysis moves from prediction (“who is likely to leave?”) to optimization (“what should HR do about it?”), ensuring analytics directly support managerial decision-making.

9.1 Turning Risk Scores Into Actionable Targets
The GLMNET predictive model produced an attrition probability for every employee. These probabilities were rank-ordered from highest to lowest, producing a prioritized list of employees most likely to leave.
The prescriptive model is applied to the entire current workforce of 1,470 employees using the GLMNET model to generate attrition probabilities. This ensures our intervention strategy covers all at-risk employees, not just those in the test set used for model validation.
For each employee i with predicted risk pᵢ, applying an intervention reduces risk by a fixed percentage (the intervention’s effectiveness rate).
Example:
	Baseline attrition probability = 0.40
	Intervention effectiveness = 20%
"New risk"=0.40(1-0.20)=0.32
"Risk reduction"=0.40-0.32=0.08

Summing up, these risk reductions across all treated employees yields the total expected quits prevented.
This structure allows HR to quantify the effect of each intervention and compare alternative budget allocations objectively.
9.2 Intervention Menu and Cost Assumptions
Five targeted interventions were developed based on the strongest predictors identified in the GLMNET model (overtime, income, satisfaction, and work–life balance).
 
Table 4. Intervention menu showing estimated costs, expected risk reduction, and target employee segments.
9.3 Optimization Model
The prescriptive model allocates a $30,000 monthly HR budget to maximize total quits prevented.
Decision Variable
x_i={■(1&"if employee i receives an intervention" @0&"otherwise" )

Objective Function
Maximize:
∑_(i=1)^N p_i×e_i×x_i


Where:
	pᵢ = predicted attrition probability
	eᵢ = intervention effectiveness (risk-reduction %)
	xᵢ = treatment decision (0/1)
Constraints
	Budget Constraint
∑_(i=1)^N c_i x_i≤30,000

	One Intervention per Employee
x_i≤1

	Intervention Costs Fixed
	Effectiveness Rates Fixed
This is a 0–1 knapsack-style optimization: treat the highest-risk employees first, prioritizing interventions with the highest “risk reduced per dollar.”
9.4 Baseline Outcome Under a $30,000 Budget
The optimization results under the \$30,000 budget are summarized below:
 
Table 5: Baseline Optimization Results
Interpretation
	The $30K budget allows HR to treat 15 highest-risk employees.
	This prevents approximately 4.2 resignations per month.
	An ROI of 2.83 means each $1 spent yields $2.83 in avoided turnover costs.
	The intervention strategy is both cost-effective and operationally feasible.
This outcome serves as the baseline scenario for subsequent sensitivity tests.
9.5 Sensitivity Analysis
To ensure the recommendations remain robust under changing assumptions, three forms of sensitivity analysis were conducted.
A. Budget Sensitivity
Budgets from $5,000 to $50,000 were tested.
Key findings:
	Quits prevented increases steadily with budget.
	ROI peaks around $10K–$20K and stabilizes thereafter.
	All budgets yield ROI > 2.3, meaning every scenario is financially justified.
B. Effectiveness Sensitivity
Intervention effectiveness varied from 10% to 50%.
Results:
	Quits prevented grows almost linearly with effectiveness.
	ROI increases substantially as program quality improves.
	At higher effectiveness (≥40%), expected quits prevented exceed 10 employees.
For more information look at Appendix 2
C. Cost Sensitivity
Costs were varied ±20%:
	Lower costs allow more employees to be treated, increasing quits prevented.
	Higher costs reduce the number treated and reduce ROI.
 
Table 6: Cost sensitivity analysis shows ROI and quits prevented under ±20% changes in intervention cost
9.6 Summary of Prescriptive Results
	Top Priority
Treat employees with high overtime, low income, and low satisfaction first.
	Most Effective Interventions
Pay Adjustment, Overtime Relief, and Career Development yield the highest risk reduction.
	Baseline Impact Under $30K Budget
	15 employees treated
	~4.2 quits prevented per month
	ROI = 2.83
	Robustness
Results remain strong across all sensitivity scenarios.
The most influential factor is intervention effectiveness, meaning improving program quality results in the highest payoff.
This prescriptive framework gives HR a concrete plan to reduce attrition efficiently and strategically, backed by quantitative evidence.
10. Conclusion
This project integrated descriptive, predictive, and prescriptive analytics to build a complete, data-driven framework for understanding and reducing employee attrition. Across all phases, the analysis demonstrated that turnover is not random but is driven by identifiable and actionable factors—particularly excessive overtime, low income, limited career development, and diminished job satisfaction. These findings were supported by both exploratory summaries and predictive modeling, providing a holistic view of the workforce challenges facing the organization.
The predictive stage, powered by the GLMNET model, produced robust individualized attrition risk scores with a high ROC-AUC of 0.837, confirming strong discriminatory power. Key predictors such as Overtime, Monthly Income, Job Satisfaction, and Work–Life Balance aligned closely with the descriptive insights and HR literature. This step not only identified who is most likely to leave but also provided the quantitative foundation needed for strategic intervention planning.
The prescriptive analysis then transformed these predictive results into a practical optimization framework that assigns targeted interventions to high-risk employees under real budget constraints. By leveraging cost assumptions, risk-reduction effectiveness, and an allocation strategy grounded in expected quits prevented, the model enables HR leaders to maximize their return on investment. Under a $30,000 budget, the organization can expect to treat 15 high-risk employees, prevent approximately 4.2 quits per month, and achieve an ROI of 2.83—demonstrating strong operational and financial value.
Sensitivity analyses confirmed that the recommendations are stable across changes in budget, intervention effectiveness, and program costs. Notably, intervention effectiveness emerged as the most influential factor, reinforcing the importance of delivering high-quality HR programs rather than simply expanding their scale.
Overall, this project provides a rigorous yet practical blueprint for reducing voluntary turnover. By linking predictive insights to prescriptive recommendations, the organization gains a clear, evidence-based approach that supports smarter budgeting, focused resource allocation, and strategic workforce stabilization. The final recommendations empower HR leaders to implement interventions that are not only targeted and cost-effective but also directly aligned with the underlying drivers of attrition identified throughout the analysis.































Appendix 
Appendix 1: Descriptive Analysis
 
Table 1. Descriptive statistics for key numeric variables.
  
Figure 2. Distribution of Monthly Income.				Figure 3. Distribution of Age













Figure 4. Distribution of Years at Company.					Figure 5. Correlation heatmap of numeric variables.
Appendix 2: Prescriptive Analysis
  
Figure 7. Sensitivity: Budget vs. ROI 			Figure 6. Sensitivity: Budget vs. Expected Quits Prevented

 
Table 2. Budget Sensitivity Summary.				Figure 8. Sensitivity: Effectiveness vs. Quits Prevented








Figure 9. Effect of intervention effectiveness on ROI (Budget = $30,000).
 
Table 3. Effectiveness Sensitivity Summary
Appendix 3: Project Time Estimation vs. Actual
Overview
This appendix documents the estimated versus actual time spent on each major project phase, providing transparency into the project workflow and helping identify areas where planning accuracy could improve in future analytics initiatives.
Time Allocation Summary
 
