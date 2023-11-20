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

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/7fc0dfd7-87dd-4a6c-8f45-3ceca18e4910)

```
@startsalt

{
  <&person> Login    | "MyName   "
  <&key> Password | "****     "
  [OK <&account-login>] | [Cancel <&circle-x>]
}

@endsalt
```

## Sequence

### Participants

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/4f88674a-a06f-4494-b99d-62d4365b21d4)

```
@startuml

title "Participants - Sequence Diagram"

actor User
boundary "Web GUI" as GUI
control "Shopping Cart" as SC
entity Widget
database Widgets

@enduml
```

### Messages

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/15a2092f-ada7-441f-bdd3-18a3f6506791)

```
@startuml

title "Messages - Sequence Diagram"

actor User
boundary "Web GUI" as GUI
control "Shopping Cart" as SC
entity Widget
database Widgets

User -> GUI : To boundary
GUI -> SC : To control
SC -> Widget : To entity
Widget -> Widgets : To database

@enduml
```

### Comments

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/791f61b9-c8fa-4052-8434-db6833c822e7)

```
@startuml

title "Comments - Sequence Diagram"

'This is a single line comment

/'
This is a multi-
line comment
'/

actor User
boundary "Web GUI" as GUI
control "Shopping Cart" as SC
entity Widget
database Widgets

User -> GUI : To boundary
GUI -> SC : To control
SC -> Widget : To entity
Widget -> Widgets : To database

@enduml
```

### Message Styles

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/8adf11af-cb9e-4195-86e6-cd86a9120a04)

```
@startuml

title Message Style - Sequence Diagram

Bob -> Alice
Bob ->> Alice
Bob -\ Alice
Bob \- Alice
Bob //-- Alice

Bob ->o Alice
Bob o\-- Alice

Bob <-> Alice
Bob <->o Alice

@enduml
```

## State

### Simple State

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/097a32f1-cfb5-4997-a691-78b4b9eaf311)

```
@startuml

title Simple State Model
[*] --> GlassEmpty
GlassEmpty --> [*]
GlassEmpty : Contents - void

GlassEmpty -> GlassFull
GlassFull : Water
GlassFull --> [*]

note right
this is a note
end note

@enduml
```

### Simple Composite State

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/505bf781-4bfa-4297-842f-a0efab32974d)

```
@startuml

title Simple Composite State Model
[*] --> NeilDiamond
state NeilDiamond 

state "Neil Diamond" as NeilDiamond {
  state Dancing
  state Singing
  state Smiling
  Dancing --> Singing
  Singing --> Smiling
  Smiling --> Dancing
}

@enduml
```

### Simple Orthogonal Composite State

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/98d065fa-8b16-40b3-9a48-e576739dca88)

```
@startuml

title Simple Orthogonal Composite State Model
[*] --> NeilDiamond
state NeilDiamond 

state "Neil Diamond Onstage" as NeilDiamond {
  state Dancing
  state Singing
  state Smiling
  Dancing --> Singing
  Singing --> Smiling
  Smiling --> Dancing
}

state NDoff
state "Neil Diamond in Dressing Room" as NDoff {
  state ThinkingAboutAmerica
  state WatchingGlee
  ThinkingAboutAmerica --> WatchingGlee
  WatchingGlee --> ThinkingAboutAmerica
}

NeilDiamond -Right-> NDoff : Walking
NDoff -Left-> NeilDiamond :Running

@enduml
```

### Concurrent State 3CPO

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/a7507672-61dd-47a7-90f1-624f8cf3bb01)

```
@startuml

Title Concurrent State - C3PO
[*] --> InDanger
State "In Danger" as InDanger {
  [*] -> Worrying
  Worrying --> Complaining
  Complaining --> Worrying
  --
  state "Having Illusions of Grandeur" as grandeur
  state "Calculating Odds of Survival" as survival
  [*] -> grandeur
  grandeur --> survival
  survival --> grandeur
  --
  state "Being Prissy" as prissy
  state "Hating Chewbacca" as chewbacca
  [*] -> prissy
  prissy --> chewbacca 
  chewbacca --> prissy
} 

@enduml
```

### Arrows and Notes

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/484827ee-5bee-412f-ae51-a16cd867846a)

```
@startuml

Title Arrows and Notes
State Hungry
State "Eating Burrito" as EatingBurrito
State Full
State Sleeping

note left of Hungry : Single line note
note right of EatingBurrito
    Notes can also 
    take up multiple
    lines like this
end note

Hungry -right-> EatingBurrito
EatingBurrito -down-> Full
Full -left-> Sleeping
Sleeping -up-> Hungry

@enduml
```

## Themes

### List All Themes

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/4171c448-a375-4a93-bbb3-ccadf4a63295)

```
@startuml
help themes
@enduml
```

### None

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/2e6ae00b-f53c-4159-8713-a7a502793275)

```
@startuml

!theme _none_

title Relationships - Class Diagram

class Dwelling {
  +Int Windows
  +void LockTheDoor()
}

class Apartment
class House
class Commune
class Window
class Door

Dwelling <|-down- Apartment: Inheritance
Dwelling <|-down- Commune: Inheritance
Dwelling <|-down- House: Inheritance
Dwelling "1" *-up- "many" Window: Composition
Dwelling "1" *-up- "many" Door: Composition

@enduml
```

### Black Knight

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/030796ed-b0e6-47f7-a305-985ded351c9f)

```
@startuml

!theme black-knight

title Relationships - Class Diagram

class Dwelling {
  +Int Windows
  +void LockTheDoor()
}

class Apartment
class House
class Commune
class Window
class Door

Dwelling <|-down- Apartment: Inheritance
Dwelling <|-down- Commune: Inheritance
Dwelling <|-down- House: Inheritance
Dwelling "1" *-up- "many" Window: Composition
Dwelling "1" *-up- "many" Door: Composition

@enduml
```

### Cyborg-Outline

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/1e3bbd08-8148-4e57-b602-c5d01ea1522d)

```
@startuml

!theme cyborg-outline

title Relationships - Class Diagram

class Dwelling {
  +Int Windows
  +void LockTheDoor()
}

class Apartment
class House
class Commune
class Window
class Door

Dwelling <|-down- Apartment: Inheritance
Dwelling <|-down- Commune: Inheritance
Dwelling <|-down- House: Inheritance
Dwelling "1" *-up- "many" Window: Composition
Dwelling "1" *-up- "many" Door: Composition

@enduml
```

## Timing

### Robust

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/7d1d5efe-101b-496d-a502-9a791c057b45)

```
@startuml

robust "Job Queue" as JQ

@0
JQ is Idle

@50
JQ is Processing

@250
JQ is Logging

@250
JQ is Waiting

@500
JQ is Idle

@enduml
```

### Clock

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/c4717d04-6fdb-4704-b45a-3884328bc288)

```
@startuml

clock clk with period 1
robust "Job Queue" as JQ

@0
JQ is Idle

@2
JQ is Processing

@5
JQ is Logging

@10
JQ is Waiting

@15
JQ is Idle

@enduml
```

### Extras

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/6b8d33f8-3bb6-4861-a542-1b3b91e52fb0)

```
@startuml

Title Job Queue
header: Software Department
footer: Sprint 32
legend
Insert Legend Here
end legend
caption Team T-Rex

robust "Job Queue" as JQ

@0
JQ is Idle

@2
JQ is Processing

@5
JQ is Logging

@10
JQ is Waiting

@15
JQ is Idle

@enduml
```

### Concise

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/218a5bc5-315a-4ac9-9dd5-e9abbfbbfa8a)

```
@startuml

clock clk with period 1
robust "Job Queue" as JQ
concise "User" as U

@0
JQ is Idle
U is "Run Feature"

@2
JQ is Processing
U is Waiting

@12
JQ is Logging
U is "Checking Log"

@15
JQ is Idle
U is Done

@enduml
```

### Binary

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/27074394-6c8b-404f-81ad-11b85be698a8)

```
@startuml
clock clk with period 1
binary "ReadWrite" as RW

@0
RW is low

@2
RW is high

@5
RW is low

@6
RW is high

@enduml
```

### Relative Timing

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/a46607a9-44c5-4205-9a1e-6d562f1a8315)

```
@startuml

robust "Job Queue" as JQ
concise "User" as U

@0
JQ is Idle
U is "Wait"

@2
JQ is Processing
U is Waiting
U -> JQ : "Clicked Button"

@6
JQ -> U@+1 : Almost Complete Message

@7
U is "Waiting"

@12
U -> JQ : "DB Job Status"
JQ is Logging
U is "Checking Log"

@15
JQ is Idle
U is Done

@enduml
```

### Participant Oriented

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/2a5ba66a-c296-49c4-abf4-0a2bc89cf152)

```
@startuml
robust "Work" as W
concise "General" as G

@W
0 is "Main Process"
+5 is "Start worker Process 1"
+1 is "Start worker Process 2"
+1 is "Start worker Process 3"
+1 is "Start worker Process 4"
+1 is "Main Process"

@G
0 is Waiting
+5 is "Process Images"
+4 is "Done"
@enduml
```

### Color, Highlight, Hide, Constraint

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/f2cb9377-ade6-4cae-83fe-5530e7a712dc)

```
@startuml
robust "Work" as W
concise "General" as G

@W
0 is "Main Process"
+5 is "Start worker Process 1"
+1 is "Start worker Process 2"
+1 is "Start worker Process 3"
+1 is "Start worker Process 4"
+1 is "Main Process"

@G
0 is Waiting #yellow
+5 is "Process Images" #green
+4 is "Done" #pink

@2 <-> @+1 : {Too long}

highlight 6 to 7 #Gold;line:Red : "Process 2 Updated Database"

hide time-axis

@enduml
```

### Date

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/112ffb1c-be9f-47da-88e2-8e57135998d1)

```
@startuml

robust "Business Process" as BP

@2021/01/26
BP is "New Work Order"

@2021/02/02
BP is "Picked Up By Team"

@2021/02/04
BP is "Product Delivered"

@enduml
```

### Time

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/0d277618-2599-49c2-8c63-68b9e7c35a66)

```
@startuml

robust "My Day" as MD

@08:00:00
MD is "Get to work"

@11:30:00
MD is "Lunch!!!!"

@12:30:00
MD is "Get to work"

@15:00:00
MD is "Ride bike home"

@enduml
```

## Use Case

### Use Cases

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/f8b8c88d-3125-4fb1-b3f4-8307c2ea9a77)

```
@startuml

skin rose

title Use Case Diagram 


(Login)
(Run Process) as (Proc1)
usecase (Undo Process)
usecase (Log Out) as UC4

@enduml
```

### Actors

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/064517bb-3afe-4415-aa88-477f786fd79e)

```
@startuml

skin rose

title Actors - Use Case Diagram 


:Administrator:
:Standard User: as SU  
actor Accountant
actor :Client: as C

@enduml
```

### Connections

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/2dc10768-3554-419a-975a-182d2e2bb889)

```
@startuml

skin rose

Employee -up-|> User
Client -up-|> User
Supervisor -up-|> User
Employee --> (Login)
Supervisor --> (Login)
Client ..> (Login) : NO!!!!
Supervisor --> (Create / Delete User): I am god

@enduml
```

### Stereotypes

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/c1d7b0cb-a742-4fe2-ad5a-2834ca99aa58)

```
@startuml

skin rose

title Stereotypes - Use Case Diagram


(Login) as L
(Upload File) as UF<<Manual>>
actor :User: as U<<Person>>
:HAL: as H<<Computer>>

U -> UF
U ---> (L)
H <.up.> (L)

@enduml
```

### Directions

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/fc3d229d-8dc5-4f0a-afb4-b87cce054da2)

```
@startuml

skin rose

title Directions - Use Case Diagram

actor :Admin: as A

A -> (Login)
A --> (Logout)
A -left-> (Copy / Paste)
A -up-> (Bulk Upload)
A ---> (Throw Computer Out Of Window!!!)

@enduml
```

### Package

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/da108667-9404-436f-bfcf-6e888bf336bd)

```
@startuml

skin rose

title Package - Use Case Diagram


rectangle Features {
    (Login)
    (Create / Delete User) as CDU
}

:Employee: 
:Client:
:Supervisor:

Employee --> (Login)
Supervisor --> (Login)
Client ..> (Login) : NO!!!!
Supervisor ---> CDU: I am god

@enduml
```

## Work Breakdown Structure

### OrgMode Syntax

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/01f5e911-9795-491e-ad9d-2ca2f427d835)

```
@startwbs

skin rose

* Software Project
** Requirements
*** Purpose
*** Description
*** End-user needs
*** High level estimation
** Design
*** Build Design Document
**** Concise text description
**** Highly informative UML diagrams
*** Build team
**** John (The database) Dawkins
**** Sally (The javascript) Marten
**** Fred (The Animal) Johnson
*** Start detailed estimation
** Implemetation
*** Setup DevOps
*** Write Unit Tests
*** Write Code!!!!! :)
** Testing
*** Make sure unit tests are working
*** Regression test everything
*** Smoke test before release
*** Performance testing
** Deployment
*** Please make sure this is automated!!
** Maintenance
*** Measure usage of all features
*** Think about what functions can be removed
*** Optimize any IT systems
@endwbs
```

### Direction

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/ec453536-04b9-4d77-a337-984f3b232851)

```
@startwbs

skin rose

* Software Project
** Design
*** Build Design Document
****< Concise text description
**** Highly informative UML diagrams
***< Build team
****< John (The database) Dawkins
****> Sally (The javascript) Marten
****< Fred (The Animal) Johnson
***< Start detailed estimation
@endwbs
```

### Arithmetic Notation

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/d982a194-9e7e-4f5f-b783-4c788b771a43)

```
@startwbs

skin rose

+ Software Project
++ Design
+++ Build Design Document
++++ Concise text description
++++ Highly informative UML diagrams
+++ Build team
++++ John (The database) Dawkins
++++ Sally (The javascript) Marten
++++ Fred (The Animal) Johnson
+++ Start detailed estimation
@endwbs
```

### Icons

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/ccbbb509-429f-4b49-be18-05b5bb103326)

```
@startwbs

skin rose

+ Software Project
++ Design
+++ <&document>Build Design Document
++++ <&text>Concise text description
++++ <&share>Highly informative UML diagrams
+++ Build team
++++ <&person>John (The database) Dawkins
++++ <&person>Sally (The javascript) Marten
++++ <&person>Fred (The Animal) Johnson
+++ <&person>Start detailed estimation
@endwbs
```

### Arithmetic Spaces & No Boxes

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/0902d419-dc4d-4dfc-8210-873869db8e0a)

```
@startwbs

skin rose

+ Software Project
 + Design
  + <&document>Build Design Document
   + <&text>Concise text description
   +_ <&share>Highly informative UML diagrams
  + Build team
   + <&person>John (The database) Dawkins
   + <&person>Sally (The javascript) Marten
   + <&person>Fred (The Animal) Johnson
  + <&person>Start detailed estimation
@endwbs
```

### Multiline & Color

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/6cdf3668-36da-48da-8c57-d6903ae154cd)

```
@startwbs

skin rose

<style>
wbsDiagram {
  .pinkname {
      BackgroundColor pink
  }
}
</style>

* Software Project
**[#SkyBlue] Design
***< Build Design Document
****_ Concise text description
****_ Highly informative UML diagrams
***: Build team
 - John (The database) Dawkins
 - Sally (The javascript) Marten
 - Fred (The Animal) Johnson; <<pinkname>>
*** Start detailed estimation
@endwbs
```

### Style & Color

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/fabadf64-9db3-4dce-b919-7e0d88c4673c)

```
@startwbs

skin rose

<style>
wbsDiagram {
    
    Linecolor black
    .pinkname {
        BackgroundColor pink
    }
    arrow {
        LineColor green
    }
    :depth(0) {
        BackgroundColor White
        RoundCorner 10
        LineColor red
    }
    arrow {
        :depth(2) {
            LineColor blue
            LineStyle 4
            LineThickness .5
        }
    }
    node {
        :depth(2) {
            LineStyle 2
            LineThickness 2.5
        }
    }
    boxless {
        FontColor darkgreen
    }
}
</style>

* Software Project
**[#SkyBlue] Requirements
***< ...
**[#SkyBlue] Design
***< Build Design Document
****_ Concise text description
****_ Highly informative UML diagrams
***: Build team
 - John (The database) Dawkins
 - Sally (The javascript) Marten
 - Fred (The Animal) Johnson; <<pinkname>>
*** Start detailed estimation
@endwbs
```

## XEarth

### Basic

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/6e4cbd28-0741-4691-80f2-b1b98f6ef7c1)

```
@startuml
xearth
@enduml
```

### Add Place

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/405aaaef-8710-47ad-bf40-c0c9c854cc80)

```
@startuml
xearth(600,600)
viewMagnification = 1.0
daySideBrightness = 100
nightSideBrightness = 50
terminatorDiscontinuity = 30
sunPosRelLong = -40
sunPosRelLat = 20
39.75 -105.00 "Denver"
@enduml
```

### Add More Stars

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/9dbbfedf-e759-4acf-8071-a85cc2139f94)

```
@startuml
xearth(300,300)
starsP = true
starFrequency = 0.025
bigStars = 20
@enduml
```

### Relative View From Sun

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/8e755da0-0716-46ff-84d6-89bf83f17d0a)

```
@startuml
xearth(300,300)
viewPositionType = Sun-relative
sunPosRelLat = -10
sunPosRelLong = 40
@enduml
```

### Change Grid Configuration

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/1209add3-6058-49ec-b9ac-69930f3fb963)

```
@startuml
xearth(300,300)
gridP = true
gridDivision = 9
gridPixelDivision = 8
@enduml
```

### Fixed Position without Shading

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/359ab8b5-d4bf-4cbe-8e12-f53bc7c1a1ed)

```
@startuml
xearth(300,300)
viewPositionType = Fixed
viewPosLat = -30
viewPosLong = -30
shadeP = false
gridP = false
@enduml
```

### View From Moon Changing Luminacity

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/7ce5b704-0d37-42a5-be3b-6d27e1eeb010)

```
@startuml
xearth(300,300)
viewPositionType = Moon
daySideBrightness = 100
nightSideBrightness = 30
terminatorDiscontinuity = 50
@enduml
```

### Adding Cities

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/8b8f16db-bb13-49f2-8abe-e2d55532dc05)

```
@startuml
xearth
 61.17 -150.00 "Anchorage"           # Alaska, USA
 38.00   23.73 "Athens"              # Greece
 33.4    44.4  "Baghdad"             # Iraq
 13.73  100.50 "Bangkok"             # Thailand
 39.92  116.43 "Beijing"             # China
 52.53   13.42 "Berlin"              # Germany
 32.3   -64.7  "Bermuda"             # Bermuda
 42.33  -71.08 "Boston"              # Massachusetts, USA
-15.8   -47.9  "Brasilia"            # Brazil
 -4.2    15.3  "Brazzaville"         # Congo
-34.67  -58.50 "Buenos Aires"        # Argentina
 31.05   31.25 "Cairo"               # Egypt
 22.5    88.3  "Calcutta"            # India
-33.93   18.47 "Cape Town"           # South Africa
 33.6    -7.6  "Casablanca"          # Morocco (Rabat?)
 41.83  -87.75 "Chicago"             # Illinois, USA
 32.78  -96.80 "Dallas"              # Texas, USA
 28.63   77.20 "New Delhi"           # India
 39.75 -105.00 "Denver"              # Colorado, USA
 24.23   55.28 "Dubai"               # UAE (Abu Dhabi?)
-27.1  -109.4  "Easter Island"       # Easter Island
-18.0   178.1  "Fiji"                # Fiji
 13.5   144.8  "Guam"                # Guam
 60.13   25.00 "Helsinki"            # Finland
 22.2   114.1  "Hong Kong"           # Hong Kong
 21.32 -157.83 "Honolulu"            # Hawaii, USA
 52.2   104.3  "Irkutsk"             # Irkutsk, Russia
 41.0    29.0  "Istanbul"            # Turkey (Ankara?)
 -6.13  106.75 "Jakarta"             # Indonesia
 31.8    35.2  "Jerusalem"           # Israel
 34.5    69.2  "Kabul"               # Afghanistan
 27.7    85.3  "Kathmandu"           # Nepal
 50.4    30.5  "Kiev"                # Ukraine
  3.13  101.70 "Kuala Lumpur"        # Malaysia
  6.45    3.47 "Lagos"               # Nigeria
-12.10  -77.05 "Lima"                # Peru
 51.50   -0.17 "London"              # United Kingdom
 40.42   -3.72 "Madrid"              # Spain
 14.6   121.0  "Manila"              # The Phillipines
 21.5    39.8  "Mecca"               # Saudi Arabia
 19.4   -99.1  "Mexico City"         # Mexico
 25.8   -80.2  "Miami"               # Florida, USA
  6.2   -10.8  "Monrovia"            # Liberia
 45.5   -73.5  "Montreal"            # Quebec, Canada
 55.75   37.70 "Moscow"              # Russia
 -1.28   36.83 "Nairobi"             # Kenya
 59.93   10.75 "Oslo"                # Norway
 48.87    2.33 "Paris"               # France
-32.0   115.9  "Perth"               # Australia
 45.5  -122.5  "Portland"            # Oregon, USA
 -0.2   -78.5  "Quito"               # Ecuador
 64.15  -21.97 "Reykjavik"           # Iceland
-22.88  -43.28 "Rio de Janeiro"      # Brazil
 41.88   12.50 "Rome"                # Italy
 11.0   106.7  "Ho Chi Minh City"    # Vietnam (Hanoi?)
 37.75 -122.45 "San Francisco"       # California, USA
  9.98  -84.07 "San Jose"            # Costa Rica
 18.5   -66.1  "San Juan"            # Puerto Rico
-33.5   -70.7  "Santiago"            # Chile
  1.2   103.9  "Singapore"           # Singapore
 42.67   23.30 "Sofia"               # Bulgaria
 59.33   18.08 "Stockholm"           # Sweden
-33.92  151.17 "Sydney"              # Australia
-17.6  -149.5  "Tahiti"              # Tahiti
 16.8    -3.0  "Timbuktu"            # Mali (Bamako?)
 35.67  139.75 "Tokyo"               # Japan
 43.70  -79.42 "Toronto"             # Ontario, Canada
 32.9    13.2  "Tripoli"             # Libya
 47.9   106.9  "Ulan Bator"          # Mongolia
 49.22 -123.10 "Vancouver"           # B.C., Canada
 48.22   16.37 "Vienna"              # Austria
 38.9   -77.0  "Washington"          # United States
-41.28  174.78 "Wellington"          # New Zealand
 62.5  -114.3  "Yellowknife"         # N.T., Canada
 90.00    0.00 "North Pole"          # North Pole
-90.00    0.00 "South Pole"          # South Pole
@enduml
```

## YAML

### One Element

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/7f8dd4a3-0dae-41cd-b5aa-d81658877c01)

```
@startyaml

Hello:  World <&globe>

@endyaml
```

### Array of Elements

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/f625f48e-4f27-4a61-b45d-41720513e2fe)

```
@startyaml

Hello:
  - Thing 1
  - Thing 2    
  - Thing 3  

World:
  - Thing 1
  - Thing 2    
  - Thing 3   

@endyaml
```

### AWS Cloud Formation

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/0256c412-a664-49ec-92cc-cf1791c7b728)

```
@startyaml

# https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/gettingstarted.templatebasics.html

Parameters:
  KeyName:
    Description: Name of an existing EC2 KeyPair to enable SSH access into the WordPress web server
    Type: AWS::EC2::KeyPair::KeyName
  WordPressUser:
    Default: admin
    NoEcho: true
    Description: The WordPress database admin account user name
    Type: String
    MinLength: 1
    MaxLength: 16
    AllowedPattern: "[a-zA-Z][a-zA-Z0-9]*"
  WebServerPort:
    Default: 8888
    Description: TCP/IP port for the WordPress web server
    Type: Number
    MinValue: 1
    MaxValue: 65535

@endyaml
```

### Styling

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/9b85f29b-1c34-4e0f-b733-c17c0f5166d6)

```
@startyaml

<style>

yamlDiagram {

  node {
    FontSize 16
    FontStyle normal
    FontColor blue
    BackGroundColor lightgray
    LineColor blue

    RoundCorner 10
    LineThickness 1
    LineStyle 6-10
    
    separator {
      LineStyle 3
      LineThickness 2
      LineColor red
    }
    
  }
  
  arrow {
    LineColor green
    LineThickness 5
    LineStyle 2-5
  }
  
}

</style>

HealthCheck:
  Target: !Join 
    - ''
    - - 'HTTP:'
      - !Ref WebServerPort
      - /

@endyaml
```

### Highlighting

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/47994e85-5913-4551-8ef6-b1bc776d87f1)

```
@startyaml

# https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/gettingstarted.templatebasics.html

#highlight "Parameters" / "KeyName"
#highlight "Parameters" / "WordPressUser" / "Description"

Parameters:
  KeyName:
    Description: Name of an existing EC2 KeyPair to enable SSH access into the WordPress web server
    Type: AWS::EC2::KeyPair::KeyName
  WordPressUser:
    Default: admin
    NoEcho: true
    Description: The WordPress database admin account user name
    Type: String
    MinLength: 1
    MaxLength: 16
    AllowedPattern: "[a-zA-Z][a-zA-Z0-9]*"
  WebServerPort:
    Default: 8888
    Description: TCP/IP port for the WordPress web server
    Type: Number
    MinValue: 1
    MaxValue: 65535

@endyaml
```

### Complex YAML.org

![image](https://github.com/Soonbum/How_to_PlantUML/assets/16474083/a5f81e85-77dc-46c3-aa0b-8eb8a79e87b9)

```
@startyaml

# yaml.org

YAML: YAML Ain't Markup Language™

What It Is:
  YAML is a human-friendly data serialization
  language for all programming languages.

YAML Resources:
  YAML Specifications:
  - YAML 1.2:
    - Revision 1.2.2      # Oct 1, 2021 *New*
    - Revision 1.2.1      # Oct 1, 2009
    - Revision 1.2.0      # Jul 21, 2009
  - YAML 1.1
  - YAML 1.0

  YAML Matrix Chat:  '#chat:yaml.io'     # Our New Group Chat Room!
  YAML IRC Channel:  libera.chat#yaml    # The old chat
  YAML News:         twitter.com/yamlnews
  YAML Mailing List: yaml-core           # Obsolete, but historical

  YAML on GitHub:                        # github.com/yaml/
    YAML Specs:        yaml-spec/
    YAML 1.2 Grammar:  yaml-grammar/
    YAML Test Suite:   yaml-test-suite/
    YAML Issues:       issues/

  YAML Reference Parsers:
  - Generated Reference Parsers
  - YPaste Interactive Parser

  YAML Test Matrix:   matrix.yaml.io

YAML Frameworks and Tools:
  C/C++:
  - libfyaml      # "C" YAML 1.2 processor (YTS)
  - libyaml       # "C" Fast YAML 1.1 (YTS)
  - libcyaml      # YAML de/serialization of C data (using libyaml)
  - yaml-cpp      # C++ YAML 1.2 implementation

  Crystal:
  - YAML          # YAML 1.1 from the standard library

  C#/.NET:
  - YamlDotNet    # YAML 1.1/(1.2) library + serialization (YTS)
  - yaml-net      # YAML 1.1 library

  D:
  - D-YAML        # YAML 1.1 library w/ official community support (YTS)

  Dart:
  - yaml          # YAML package for Dart

  Delphi:
  - Neslib.Yaml   # YAML 1.1 Delphi binding to libyaml (YTS)

  Elixir:
  - yaml-elixir   # YAML support for the Elixir language

  Erlang:
  - yamerl        # YAML support for the Erlang language

  Golang:
  - Go-yaml       # YAML support for the Go language
  - Go-gypsy      # Simplified YAML parser written in Go
  - goccy/go-yaml # YAML 1.2 implementation in pure Go

  Haskell:
  - HsYAML         # YAML 1.2 implementation in pure Haskell (YTS)
  - YamlReference  # Haskell 1.2 reference parser
  - yaml           # YAML 1.1 Haskell framework (based on libyaml)

  Java:
  - SnakeYAML Engine  # Java 8+ / YAML 1.2
  - SnakeYAML         # Java 5 / YAML 1.1
  - YamlBeans         # To/from JavaBeans. YAML 1.0/1.1
  - eo-yaml           # YAML 1.2 for Java 8. Packaged as a Module (Java 9+)
  - Chronicle-Wire    # Java Implementation

  JavaScript:
  - yaml          # JavaScript parser/stringifier (YAML 1.2, 1.1) (YTS)
  - js-yaml       # Native PyYAML port to JavaScript (Demo)

  Nim:
  - NimYAML       # YAML 1.2 implementation in pure Nim (YTS)

  OCaml:
  - ocaml-yaml    # YAML 1.1/1.2 via libyaml bindings
  - ocaml-syck    # YAML 1.0 via syck bindings

  Perl Modules:
  - YAML          # Pure Perl YAML 1.0 Module
  - YAML::XS      # Binding to libyaml
  - YAML::Syck    # Binding to libsyck
  - YAML::Tiny    # A small YAML subset module
  - YAML::PP      # A YAML 1.2/1.1 processor (YTS)

  PHP:
  - The Yaml Component  # Symfony Yaml Component (YAML 1.2)
  - php-yaml      # libyaml bindings (YAML 1.1)
  - syck          # syck bindings (YAML 1.0)
  - spyc          # yaml loader/dumper (YAML 1.?)

  Python:
  - PyYAML        # YAML 1.1, pure python and libyaml binding
  - ruamel.yaml   # YAML 1.2, update of PyYAML; comments round-trip
  - PySyck        # YAML 1.0, syck binding
  - strictyaml    # Restricted YAML subset

  R:
  - R YAML        # libyaml wrapper

  Raku:
  - YAMLish       # Port of YAMLish to Raku
  - YAML::Parser::LibYAML  # LibYAML wrapper

  Ruby:
  - psych         # libyaml wrapper (in Ruby core for 1.9.2)
  - RbYaml        # YAML 1.1 (PyYAML Port)
  - yaml4r        # YAML 1.0, standard library syck binding

  Rust:
  - yaml-rust     # YAML 1.2 implementation in pure Rust
  - serde-yaml    # YAML de/serialization of structs

  Shell:
  - parse_yaml    # Simple YAML parser for Bash using sed and awk
  - shyaml        # Read YAML files - jq style

  Swift:
  - Yams          # libyaml wrapper

  Others:
  - yamlvim       # YAML dumper/emitter in pure vimscript

Related Projects:
  - Rx            # Multi-Language Schemata Tool for JSON/YAML
  - Kwalify       # Ruby Schemata Tool for JSON/YAML 
  - pyKwalify     # Python Schemata Tool for JSON/YAML
  - yatools.net   # Visual Studio editor for YAML
  - JSON          # Official JSON Website
  - Pygments      # Python language Syntax Colorizer /w YAML support
  - yamllint      # YAML Linter based on PyYAML
  - YAML Diff     # Semantically compare two YAML documents
  - JSON Schema   # YAML-compliant JSON standard for data validation
          
@endyaml
```
