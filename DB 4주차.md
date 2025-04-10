## like

**SQL에서는 문자열을 비교할 때 LIKE 연산자를 사용하고, 특수 문자 %와 _을 활용하여 패턴을 정의할 수 있음**

<br/>

**1. % (퍼센트) : 아무 글자나 여러 개 올 수 있다는 의미**

예시1) 'Comp%'

'Comp'로 시작하는 모든 단어를 찾음

가능한 결과: "Computer", "Compilers", "Comp123"

<br/>

예시2) '%SQL%'

"SQL"이 어디든 포함된 단어를 찾음

가능한 결과: "Advanced SQL", "SQL Basics", "Introduction to SQL"

<br/>

**2. _ (언더스코어) : 한 글자만 아무거나 가능**

'_' 는 딱 한 글자만 올 수 있는 자리를 의미함

<br/>

예시1 : 'C_mp'

"C"로 시작하고, 중간에 한 글자가 있으며, "mp"로 끝나는 단어를 찾음

가능한 결과: "Camp", "Comp", "Cimp"

불가능한 단어: "Champ", "Cmap" (글자가 하나가 아니므로)

<br/>

다른 예제: '__3'

첫 번째와 두 번째는 아무거나 올 수 있고 "3"로 끝나는 단어를 찾음

가능한 결과: "A13", "7B3", "qX3"

<br/>

**% 또는 _를 사용하려면 like와 함께 사용해야함**

<br/>

## length

**문자열이 몇 글자인지 확인할 때 사용함. 만약 한글, 유니코드의 문자열 길이를 구하려면 CHAR_LENGTH() 사용**

```ruby
select name 
from instructor as t
where length(t.name) > 6;
```

<br/>

## order by

ORDER BY 절을 사용하면 쿼리 결과를 원하는 순서로 정렬할 수 있음. 기본적으로 오름차순(ascending, ASC)이 기본값

```ruby
오름차순 예시
select name 
from instructor as t
order by name; ▷ 알파벳 순서대로 정렬됨 (order by name adc; 과 동일)


내림차순 예시
select distinct name
from instructor
order by name desc; ▷ desc를 이용하여 내림차순으로 정렬
```

만약 order by salary desc, name asc; 와 같이 된다면, 처음 salary를 내림차순으로 정렬하고, **해당 salary의 이름이 같은 경우 name은 오름차순으로 정렬됨**

**따라서, order by A , B 에서 기준은 A가 됨**

```ruby
select salary, name
from instructor
order by salary desc, name asc; 
```

위 코드의 결과를 보면 아래와 같이 salary가 먼저 정렬되고, Kim → Singh에서 오름차순으로 정렬되어 있음

![image](https://github.com/user-attachments/assets/03760050-833b-4b13-8e42-3bcb46e4bc49)

<br/>

## between 

BETWEEN A AND B : 값이 A 이상 B 이하인 경우를 조건으로 함

```ruby
SELECT name, population
FROM country
WHERE population BETWEEN 40000000 AND 50000000;
```

<br/>

## Tuple Comparison(튜플 비교)

Tuple Comparison : 한 번에 여러 열을 비교할 수 있는 방법 

(column1, column2) = (value1, value2) 형태로 비교하면, 두 열이 각각 해당 값과 동시에 일치하는 행만 선택

```ruby
SELECT *
FROM country
WHERE (continent, population) = ('Asia', 46844000);
```


































































