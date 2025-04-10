## 두 개의 table 연결하기 

문제 : 2017 가을(fall), 또는 2017 봄(spring)에 열린 강의를 찾고, 해당 강의 이름을 추출해라

상황: 현재 연도와 계절은 section table에 저장되어 있지만, 강의 이름 속성이 존재하지 않음 

해결 방법 : course table에 course_id 속성과 section table의 course_id 속성을 조건문으로 결합한 뒤 course table로 넘어가서 강의명 추출 

```ruby
select c1.dept_name
from section as s1, course as c1
where s1.semester = 'fall' and s1.year ='2017' and s1.course_id = c1.course_id

union

select c1.dept_name
from section as s1, course as c1
where s1.semester = 'spring' and s1.year = '2018' and s1.course_id = c1.course_id;
```

위 코드에서 
