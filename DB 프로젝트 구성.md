## soccer DB 테이블 정의 

### Player (player_id, name, age, team, position, preferred_foot, transfer_value)

- player_id : 선수 고유 ID
  
- name : 축구 선수 이름

- age : 선수 나이

- team : 축구 팀

- position : 축구 포지션

- preferred_foot : 주발이 무엇인지

- transfer_value : 이적시장 가치 (선수를 영입할 때 얼마가 필요한지)

<br/>

### Team (team_id, name, founded_year, home_stadium, league)

- team_id : 팀 고유 id

- name : 팀 이름

- founded_year : 창단 연도

- home_stadium : 홈 구장 이름 

- league : 소속 리그

<br/>

### leagues (league_id, league_name, country, tier, number_of_teams)

- league_id : 리그 고유 식별자

- league_name : 이름

- country : 리그 소속 국가

- tier : 리그 수준

- number_of_teams : 참여 팀 수

<br/>

### matches (match_id, league_id, season, match_date, home_team_id, away_team_id, stadium, referee_name, attendance)

- match_id : 경기 고유 ID 

- league_id : 리그 ID

- season : 시즌 정보

- match_date : 경기 날자

- home_team_id : 홈 팀 ID

- away_team_id : 원정 팀 ID

- stadium : 경기장 이름

- referee_name : 주심 이름

- attendance : 관중 수

<br/>

### transfers (transfer_id, player_id, player_name, from_team, to_team, transfer_fee)

- transfer_id : 이적 고유 ID

- player_id :  이적한 선수 ID

- player_name : 이적 선수 이름

- from_team : 이전 소속 팀 

- to_team : 새 소속 팀 





















































