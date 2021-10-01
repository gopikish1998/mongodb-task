1. Insert Users\
`db.users.insertMany({
        "id":1,
        "student_name":"Abhinav",
        "student_email":"abhinav@gmail.com"
    },
    {
        "id":2,
        "student_name":"Mohammad",
        "student_email":"mohammad@gmail.com"
    },
    {
        "id":3,
        "student_name":"Akanksha",
        "student_email":"akanksha@gmail.com"
    },
    {
        "id":4,
        "student_name":"Arya",
        "student_email":"arya@gmail.com"
    },
    {
        "id":5,
        "student_name":"Gopi",
        "student_email":"gopi@gmail.com"
    })`\
2. Insert codekata\
`db.codekata.insertMany( {
        "student_id":1,
        "problems":150
    },
    {
        "student_id":2,
        "problems":130
    },
    {
        "student_id":3,
        "problems":200
    },
    {
        "student_id":4,
        "problems":225
    },
    {
        "student_id":5,
        "problems":165
    })`\
3. Insert Attendance\
`db.attendance.insertMany({
        "student_id":1,
        "attended":60
    },
    {
        "student_id":2,
        "attended":75
    },
    {
        "student_id":3,
        "attended":80
    },
    {
        "student_id":4,
        "attended":85
    },
    {
        "student_id":5,
        "attended":95
    })`\
4. Insert topics
`db.topics.insertMany( {
        "id":1,
        "topic_name":"HTML",
        "month": "June"
    },
    {
        "id":2,
        "topic_name":"CSS",
        "month":"Sepetember"
    },
    {
        "id":3,
        "topic_name":"JavaScript",
        "month":"August"
    },
    {
        "id":4,
        "topic_name":"ReactJS",
        "month":"October"
    },
    {
        "id":5,
        "topic_name":"NodeJS",
        "month":"October"
    })`\
5. Insert tasks\
`db.tasks.insertMany({
        "id":1,
        "task_name":"WebPage",
        "month":"June"
    },
    {
        "id":2,
        "task_name":"CSS Card",
        "month":"July"
    },
    {
        "id":3,
        "task_name":"JS Pagination";
        "month":"September"
    },
    {
        "id":4,
        "task_name":"React Frontend",
        "month": "October"
    },
    {
        "id":5,
        "task_name":"NodeJS Backend",
        "month": "October"
    })`\
 6. Insert COmapany Drives\
 `db.companies.insertMany(    {
        "name":"Google",
        "student_id":[1,2],
        "date":20,
        "month":10,
        "year":2020
    },
    {
        "name":"Amazon",
        "student_id":[1,2,3],
        "date":24,
        "month":10,
        "year":2020
    },
    {
        "name":"TCS",
        "student_id":[2,3,5],
        "date":16,
        "month":10,
        "year":2020
    },
    {
        "name":"Juspay",
        "student_id":[4,5],
        "date":12,
        "month":10,
        "year":2020
    },
    {
        "name":"RazorPay",
        "student_id":[3,4],
        "date":30,
        "month":10,
        "year":2020
    } )`\
7. Insert Mentors\
`db.mentors.insertMany( {
        "id":1,
        "mentor_name":"Rajavasanthan",
        "topics":[3,4,5],
        "mentees":20
    },
    {
        "id":2,
        "mentor_name":"Venkat",
        "topics":[1,2],
        "mentees":24
    },
    {
        "id":3,
        "mentor_name":"Raghav",
        "topics":[2,3],
        "mentees":13
    },
    {
        "id":4,
        "mentor_name":"Gopi",
        "topics":[1,2],
        "mentees":10
    },
    {
        "id":5,
        "mentor_name":"Sivaranjani",
        "topics":[4,5],
        "mentees":17
    })`\
    
    
---------------------------------------------------------------------------------------
###Queries

1. Find all the topics and tasks which are thought in the month of October\
  `db.topics.find({"month":"October"})`\
  `db.tasks.find({"month":"October"})`\
2. Find all the company drives which appeared between 15 oct-2020 and 31-oct-2020\
  `db.companies.find({"month":"October","year":2020,"date":{$gte:15,$lte:31}})`\
3. Find all the company drives and students who are appeared for the placement.\
  `db.companies.aggregare([{
    $lookup: {
            from: "users",
            localField: "student_id",
            foreignField: "id",
            as: "students"
        }
}])`\
4. Find the number of problems solved by the user in codekata\
  `db.codekata.find()`\
5. Find all the mentors with who has the mentee's count more than 15\
  `db.mentors.find({"mentees":{$gt:15}})`\
