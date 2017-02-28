# Struct(값이 복사된다, 여러 데이터를 한꺼번에, 상속불가)
```swift
struct Task {
	var title:String
	var time:Int?
}

var callTask = Task(title: "Call to Jun", time: 10*60)
var reportTask = Task(title: "Report to Boss", time: nil)
var todayTask:[Task] = []
todayTask += [callTask, reportTask]
// todayTask 에 들어가는 callTask는 복사된 값이다
todayTask[1].time = 15*60
callTask.title = "Call to Minha"
// 이때 callTask 원본을 변경해도 todayTask에 들어간 callTask는 복사본이므로 바꾸지 못한다
print("today task=\(todayTask), callTask=\(callTask)")


struct Car {
    let name:String
    var distance:Double
}

// tryCar의 모델명은 "트라이카"이고, 총 주행 거리는 29.9km입니다.
var tryCar = Car(name: "트라이카", distance: 29.9)

print("tryCar의 모델 명은 \(tryCar.name)이고, 총 주행 거리는 \(tryCar.distance)입니다.")
```
***

# Class(참조, 상속가능) (class = 우유,  object = 바나나우유)
```swift
struct Task {
	var title:String
	var time:Int?

	var owner:Employee
	var participant:Employee?
}

class Employee {
	var name:String?
	var phoneNumber:String?
	var boss:Employee?
}

//class는 let으로 만들어도 수정이 가능하다
let me:Employee = Employee()
me.name = "Alex"
me.phoneNumber = "010-4445-6544"

let toby = Employee()
toby.name = "Toby"
toby.phoneNumber = "011-4333-5555"
print("\(toby.phoneNumber)")

var callTask = Task(title: "Call to Toby", time: 10*60, owner: me, participant: toby)
var reportTask = Task(title: "Report to Boss", time: nil, owner: me, participant: nil)
var todayTask:[Task] = []
callTask.participant?.phoneNumber = "010-3455-5555"
print("\(toby.phoneNumber)")
// 복사본을 수정했는데 원본도 수정되었다

todayTask += [callTask, reportTask]
// todayTask 에 들어가는 callTask는 복사된 값이다
todayTask[1].time = 15*60
callTask.title = "Call to Minha"
// 이때 callTask를 변경해도 todayTask에 들어간 callTask는 복사본이므로 바꾸지 못한다
print("today task=\(todayTask), callTask=\(callTask)")


class Car {
    var mileage:Double = 0
}

let mini01 = Car()
mini01.mileage += 51.2


let mini02 = Car()
mini02.mileage += 21.6

mini01.mileage += 17.3


print("mini 01 run \(mini01.mileage)\nmini 02 run \(mini02.mileage)")


```
***
