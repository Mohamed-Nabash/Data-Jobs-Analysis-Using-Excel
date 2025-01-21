# **Data Jobs Analysis**

## **Introduction** 

As a job seeker, I’m often surprised by the lack of data exploring the most ideal data science jobs and skills in the market. I set out to understand what skills top employers are looking for and how to earn higher salaries.

### **Questions to Analyze**

To understand the data science job market, I asked the following:

1. **Do more skills get you better pay?**
2. **What’s the salary for data jobs in different regions?**
3. **What are the top skills of data professionals?**
4. **What’s the pay for the top 10 skills?**

### **Excel Skills Used**

The following Excel skills were utilized for analysis:

- 📊 **Pivot Tables**
- 📈 **Pivot Charts**
- 🧮 **DAX (Data Analysis Expressions)**
- 🔍 **Power Query**
- 💪 **Power Pivot**

### **Data Jobs Dataset**

O dataset utilizado neste projeto é de 2023. It includes detailed information on:

- 👨‍💼 **Job titles**
- 💰 **Salaries**
- 📍 **Locations**
- 🛠️ **Skills**

## 1️⃣ Do more skills get you better pay?

### 🔍 **Skill: Power Query (ETL)**

#### 📥 **Extract**

I first used Power Query to extract the original data (`data_jobs_salary_all.xlsx`) and create two queries:

- 🗃️ First one with all the data jobs information.
- 🔧 The second listing the skills for each job ID.

#### 🔄 **Transform**

I transformed each query by changing column types, removing unnecessary columns, cleaning text to eliminate specific words, and trimming excess whitespace.

- 📊 data_jobs_salary

![](/assets/transform_salary_table.PNG)

- 🛠️ data_job_skills

![](/assets/transform_skills_table.PNG)

#### 🔗 **Load**

I loaded both transformed queries into the workbook, setting the foundation for my subsequent analysis.

- 📊 data_jobs_salary

![](/assets/salary_table.PNG)

- 🛠️ data_job_skills

![](/assets/skills_table.PNG)

### 📊 **Analysis**

💡 **Insights**

- 📈 There is a positive correlation between the number of skills requested in job postings and the median salary, particularly in roles like Senior Data Engineer and Data Scientist.

- 💼 Roles that require fewer skills, like Business Analyst, tend to offer lower salaries, suggesting that more specialized skill sets command higher market value.

![](/assets/analysis_1.PNG)



## 2️⃣ **What’s the salary for data jobs in different regions?**

### 🧮 **Skills: PivotTables & DAX**

#### 📈 **Pivot Table**

- 🔢 I created a PivotTable using the Data Model I created with Power Pivot.
- 📊 I moved the `job_title_short` to the rows area and `salary_year_avg` into the values area.
- 🧮 Then I added new measure to calculate the median salary for **Brazil** jobs.

```excel
=CALCULATE([Median Salary]; 
data_jobs_salary[job_country]="Brazil")
```

#### 🧮 **DAX**

- To calculate the median year salary I used DAX.

```excel
Median Salary := MEDIAN(data_jobs_all[salary_year_avg])
```

### 📊 **Analysis**

💡 **Insights**

- 💼 Software engineers have high salaries in countries like Brazil and Argentina, while in the international market they are below average. Job roles like Senior Data Engineer and Data Scientist command higher median salaries internationally

- 💰 The salary of a data scientist in Brazil is significantly lower than in non-BR countries.

![](/assets/analysis_2.PNG)

## 3️⃣ **What are the top skills of data professionals?**

### 🔧 **Skill: Power Pivot**

#### 💪 **Power Pivot**

- 🔗 I created a data model by integrating the `data_jobs_salary` and `data_jobs_skills` tables into one model.
- 🧹 Since I had already cleaned the data using Power Query; Power Pivot created a relationship between these two tables.

#### 🔗 **Data Model**

- I created a relationship between my two tables using the `job_id` column.

![](/assets/diagram_view.PNG)

#### 📃 **Power Pivot Menu**

- The Power Pivot menu was used to refine my data model and makes it easy to create measures.

![](/assets/power_pivot_menu.PNG)

### 📊 **Analysis**

💡 **Insights**

- 💻 SQL and Python dominate as top skills in data-related jobs, reflecting their foundational role in data processing and analysis.

- 📈 R is very present, demonstrating that tools for statistical analysis are important.

- ☁️ Emerging technologies like AWS and Azure also show significant presence, underlining the industry's shift towards cloud services and big data technologies.

![](/assets/analysis_3.PNG)

## 4️⃣ **What’s the pay of the top 10 skills?**

### 📊 **Skill: Advanced Charts (Pivot Chart)**

#### 📈 **PivotChart**

I created a combo PivotChart to plot median salary and skill likelihood (%) from my PivotTable.
- 🪙 **Primary Axis:** Median Salary (as a Clustered Column)
- 👍 **Secondary Axis:** Skill Likelihood (as a Line with Markers)

To customize the chart, I added a title axis title, removed the lines (skill likelihood), and changed the markers to diamonds.

### 📊 **Analysis**

💡 **Insights**

- 💰 Higher median salaries are associated with skills like Spark, AWS, and Java.
- 👨🏼‍💻 Skills like Python and SQL are among the highest paid, suggesting their critical role in high-paying tech jobs.

![](/assets/analysis_4.PNG)

![image](https://github.com/user-attachments/assets/8c325239-1173-486a-b702-6353c1df7b7a)


## **Conclusion**

As a job seeker I did this project to help me gain some insights into the job market in data. Using data from real-world job postings, I analyzed salaries, locations, job titles, and essential skills. By leveraging Excel features like Power Query, PivotTables, DAX, and charts, I discovered key correlations between multiple skills and higher salaries.

I hope this project serves as a practical guide for data professionals and provides an overview of the skills needed for higher-paying roles.
