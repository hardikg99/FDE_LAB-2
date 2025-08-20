Objective
This lab experiment provides practical experience in building a basic ETL (Extract, Transform, Load) data pipeline using Python. It guides participants through the core stages of the pipeline from extracting raw healthcare data, transforming it into a usable format, and loading it into a target system. The activity also simulates the roles and responsibilities of key stakeholders, such as data engineers, data scientists, machine learning engineers, and business analysts, to demonstrate their collaborative contributions in the data pipeline.

Outcomes
1.	Identify and describe the stages of the data engineering lifecycle.
2.	Explain the roles and responsibilities of different stakeholders at each stage.
3.	Perform basic healthcare data engineering tasks within a simulated environment.
4.	Collaborate across simulated stakeholder roles to design and implement a data-driven solution.

Materials
•	A pre-packaged CSV file patients_data_with_doctor.csv representing raw patient treatment data (including treatment costs, doctor mapping, and treatment dates).
•	A pre-packaged CSV file doctors_info.csv representing doctor profiles (doctor_id, doctor_name, specialty).
•	A pre-packaged JSON file patient_feedback.json representing patient feedback with scores.
•	A simple mock "data warehouse" (folder) and "reverse ETL output" (folder) for enriched data.

Lab Procedure:

Stage 1: Problem Definition and Requirements Gathering (Business Analyst)
Business Analyst Tasks:
1.	Review the provided patients_data_with_doctor.csv, doctors_info.csv, and patient_feedback.json.
2.	Formulate the business question:
o	“Who are the top 5 doctors by revenue, and how does patient feedback vary for these doctors?”
o	“Which patients can be classified as VIPs based on treatment costs, visits, and feedback?”
3.	Required data points:
o	doctor_id, specialty, treatment_cost, room_cost, patient_feedback_score, patient_id.
4.	Desired outcome:
o	A report showing top 5 doctors with total revenue and average feedback.
o	A classification of patients into VIP and Non-VIP for targeted services.

Stage 2: Data Ingestion and Cleansing (Data Engineer)
Data Engineer Tasks:
1.	Ingestion: Read the raw CSV and JSON files.
2.	Cleansing:
o	Convert treatment_cost and room_cost into numeric values.
o	Standardize missing values (impute with 0 or drop invalid rows).
o	Handle inconsistent date formats.
3.	Transformation:
o	Calculate total_revenue = treatment_cost + room_cost.
o	Aggregate patient feedback scores per patient.
o	Join patient, doctor, and feedback data.
4.	Loading: Store the cleaned and enriched dataset into data_warehouse/processed_healthcare_data.csv.

Stage 3: Data Analysis (Data Analyst)
Data Analyst Tasks:
1.	Access the processed dataset from the warehouse.
2.	Group data by doctor_id to calculate:
o	total_revenue (sum of treatment + room cost per doctor).
o	avg_feedback (average patient feedback score).
3.	Identify top 5 doctors by revenue.

Results:
Top 5 Doctors by Revenue & Feedback
Doctor_id	Specialty	Total_revenue	Avg_feedback
D039	Medical sales representative	160905.05	2.94
D042	Retail buyer	159369.34	2.83
D018	Advertising art director	134953.36	2.90
D040	Health visitor	132596.89	2.58
D012	Automotive engineer	131264.42	3.40

Feedback to Data Engineer:
•	Some feedback scores are missing for certain patients (need more comprehensive survey collection).
•	Date information could be standardized further for advanced time-based analysis.

Stage 4: Reporting and Business Insights (Business Analyst)
Business Analyst Tasks:
1.	Review the top doctors and feedback scores.
2.	Interpret findings:
o	Doctor D039 generates the highest revenue but has relatively average patient feedback (2.94). This suggests possible service quality issues despite strong financial performance.
o	Doctor D012, though ranked 5th in revenue, has the highest feedback (3.40) among the top 5 — an opportunity to highlight quality service.
3.	Report actionable insights:
o	Focus retention strategies on high-revenue doctors with low feedback (D039, D042).
o	Promote and reward doctors with strong patient satisfaction (D012).
o	Use this combined insight for doctor training programs and patient engagement policies.

Stage 5: VIP Patient Classification (ML Engineer)
ML Engineer Tasks:
1.	Analyze patient-level features:
o	total_revenue, visits, avg_spent, avg_feedback.
2.	Preprocess: Handle missing values and normalize.
3.	Apply K-Means clustering to classify patients into VIP and Non-VIP.
4.	Enrich dataset with new column vip_status.
5.	Perform Reverse ETL: Save enriched data to reverse_etl_output/enriched_healthcare_data.csv.

Results:
Sample of Enriched Patients with VIP Tag
patient_id	doctor_id	total_revenue	avg_feedback	vip_status
P0067	D006	4656.11	4.5	Non-VIP
P0006	D022	6178.69	2.4	Non-VIP
P0637	D014	9066.92	4.8	Non-VIP
P0314	D003	6408.05	1.8	Non-VIP
P0326	D012	6917.96	4.2	VIP

Final Report Summary
•	Business Question: Who are the top 5 revenue-generating doctors, how do patients rate them, and which patients can be considered VIPs?
•	Key Findings:
o	D039 and D042 are top revenue doctors but have mediocre patient feedback.
o	D012 stands out with strong feedback and good revenue.
o	Patients like P0326 are classified as VIPs due to high spending and positive feedback.
•	Recommendations:
o	Improve quality of service for high-revenue but low-feedback doctors.
o	Use VIP classification for personalized offers and targeted care programs.
o	Expand feedback collection to strengthen future predictive models.

