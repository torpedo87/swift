# Nil(js의 null)
```swift
var title : String = "Storyboard"

// optional 선언시 ?
var ratings : [Int]? = nil
var supportURL : String? = nil

// optional 사용시 값 존재 확실시 !
var bookDescription:String = "\(title)"
if ratings != nil {
	bookDescription += "has \(ratings!.count) ratings"
}
if supportURL != nil {
	bookDescription += "\r\nsupport web page : \(supportURL)"
}
print("\(bookDescription)")
```
***
# ! 줄이기
##1. if let(optional binding)
```swift
// ! 를 줄이기(optional binding)
//if let num = number{}    =   if number != nil {let num = number!}
if let theRatings = ratings {
	bookDescription += "has \(theRatings) ratiings"
}
if let theURL = supportURL {
	bookDescription += "\r\nsupport web page : \(theURL)"
}


struct WatchDevice {
    var pairediPhone:String? //애플와치와 쌍을 이루는 아이폰의 이름.
    var appInstalled = false //어플리케이션의 설치 유무
    enum WatchSize {
        case m42, m38
    }
}
var appleWatch:WatchDevice? = nil
appleWatch = WatchDevice(pairediPhone: "링고스타의 아이폰", appInstalled: true)
// ①appleWatch에 대해 optional binding으로 watch라는 새로운 변수를 생성해주세요.
if let watch = appleWatch {
    // ②watch와 쌍을 이루는 아이폰의 이름에 대해
    // optional binding으로 phoneName이라는 새로운 변수를 생성해 주세요.
    if let phoneName = watch.pairediPhone {
        print ("AppleWatch가 \(phoneName)과 쌍을 이룹니다.")
    }
}

struct WatchDevice {
    var pairediPhone:String? //애플와치와 쌍을 이루는 아이폰의 이름.
    var appInstalled = false //어플리케이션의 설치 유무
    enum WatchSize {
        case m42, m38
    }
}
var appleWatch:WatchDevice? = nil
appleWatch = WatchDevice(pairediPhone: "링고스타의 아이폰", appInstalled: true)
// appleWatch에 appleWatch에 대해 optional binding으로 phoneName이라는 새로운 변수를 생성해 주세요
if let phoneName = appleWatch?.pairediPhone {
    print ("AppleWatch가 \(phoneName)과 쌍을 이룹니다.")
}
```
***

##2. 처음 선언시 ?대신 !
```swift
var ratings : [Int]? = nil
var supportURL : String! = nil
supportURL = "www.codershigh.com"

var bookDescription:String = "\(title)"
if let theRatings = ratings {
	bookDescription += "has \(theRatings.count) ratiings"
}

bookDescription += "\r\nsupport web page : \(supportURL)"


print("\(bookDescription)")
```
***
