# databases

![](databases/education%20database%20system/UML%20screenshot.jpg)
![](databases/education%20database%20system/ERD%20sereenshot.jpg)
![](databases/library%20database%20system/EER.jpg)

SQL Queries : 

create table members (
id char(9) primary key ,
fname varchar(15) unique,
lname varchar(15) unique,
pin varchar (15) ,
datebirth date,
satejoind date,
expiry date,
city varchar (15),
street varchar (20));



create table member_type(
id char(9) primary key,
membertype varchar(20),
permission varchar(20),
fname varchar(15) ,
lname varchar(15) ,
descr varchar(20) ,
foreign key (id) references member(id)   ON DELETE CASCADE);



create table memberscontact(
id char(9) ,
contactnumber char(10) ,
foreign key(id) references member(id) ON DELETE CASCADE,
primary key (id,contactnumber)
);



create table privileges (
privilegeNo varchar(10),
nameOfPrivilege varchar (15),
loanPeriod varchar (15)	,
MaxItemToBorrow varchar(10),
MaxItemToRenewal varchar(10));




create table loans (
loanNo varchar(10) primary key,
status varchar (20),
dateLoaned date ,
dueDate date );



 create table fines(
   id char(9),
   amount int ,
   descr varchar (15) ,
   status varchar (15),
   foreign key(id) references member(id) ON DELETE CASCADE);




create table ShortLoans (
callNo varchar (10) , 
dat DATE,
expiry DATE,
membersRequest varchar (10),
status varchar(15) );






create table books (
ISSN varchar(15) primary key,
Author varchar(15),
publisher varchar(15),
BooksNotes varchar(15),
Status varchar(15),
PhysicsOrElec varchar(10));






create table SoundRecord (
UniqueNumber varchar(10) primary key,
location  varchar(15),
publisher varchar(10),
description varchar(10));






create table Thesises (
callNo varchar(10) primary key,
Author varchar(10),
location varchar(10),
description varchar(10));




create table Journal_s (
callNo varchar(10) primary key,
availability varchar(15),
title varchar(15));



create table Room_s(
RoomNo varchar(10) primary key,
Status varchar(15),
duration varchar(15),
location varchar (15) ,
type varchar (10) );




create table OnlineDatabase(
staff varchar(10),
student varchar(10));




create table Collections(
SerialNumber varchar(10) primary key,
name varchar(15) unique,
Type varchar (10) );












create table loan_and_fine (loanNo varchar(10) references loans(loanNo) ON DELETE CASCADE , 
id char(9) references member(id) ON DELETE CASCADE );






create table book_and_Journal ( ISSN varchar(10) references book(ISSN ) ON DELETE CASCADE,
 callNo varchar(10) references Journal (callNo) );






create table book_and_thesis ( ISSN varchar(10) references book(ISSN ) ON DELETE CASCADE,
callNo varchar(10) references Thesis (callNo) ON DELETE CASCADE);




INSERT INTO  member_type
VALUES ('S0001','post graduate','Available','Ahmed','Nasser','Scintefic'),
       ('S0002','under graduate','Available','Ali','Ahmed','medical'),
       ('S0003','Staff','Not Available','Nasser','Ali','art'),
       ('S0004','community pattrons','Available','Fares','mohammed','art'),
       ('S0005','Staff','Not Available','Mohammed','saleh','history');
       
       




insert into books
values ('00385534','Tommy','Pearson','No notes','Available','Elec'),
('00988133','Harvy','RELX','No notes','Not Available','Elec'),
('04773411','Steve','RELX','No notes','Available','Elec'),
('08763455','Richard','Walters','No notes','Not Available','Physics'),
('11735545','Tommy','RELX','No notes','Available','Physics');






insert into ShortLoans
values ('528376331','2019-03-08','2019-03-09','2 Books','Available'),
('578271536','2019-05-03','2019-03-06','2 Books','Available'),
('577798634','2019-01-02','2019-03-04','2 Books','Not Available'),
('584711293','2019-08-09','2019-03-10','2 Books','Available'),
('582933245','2019-09-06','2019-03-07','2 Books','Not Available');




insert into Thesises
values ('502227365','Harvy','University',''),
('503762845','Harvy','University',''),
('504865234','Tommy','University',''),
('504873324','Steve','University',''),
('509337456','Tommy','University','');






insert into Journal_s
values ('502227365','Not Available','cooking'),
('503762845','Available','Sport'),
('504865234','Available','Sport'),
('504873324','Not Available','Reading'),
('509337456','Available','Freedoom');





insert into Collections
values ('293411','Physics','Science'),
('586512','Sport','Science'),
('680036','Biology','Moral'),
('826344','Math','Science'),
('836413','Art','Moral');









INSERT INTO  members
VALUES ('S0001','Abdullah','Ahmed','665445','02-03-1997','02-03-2015','02-03-2030','Buraidah','king khalid'),
       ('S0002','Abdullrahman','Abdullah','645445','04-06-1999','02-03-2016','05-07-2030','Buraidah','king Abdulaziz'),
       ('S0003','Mazen','Alharpy','665885','02-08-1991','01-07-2015','09-03-2030','Onaizah','king Abdullah'),
       ('S0004','Saad','Majed','665755','08-05-1995','09-04-2015','04-07-2030','Bukairyah','king khalid'),
       ('S0005','Kareem','Ahmed','634445','02-03-1992','02-03-2016','05-03-2030','Al rass','king salman');




insert into Room_s
values ('234','Available','5 Days','University','Lab'),
('355','Available','2 Days','University','Lab'),
('365','Not Available','2 Days','University','Reading room'),
('504','Not Available','4 Days','University','Reading room'),
('845','Available','6 Days','University','Working room');



INSERT INTO  privileges
VALUES ('11190','Allowed','2 Months','2','2'),
      ('28806','Not Allowed','3 Months','4','1'),
      ('37797','Allowed','5 Months','3','2'),
      ('27763','Allowed','2 Months','5','1'),
      ('87741','Not Allowed','8 Months','4','2');
 
 
 
 
 



insert into SoundRecord
values ('32499','University','RELX'),
('32577','University','RELX'),
('32744','University','RELX'),
('34566','University','Pearson'),
('34711','University','Walters');






insert into OnlineDatabase
values ('Ahmed','Yousef'),
('Ali','Khalid'),
('Ibrahim','Ali'),
('Fares','Saleh'),
('Abdullah','Nasser');








insert into fines
values ('S0001','25','Late','Available'),
('S0002','20','Book is Damaged','Available'),
('S0003','30','Late','Not Available'),
('S0004','35','Late','Available'),
('S0005','15','Late','Not Available');






insert into loans
values ('11190','Available','2019-02-06','2019-02-08'),
('27763','Available','2019-02-07','2019-02-09'),
('28806','Not Available','2019-02-03','2019-02-06'),
('37797','Available','2019-02-01','2019-02-06'),
('87741','Not Available','2019-02-01','2019-02-09');






INSERT INTO  memberscontact
VALUES ('S0001','554279653'),
       ('S0002','554367865'),
       ('S0003','554378643'),
       ('S0004','559877898'),
       ('S0005','577875311');
 
