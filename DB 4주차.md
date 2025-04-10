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
select name 
from instructor as t
order by name; -> 알파벳 순서대로 정렬됨
```
