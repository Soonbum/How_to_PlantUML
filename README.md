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

### Hello World

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/b785cc38-78ee-4d41-842f-e6f84a5c5366)

```
@startuml
digraph G {
    Hello -> World
} 
@enduml
```

### World Dynamics

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/6ea8132d-b5a8-40a8-840b-8c9d79af86f8)

```
@startuml

digraph world {
size="7,7";
	{rank=same; S8 S24 S1 S35 S30;}
	{rank=same; T8 T24 T1 T35 T30;}
	{rank=same; 43 37 36 10 2;}
	{rank=same; 25 9 38 40 13 17 12 18;}
	{rank=same; 26 42 11 3 33 19 39 14 16;}
	{rank=same; 4 31 34 21 41 28 20;}
	{rank=same; 27 5 22 32 29 15;}
	{rank=same; 6 23;}
	{rank=same; 7;}

	S8 -> 9;
	S24 -> 25;
	S24 -> 27;
	S1 -> 2;
	S1 -> 10;
	S35 -> 43;
	S35 -> 36;
	S30 -> 31;
	S30 -> 33;
	9 -> 42;
	9 -> T1;
	25 -> T1;
	25 -> 26;
	27 -> T24;
	2 -> {3 ; 16 ; 17 ; T1 ; 18}
	10 -> { 11 ; 14 ; T1 ; 13; 12;}
	31 -> T1;
	31 -> 32;
	33 -> T30;
	33 -> 34;
	42 -> 4;
	26 -> 4;
	3 -> 4;
	16 -> 15;
	17 -> 19;
	18 -> 29;
	11 -> 4;
	14 -> 15;
	37 -> {39 ; 41 ; 38 ; 40;}
	13 -> 19;
	12 -> 29;
	43 -> 38;
	43 -> 40;
	36 -> 19;
	32 -> 23;
	34 -> 29;
	39 -> 15;
	41 -> 29;
	38 -> 4;
	40 -> 19;
	4 -> 5;
	19 -> {21 ; 20 ; 28;}
	5 -> {6 ; T35 ; 23;}
	21 -> 22;
	20 -> 15;
	28 -> 29;
	6 -> 7;
	15 -> T1;
	22 -> T35;
	22 -> 23;
	29 -> T30;
	7 -> T8;
	23 -> T24;
	23 -> T1;
}
@enduml
```

### Data Structures

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/a61c70cd-8211-4cb4-8927-d270f9a5bf44)

```
@startuml
digraph g {
graph [
rankdir = "LR"
];
node [
fontsize = "16"
shape = "ellipse"
];
edge [
];
"node0" [
label = "<f0> 0x10ba8| <f1>"
shape = "record"
];
"node1" [
label = "<f0> 0xf7fc4380| <f1> | <f2> |-1"
shape = "record"
];
"node2" [
label = "<f0> 0xf7fc44b8| | |2"
shape = "record"
];
"node3" [
label = "<f0> 3.43322790286038071e-06|44.79998779296875|0"
shape = "record"
];
"node4" [
label = "<f0> 0xf7fc4380| <f1> | <f2> |2"
shape = "record"
];
"node5" [
label = "<f0> (nil)| | |-1"
shape = "record"
];
"node6" [
label = "<f0> 0xf7fc4380| <f1> | <f2> |1"
shape = "record"
];
"node7" [
label = "<f0> 0xf7fc4380| <f1> | <f2> |2"
shape = "record"
];
"node8" [
label = "<f0> (nil)| | |-1"
shape = "record"
];
"node9" [
label = "<f0> (nil)| | |-1"
shape = "record"
];
"node10" [
label = "<f0> (nil)| <f1> | <f2> |-1"
shape = "record"
];
"node11" [
label = "<f0> (nil)| <f1> | <f2> |-1"
shape = "record"
];
"node12" [
label = "<f0> 0xf7fc43e0| | |1"
shape = "record"
];
"node0":f0 -> "node1":f0 [
id = 0
];
"node0":f1 -> "node2":f0 [
id = 1
];
"node1":f0 -> "node3":f0 [
id = 2
];
"node1":f1 -> "node4":f0 [
id = 3
];
"node1":f2 -> "node5":f0 [
id = 4
];
"node4":f0 -> "node3":f0 [
id = 5
];
"node4":f1 -> "node6":f0 [
id = 6
];
"node4":f2 -> "node10":f0 [
id = 7
];
"node6":f0 -> "node3":f0 [
id = 8
];
"node6":f1 -> "node7":f0 [
id = 9
];
"node6":f2 -> "node9":f0 [
id = 10
];
"node7":f0 -> "node3":f0 [
id = 11
];
"node7":f1 -> "node1":f0 [
id = 12
];
"node7":f2 -> "node8":f0 [
id = 13
];
"node10":f1 -> "node11":f0 [
id = 14
];
"node10":f2 -> "node12":f0 [
id = 15
];
"node11":f2 -> "node1":f0 [
id = 16
];
}
@enduml
```

### Graph Cluster Node Gradient

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/3b7a33c3-129b-40eb-bb3f-22173c6d266c)

```
@startuml
digraph G {
bgcolor="purple:pink" label="agraph" fontcolor="white"
  subgraph cluster1 {fillcolor="blue:cyan" label="acluster" fontcolor="white" style="filled" gradientangle="270"
		node [shape=box fillcolor="red:yellow" style="filled" gradientangle=90]
		anode;
	}

} 
@enduml
```

## Icons

### Default Library

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/70b73768-524d-43ea-9598-e4e4eec92e3b)

```
@startuml
'https://plantuml.com/stdlib
stdlib
@enduml
```

### List Open Iconic

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/d233829b-58d8-40c3-b9dc-c990c4c1c964)

```
@startuml
'https://plantuml.com/openiconic
listopeniconic
@enduml
```

### Open Iconic Example

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/21c76e41-1e33-45bf-b56c-6dbe5d579ab8)

```
@startsalt
{
  <&person*2> | "MyName                "
  <&key*2> | "****                  "
  [Cancel <&circle-x>] | [OK <&account-login>]
}
@endsalt
```

### List Archimate Sprites

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/1d8c2437-f9a0-4de0-9942-bce961946038)

```
@startuml
'https://plantuml.com/archimate-diagram
listsprites
@enduml
```

### Hitchhiker's Guide

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/1830c75c-446d-4c86-bb7a-f883d7539091)

```
@startuml

!define osaPuml https://raw.githubusercontent.com/Crashedmind/PlantUML-opensecurityarchitecture2-icons/master
!include osaPuml/Common.puml
!include osaPuml/User/all.puml
!include osaPuml/Hardware/all.puml
!include osaPuml/Misc/all.puml
!include osaPuml/Server/all.puml
!include osaPuml/Site/all.puml

listsprites

footer %filename() rendered with PlantUML version %version()\nThe Hitchhiker’s Guide to PlantUML

@enduml
```

### Hitchhiker's Guide Example

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/c782c8a2-8013-485f-907b-6e61a0c4d1da)

```
@startuml

!define osaPuml https://raw.githubusercontent.com/Crashedmind/PlantUML-opensecurityarchitecture2-icons/master
!include osaPuml/Common.puml
!include osaPuml/User/all.puml
!include osaPuml/Hardware/all.puml
!include osaPuml/Misc/all.puml
!include osaPuml/Server/all.puml
!include osaPuml/Site/all.puml

' Users
osa_user_green_developer: <$osa_user_green_developer>
osa_user_green_operations: <$osa_user_green_operations>
osa_user_green_business_manager: <$osa_user_green_business_manager>

' Devices
osa_desktop: <$osa_desktop>
osa_laptop: <$osa_laptop>
osa_iPhone: <$osa_iPhone>
osa_server: <$osa_server>

' Network
osa_device_wireless_router: <$osa_device_wireless_router>
osa_hub: <$osa_hub>
osa_firewall: <$osa_firewall>
osa_osa_cloud: <$osa_cloud>

footer %filename() rendered with PlantUML version %version()\nThe Hitchhiker’s Guide to PlantUML

@enduml
```

## JSON

### Object

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/88ada9e3-8bca-4323-9b15-7c9d9a1f7af2)

```
@startjson

{ "name" : "Mark" }

@endjson
```

### Array

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/a2dc991f-390f-4bc4-86df-06ce9114371b)

```
@startjson

["Apple","Banana", "Fig", "Pear"]

@endjson
```

### Array of Objects

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/361f8e73-1459-4afc-b591-c338de5382e2)

```
@startjson

[
  {
    "name" : "Mark", 
    "age" : 31, 
    "city" : "New York"
  },
  {
    "name" : "Amy", 
    "age" : 24, 
    "city" : "Denver"
  },
  {
    "name" : "Steve", 
    "age" : 75, 
    "city" : "San Angelo"
  }
]

@endjson
```

### Complex

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/b8c925a2-9d4b-4b7d-87d3-c707bbfb66b9)

```
@startjson

{
  "people" : [
      {
        "name" : "Mark", 
        "age" : 31, 
        "city" : "New York",
        "phone": [
          {
            "type": "home",
            "number": "867-5309"
          },
          {
            "type": "mobile",
            "number": "646 555-4567"
          }
        ]
      },
      {
        "name" : "Amy", 
        "age" : 24, 
        "city" : "Denver",
        "pets" : [ "Spot", "George", "Fred"]
      },
      {
        "name" : "Steve", 
        "age" : 75, 
        "city" : "San Angelo"
      }
    ]
}

@endjson
```

### Highlighting

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/dca34464-1e2e-4e45-be7a-9030060f1262)

```
@startjson

#highlight "people"
#highlight "people" / "2" / "age"
#highlight "people" / "0" / "phone" / "0" / "type"

{
  "people" : [
      {
        "name" : "Mark", 
        "age" : 31, 
        "city" : "New York",
        "phone": [
          {
            "type": "home",
            "number": "867-5309"
          },
          {
            "type": "mobile",
            "number": "646 555-4567"
          }
        ]
      },
      {
        "name" : "Amy", 
        "age" : 24, 
        "city" : "Denver",
        "pets" : [ "Spot", "George", "Fred"]
      },
      {
        "name" : "Steve", 
        "age" : 75, 
        "city" : "San Angelo"
      }
    ]
}

@endjson
```

### Data Types

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/95471978-245a-4bb5-ba80-bb38c86096a3)

```
@startjson

{
  "null" : null,
  "string" : "String", 
  "boolean" : true,
  "boolean" : false, 
  "number" : 1000,
  "array": ["Apple", "Banana", "Grapes"],
  "object": { "type": "home", "number": "867-5309"},
  "array of objects" :
  [
  { "type": "home", "number": "867-5309"},
  { "type": "mobile", "number": "867-5309"},
  { "type": "fax", "number": "867-5309"} ]
}

@endjson
```

### In Other Diagrams

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/ed4a116e-d34a-4eff-bc92-ef826c0ba010)

```
@startuml

title Classes - Class Diagram

class Dwelling {
  +Int Windows
  +void Lock()
}

class House
class Commune

json HouseInfo {
   "Doors":"2",
   "Windows":"24",
   "Color": ["Green", "White"]
}

House --> HouseInfo : "Details"

@enduml
```

## MindMap

### Basic

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/c260ce00-ab6c-470a-b23c-db3494082d25)

```
@startmindmap

'Compatible with OrgMode 

* Solving \n Global \n Warming

** Eating differently
*** Vegan
*** Vegetarian
*** Less processed foods
*** Buy local food
** Travel
*** Bike more
*** Ride buses
*** Buy an electric car

left side

** Home
*** Energy audit
*** Use a cloths line
*** Add insulation
*** Get solar panels
** Be a role model
*** Vote
*** Encourage others
*** Teach your kids

@endmindmap
```

### Colors & Remove Box

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/0ab69f8a-c81f-41ad-9f7f-788a57333c12)

```
@startmindmap

<style>
mindmapDiagram {
  .green {
    BackgroundColor lightgreen
  }
  .rose {
    BackgroundColor #FFBBCC
  }
}
</style>

* Solving \n Global \n Warming <<rose>>

**[#lightgreen] Eating differently
***[#Orange] Vegan
***[#Orange] Vegetarian
***[#Orange] Less processed foods
***[#Orange] Buy local food
** Travel <<green>>
***[#Orange] Bike more
***[#Orange] Ride buses
***[#Orange] Buy an electric car

left side

** Home <<green>>
***[#Orange] Energy audit
***[#Orange] Use a cloths line
***[#Orange] Add insulation
***[#Orange] Get solar panels
**[#lightgreen] Be a role model
***_ Vote
***_ Encourage others
***_ Teach your kids

@endmindmap
```

### Multilines

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/64106192-1f75-4d81-a307-2a1e4ce361c7)

```
@startmindmap

* Solving \n Global \n Warming
**[#lightgreen] Eating differently
***[#Orange] Vegan
***[#Orange] Vegetarian
***[#Orange] Less processed foods
***[#Orange] Buy local food
** Travel
***:-Bike more
-Skateboard more
-Walk more
;
***:-Ride buses
-Ride UBER
-Ride carpool
;
***:-Buy an electric car
-Buy an electric scooter
-Buy an electric skateboard
;

@endmindmap
```

### Arithmetic Notation

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/132aec63-9dd5-4937-9109-e02670c676dc)

```
@startmindmap

+ Solving \n Global \n Warming
++ Eating differently
+++ Vegan
+++ Vegetarian
+++ Less processed foods
+++ Buy local food
++ Travel
+++ Bike more
+++ Ride buses
+++ Buy an electric car

-- Home <<green>>
--- Energy audit
--- Use a cloths line
--- Add insulation
--- Get solar panels
-- Be a role model
--- Vote
--- Encourage others
--- Teach your kids

@endmindmap
```

### Markdown Syntax

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/f1b2be4e-0499-43c9-9d2b-30fe4dd087d5)

```
@startmindmap

* Solving \n Global \n Warming
 * Eating differently
  * Vegan
  * Vegetarian
  * Less processed foods
  * Buy local food
 * Travel
  * Bike more
  * Ride buses
  * Buy an electric car

 * Home
  *_ Energy audit
  *_ Use a cloths line
  *_ Add insulation
  *_ Get solar panels
 * Be a role model
  *_ Vote
  *_ Encourage others
  *_ Teach your kids

@endmindmap
```

### Extras

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/f4e5838b-96a8-402a-b8b8-e00cb1b60d29)

```
@startmindmap

caption Save World Diagram
title Save the World

header
Draft One
endheader

center footer 1 of 3

legend left
|= |= Type |
|<back:#FFBBCC>   </back>| Problem |
|<back:lightgreen>   </back>| Areas |
|<back:Orange>   </back>| Actions |
endlegend

<style>
mindmapDiagram {
  .green {
    BackgroundColor lightgreen
  }
  .rose {
    BackgroundColor #FFBBCC
  }
}
</style>

* Solving \n Global \n Warming <<rose>>

**[#lightgreen] Eating differently
***[#Orange] Vegan
***[#Orange] Vegetarian
***[#Orange] Less processed foods
***[#Orange] Buy local food
** Travel <<green>>
***[#Orange]:Bike more
Skateboard more
Walk more
;
***[#Orange]:Ride buses
Ride UBER
Ride carpool
;
***[#Orange]:Buy an electric car
Buy an electric scooter
Buy an electric skateboard
;

left side

** Home <<green>>
***[#Orange] Energy audit
***[#Orange] Use a cloths line
***[#Orange] Add insulation
***[#Orange] Get solar panels
**[#lightgreen] Be a role model
***_ Vote
***_ Encourage others
***_ Teach your kids

@endmindmap
```

### Styles

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/b9efc70d-a631-4e24-9da9-6a6891479f60)

```
@startmindmap

<style>

node {
    Padding 12
    Margin 3
    HorizontalAlignment center
    LineColor blue
    LineThickness 3.0
}

rootNode {
    LineStyle 8.0;3.0
    LineColor blue
    BackgroundColor lightgreen
    LineThickness 3.0
    RoundCorner 0
    Shadowing 5
}

leafNode {
    LineStyle 1
    LineColor red
    LineThickness 1.0
    RoundCorner 20
    Padding 3
}

arrow {
    LineStyle 4
    LineThickness 1
    LineColor blue
}
</style>

* Solving \n Global \n Warming

** Eating differently
*** Vegan
*** Vegetarian
*** Less processed foods
*** Buy local food
** Travel
***:Bike more
Skateboard more
Walk more
;
***:Ride buses
Ride UBER
Ride carpool
;
***:Buy an electric car
Buy an electric scooter
Buy an electric skateboard
;

left side

** Home
*** Energy audit
*** Use a cloths line
*** Add insulation
*** Get solar panels
** Be a role model
***_ Vote
***_ Encourage others
***_ Teach your kids

@endmindmap
```

## 기타

### Oregon Trail :)

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/de0cbe54-625e-4ea2-8090-1a0c34242d49)

```
@startuml
'https://plantuml.com/oregon-trail
run oregon trail
@enduml
```

### Handwritten Diagram

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/ef32ecbe-b6ae-4c22-bc1f-29fe3459e61b)

```
@startuml

'https://plantuml.com/handwritten
skinparam handwritten true

Alice -> Bob : hello
note right: Not validated yet
@enduml
```

### Steve Jobs 1955 - 2011

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/43c21d25-24e5-4b33-849d-d7e980303185)

```
@startuml
'https://plantuml.com/steve
apple II
@enduml
```

### Smetana project

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/46abfb6a-bb43-4859-9358-71f20eafd78f)

```
@startuml

'https://plantuml.com/smetana02

!pragma layout smetana
class Foo1

Foo1 --> Foo2
Foo1 --> Foo3
Foo1 ---> Foo4 : test 4
Foo1 ----> Foo5 : test 5

@enduml
```

### Sudoku

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/30a2de8e-e8a5-4b6c-b3e7-3fcee4efa7c2)

```
@startuml
'https://plantuml.com/sudoku
sudoku
@enduml
```

### Colors

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/7c5da2b5-e561-44da-9863-84a6d0ec7c96)

```
@startuml
'https://plantuml.com/color
colors
@enduml
```

### Colors Close To

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/f652e901-53f7-454f-9276-711c0d62549f)

```
@startuml
colors chocolate
@enduml
```

### Write Code

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/a9796fcc-3a96-48ee-a45b-6c2f6021965c)

```
@startuml

Alice -> Bob : hello
note right
<code>
main() {
  printf("Hello world");
}
</code>
end note
@enduml
```

### Legacy HTML

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/4f1c6228-c361-41f4-850d-89323ce37c7f)

```
@startuml

:* You can change <color:red>text color</color>
* You can change <back:cadetblue>background color</back>
* You can change <size:18>size</size>
* You use <u>legacy</u> <b>HTML <i>tag</i></b>
* You use <u:red>color</u> <s:green>in HTML</s> <w:#0000FF>tag</w>
----
* Use image : <img:http://plantuml.com/logo3.png>
;
@enduml
```

### Escape Character

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/d2922371-ded8-4d67-ad33-1f036f6945f7)

```
@startuml

object demo {
  This is not ~___underscored__.
  This is not ~""monospaced"".
}
@enduml
```

### Emphasized Text

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/f2782847-bbf9-4e1a-9853-24bd82e07ac7)

```
@startuml

Alice -> Bob : hello --there--
... Some ~~long delay~~ ...
Bob -> Alice : ok
note left
  This is **bold**
  This is //italics//
  This is ""monospaced""
  This is --stroked--
  This is __underlined__
  This is ~~waved~~
end note
@enduml
```

### Lists

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/eb021315-91e0-4dad-8041-d056333b37d0)

```
@startuml

object demo {
  * Bullet list
  * Second item
}
note left
  * Bullet list
  * Second item
  ** Sub item
end note

legend
  # Numbered list
  # Second item
  ## Sub item
  ## Another sub item
  # Third item
end legend
@enduml
```

## Network

### Basic Network

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/c0d0ca4d-7738-4075-82fa-5c758eb2c1ea)

```
@startuml

nwdiag {
  network home {
      address = "192.x.x.x/24"

      venus [address = "192.x.x.1"];
      mars [address = "192.x.x.2"];
  }
}
@enduml
```

### Two Levels

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/211c6360-2529-4dcd-8780-d85a01b1d30a)

```
@startuml

nwdiag {
  network dmz {
      address = "45.x.x.x/24"

      webserver [address = "45.x.x.1"];

  }
  network internal {
      address = "192.x.x.x/24"
      
      webserver [address = "45.x.x.1"];

      venus [address = "192.x.x.1"];
      mars [address = "192.x.x.2"];
  }
}
@enduml
```

### Grouping & Color

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/77898170-70e2-41df-bf1b-dd5c5ce41469)

```
@startuml

nwdiag {
    
    internet [ shape = cloud];
    internet -- router;
    
    group {
        color = "#FFAAAA";
        
        webserver;
        database;
    }
    
    network dmz {
        address = "45.x.x.x/24"
        router
        webserver [address = "45.x.x.1, 45.x.x.2"];
    
    }
    network internal {
        address = "192.x.x.x/24"
        router
        database [address = "192.x.x.1"];
        mars [address = "192.x.x.2"];
    }
}
@enduml
```

### Description & Icons

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/8a88b94d-d4e7-4b06-9c20-3b4f48a5e25b)

```
@startuml

nwdiag {
    
    internet [ shape = cloud];
    internet -- router;
    
    group {
        description = "This is my web group"
        color = "#FFAAAA";
        webserver;
        database;
    }
    
    network dmz {
        address = "45.x.x.x/24"
        router
        webserver [address = "45.x.x.1, 45.x.x.2", description = "<&spreadsheet*4>\n db"];
    
    }
    network internal {
        description = "This is my home network"
        color = "palegreen"
        address = "192.x.x.x/24"
        router [description = "<&cog*4>\n router"]
        database [address = "192.x.x.1", description = "<&spreadsheet*4>\n db", shape = database];
        mars [address = "192.x.x.2", description = "<&star*4>\n db"];
    }
}
@endum
```

### Network Objects

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/92931ee7-eedc-45d4-b5e2-18c34db5cc58)

```
@startuml

nwdiag {
  network Shapes1 {
    Actor       [shape = actor]       
    Agent       [shape = agent]       
    Artifact    [shape = artifact]    
    Boundary    [shape = boundary]    
    Card        [shape = card]        
    Cloud       [shape = cloud]       
    Collections [shape = collections] 
    Component   [shape = component]   
  }
    network Shapes2 {
    Control     [shape = control]     
    Database    [shape = database]    
    Entity      [shape = entity]      
    File        [shape = file]        
    Folder      [shape = folder]      
    Frame       [shape = frame]       
    Hexagon     [shape = hexagon]     
    Interface   [shape = interface]   
  }
  network Shapes3 {
    Label       [shape = label]       
    Node        [shape = node]        
    Package     [shape = package]     
    Person      [shape = person]      
    Queue       [shape = queue]       
    Stack       [shape = stack]       
    Rectangle   [shape = rectangle]   
    Storage     [shape = storage]     
    Usecase     [shape = usecase]     
  }
}
@enduml
```

## Object

### Properties

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/362d26e3-b8fc-41be-bd16-51503846453e)

```
@startuml

object ObjectOne
object "Object Two" as o2

o2 : id = 1
o2 : Name = "John"

@endumlml
```

### Relationships

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/e8d8624e-d7ba-4504-9880-fe13dc09a7aa)

```
@startuml

title Simple Object Diagram

object Germany
object France
object Spain
object USA
object Mexico
object Russia
object Canada
object Japan

Germany <|-- France
Spain *-- USA
Mexico o-- Russia
Canada .. Japan

Germany : Liquor = Jagermeister
France : Liquor = Wine
Spain : Liquor = Wine
USA : Liquor = BudLight
Mexico : Liquor = Taquilla
Russia : Liquor = Vodka
Canada : Liquor = Beer
Japan : Liquor = Sake

@enduml
```

### Nesting Approach

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/71abfa24-6fa5-4a98-8793-d388dfbd6b70)

```
@startuml

object "Object Two" as o2 {
    id = 1
    Name = "John"
}

```

## Salt GUI

### Basic Elements

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/82c77160-9e0b-4a2a-93ac-6c3a3e004999)

```
@startuml

salt
{
  Just plain text
  [This is my button]
  ()  Unchecked radio
  (X) Checked radio
  []  Unchecked box
  [X] Checked box
  "This is a textbox   "
  ^This is a droplist^
}

@enduml
```

### Grid

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/41fd9c68-dcb6-4f6a-97c5-bf56eb8c48e2)

```
@startsalt

{
  User Name:| "Justin     "
  Password: | "****       "
  [Ok    ]  | [  Close   ]
}

@endsalt
```

### Separator

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/cb7968d6-5c78-474b-988a-76df3bacbd29)

```
@startsalt

{
  This is a dotted line
  ..
  This is a double line
  ==
  This is a thick solid line
  ~~
  This is a thin solid line
  --
}

@endsalt
```

### Tree View

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/09bd9906-5b68-4810-8734-ff70449d25a1)

```
@startsalt

{
    {T
     + Food
     ++ Fruit
     +++ Grape
     +++ Orange
     +++ Apple
     ++++ Honey Crisp
     ++++ Granny Smith
     +++ Banana
     ++ Vegetables
     +++ Bell pepper
     +++ Spinach
     +++ Mushroom
     ++++ Crimini
     ++++ Shitaki
    }
}

@endsalt
```

### Brackets

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/31c9f5d7-1c2a-4b48-a287-c8ed24a96bd9)

```
@startsalt

{
Name         | "                 "
Direction:   | { (X) Left | () Right | () Up | () Down }
Attending?:  | {  [] Yes | [] No  
                  [] Maybe }
 [Browse...] }
}

@endsalt
```

### Tabs

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/799d642c-67c0-4a78-b497-1a47819c866a)

```
@startsalt

{+

    {/ <b>General | Fullscreen | Behavior | Saving }

    {
    Name         | "                 "
    Direction:   | { (X) Left | () Right | () Up | () Down }
    Attending?:  | {  [] Yes | [] No  
                      [] Maybe }
     [Browse...] }
    }

}

@endsalt
```

### Menus

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/4f12e728-5a36-479b-ae7f-c7de77fdc62b)

```
@startsalt

{+

{* File | Edit | Source | Refactor 
 Refactor | New | Open File | - | Close | <b>Close All</b> }

    {/ <b>General | Fullscreen | Behavior | Saving }

    {
    Name         | "                 "
    Direction:   | { (X) Left | () Right | () Up | () Down }
    Attending?:  | {  [] Yes | [] No  
                      [] Maybe }
     [Browse...] }
    }

}

@endsalt
```

### Iconic Symbols

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/ce90c4e9-3b3e-4741-8eea-9632c64100c2)

```
@startuml
listopeniconic
@enduml
```

### Iconic Example Usage

## Sequence

### Participants

### Messages

### Comments

### Message Styles

## State

### Simple State

### Simple Composite State

### Simple Orthogonal Composite State

### Concurrent State 3CPO

### Arrows and Notes

## Themes

### List All Themes

### None

### Black Knight

### Cyborg-Outline

## Timing

### Robust

### Clock

### Extras

### Concise

### Binary

### Relative Timing

### Participant Oriented

### Color, Highlight, Hide, Constraint

### Date

### Time

## Use Case

### Use Cases

### Actors

### Connections

### Stereotypes

### Directions

### Package

## Work Breakdown Structure

### OrgMode Syntax

### Direction

### Arithmetic Notation

### Icons

### Arithmetic Spaces & No Boxes

### Multiline & Color

### Style & Color

## XEarth

### Basic

### Add Place

### Add More Stars

### Relative View From Sun

### Change Grid Configuration

### Fixed Position without Shading

### View From Moon Changing Luminacity

### Adding Cities

## YAML

### One Element

### Array of Elements

### AWS Cloud Formation

### Styling

### Highlighting

### Complex YAML.org
