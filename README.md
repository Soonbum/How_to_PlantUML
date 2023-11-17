# PlantUML 사용법

1. 설치
  - JRE 설치 필수 (PATH 등록할 것)
  - Visual Studio Code > Markets > PlantUML (jebbs) 검색
2. 지원하는 확장자
  - *.wsd, *.pu, *.puml, *.plantuml, *.iuml
3. 프리뷰 보기
  - Alt + D
4. 다른 파일로 내보내기
  - VS Code에서 F1을 누르고 plantuml export 검색

# 참조 사이트

- <https://plantuml.com/>
- <https://www.planttext.com>

# UML 문법

## Activity

### Activity

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/39cba7c2-d93e-4b00-b7f6-c90c55fdf8f4)


```
@startuml

title Activity Diagram

start

:핫윙을 먹는다;

note left
  이것은 노트입니다.
  * start 키워드로 시작해서 stop 키워드로 끝납니다.
  * Activity는 콜론으로 시작해서 세미콜론으로 끝납니다.
end note

:홈브루를 마신다;

stop

@enduml
```

### Conditional

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/096ec47d-5a28-4292-a246-b440dee6b3ea)

```
@startuml

title Conditional - Activity Diagram 

start

:핫윙을 먹는다;
note right: 오른쪽에 노트 붙이기

:홈브루를 마신다;
note left: 왼쪽에 노트 붙이기

if (게임을 켤까요?) then (yes)
  :__재밌다__!!!;
else (no)
  :재미없다;
endif

:침대로 간다;

stop

@enduml
```

### Notes

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/64b13364-1b77-4b12-8dcc-daf1c3b3ac78)

```
@startuml

title Notes - Activity Diagram 

start

:핫윙을 먹는다;

note right
  노트를 여러 줄 넣을 수 있습니다.
  ....
  //이탤릭체입니다//
  ----
  <b>HTML</b> 태그도 넣을 수 있습니다
  ====
  * 불렛 기호를 넣을 수 있습니다
  ____
  "" 코드 블럭을 넣을 수 있습니다""
end note

:홈브루를 마신다;

stop

@enduml
```

### Repeat

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/75da7f53-1c13-4420-913e-f863b3e16e31)

```
@startuml

title Repeat - Activity Diagram 

start

repeat
  :핫윙을 먹는다;
  :홈브루를 마신다;
repeat while (아직도 배고파?)

stop

@enduml
```

### While Loop

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/b7d2ca36-78db-407c-a97c-e58da8c0f61a)

```
@startuml

title While Loop - Activity Diagram 

start

while (배고파?)  is (응)
  :핫윙을 먹는다;
  :홈브루를 마신다;
endwhile (아니)

:잠자러 간다;

stop

@enduml
```

### Parallel

### Color

## Class

## Component

## Deployment

## Design Patterns

## Gantt

## GraphViz

## Icons

## JSON

## MindMap

## 기타

## Network

## Object

## Salt GUI

## Sequence

## State

## Themes

## Timing

## Use Case

## Work Breakdown Structure

## XEarth

## YAML
