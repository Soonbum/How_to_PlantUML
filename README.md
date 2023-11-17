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

### Abstract Factory

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/4dfdba97-ee1e-4ee3-b9c3-ff0afff3f2d7)

```
@startuml

interface AbstractFactory {
    +createProductA(): AbstractProductA
    +createProductB(): AbstractProductB
}

class ConcreteFactory1 {
    +createProductA(): AbstractProductA
    +createProductB(): AbstractProductB
}

class ConcreteFactory2 {
    +createProductA(): AbstractProductA
    +createProductB(): AbstractProductB
}

interface AbstractProductA {
    +operation(): void
}

interface AbstractProductB {
    +operation(): void
}



class ConcreteProductA1 {
    +operation(): void
}

class ConcreteProductB1 {
    +operation(): void
}

class ConcreteProductA2 {
    +operation(): void
}

class ConcreteProductB2 {
    +operation(): void
}

AbstractFactory <|.. ConcreteFactory1
AbstractFactory <|.. ConcreteFactory2
AbstractProductA <|..up- ConcreteProductA1
AbstractProductB <|..up- ConcreteProductB1
AbstractProductA <|..up- ConcreteProductA2
AbstractProductB <|..up- ConcreteProductB2
ConcreteFactory1 ..> ConcreteProductA1
ConcreteFactory1 ..> ConcreteProductB1
ConcreteFactory2 ..> ConcreteProductA2
ConcreteFactory2 ..> ConcreteProductB2

AbstractFactory <-up- "Client" : operation()
AbstractProductA <-up- "Client" : operation()
AbstractProductB <-up- "Client" : operation()

@enduml
```

### Singleton

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/0b63d77f-08c7-41b3-9f0a-6f145210ef5b)

```
@startuml

class Singleton {
    -{static} instance: Singleton
    +{static} getInstance(): Singleton
    +operation(): void
}

Singleton -> Singleton : getInstance()
Singleton -up-> "Client" : operation()
note left of Singleton::instance
    private static Singleton instance;
end note

@enduml
```

### Observer

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/80ee777b-0179-468e-8562-2903bd358d3c)

```
@startuml

title Observer

interface Subject <<interface>> {
    + registerObserver(observer: Observer)
    + removeObserver(observer: Observer)
    + notifyObservers()
}

interface Observer <<interface>> {
    + update()
}

class MyTopic implements Subject {
    - observers: Observer[]
    + registerObserver(observer: Observer)
    + removeObserver(observer: Observer)
    + notifyObservers()
}

class User implements Observer {
    - username: string
    + update()
}

MyTopic --> "Observers 1..*" Observer
User ..> Subject : "Topic 0..1"

@enduml
```

## Gantt

### Lasts

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/d6db899b-5d34-4192-afba-117b22cb8772)

```
@startgantt

Project starts 2020-02-01

-- Team 1 --
[T1 - Requirements] lasts 6 days
[T1 - Design] lasts 7 days
[T1 - Implementation] lasts 13 days

-- Team 2 --
[T2 - Requirements] lasts 1 week and 4 days
[T2 - Implementation] lasts 2 weeks

@endgantt
```

### Starts

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/73ea4237-7a52-44ec-b492-98c556fa270e)

```
@startgantt

Project starts 2020-02-01

-- Team 1 --
[T1 - Requirements] lasts 6 days
[T1 - Design] lasts 7 days
[T1 - Implementation] lasts 13 days

[T1 - Requirements] starts 2020-02-02
[T1 - Design] starts 2020-02-06
[T1 - Implementation] starts 2020-02-08


-- Team 2 --
[T2 - Requirements] lasts 1 week and 4 days
[T2 - Implementation] lasts 2 weeks

[T2 - Requirements] starts 2020-02-02
[T2 - Implementation] starts 2020-02-07

@endgantt
```

### Starts & Ends

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/b0bc8d13-fe14-4531-9d96-59f549aabbd2)

```
@startgantt

Project starts 2020-02-01

-- Team 1 --
[T1 - Requirements] lasts 6 days
[T1 - Design] lasts 7 days
[T1 - Implementation] lasts 13 days

[T1 - Requirements] ends 2020-02-07
[T1 - Design] ends 2020-02-12
[T1 - Implementation] ends 2020-02-20

-- Team 2 --
[T2 - Requirements] starts 2020-02-02
[T2 - Requirements] ends 2020-02-13
[T2 - Implementation] starts 2020-02-07
[T2 - Implementation] ends 2020-02-20

-- Team 3 --
[T3 - Requirements] starts 2020-02-02 and ends 2020-02-13
[T3 - Implementation] starts 2020-02-07 and ends 2020-02-20

@endgantt
```

### Constraints and Short Names

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/07b67053-ff34-4997-badd-b7069fa9ecfe)

```
@startgantt

Project starts 2020-02-01

-- Team 1 --
[T1 - Requirements] lasts 6 days
[T1 - Design] lasts 7 days

[T1 - Requirements] ends 2020-02-07

'Adding constraint
[T1 - Design] starts at [T1 - Requirements]'s end

'Short Name
[T1 - Implementation] as [I] lasts 13 days
[I] starts at [T1 - Design]'s end

@endgantt
```

### Colors and Completed

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/29c94f39-7b43-4572-8908-fc42a23a0dd8)

```
@startgantt

Project starts 2020-02-01

-- Team 1 --
[T1 - Requirements] as [T1R] lasts 1 week and 4 days and is 22% complete
[T1 - Implementation] as [T1I] starts 2020-02-10 and ends 2020-02-22

[T1R] is colored in pink
[T1I] is colored in lightblue
[T1I] is 90% completed

-- Days Off --
[Holidays] starts 2020-02-12 and ends 2020-02-14
[Holidays] is colored in GreenYellow

@endgantt
```

### Then, Milestones, and Hyperlinks

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/09b4d1f7-905f-4cf2-b682-671e3710da6d)

```
@startgantt

Project starts 2020-02-01

-- Team 1 --
[T1 - Requirements] as [T1R] lasts 6 days
then [T1 - Design] as [T1D] lasts 7 days

'Maps work when you use html map link type
[T1R] links to [[http://www.google.com]]
[T1D] links to [[http://www.yahoo.com]]

'Milestones
[Party for Team] as [PFT] happens at [T1 - Design]'s end
[PFT] is colored in Red

@endgantt
```

### Daily & Closed Days

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/39311c26-63a4-4a9b-94e3-c7ff1215e8d3)

```
@startgantt

'Can be daily, weekly, or monthly
ganttscale daily

saturdays are closed
sunday are closed

2020/02/06 is closed
2020/03/10 to 2020/03/12 is closed

Project starts 2020-02-01

-- Team 1 --
[Version 1] as [V1] lasts 10 days
then [Version 2] as [V2] lasts 21 days

@endgantt
```

### Weekly

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/da38be89-aee2-4453-9854-bc0f8282b5cb)

```
@startgantt

'Can be daily, weekly, or monthly
ganttscale weekly

saturdays are closed
sunday are closed

2020/02/06 is closed
2020/03/10 to 2020/03/12 is closed

Project starts 2020-02-01

-- Team 1 --
[Version 1] as [V1] lasts 14 days
then [Version 2] as [V2] lasts 45 days
then [Version 3] as [V3] lasts 50 days

@endgantt
```

### Resource Usages

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/c165513f-6910-47bd-b715-95cac582ea30)

```
@startgantt

'Can be daily, weekly, or monthly
ganttscale daily

2020/02/06 is closed
2020/02/10 to 2020/02/12 is closed

Project starts 2020-02-01

-- Team 1 --
[Support] as [s] on {John:10%} {Marcy:10%} lasts 10 days
[Version 1] as [V1] on {John:50%} {Marcy:20%} lasts 4 days
then [Version 2] as [V2] on {John:60%} {Marcy:10%} lasts 14 days
then [Version 3] as [V3] on {John:10%} {Marcy:20%} lasts 8 days

{John} is off on 2020-02-06
{Marcy} is off on 2020-02-06

{John} is off on 2020-02-10 to 2020-02-12
{Marcy} is off on 2020-02-10 to 2020-02-12

@endgantt
```

### Notes

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/443b439f-f054-4fdd-addd-3c78705c4a24)

```
@startgantt

Project starts 2020-02-01

-- Team 1 --
[T1 - Requirements] as [T1R] lasts 8 days
note bottom
1. Chat w/ client
2. Write doc
3. Review with team
end note
[T1R] ends 2020-02-10

[T1 - Design] lasts 7 days
note bottom
1. List test cases
2. Think about performance
3. Security
end note


'Adding constraint
[T1 - Design] starts at [T1 - Requirements]'s end

'Short Name
[T1 - Implementation] as [I] lasts 13 days
[I] starts at [T1 - Design]'s end
note bottom
Go!!
end note

@endgantt
```

### Links & Colors

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/609e6244-dd49-4d1d-a965-8c83f253b663)

```
@startgantt

Project starts 2020-02-01

-- Team 1 --
[T1 - Requirements] as [T1R] lasts 8 days 
note bottom
1. Chat w/ client
2. Write doc
3. Review with team
end note
[T1R] ends 2020-02-10

[T1 - Design] as [T1D] lasts 7 days and starts 3 days after [T1R]'s end with blue dotted link
note bottom
1. List test cases
2. Think about performance
3. Security
end note

'Short Name
[T1 - Implementation] as [I] lasts 9 days and starts 5 days after [T1D]'s end with green dashed link

note bottom
Go!!
end note

@endgantt
```

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
