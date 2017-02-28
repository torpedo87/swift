# Function(중복되는 코드를 정리하기 위해 사용)
```swift
var title : String = "Storyboard"
var ratings : [Double]? = nil
var supportURL : String! = nil
supportURL = "www.codershigh.com"
ratings = [4.5, 3.0, 5.0, 2.5]

func ratingRecord (history:[Double]) -> (average:Double, min:Double, max:Double) {
	var sum = 0.0, min = history[0], max = history[0]
	for value in history {
		if min > value { min = value }
		if max < value { max = value }
		sum += value
	}
	let average = sum / Double(history.count)
	return (average, min, max)
}

var bookDescription:String = "\(title)"
if let theRatings = ratings {
	let record = ratingRecord(theRatings)
	bookDescription += "has \(theRatings.count) ratiings, \r\n average is \(record.average), from \(record.min) to \(record.max)"
}
bookDescription += "\r\nsupport web page : \(supportURL)"
print("\(bookDescription)")



typealias Time = (minute:Int, second:Int)

let lunch = (16, 37)
let walk = (18, 48)

// 함수의 인자와 리턴 타입을 명시해주세요
func addTime (time1:Time, time2:Time) -> (minute:Int, second:Int) {
    let secondSum = time1.second + time2.second
    let second = secondSum % 60
    let minute = time1.minute + time2.minute + (secondSum / 60)

    // minute과 second를 이용해서 적절한 값을 리턴해주세요
    return (minute, second)
}

//atNoon의 값은 (35, 25) 이어야 합니다.
let atNoon = addTime(lunch, time2:walk)
print(atNoon)

```
***
