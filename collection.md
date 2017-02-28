# let(상수) vs var(변수)
```swift
var announcement:String = ""
let intro = "다음 역은 "
let outro = "입니다."

let station = "판교역"

announcement = intro + station + outro
print(announcement)
```
***

# number vs string
```swift
//문자
let name = "Jun"
var greeting = "Hello"
greeting += " "+ name
let characters = name.characters
let count = characters.count
let url = "www.codershigh.com"
let hasProtocol = url.hasPrefix("http://")
print("\(name)")

//숫자
var currentSpeed:Int = 110
currentSpeed += 10
let intMax = Int.max
let UintMax = UInt.max
let intMin = Int.min
let UintMin = UInt.min
let pi = 3.14
let divider = 2
let halfPi = 3.14/Double(divider)

//타입 변경해서 맞춰주어야 한다
let distance = 69500
let description = "판교에서 파주는 " + String(Double(distance)/1000) + "km 거리입니다."

print(description)
```
***

# tuple(배열과 비슷하나 소괄호 사용, 길이 변경 불가)
```swift
let time1 = (9,0,48)
time1.0
let time2:(h:Int, m:Int, s:Int) =(11,51,5)
time2.h
let duration = (time1, time2)
let (start, end) = duration
let endHour = end.h
typealias Time = (h:Int, m:Int, s:Int)
typealias Duration = (start:Time, end:Time)
let today:Duration=((9,10,23),(17,8,21))
print("I studied until \(today.end.h) today")


typealias Triathlon = (swim:Int, cycle:Int, running:Int)
let sprint = Triathlon(750, 20000, 5000)
let ironMan = Triathlon(3800, 180000, 42200)
let times = ironMan.cycle/sprint.cycle

```
***

# [Collection](http://swift.leantra.kr/#collection-types)
1. Array(순서대로 접근)
```swift
//array 선언
var meetingRooms:Array<String> = ["jun","minha","wala"]
var groups:[Int] = [10, 8, 14, 9]

//array 추가
meetingRooms += ["extra"]
let maxSpeed:Int = 200
var currentSpeed:Int = 110
currentSpeed += 10

var speedHistory:[Int] = []
speedHistory += [currentSpeed]
let gpsSpeed0901 = 114.1
speedHistory.append(Int(gpsSpeed0901))

//heros에 newHero를 맨 앞으로 추가해보세요
var heros = ["프린스", "마녀", "해골 군대", "고블린 통"]
let newHero = "흑룡"
heros.insert(newHero, atIndex: 0)
print(heros)

//array 불러오기
speedHistory[0]
speedHistory.first
speedHistory.last

//array 복사
let historyBackup = speedHistory
speedHistory += [150]

```
***
2. Dictionary(key로 접근, 대괄호사용)
```swift
var roomCapacity:[String:Int]=["jun":5, "minha":3, "wala":6]

// 추가
roomCapacity["extra"]=10

//불러오기(리턴값 = lazymap collection)
roomCapacity["jun"]
let roomNames = roomCapacity.keys
let capacities = roomCapacity.values

//array형태로 불러오기
let roomNames=[String](roomCapacity.keys)
let capacities=[Int](roomCapacity.values)

```
***
3. Set(순서 없는 배열, 값이 포함되어있는지 확인) - 집합연산이 용이
```swift
//set
let subway2:Set =["시청", "을지로", "신도림"]
let subway1:Set =["개봉", "신도림", "영등포"]
//교집합
let transfer = subway1.intersect(subway2)

let heros:Set = ["프린스", "마녀", "해골 군대", "고블린 통"]
let oppHeros:Set = ["자이언트 해골", "고블린 통", "대형석궁", "프린스"]
let intersectHeros:Set = heros.intersection(oppHeros)
print(intersectHeros)

//1호선-교집합
let notTransfer = subway1.subtract(subway2)
//합집합
let union = subway1.union(subway2)
//합집합-교집합
let exOR = subway1.exclusiveOr(subway2)

```
***
