
Instructions:
Using Pandas and Jupyter Notebook, create a report that includes an analysis of thed istrict-wide standardized test results. Your task is to aggregate the data to showcase obvious trends in school performance.
Your report must include a written description of at least two observable trends based on the data

2/15/24: Corrections to assignment
Corrected school spending calculations, scores by school type



Note on code sources & and its location within repo:
#% passing math (the percentage of students who passed math) scores equal to or greater than 70 - sourced from starter code
passing_math_count = school_data_complete[(school_data_complete["math_score"] >= 70)].count()["student_name"]
passing_math_percentage = (passing_math_count / student_count * 100)

#% passing reading (the percentage of students who passed reading)- sourced from starter code
passing_reading_count = school_data_complete[(school_data_complete['reading_score'] >= 70)].count()['student_name']
passing_reading_percentage = passing_reading_count/student_count * 100

#calculate total student count per school - OpenAI. (2024). ChatGPT (January 2022 version) [Large language model]. https://chat.openai.com
per_school_counts = school_data_complete.groupby('school_name')['student_name'].count()

#calculate total student count per school - OpenAI. (2024). ChatGPT (January 2022 version) [Large language model]. https://chat.openai.com
per_school_counts = school_data_complete.groupby('school_name')['student_name'].count()

#Calculate the number of schools with math scores of 70 or higher - OpenAI. (2024). ChatGPT (January 2022 version) [Large language model]. https://chat.openai.com
students_passing_math = school_data_complete[school_data_complete['math_score'] >= 70]
school_students_passing_math = students_passing_math.groupby('school_name')['student_name'].count()

#Calculate the number of schools with reading scores of 70 or higher - OpenAI. (2024). ChatGPT (January 2022 version) [Large language model]. https://chat.openai.com
students_passing_reading = school_data_complete[school_data_complete['reading_score'] >= 70]
school_students_passing_reading = students_passing_reading.groupby('school_name')['student_name'].count()

#Use the provided code to calculate the schools that passed both math and reading with scores of 70 or higher - sourced from starter code
students_passing_math_and_reading = school_data_complete[
    (school_data_complete["reading_score"] >= 70) & (school_data_complete["math_score"] >= 70)]
school_students_passing_math_and_reading = students_passing_math_and_reading.groupby("school_name")['student_name'].count()

#Use the provided code to calculate the schools that passed both math and reading with scores of 70 or higher - sourced from starter code
students_passing_math_and_reading = school_data_complete[
    (school_data_complete["reading_score"] >= 70) & (school_data_complete["math_score"] >= 70)]
school_students_passing_math_and_reading = students_passing_math_and_reading.groupby(["school_name"]).size()

#Use the provided code to calculate the passing rates - sourced from starter code 
per_school_passing_math = school_students_passing_math / per_school_counts * 100
per_school_passing_reading = school_students_passing_reading_schools / per_school_counts * 100
overall_passing = school_students_passing_math_and_reading / per_school_counts * 100

#Create a new DataFrame for the above calculations & columns called per_school_summary
# Formatting -- source from starter code

#create a new data frame with the above calculations
# Formatting - code source from starter code

#Use the provided code to calculate the passing rates - sourced from starter code 
per_school_passing_math = school_students_passing_math / per_school_counts * 100
per_school_passing_reading = school_students_passing_reading_schools / per_school_counts * 100
overall_passing = school_students_passing_math_and_reading / per_school_counts * 100
overall_passing_rate

# Use the code provided to separate the data by grade - from starter code
# Group by `school_name` and take the mean of the `math_score` column for each. - sourced variable names from starter code
ninth_grade_math_scores = ninth_graders.groupby('school_name')['math_score'].mean()
tenth_grader_math_scores = tenth_graders.groupby('school_name')['math_score'].mean()
eleventh_grader_math_scores = eleventh_graders.groupby('school_name')['math_score'].mean()
twelfth_grader_math_scores = twelfth_graders.groupby('school_name')['math_score'].mean()

# Minor data wrangling - sourced from starter code
math_scores_by_grade.index.name = None

# Establish the bins -- code source provided in challenge assignment instructions
spending_bins = [0, 585, 630, 645, 680]
group_names = [("<$585"), ("$585-630"), ("$630-645"), ("$645-680")]

#  Use the following code to then calculate mean scores per spending range. - code source from challenge assignment instructions, OpenAI. (2024). ChatGPT (January 2022 version) [Large language model]. https://chat.openai.com
spending_math_scores = school_spending_df.groupby("Spending Ranges (Per Student)", observed=False)["Average Math Score"].mean()
spending_reading_scores = school_spending_df.groupby(["Spending Ranges (Per Student)"], observed=False)["Average Reading Score"].mean()
spending_passing_math = school_spending_df.groupby(["Spending Ranges (Per Student)"], observed=False)["% Passing Math"].mean()
spending_passing_reading = school_spending_df.groupby(["Spending Ranges (Per Student)"], observed=False)["% Passing Reading"].mean()
overall_passing_spending = school_spending_df.groupby(["Spending Ranges (Per Student)"], observed=False)["% Overall Passing"].mean()

# Establish the bins. - code sourced from challenge assignment instructions
size_bins = [0, 1000, 2000, 5000]
labels = ["Small (<1000)", "Medium (1000-2000)", "Large (2000-5000)"]

# Categorize the spending based on the bins - (Tebalelo AskBCS Learning Assistant, personal communication, January 15, 2024)
# Use `pd.cut` on the "Total Students" column of the `per_school_summary` DataFrame.
per_school_counts = school_data_complete.groupby('school_name').count()['student_name']
per_school_summary["School Size"] = pd.cut(per_school_counts, size_bins, labels=labels, include_lowest=True)
per_school_summary.sort_values(['School Size'])

# Calculate averages for the desired columns - code sourced from PyCitySchools starter code, OpenAI. (2024). ChatGPT (January 2022 version) [Large language model]. https://chat.openai.com
size_math_scores = per_school_summary.groupby("School Size", observed=False)["Average Math Score"].mean()
size_reading_scores = per_school_summary.groupby("School Size", observed=False)["Average Reading Score"].mean()
size_passing_math = per_school_summary.groupby("School Size", observed=False)["% Passing Math"].mean()
size_passing_reading = per_school_summary.groupby("School Size", observed=False)["% Passing Reading"].mean()
size_overall_passing = per_school_summary.groupby("School Size", observed=False)["% Overall Passing"].mean()

#  Use the following code to then calculate mean scores per spending range. - code sourced from challenge assignment instructions, OpenAI. (2024). ChatGPT (January 2022 version) [Large language model]. https://chat.openai.com
spending_math_scores = school_spending_df.groupby("Spending Ranges (Per Student)", observed=False)["Average Math Score"].mean()
spending_reading_scores = school_spending_df.groupby(["Spending Ranges (Per Student)"], observed=False)["Average Reading Score"].mean()
spending_passing_math = school_spending_df.groupby(["Spending Ranges (Per Student)"], observed=False)["% Passing Math"].mean()
spending_passing_reading = school_spending_df.groupby(["Spending Ranges (Per Student)"], observed=False)["% Passing Reading"].mean()
overall_passing_spending = school_spending_df.groupby(["Spending Ranges (Per Student)"], observed=False)["% Overall Passing"].mean()

