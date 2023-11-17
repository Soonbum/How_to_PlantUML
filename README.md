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

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/bdb4693a-ec5a-488f-9a1e-931f5fad00bc)

```
@startuml

title Parallel - Activity Diagram 

start

:핫윙을 먹는다;

:홈브루를 마신다;

if (게임을 켤까?) then (응)
  fork
    :__재밌다__!!!;
  fork again
    :TV를 보면서 소리를 지른다!!;
  end fork
else (no)
  :재미없다;
  :팝 타르트를 먹는다;
endif

:잠자러 간다;

stop

@enduml
```

### Color

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/3c5bc766-4755-4a52-aa7c-455ff076f4b8)

```
@startuml

title Color - Activity Diagram 

skinparam backgroundColor #AAAAAA
skinparam activity {
  StartColor Red
  EndColor Blue
  BackgroundColor Green
  BorderColor Yellow
}

start

:핫윙을 먹는다;

:홈브루를 마신다;

stop

@enduml
```

## Class

### Classes

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/3f3a5462-0d15-409e-8147-f59587570874)

```
@startuml

title Classes - Class Diagram

class 주거지 {
  +Int 창문들
  +void 잠금()
}

class 아파트
class 하우스
class 기숙사

@enduml
```

### Relationships

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/67c74997-65f6-482b-a5a8-47dfb751fb19)

```
@startuml

title Relationships - Class Diagram

class 주거지 {
  +Int 창문들
  +void 문잠금()
}

class 아파트
class 하우스
class 기숙사
class 창문
class 문

Dwelling <|-down- 아파트: Inheritance
Dwelling <|-down- 기숙사: Inheritance
Dwelling <|-down- 하우스: Inheritance
Dwelling "1" *-up- "many" 창문: Composition
Dwelling "1" *-up- "many" 문: Composition

@enduml
```

### Types

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/7a21fba1-8866-4152-826f-4f68fe21d58c)

```
@startuml

title Types - Class Diagram

skinparam componentStyle uml2

abstract class AbstractList {

}

class Test << general >> {
}

class System << (S,#FF7700) Singleton >>
class Date << (D,orchid) >>

class Foo1<Generics tag> {
  You can use
  several lines
  ..
  as you want
  and group
  ==
  things together.
  __
  You can have as many groups
  as you want
  --
  End of class
}

class User {
  .. Simple Getter ..
  + getName() : String
  + getAddress() : Address
  .. Some setter ..
  + setName() : String
  __ private data __
  -int age
  -- crypted --
  -String password
}

enum TimeUnit {
  DAYS
  HOURS
  MINUTES
}

interface List {

}

annotation SuppressWarnings

class Object << general >>
Object <|--- ArrayList

@enduml
```

### Properties / Methods

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/b95de903-38ba-41c1-9d44-124d99e98572)

```
@startuml

title Properties / Methods - Class Diagram

skinparam componentStyle uml2
class Car {
  .. Field Examples ..
- Name: Type { arg1, arg2, argn }
+Name: Type { arg1, arg2, argn }
#Name: Type { arg1, arg2, argn }
~Name: Type { arg1, arg2, argn }

  .. Method Examples ..
-Name(): Type { arg1, arg2, argn }
+Name(): Type { arg1, arg2, argn }
#Name(): Type { arg1, arg2, argn }
~Name(): Type { arg1, arg2, argn }

  .. Static Example ..
+{static} Name(): Type { arg1, arg2, argn }

  .. Abstract Example ..
+{abstract} Name(): Type { arg1, arg2, argn }
}

class Car
ICar ()- Car
ICar2 ()-- Car
Car -() ICar3

@enduml
```

### Interfaces

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/90b2ba27-bae3-46ad-98ea-2e0dcad1e3de)

```
@startuml

title Interfaces - Class Diagram

class Car
ICar ()- Car
ICar2 ()-- Car
Car -() ICar3

@enduml
```

### Packages

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/92170236-9fea-46e5-83f9-3701f633196a)

```
@startuml

title Packages - Class Diagram

package Node <<Node>> {
  class Worker1
}

package Rectangle <<Rect>> {
  class Worker2
}

package Folder <<Folder>> {
  class Worker3
}

package Frame <<Frame>> {
  class Worker4
}

package Internet <<Cloud>> {
  class Worker5
}

package Database <<Database>> {
  class Worker6
}

@enduml
```

## Component

### Components

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/f56800a5-43e2-43c7-aa41-5eeffe320af3)

```
@startuml

title Components - Component Diagram

[Business Logic]
[Data Access] as DA  
component [Graphic User\nInterface] as GUI

@enduml
```

### Interfaces

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/0cac1ea7-35d7-4236-b2d2-cb155c01cfd3)

```
@startuml

title Interfaces - Component Diagram

[Business Logic]
[Data Access] as DA  
component [Graphic User\nInterface] as GUI

interface IMath as Math
interface "IItems" as Items

[Business Logic] -- Math
DA .. Items

@enduml
```

### Packages

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/7363a1ff-5903-40a9-9781-6730963bfcb2)

```
@startuml

title Packages - Component Diagram

package "Front End" {
    component [Graphic User\nInterface] as GUI
}

cloud Internet {
}
 
node "Middle Tier" {
    [Business Logic]
    [Data Access] as DA  
    interface IMath as Math
    interface "IItems" as Items
} 

database "PostgreSQL\n" {
    [Stored Procs]
}

GUI -down-> Internet
Internet -down-( Math
[Business Logic] -up- Math
DA -- Items
[Business Logic] --( Items
DA .. [Stored Procs]

@enduml
```

### Labels and Notes

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/bd30c93e-92ac-47c8-9452-128ff9a1fb9a)

```
@startuml

skinparam componentStyle uml2

title Packages - Component Diagram

package "Front End" {
    component [Graphic User\nInterface] as GUI
}

cloud Internet {
}
 
node "Middle Tier" {
    [Business Logic]
    [Data Access] as DA  
    interface IMath as Math
    note left of Math : 이것은 웹 서비스\nInterface
    note right of Math : 아래 라벨을\n보십시오
    interface "IItems" as Items
    
    note left of [Business Logic]
        노트는 이것처럼
        여러 줄이 될 수
        있습니다
    end note
    
} 

database "PostgreSQL\n" {
    [Stored Procs]
}

GUI -down-> Internet
Internet -down-( Math
[Business Logic] -up- Math : Web Services
DA -up- Items  : .Net
[Business Logic] --( Items
DA .. [Stored Procs]

@enduml
```

## Deployment

### All the Elements

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/6e8f17f4-31ad-4128-a4a0-afb364e7a6d9)

```
@startuml

entity entity
file file
folder folder
boundary boundary
card card
cloud cloud
collections collections
component component
frame frame
actor actor
agent agent
artifact artifact
control control
database database
rectangle rectangle
storage storage
interface interface
label label
node node
package package
queue queue
stack stack
usecase usecase

@enduml
```

### Line Types

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/681f0566-4c8f-414f-b103-42aeb4ea271d)

```
@startuml

1 -- 2 : solid
1 .. 3 : dashed
1 -[hidden]- 4 : hidden
1 ~~ 5 : dotted
1 == 6 : bold

@enduml
```

### Relationships

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/2d916bf8-b43d-4f94-9ddb-f9d20c600de5)

```
@startuml

node 1

1 <-up- 2
1 -up-> 4
1 <-up-> 3

1 --* 7
1 --o 8
1 --+ 9
1 --# 10
1 -->> 11
1 --0 12
1 --^ 13
1 --(0 14
1 -- 15

@enduml
```

### Interfaces

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/f797938f-f696-4484-bda3-1fac935f1940)

```
@startuml

storage Thing1
storage Thing2
storage Thing3
storage Thing4
storage Thing5
Thing1 -0- Thing2
Thing1 -0)- Thing3
Thing1 -(0- Thing4
Thing1 -(0)- Thing5

@enduml
```

### Nesting

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/1691f787-0b82-45db-b636-a8df0907eef2)

```
@startuml

artifact artifact {
 card card {
  cloud cloud {
   component component {
    database database {
     file file {
      folder folder {
       frame frame {
        node node {
         package package {
          queue queue {
           stack stack {
            rectangle rectangle {
             storage storage {
             }
            }
           }
          }
         }
        }
       }
      }
     }
    }
   }
  }
 }
}

@endum
```

### Mixed

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/b8d1fbf1-53a3-4a71-b00e-2e27444cd352)

```
@startuml

skinparam rectangle {
    roundCorner<<Concept>> 54
}

rectangle "Concept Model" <<Concept>> {
    rectangle "Example 1" <<Concept>> as ex1
    rectangle "Another rectangle"
    actor John
    frame Nested {
        cloud Web
        rectangle "Another One"
    }
    card Card {
     package System
    }
}
database Database
queue Queue

@enduml
```

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
