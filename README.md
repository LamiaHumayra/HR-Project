# HR-Project
Recently, I completed a self-guided data analytics project using a messy HR dataset to practice my full workflow — from raw data to insights and dashboards.
🔍 Here's what I did:
 ✅ Cleaned and preprocessed over 1000+ rows of HR data in Excel (missing values, duplicates, formatting issues)
 📊 Performed descriptive statistical analysis to uncover key metrics like attrition rate, job satisfaction, and overtime trends
 🧠 Wrote SQL queries in DB Browser to answer deeper HR questions
 📈 Built a Power BI dashboard with interactive visuals showing:
 – Attrition breakdown by department, tenure, and overtime
 – Job satisfaction trends
 – Tenure group analysis (New, Mid-Level, Veteran)

HR Data Analytics Project from Scratch (End-to-End)

Here's my SQL Code for the project

-- total employee count

select count(*) as total_employee_count from hr

-- attrition count and rate

select count(*) as total,
sum ( case when Attrition = 'Yes' then 1 else 0 END) as left_employess,
round (100 * sum ( case when Attrition = 'Yes' then 1 else 0 END) / count (*),2 ) as attrition_rate
from hr

--attrition by Department

select Department, count(*) as total_in_dept,
sum( case when attrition = 'Yes' then 1 else 0 end) as left_per_dept,
round (100 * sum( case when attrition = 'Yes' then 1 else 0 end)/ count(*)) as dept_attrition
from hr
group by Department

-- overtime vs attrition comparison

select OverTime, count(*) as total,
sum ( case when attrition = 'Yes' then 1 else 0 end) as left_emp,
round ( 100 * sum ( case when attrition = 'Yes' then 1 else 0 end) / count(*) ,2 ) as attrition_overtime
from hr 
group by OverTime

-- average job satisfaction by Department

select Department, 
round(avg(JobSatisfaction), 2) as avg_satisfaction 
from hr
group by Department





