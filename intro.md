### Intro to d3 ###

SQL, which stands for "Structured Query Language" is a programming language specifically for working with relational databases. While there are many other similar programming languages, SQL is the most widely used. 

Some history on SQL (from Wikipedia):
>SQL was initially developed at IBM by Donald D. Chamberlin and Raymond F. Boyce in the early 1970s. This version, initially called SEQUEL (Structured English Query Language), was designed to manipulate and retrieve data stored in IBM's original quasi-relational database management system, System R, which a group at IBM San Jose Research Laboratory had developed during the 1970s. The acronym SEQUEL was later changed to SQL because "SEQUEL" was a trademark of the UK-based Hawker Siddeley aircraft company.

>In the late 1970s, Relational Software, Inc. (now Oracle Corporation) saw the potential of the concepts described by Codd, Chamberlin, and Boyce and developed their own SQL-based RDBMS with aspirations of selling it to the U.S. Navy, Central Intelligence Agency, and other U.S. government agencies. In June 1979, Relational Software, Inc. introduced the first commercially available implementation of SQL, Oracle V2 (Version2) for VAX computers.

>After testing SQL at customer test sites to determine the usefulness and practicality of the system, IBM began developing commercial products based on their System R prototype including System/38, SQL/DS, and DB2, which were commercially available in 1979, 1981, and 1983, respectively.

### SQL Syntax ###
#### Clauses ####
In SQL, you have multiple types of **clauses** that perform specific functions. The two most important clauses are the **SELECT** clause and the **FROM** clause, which are both required to pull any information for a database. For example, let's look at some student data:

```
Student                Tests_Taken
---------------------- -----------
John                    3
Jill                    1
Steve                   5
Jackie                  1
Bob                     0
```

And let's say this data is stored in a table called student_test_data. If we wanted to pull this whole table in SQL, we would write the following:

```
SELECT *
 FROM  student_test_data
```
The output would be the data we saw above, because what we're saying is that we want to SELECT all (represented by `*`) the data FROM the table called student_test_data. We could also pull just the names of the students by specifying which **fields** we want:

```
SELECT Student
 FROM  student_test_data
```

Other important clauses are the **WHERE** and the **GROUP BY** clause. The **WHERE** clause allows you to supply parameters for your data pull. From our example data, if you wanted only the names of students that have taken a test, you would write this:

```
SELECT Student
 FROM  student_test_data
 WHERE Tests_Taken > 0
```
And that would output -> John, Jill, Steve, Jackie

SQL uses most regular operators, such as:

```
Operator  Description	
--------  -----------
=	      Equal to	
<>	      Not equal to 
!=        Not equal to
>	      Greater than
<	      Less than	
>=	      Greater than or equal
<=	      Less than or equal 

```


So far what we've been looking at ways of pulling data from tables in a "raw" format, without any manipulation to the original dataset. One type of manipulation is aggregation, which is where we use the **GROUP BY** clause in SQL.  The **GROUP BY** clause is used in conjunction with a **function** to perform some time of aggregation. Going back to our example, if we wanted to know how many people took tests, we could count the number of people in our dataset using the count() function:

```
SELECT count(Student)
 FROM  student_test_data
```

Then if we wanted to know how many students took the same number of tests, we use the **GROUP BY** clause and specify "Tests_Taken" as our aggregation field:

```
SELECT Tests_Taken,
       count(Student)
 FROM  student_test_data 
 GROUP BY Tests_Taken 
```

The output from this query would look like this:

```
Tests_Taken  count(Student)
------------ --------------
0            1
1            2
3            1
5            1
```

Two students, Jill and Jackie, had taken one test, while all the other students took a different number of tests.

#### Joins #####

Often when working with relational databases, you want to combine data from multiple tables. To do this in SQL, you do what is called a **JOIN**. While **JOIN** is really just another type of clause, it's a bit different than the rest.  One, it functions within another clause, the **FROM** clause.  Two, there are variations of the **JOIN** clause, such as the **LEFT JOIN**.  Let's walk through a few examples of joins, but first, we need a a second example table to work with:

```
Student                Home_State
---------------------- -----------
John                    NY
Jill                    NY
Steve                   CO
Jackie                  MA
```
Let's call this table student_home_state.  Now if we want to combine data from student_test_data and student_home_state, we'll use the **JOIN** syntax as follows:

```
SELECT student_test_data.Student,
       student_test_data.Tests_Taken,
       student_home_data.Home_State
       
 FROM  student_test_data 
 JOIN  student_home_state
   ON  student_test_data.Student = student_home_state.Student
```
And here's what this will return:

```
Student                Tests_Taken  Home_State
---------------------- -----------  ----------
John                    3           NY
Jill                    1           NY
Steve                   5           CO
Jackie                  1           MA
```

Notice a few things here - 

1. After stating **JOIN**, you must specify what you're joining **ON**.
2. When you have multiple tables, fields must have a table indication.
3. Only four students came back in the results.  That's because in a **JOIN**, you limit your results to which records exist in both tables. To allow for NULL values (values that do not exist), you need to use a **LEFT JOIN**, like this:

```
SELECT student_test_data.Student,
       student_test_data.Tests_Taken,
       student_home_data.Home_State
       
 FROM  student_test_data 
 LEFT JOIN student_home_state
   ON  student_test_data.Student = student_home_state.Student
```

Which would return:

```
Student                Tests_Taken  Home_State
---------------------- -----------  ----------
John                    3           NY
Jill                    1           NY
Steve                   5           CO
Jackie                  1           MA
Bob                     0           NULL
```

