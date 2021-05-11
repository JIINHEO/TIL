# Swift


###  Any 
> Swift의 모든 타이블 지칭하는 키워드  
```
var someAny: Any = 100
someAny = "어떤 타입도 수용 가능합니다."
someAny = 123.12
```

### AnyObject 
> 모든 클래스 타입을 지칭하는 프로토콜   
```
class SomeClasee {}
var someAnyObject: AnyObject = SomeClass()
```

### nil 
> 없음을 의미하는 키워드
```
someAny = nil // error: 어떤 데이터 값이나 들어올 수 있지만, 빈 값은 들어갈 수 없다.
```


<br>

## 컬렉션 타입

### Array
> 순서가 있는 리스트 컬렉션 
```
var integers: Array<Int> = Array<Int>()
integers.append(1) //[]
integers.append(100) //[1]

integer.contains(100) //true
integer.contains(99) // false

integer.remove(at: 0) //1 (0번째 값을 없앰)
integer.removeLast() //100
integer.removeAll() //[]

integer.count //0

var strings: [String] = [String]() //빈 String Array 생성
var character: [Character] = [] //빈 Chracter Array 생성

let immutableArray = [1, 2, 3] //불변 Array 생성
```

### Dictionary
> 키와 값의 쌍으로 이루어직 컬렉션
```
var anyDictionary: Dictionary<String, Any> = [String: Any]()
// key가 String타입이고 Value가 Any인 빈 Dictionary 생성

anyDictionary["somekey"] = "value" // "value"
anyDictionary["anotherKey"] = 100 //100
anyDictionary //["somekey": "value", "anotherKey": 100]
anyDictionary["somekey"] = "dictionary" // "dictionary"
anyDictionary //["somekey": "dictionary", "anotherKey": 100]

anyDictionary.removeValue(forkey: "anotherKey") //100
anyDictionary["someKey:] = nil //nil
//위의 2개는 같은 표현
anyDictionary // [:]

let emptyDictionary: [String: String] = [:] //빈 딕셔너리다
let initalizedDictionary: [String: String] = ["name": "jiin", "gender": "female"]

let someValue: String = initalizedDictionary["name"]
//Error - initalizedDictionary의 name에 값이 있을수도 있고, 없을수도 있는 불확실성 때문
```

### Set
> 순서가 없고, 멤버가 유일한 컬렉션
```
var integerSet: Set<Int> = Set<Int>() //빈 Int Set 생성 
integerSet.insert(1)  //(inserted true, memberAfterInsert1)
integerSet.insert(100)  //(inserted true, memberAfterInsert100)
integerSet.insert(99) //(inserted true, memberAfterInsert99)
integerSet.insert(99) //(inserted false, memberAfterInsert99) 중복된값 허용 x
integerSet {100, 99, 1}

integerSet.contains(1) //true
integerSet.contains(2) //false

integerSet.remove(100)
integerSet.removeFirst() //99

integerSet.count //1

let setA: Set<Int> = [1, 2, 3, 4, 5]
let setB: Set<Int> = [3, 4, 5, 6, 7]

let union: Set<Int> = setA.union(setB) //{2,4,5,6,7,3,1} 합집합
let sortedUnion: [Int] = union.sorted() //{1,2,3,4,5,6,7} 정렬
let intersection: Set<Int> = setA.intersection(setB)//{5,3,4} 교집합
let subtracting: Set<Int> = setA.subtracting(setB)//{2,1} 차집합
```

<br>

## 함수
### 함수의 선언
```
// func 함수이름(매개변수1이름: 매개변수1타입, 매개변수2이름: 매개변수2타입 ...) -> 반환타입 {
//  함수 구현부
//  return 반환값
// }


func sum(a: Int, b: Int) -> Int {
  return a + b
}
```

### 반환 값이 없는 함수
```
// func 함수이름(매개변수1이름: 매개변수1타입, 매개변수2이름: 매개변수2타입 ...) -> void {
// 함수 구현부
// return
// }

func printMyName(name: String) -> Void {
print(name)
```


### 매개변수가 없는 함수
```
// func 함수이름() -> 반환타입 {
// 함수 구현부
// return 반환값
// }
 
func maximumIntegerValue() -> Int {
  return Int.max
 }
```

### 매개변수와 반환값이 없는 함수
```
// func 함수이름() -> void {
// 함수 구현부
// return
// }

func hello() -> void { print("hello") }
```

### 함수의 호출
```
sum(a: 3, b: 5) //8
printMyName(name: "jiin") //jiin
printYourName(name: "jiin") //jiin
maximumIntegerValue() //Int의 최댓값
hello() //hello
```

### 매개변수 기본 값
> 매개변수에 기본적으로 전달될 값을 미리 지정해 둘 수 있습니다.  
> 기본값을 갖는 매개변수는 애배견수 목록 중 뒤쪽에 위치하는 것이 좋습니다.   
```
// func 함수이름(매개변수1이름: 매개변수1타입, 매개변수2이름: 매개변수2타입 = 매개변수 기본값 ...) -> 반환타입 {
// 함수 구현부
// return 반환값
// }

func greeting(friend: String, me: String = "jiin") {
  print("Hellog \(friend)! I'm \(me)")
}

greeting(friend: "hana") //Hello hana! I'm jiin
greeting(frieng: "john", me: "eric") //Hello john! I'm eric
```

### 전달인자 레이블(Argument Label)
> 함수를 호출할 때 함수 사용자의 입장에서 매개변수의 역할을 좀 더 명확하게 표현하고자 할 때 사용합니다.  
> 전달인자 레이블은 변경하여 동일한 이름의 함수를 중복으로 생성 가능합니다.
```
// func 함수이름(전달인자 레이블 매개변수1이름: 매개변수1타입, 전달인자 레이블 매개변수2이름: 매개변수2타입...) -> 반환타입 {
// 함수구현부 
// return
// }

//함수 내부에서 전달인자를 사용할 때에는 매개변수 이름을 사용합니다.
func greeting(to friend: String, from me: String) {
  print("Hello \(friend)! I'm \(me)")
 }
 
 //함수를 호출할 때에는 전달인자 레이블을 사용해야 합니다.
 greeting(to: "hana", from: "jiin") //Hello hana! I'm jiin
```

### 가변 매개변수
> 전달 받을 값의 개수를 알기 어려울 때 사용합니다.  
> 가변 매개변수는 함수당 하나만 가질 수 있습니다.  
> 기본값이 있는 매개변수와 같이 가변 매개변수 역시 매개변수 목록 중 뒤쪽에 위치하는 것이 좋습니다.
```
/ func 함수이름(매개변수1이름: 매개변수1타입, 전달인자 레이블 매개변수2이름: 매개변수2타입...) -> 반환타입 {
//    /* 함수 구현부 */
//    return
// }

func sayHelloToFriends(me: String, friends: String...) -> String {
    return "Hello \(friends)! I'm \(me)!"
}

print(sayHelloToFriends(me: "jiin", friends: "hana", "eric", "wing"))
// Hello ["hana", "eric", "wing"]! I'm jiin!

print(sayHelloToFriends(me: "jiin"))
// Hello []! I'm jiin!
```
### 데이터 

