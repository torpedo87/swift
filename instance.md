# instance(객체)
##초기화
```swift
struct Task {
  //stored property(메모리를 차지하는 property)
	var title:String
	var time:Int?

	var owner:Employee
	var participant:Employee?

  var type:TaskType
  enum TaskType {
    case Call
    case Report
    case Meet
    case Support

    //computed property(평소에는 메모리는 차지하지 않는 property)
    var typeTitle:String {
      get {
        let titleString:String
        switch self {
          case .Call:
            titleString = "Call"
          case .Report:
            titleString = "Report"
          case .Meet:
            titleString = "Meet"
          case .Support:
            titleString = "Support"         
        }
        return titleString
      }
    }
  }

  //초기화메소드
  init(type:TaskType, owner:Employee) {
    self.type = type
    self.title = type.typeTitle
    self.owner = owner
    self.time = nil
    self.participant = nil
  }
}

class Employee {
	var name:String?
	var phoneNumber:String?
	var boss:Employee?

  //class 초기화 메소드
  init (name:String){
    self.name = name
  }
  convenience init (name:String, phone:String) {
    self.init(name:name)
    self.phoneNumber = phone
  }
}




//class는 let으로 만들어도 수정이 가능하다
let me:Employee = Employee(name: "Alex", phone: "010-4445-6544")
//me.name = "Alex"
//me.phoneNumber = "010-4445-6544"

let toby = Employee(name: "Toby")
//toby.name = "Toby"
toby.phoneNumber = "011-4333-5555"
print("\(toby.phoneNumber)")

var callTask = Task(type:.Call, owner: me)
//var callTask = Task(title: "Call to Toby", time: 10*60, owner: me, participant: toby, type:.Call)
var reportTask = Task(type:.Report, owner: me)
//var reportTask = Task(title: "Report to Boss", time: nil, owner: me, participant: nil, type:Task.TaskType.Report)
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
```
***

```swift
enum Fuel {
    case Gasoline
    case Diesel
    case LPG
}

class Car {
    let seats:Int
    let fuel:Fuel
    var mileage:Double = 0

    // 19~20번째 코드를 수용하는 인자를 선언해보세요.
    init(seats:Int, fuel:Fuel){
        //받은 인자들을 클래스 속성에 적절히 대입해보세요
				self.seats = seats
      	self.fuel = fuel
    }
}

let mini01 = Car(seats: 5, fuel: .Diesel)
let mini02 = Car(seats: 5, fuel: .Gasoline)

```
***
