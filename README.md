# SQL-challenge

### **Data Engineering**

Use the information you have to create a table schema for each of the six CSV files. Remember to specify data types, primary keys, foreign keys, and other constraints.

For the primary keys check to see if the column is unique, otherwise create a composite key. Which takes to primary keys in order to uniquely identify a row.
Be sure to create tables in the correct order to handle foreign keys.



![github](https://github.com/Jackelyneg/SQL-challenge/blob/main/ERD%20image.png)


Import each CSV file into the corresponding SQL table. Note be sure to import the data in the same order that the tables were created and account for the headers when importing to avoid errors.

### **Data Analysis**
Once you have a complete database, do the following:

- List the following details of each employee: employee number, last name, first name, sex, and salary.
  
      select e.emp_no,e.last_name,e.first_name,e.sex, s.salary 
      from employees as e
      join salaries as s 
      on e.emp_no = s.emp_no

- List first name, last name, and hire date for employees who were hired in 1986.
      
      select first_name, last_name, hire_date 
      from employees
      where hire_date between '1986-01-01' and '1986-12-31'

- List the manager of each department with the following information: department number, department name, the manager's employee number, last name, first name.

      select e.first_name, e.last_name,d.dept_name, dm.emp_no
      from employees as e
      join dept_manager as dm
      on e.emp_no = dm.emp_no
      join departments as d
      on dm.dept_no = d.dept_no

- List the department of each employee with the following information: employee number, last name, first name, and department name.
      
      select e.emp_no,e.last_name, e.first_name,d.dept_name
      from employees as e
      join dept_emp as de
      on e.emp_no = de.emp_no
      join departments as d
      on de.dept_no = d.dept_no

- List first name, last name, and sex for employees whose first name is "Hercules" and last names begin with "B."

      select first_name, last_name, sex
      from employees
      where first_name = 'Hercules' and last_name like 'B%'


- List all employees in the Sales department, including their employee number, last name, first name, and department name.

      select e.first_name,e.last_name,d.dept_name,e.emp_no
      from employees as e 
      join dept_emp as de
      on e.emp_no = de.emp_no
      join departments as d
      on de.dept_no = d.dept_no
      where dept_name = 'Sales'

- List all employees in the Sales and Development departments, including their employee number, last name, first name, and department name.

      select e.emp_no, e.last_name, e.first_name,d.dept_name
      from employees as e
      join dept_emp as de
      on e.emp_no = de.emp_no
      join departments as d
      on de.dept_no = d.dept_no
      where dept_name in ('Sales','Development')

- In descending order, list the frequency count of employee last names, i.e., how many employees share each last name.

      select last_name, count(last_name) as count_last_name
      from employees
      group by last_name
      order by count_last_name desc
      
## **Bonus Challenge**

- Create a histogram to visualize the most common salary ranges for employees.



![Github](https://github.com/Jackelyneg/SQL-challenge/blob/main/Images/salary_hist.png)
- Create a bar chart of average salary by title.

![Github](https://github.com/Jackelyneg/SQL-challenge/blob/main/Images/salary_bar.png)
