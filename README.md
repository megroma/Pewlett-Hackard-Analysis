# Pewlett Hackard Analysis
## Overview
Pewlett Hackard has asked us to assist the HR analyst to determine how many employees will qualify for a retirement package as well as see how many positions will need to be replaced as the employees retire. We have also been tasked with collecting employee information for those that may qualify for a pilot program to assist in mentoring those new to the roles. 

## Results
- Almost 2/3 of those retiring are in senior roles. There are almost 60 thousand in senior roles that will need to be replaced. 
-About half of all employees retiring or 45 thousand are in an engineering role. This needs to be the focus of the recruitment and training and development team to make sure that they can secure the knowledge base and efficiently replace the employees to the correct level. 
-There are two managers that need to be replaced. While only having two roles to fill is not a lot there are no other managers apart of the mentorship program. 
-There are 1549 employees that will qualify for the mentorship program. 
- The mentors and those retiring span all departments and most roles. There are 240124 current employees and of these more than 1/3 will be retiring soon. 

## Summary
There are 90398 roles that need to be filled. The departments that will be hit the hardest are the Production and Development department Followed closely by the Sales team. As shown below in the retiring_titles_dept created with the following query:
    Select count(ut.title), ut.title, de.dept_no
    into retiring_titles_dept
    from unique_titles as ut
    left join dept_emp as de
    on (ut.emp_no = de.emp_no)
    group by title, dept_no
    order by count DESC;

As currently defined there would only be 1549 employees eligible for the mentorship program. As there are over 90000 positions needing to be mentored this on average would be 58 mentees to one mentor. This is a lot for one mentor to handle especially as a part time role. The available mentors were broken down further using the following Query:
    Select count(me.title), me.title
    from mentorship_eligibilty as me
    group by title
    order by count DESC;

This overload for the mentors is further apparent when taken into consideration the role each would be mentoring. There would be 1 mentor for every: 174 Senior Engineer, 50 Senior Staff, 28 Engineer, 79 Staff, 58 Technique leader, 23 Assistant Engineer, and there would not be a mentor for the next manager role. I would recommend expanding this mentorship program with an emphasis on the Senior Engineer because these are the roles that will experience the most strain from the loss. 
