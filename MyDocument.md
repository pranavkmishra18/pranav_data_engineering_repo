NYC Jobs Data Engineering Assessment
I worked on the NYC jobs dataset using PySpark. The goal was to explore the data, clean it properly and answer the KPIs given in the assignment.
First I checked number of rows, columns, null values and salary frequency types. Salary was not consistent because some were annual, some hourly and some daily. So I created salary midpoint and then converted everything into annual salary.
For feature engineering I added a few columns:
salary_midpoint annual_salary degree_level (based on keywords like phd, master, bachelor etc) skill_count (based on preferred skills column) parsed posting_date
These were needed for correlation and time based filtering.
KPIs covered:
top 10 job categories salary distribution by category correlation between degree and salary highest salary job per agency average salary per agency for last 2 years highest paid skills
Assumptions:
midpoint represents expected salary 2080 hours per year for hourly jobs 260 working days for daily jobs degree extracted using simple keyword match
Challenges:
salary formats were different date format was inconsistent degree was inside text column skills column had noisy text
If deployed in real environment, this can run as a PySpark batch job using spark-submit. It can be scheduled daily using Airflow or cron. Processed data can be stored in parquet format in a data lake.
Overall the dataset required cleaning before doing analysis but after normalization the KPIs were straightforward to compute.



