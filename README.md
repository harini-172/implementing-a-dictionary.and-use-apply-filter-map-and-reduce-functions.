# implementing-a-dictionary.and-use-apply-filter-map-and-reduce-functions.
import pandas as pd

# Create DataFrame
df = pd.DataFrame({
    'Name': ['Alice', 'Bob', 'Charlie', 'David', 'Eve', 'Frank', 'George', 'Hannah'],
    'Age': [25, 32, 18, 47, 30, 22, 55, 29],
    'City': ['New York', 'Los Angeles', 'Chicago', 'New York',
             'Chicago', 'Los Angeles', 'New York', 'Los Angeles'],
    'Salary': [70000, 90000, 45000, 120000, 65000, 50000, 150000, 80000]
})

print("DataFrame:\n", df)

# Inspection
print("\nFirst 3 rows:\n", df.head(3))
print("\nShape:", df.shape)
print("\nStatistics:\n", df.describe())

# Sorting
print("\nSorted by Age:\n", df.sort_values('Age'))
print("\nSorted by Salary (desc):\n", df.sort_values('Salary', ascending=False))

# Filtering
print("\nAge > 30:\n", df[df['Age'] > 30])
print("\nNew York & Salary > 100000:\n",
      df[(df['City'] == 'New York') & (df['Salary'] > 100000)])

# Second DataFrame
df_dept = pd.DataFrame({
    'Name': df['Name'],
    'Department': ['HR', 'Engineering', 'Sales', 'Engineering',
                   'HR', 'Sales', 'Engineering', 'HR']
})

# Merge
df_merged = pd.merge(df, df_dept, on='Name')
print("\nMerged DataFrame:\n", df_merged)

# Grouping
print("\nAverage Salary by City:\n",
      df.groupby('City')['Salary'].mean())

print("\nEmployee Count by Department:\n",
      df_merged.groupby('Department')['Name'].count())

output
Original Employee Salaries:
{'Ravi': 45000, 'Anita': 72000, 'Karthik': 52000, 'Priya': 38000, 'Suresh': 61000}

Salaries after 10% hike:
{'Ravi': 49500, 'Anita': 79200, 'Karthik': 57200, 'Priya': 41800, 'Suresh': 67100}

Employees with salary >= 50,000:
{'Anita': 79200, 'Karthik': 57200, 'Suresh': 67100}

Total Salary Expense:
294800

Account No : 1001
Name       : Suresh
Balance    : 27000
