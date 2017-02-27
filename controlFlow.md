# if
```swift
let subway2:Set =["시청", "을지로", "신도림"]
let subway1:Set =["개봉", "신도림", "영등포"]
let transfer = subway1.intersect(subway2)
if transfer.count > 0 {
	print("환승역은 \(transfer) 입니다")
}else{
	print("환승역은 없어요")
}
```
***

# for
```swift
let subway2:Set =["시청", "을지로", "신도림"]
for station in subway2 {
	print("이번역은 \(station)입니다")
}

```
***

# switch
```swift
var roomCapacity:[String:Int]=["jun":5, "minha":3, "wala":6]
for (roomName, capacity) in roomCapacity {
	let roomDescription:String
	switch capacity {
		case 3:
		roomDescription = "\(roomName)은 스터디 룸이며 정원은 \(capacity)명 입니다"
		case 4...10:
		roomDescription = "\(roomName)은 세미나 룸이며 정원은 \(capacity)명 입니다"
		case _ where capacity > 10:
		roomDescription = "\(roomName)의 정원은 \(capacity)명이며 신청이 필요합니다"
		default:
		roomDescription = "\(roomName)의 정보를 다시 확인해주세요"
	}
}

typealias ShopingItem = (name:String, amount:Int)
let cart = ShopingItem("beer", 1)
switch cart {
case ("beer", 0...3) : //맥주 3병 이하
    print("Guide to small item counter")
case ("beer", 51...100) : //맥주 51병이상 100병 까지
    print("Call manager")
case ("beer", let amount) where amount > 100 : //맥주 100병 초과
    print("Call police")
default: //나머지(맥주 4병 이상 50병 이하)
    print("Make wait in line")

}

```
***
