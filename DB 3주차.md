## DataBase 실습 

```ruby
create database university;
use university;

create table classroom
	(building		varchar(15),
	 room_number		varchar(7),
	 capacity		numeric(4,0),	
	 primary key (building, room_number)
	);

create table department
	(dept_name		varchar(20), 
	 building		varchar(15), 
	 budget		        numeric(12,2) check (budget > 0),
	 primary key (dept_name)
	);

create table course
	(course_id		varchar(8), 
	 title			varchar(50), 
	 dept_name		varchar(20),
	 credits		numeric(2,0) check (credits > 0),
	 primary key (course_id),
	 foreign key (dept_name) references department (dept_name)
		on delete set null
	);

create table instructor
	(ID			varchar(5), 
	 name			varchar(20) not null, 
	 dept_name		varchar(20), 
	 salary			numeric(8,2) check (salary > 29000),
	 primary key (ID),
	 foreign key (dept_name) references department (dept_name)
		on delete set null
	);

create table section
	(course_id		varchar(8), 
         sec_id			varchar(8),
	 semester		varchar(6)
		check (semester in ('Fall', 'Winter', 'Spring', 'Summer')), 
	 year			numeric(4,0) check (year > 1701 and year < 2100), 
	 building		varchar(15),
	 room_number		varchar(7),
	 time_slot_id		varchar(4),
	 primary key (course_id, sec_id, semester, year),
	 foreign key (course_id) references course (course_id)
		on delete cascade,
	 foreign key (building, room_number) references classroom (building, room_number)
		on delete set null
	);

create table teaches
	(ID			varchar(5), 
	 course_id		varchar(8),
	 sec_id			varchar(8), 
	 semester		varchar(6),
	 year			numeric(4,0),
	 primary key (ID, course_id, sec_id, semester, year),
	 foreign key (course_id, sec_id, semester, year) references section (course_id, sec_id, semester, year)
		on delete cascade,
	 foreign key (ID) references instructor (ID)
		on delete cascade
	);

create table student
	(ID			varchar(5), 
	 name			varchar(20) not null, 
	 dept_name		varchar(20), 
	 tot_cred		numeric(3,0) check (tot_cred >= 0),
	 primary key (ID),
	 foreign key (dept_name) references department (dept_name)
		on delete set null
	);

create table takes
	(ID			varchar(5), 
	 course_id		varchar(8),
	 sec_id			varchar(8), 
	 semester		varchar(6),
	 year			numeric(4,0),
	 grade		        varchar(2),
	 primary key (ID, course_id, sec_id, semester, year),
	 foreign key (course_id, sec_id, semester, year) references section (course_id, sec_id, semester, year)
		on delete cascade,
	 foreign key (ID) references student (ID)
		on delete cascade
	);

create table advisor
	(s_ID			varchar(5),
	 i_ID			varchar(5),
	 primary key (s_ID),
	 foreign key (i_ID) references instructor (ID)
		on delete set null,
	 foreign key (s_ID) references student (ID)
		on delete cascade
	);

create table time_slot
	(time_slot_id		varchar(4),
	 day			varchar(1),
	 start_hr		numeric(2) check (start_hr >= 0 and start_hr < 24),
	 start_min		numeric(2) check (start_min >= 0 and start_min < 60),
	 end_hr			numeric(2) check (end_hr >= 0 and end_hr < 24),
	 end_min		numeric(2) check (end_min >= 0 and end_min < 60),
	 primary key (time_slot_id, day, start_hr, start_min)
	);

create table prereq
	(course_id		varchar(8), 
	 prereq_id		varchar(8),
	 primary key (course_id, prereq_id),
	 foreign key (course_id) references course (course_id)
		on delete cascade,
	 foreign key (prereq_id) references course (course_id)
	);

show databases; 
```

<br/>

## 설명 

1. create database university : university라는 이름의 새 데이터베이스를 생성한다.

2. use university : 현재 사용할 데이터베이스를 university로 설정한다.

3. create table <table_name> (...) : 새 테이블을 생성하며, 테이블 이름과 컬럼을 정의한다.

4. varchar(n) : 가변 길이 문자열 데이터 타입을 정의하며, 여기서 n은 최대 길이를 나타낸다. 예: varchar(15)는 최대 15자까지의 문자열을 저장할 수 있다.

5. numeric(p, s) : 고정 소수점 숫자 데이터 타입을 정의하며, p는 전체 자릿수(precision), s는 소수점 이하 자릿수(scale)를 나타낸다. (예: numeric(4,0)은 최대 4자리 정수를 저장할 수 있다.)

6. primary key (column_name, ...) : 지정된 컬럼을 기본 키로 설정하여 각 행이 고유함을 보장한다. 여러 컬럼을 기본 키로 사용할 수도 있다.

7. foreign key (column_name, ...) references <table_name> (column_name, ...) : 외래 키를 설정하여 다른 테이블과의 관계를 만든다. 지정된 컬럼이 다른 테이블의 기본 키나 고유 키를 참조하는 외래 키가 된다. 예: foreign key (dept_name) references department (dept_name)는 dept_name 컬럼이 department 테이블의 dept_name을 참조하는 외래 키로 설정됨을 의미한다.

8. on delete cascade : 부모 테이블의 데이터가 삭제될 때, 해당 데이터를 참조하는 자식 테이블의 데이터도 자동으로 삭제된다. 예: foreign key (course_id) references section (course_id) on delete cascade는 section 테이블에서 course_id가 삭제될 때, 이 외래 키를 참조하는 teaches 테이블의 관련 데이터도 삭제된다는 의미이다.

9. on delete set null : 부모 테이블의 데이터가 삭제될 때, 자식 테이블에서 해당 외래 키 컬럼의 값이 NULL로 설정된다. 예: foreign key (dept_name) references department (dept_name) on delete set null은 department 테이블의 dept_name이 삭제될 때, 이를 참조하는 instructor 또는 student 테이블의 dept_name 컬럼 값이 NULL로 설정된다는 의미이다.

10. check (condition) : 컬럼에 대해 특정 조건을 설정하며, 조건을 만족하지 않으면 해당 값을 삽입할 수 없다. 예: check (budget > 0)은 budget 컬럼에 0보다 큰 값만 저장할 수 있음을 의미한다.

11. show databases : 현재 MySQL 서버에서 존재하는 데이터베이스 목록을 표시한다.

12. unique : 고유한 값을 요구하는 제약 조건으로, 중복된 값이 삽입되지 않도록 한다. 예를 들어, primary key는 자동으로 고유 제약을 가진다.

<br/>

## Primary key 예시 

**1. 단일 컬럼을 기본 키로 설정**

```ruby
create table student (
    ID varchar(5),          -- 학생의 ID
    name varchar(20) not null,  -- 학생의 이름
    dept_name varchar(20),  -- 학생의 소속 학과
    tot_cred numeric(3,0) check (tot_cred >= 0),  -- 학생의 총 학점
    primary key (ID)       -- ID 컬럼을 기본 키로 설정
);
```

이 예시에서 student 테이블은 각 학생의 ID 컬럼을 기본 키로 설정합니다. 즉, ID는 고유해야 하고, 중복되는 값은 삽입될 수 없음

<br/>

**2. 복합 기본 키(여러 컬럼을 기본 키로 설정)**

```ruby
create table enrollment (
    student_id varchar(5),  -- 학생 ID
    course_id varchar(8),   -- 수강 과목 ID
    semester varchar(6),    -- 학기 (예: 'Fall', 'Spring' 등)
    year numeric(4,0),      -- 연도
    grade varchar(2),       -- 성적
    primary key (student_id, course_id, semester, year)  -- 학생, 과목, 학기, 연도를 복합 기본 키로 설정
);
```
enrollment 테이블에서 student_id, course_id, semester, year 네 개의 컬럼을 복합 기본 키로 설정함

이 조합이 유일해야 하므로, 동일한 학생이 동일한 과목을 여러 학기나 여러 해에 수강할 수는 있지만, 하나의 학기와 연도에서는 중복된 수강 기록이 존재할 수 없음






























