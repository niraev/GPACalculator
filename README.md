# GPACalculator
#This python code calculate your students GPA then it shows All Students ID with their GPA's and Honor Students ID
#Mehmet Mert Telioglu - 160302055

student = {}
all_courses_info = {}
students_gpa = {}

specific_course_info = []
honorstudents = []

while True:

 gpa = 0.0
 courses_total_ects = 0 

 student_id = int(input('Enter student id: '))
 all_courses_info = {}
 student[student_id] = all_courses_info

 registered_courses_num = int(input('Enter number of courses registered: ')) 

 for x in range(registered_courses_num):
  
  course_name, course_ects, course_grade = input('Enter course name, ECTS, grade: ').split(',')
  
  specific_course_info = [int(course_ects),course_grade]
  specific_course_info_tuple = tuple(specific_course_info)
  all_courses_info[course_name] = specific_course_info_tuple

  courses_total_ects = courses_total_ects + int(course_ects)
 
 lst1 = list(student.keys())

 for a in all_courses_info.keys():  
   lst = list(all_courses_info[a])  
   
   if (lst[1] == 'AA'):
       letter_grade_multiplier = 4.00
   if (lst[1] == 'BA'):
       letter_grade_multiplier = 3.50
   if (lst[1] == 'BB'):
       letter_grade_multiplier = 3.00
   if (lst[1] == 'CB'):
       letter_grade_multiplier = 2.50
   if (lst[1] == 'CC'):
       letter_grade_multiplier = 2.00
   if (lst[1] == 'DC'):
       letter_grade_multiplier = 1.50
   if (lst[1] == 'DD'):
       letter_grade_multiplier = 1.00
   if (lst[1] == 'FD'):
       letter_grade_multiplier = 0.50
   if (lst[1] == 'FF'):
       letter_grade_multiplier = 0.00

   ects = float(lst[0])

   gpa = gpa + ((ects)*(letter_grade_multiplier/courses_total_ects))

 students_gpa[lst1[(len(lst1)-1)]] = {(float(gpa))}  
  
 while True:
   desicion = input('Do you want to continue Y/N: ')
   if(desicion == 'N'):
       print(' ')
       break
   elif(desicion == 'Y'):
       break
   print('WRONG DESICION CHARACTER')

 if(desicion == 'N'):
     break
 print(' ')

lst2 = list(students_gpa)
e = 0
for i in students_gpa.keys():
    fgpa = ((list(students_gpa[i]))[0])
    print('Student id: ',lst2[e],'GPA: ',fgpa )
    if(fgpa>3.0):
        honorstudents.append(lst2[e])
    e = e +1

print(' ')
print('Honor Students with GPA above 3.0')
for i in range(len(honorstudents)):
  print(honorstudents[i])
#Mehmet Mert Tellioglu - 160302055


