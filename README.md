# PowerBI_PowerQueries
In this repository I applied most of the power queries I can make to show my capabilities.

***ALl the power queries I made for it a simple visualization you can see it from the screenshot or open the powerBI files.***

# Import Data form a website
![Page 1](/WikipediaData.png)
I loaded this data from wikipedia and used it in some visualizations.

# Import Multiple Files From A Folder
![Page 2](/MultipleFiles.png)
I loaded this data from a folder that contains multiple files then I combined them and loaded and it can be refreshed if there in new file added to be conmbined and loaded to the existing data.
![Page 3](/InsertCustomColumnInMonthlyFiles.png)
I have also done some transformations as changing the datatype of job_posted_date from decimal to datetime, replaced values in job_via column (replaced "via " with a blank value to remove it), also inserted a custom column Date to get only the date value from a datetime column.
![Page 4](/MultiplicationInMonthlyFiles.png)
I also added a mulplication column that multiple the salary_hour_avg by 2080 to a new column called salary_hour_adj.

# Import Multiple Files From A Folder To Make A Star Schema
![Page 5](/StarSchemaSource.png)
I imported star schema files from the folder and loaded without any combinations, then I took a reference for each file to work with it as a separate table (Why reference and not duplications? Because I only want the source without any next applied steps).
![Star Schema Model View](/StarSchemaModelView.png)
Then I opened the model view to add relationships between tables.
![Cross Filter](/CrossFilter.png)
While visualizing I found that the relations are not referenced right so I changed the cross filter direction to be in both directions.
![Schedule_dim](/Schedule_dim.png)
Then I decided to make the schedule in a separate table called Schedule_dim. First, I referenced the job_posting_fact table. Second, I kept the job_id and job_schedule_type and removed the other columns. Third, I replaced 'and' and ',and' with ',' to then split column with delimiter. Forth, I select job_id column and unpivoted other columns and removed the attribute column and renamed the value column to job_schedule_type. Finally, I trimmed the text to remove any extra spaces exist in the values to avoid duplicates and I also filtered the rows and removed any blank values. And I didn't forget to add the relationship and make the cross filter direction to be both.

# Merging Tables To A Single Table
Here I merged the fact and skills dimension tables to one flat table for jobs and skills.
![Merge job_posting_fact with skill_job_dim](/MergeJob_posting_factWithSkill_job_dim.png)
First, I merged job_posting_fact with skill_job_dim as new to a new table with a full outer join to get all rows from both and then expanded the skill_job_dim with unchecking the skill_id.
![Merge job_posting_fact with skill_dim](/MergeJob_posting_factWithSkill_dim.png)
Second, I merged the new table with skill_dim with a full outer join to get all rows from both and then expanded the skill_dim with unchecking the skill_id. Finally, for extra cleaning I removed some columns and renamed some columns.

# Group By
![Group By](/GroupBy.png)
I referenced the job_skills_flat table and make a group by skill and job_title_short and added some aggregation like counts rows to get the number of jobs need this skill and aggregated the median of salary_years_avg.

# M Language
![Add Column From Example](/AddColumnsFromExample.png)
From add coloum from example I chosed from selection, I selected salary_hour_adj and then wrote 52000 and then pressed enter so the power bi understood that I want to copy the data from slary_hour_adj and I selected salary_year_avg and in the first null value I wrote 120000 so the power bi understood that in the blank vlaues to copy the data from the salary_year_avg. Then in the salary_hour_bucket I add coloum from example I chosed from selection , I selected salary_hour_avg and wrote 20-30 and power bi understood and make the same in the rest of the rows.
![Add Custom Column](/CustomColumn.png)
Using M Language I added column salary_year_and_hour v1 by writing this query.

# Append
![Append](/Append.png)
I imported a folder contians multiple files and loaded them without any combination.
I opened transform data and clicked append queries as new and appended all files into a single table and renamed it as data_jobs_appended. Then I moved the files in a separate group and called it Monthly Data Separated and enabled the data load for this files.