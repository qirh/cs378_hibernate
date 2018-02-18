# CS378 Modern Web Apps. Assignment 5 (Hibernate) [![MIT license](https://img.shields.io/badge/license-MIT-lightgrey.svg)](https://https://raw.githubusercontent.com/qirh/CS378-assignment4/master/LICENSE)

## Description
Modern Web Applications Assignment#5. Done for CS 378, taught by Dr. Devdatta Kulkarni in the fall of 2016. 

* [Assignment details](https://github.com/qirh/CS378-assignment5/blob/master/assignment5.pdf)

* [Course Syllabus](https://github.com/qirh/CS378-assignment5/blob/master/syllabus.pdf)

## Commands

    mysql:
        --host=fall-2016.cs.utexas.edu -u almto3 -pPxWHQV5wg5
        
    1) Create project:
        curl -i --data "<project><name>curl</name><description>testing post on curl</description></project>" -H "Content-Type: application/xml" -X POST http://localhost:8080/assignment5/myeavesdrop/projects/

    2) Create a meeting for a project:
        curl -i --data "<meeting><name>curl</name><year>2014</year></meeting>" -H "Content-Type: application/xml" -X POST http://localhost:8080/assignment5/myeavesdrop/projects/2/meetings

    3) Get project details:
        curl -i -X GET http://localhost:8080/assignment5/myeavesdrop/projects/7

    3x) Get meeting details:
        curl -i -X GET http://localhost:8080/assignment5/myeavesdrop/projects/2/meetings/2

    x) Update Project:


    4) Update Meeting:
        curl -i --data "<meeting><name>curl</name><year>2015</year></meeting>" -H "Content-Type: application/xml" -X PUT http://localhost:8080/assignment5/myeavesdrop/projects/2/meetings/curl

    5) Delete Project:
        curl -i -X DELETE http://localhost:8080/assignment5/myeavesdrop/projects/5

    create cs378_almto3;
    use cs378_almto3;


    create table IF NOT EXISTS Projects(projectName varchar(255) NOT NULL, projectDescription varchar(255) NOT NULL, projectId int NOT NULL AUTO_INCREMENT, PRIMARY KEY(projectId));
    create table IF NOT EXISTS Meetings(meetingName varchar(255) NOT NULL, meetingYear varchar(255) NOT NULL, meetingId int NOT NULL AUTO_INCREMENT, projectId int NOT NULL, PRIMARY KEY(meetingId), FOREIGN KEY (projectId) REFERENCES Projects(projectId) ON DELETE CASCADE);

    insert into Projects(projectName, projectDescription, projectId) values("Data Management", "Data Managment course", 2);
    insert into Projects(projectName, projectDescription, projectId) values("Modern Web Apps", "Dr. dev's class", 1);

    insert into Meetings(meetingName, meetingYear, meetingId, projectId) values("Modern Web Apps", "2014", 1, 2);

    select * from Projects;
    select * from Meetings;