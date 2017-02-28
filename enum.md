# enum(연관성 있는 값들의 그룹, 타입묶음)
```swift
struct Task {
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

var callTask = Task(title: "Call to Toby", time: 10*60, owner: me, participant: toby, type:.Call)
var reportTask = Task(title: "Report to Boss", time: nil, owner: me, participant: nil, type:Task.TaskType.Report)
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
```swift
enum Fuel {
    case Gasoline // 휘발유
    case Diesel // 경유
    case LPG // 가스
}

// 빈 칸을 enum을 써서 채워보세요
let mini01Fuel = Fuel.Diesel
let mini02Fuel = Fuel.Gasoline

print("mini01은 연료로 \(mini01Fuel)을 쓰고, mini02는 연료로 \(mini02Fuel)을 씁니다")
```
***
# Associated Value
```swift
enum TaskType {
	case Call(number:String)
	case Report(to:Employee, when:String)
	case Meet(with:Employee, location:String)
	case Support(who:Employee, duration:Int)

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
```
***
