# [if](http://swift.leantra.kr/#control-flow)
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

# for(for 요소 in list)
```swift
//repeat while (javascript의 do while과 같다)
let subway2:Set =["시청", "을지로", "신도림"]
for station in subway2 {
	print("이번역은 \(station)입니다")
}


//구구단
for dan in 1...9 {
	print("\(dan)단")
	for num in 1...9 {
		print("\(dan)*\(num)=\(dan*num)")
	}
}

//학점계산기
var scores = [30, 10, 60, 70, 80, 80]
var (a,b,c) = (0,0,0)
for score in scores {
	if score >= 80 {
		a += 1
	} else if score >= 60 {
		b += 1
	} else {
		c += 1
	}
}
print("A=\(a)명, B=\(b)명, C=\(c)명")
```
***

# switch
```swift
var roomCapacity:[String:Int]=["jun":5, "minha":3, "wala":6]
for (roomName, capacity) in roomCapacity {
	let roomDescription:String
	switch capacity {
		// 1...100(1이상 100이하), 1..<100(1이상 100미만)
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
