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
func 함수이름(매개변수1이름: 매개변수1타입, 매개변수2이름: 매개변수2타입 ...) -> 반환타입 {
  함수 구현부
  return 반환값
 }
```
```
func sum(a: Int, b: Int) -> Int {
  return a + b
}
```

### 반환 값이 없는 함수
```
 func 함수이름(매개변수1이름: 매개변수1타입, 매개변수2이름: 매개변수2타입 ...) -> void {
   함수 구현부
  return
 }
```
```
func printMyName(name: String) -> Void {
print(name)
```


### 매개변수가 없는 함수
```
func 함수이름() -> 반환타입 {
  함수 구현부
 return 반환값
 }
```
```
func maximumIntegerValue() -> Int {
  return Int.max
 }
```

### 매개변수와 반환값이 없는 함수
```
func 함수이름() -> void {
  함수 구현부
 return
 }
```
```
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
func 함수이름(매개변수1이름: 매개변수1타입, 매개변수2이름: 매개변수2타입 = 매개변수 기본값 ...) -> 반환타입 {
  함수 구현부
 return 반환값
 }
```
```
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
func 함수이름(전달인자 레이블 매개변수1이름: 매개변수1타입, 전달인자 레이블 매개변수2이름: 매개변수2타입...) -> 반환타입 {
  함수구현부 
 return
 }
```
```
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
func 함수이름(매개변수1이름: 매개변수1타입, 전달인자 레이블 매개변수2이름: 매개변수2타입...) -> 반환타입 {
    /* 함수 구현부 */
  return
 }
```
```
func sayHelloToFriends(me: String, friends: String...) -> String {
    return "Hello \(friends)! I'm \(me)!"
}

print(sayHelloToFriends(me: "jiin", friends: "hana", "eric", "wing"))
// Hello ["hana", "eric", "wing"]! I'm jiin!

print(sayHelloToFriends(me: "jiin")) //가변인자에 아무것도 넣고싶지 않으면 전달인자 레이블을 생략해버리면 된다. 
// Hello []! I'm jiin!
```
### 데이터 타입으로서의 함수
> 스위프트는 함수형 프로그래밍 패러다임을 포함하는 다중 패러다임 언어이므로 스위프트의 함수는 일급 객체입니다.   
> 그래서 함수를 변수, 상수 등에 할당이 가능하고 매개변수를 통해 전달할 수도 있습니다.   
> 함수의 타입 표현 : 반환 타입을 생략할 수 없습니다.
```
(매개변수1타입, 매개변수2타입...) -> 반환타입

함수타입 사용
var someFunction:(String, String) -> Void = greeting(to:from:)
someFunction("eric","jiin") //Hello eric! I'm jiin

someFunction = greeting(friend:me:)
someFunction("eric", "jiin") // Hello eric! I'm jiin


// 타입이 다른 함수는 할당할 수 없습니다 - 컴파일 오류 발생
//someFunction = sayHelloToFriends(me: friends:)


func runAnother(function: (String, String) -> Void) { //함수 타입을 매개변수 타입으로 지정해주면 function 을 안에서도 실행해줄 수 있다. 
    function("jenny", "mike")
}

// Hello jenny! I'm mike
runAnother(function: greeting(friend:me:))

// Hello jenny! I'm mike
runAnother(function: someFunction)
```

## 조건문

### if-else 구문
```
if 조건 {           //소괄호 생략 가능, 중괄호 생략 불가능
     /* 실행 구문 */
} else if 조건 {
    /* 실행 구문 */
} else {
    /* 실행 구문 */
}
```
```
let someInteger = 100

if someInteger < 100 {
    print("100 미만")
} else if someInteger > 100 {
    print("100 초과")
} else {
    print("100")
} // 100

// 스위프트의 조건에는 항상 Bool 타입이 들어와야 합니다.
// someInteger는 Bool 타입이 아닌 Int 타입이기 때문에
// 컴파일 오류가 발생합니다.
//if someInteger { }
```

### switch 구문
> 매우 한정적인 값(ex. enum의 case 등)이 비교값이 아닌 한 default 구문은 반드시 작성해야 합니다.   
> 명시적으로 break를 하지 않아도 자동으로 case 마다 break 됩니다.   
> fallthrough 키워드를 사용하여 break를 무시할 수 있습니다.    
> 쉼표(,)를 사용하여 하나의 case 에 여러 패턴을 명시할 수 있습니다.
```
switch 비교값 {
case 패턴:
    /* 실행 구문 */
default:
    /* 실행 구문 */
}
``` 
```
// 범위 연산자를 활용하면 더욱 쉽고 유용합니다
switch someInteger {
case 0:
    print("zero")
case 1..<100:
    print("1~99")
case 100:
    print("100")
case 101...Int.max: //이상, 이하 ...-> 포함한다는거 
    print("over 100")
default:
    print("unknown")
} // 100

// 정수 외의 대부분의 기본 타입을 사용할 수 있습니다
switch "jiin" {
case "jake", "mina":
    print("jake, mina")
case "jiin":
    print("jiin!!")
default:
    print("unknown")
} // jiin!!
```
<br>

## 반복문

### for-in 구문
> 기존 언어의 for-each구문과 유사합니다.   
> Dictionary의 경우 이터레이션 아이템으로 튜플이 들어옵니다.
```
for item in items{
 /* 실행 구문*/
```
```
var integers = [1, 2, 3]
let people = ["yagom": 10, "eric": 15, "mike": 12]

for integer in integers {
    print(integer)
}

// Dictionary의 item은 key와 value로 구성된 튜플 타입입니다
for (name, age) in people {
    print("\(name): \
    (age)")
}
```
### While 구문
```
while 조건 {
    /* 실행 구문 */
}
```
```
while integers.count > 1 { //소괄호 생략 가능, 꼭 bool 값이 들어와야함 (while 1 안됨)   
    integers.removeLast()
}
```
### repeat-while 구문
> 기존 언어의 do-while 구문과 형태/동작이 유사합니다.
```
repeat {
    /* 실행 구문 */
} while 조건
```
```
repeat { //do 라는 키워드를 쓰지 않는 이유는 do는 swift 의 오류 처리 구문에 사용되기 때문이다. 
    integers.removeLast()
} while integers.count > 0
```

<br>

## 옵셔널

### 옵셔널이란??
> 값이 있을 수도, 없을 수도 있음을 표현  
> nil이 할당 될 수 있는지 없는지 표현 
```
// someOptionalParm에 nil이 할당 될 수 있다.
func someFunction(someOptionalParam: Int?) {
       // ....
}

/// someOptionalParm에 nil이 할당 될 수 없다.
func someFunction(someOptionalParam: Int) {
       // ....
}

someFunction(someOptionalParam: nil)
// someFunction(someParam: nil) 
```

### 옵셔널을 쓰는 이유
> 명시적 표현
>> 1. nil의 가능성을 코드만으로 표현 가능
>> 2. 문서/주석 작성 시간 절약 

> 안전한 사용
>> 1. 전달받은 값이 옵셔널이 아니라면 nil 체크를 하지 않고 사용 가능
>> 2. 예외 상황을 최소화 하는 안전한 코딩
>> 3. 효율적 코딩 

### 옵셔널 문법과 선언
> 옵셔널 문법 = enum + generics
```
옵셔널 선언

enum Optional<Wrapped>: ExpressibleByNiliteral {
         case none
         case some(Wrapped)
}

let optionalValue: Optional<Int> = nil
let optionalValue: Int? =nil
```

### 옵셔널 표현  
#### 1. 느낌표(!)를 이용한 암시적 추출 옵셔널
```
// Implicitly Unwrapped Optional
var implicitlyUnwrappedOptionalValue: Int! = 100

switch implicitlyUnwrappedOptionalValue {
case .none:
    print("This Optional variable is nil")
case .some(let value):
    print("Value is \(value)")
}

// 기존 변수처럼 사용 가능
implicitlyUnwrappedOptionalValue = implicitlyUnwrappedOptionalValue + 1

// nil 할당 가능
implicitlyUnwrappedOptionalValue = nil

// 잘못된 접근으로 인한 런타임 오류 발생(nil값을 넣어줬는데 접근하려다 보니)
// 옵셔널과 일반 값은 다른 타입이므로 연산불가 
//implicitlyUnwrappedOptionalValue = implicitlyUnwrappedOptionalValue + 1
```

#### 2. 물음표(?)를 이용한 옵셔널
```
// Optional
var optionalValue: Int? = 100

switch optionalValue {
case .none:
    print("This Optional variable is nil")
case .some(let value):
    print("Value is \(value)")
}

// nil 할당 가능
optionalValue = nil

// 기존 변수처럼 사용불가 - 옵셔널과 일반 값은 다른 타입이므로 연산불가
//optionalValue = optionalValue + 1
```
### 옵셔널 추출 

#### 1. 옵셔널 추출이란? (Optional Unwrapping) 
> 옵셔널에 들어있는 값을 사용하기 위해 꺼내오는 것

#### 2. 옵셔널 방식
> 옵셔널 바인딩 (Optional Binding)
>> 1. nil 체크 + 안전한 추출
>> 2. 옵셔널 안에 값이 들어있는지 확인하고 값이 있으면 값을 꺼내옴
>> 3. if-let 방식 사용
```
func printName(_ name: String) {
    print(name)
}

var myName: String? = nil

//printName(myName)
// 전달되는 값의 타입이 다르기 때문에 컴파일 오류발생

if let name: String = myName {
    printName(name)
} else {
    print("myName == nil")
}


var yourName: String! = nil

if let name: String = yourName {
    printName(name)
} else {
    print("yourName == nil")
}

// name 상수는 if-let 구문 내에서만 사용가능합니다
// 상수 사용범위를 벗어났기 때문에 컴파일 오류 발생
//printName(name)

// ,를 사용해 한 번에 여러 옵셔널을 바인딩 할 수 있습니다
// 모든 옵셔널에 값이 있을 때만 동작합니다
myName = "jiin"
yourName = nil

if let name = myName, let friend = yourName {
    print("\(name) and \(friend)")
}
// yourName이 nil이기 때문에 실행되지 않습니다

yourName = "hana"
if let name = myName, let friend = yourName { //myName, yourName 모두 값이 들어있어야 if-let 구문이 실행 가능하다.
    print("\(name) and \(friend)")
}
// jiin and hana
```
> 강제 추출 (Force Unwrapping)  
>> 옵셔널에 값이 들어있는지 아닌지 확인하지 않고 강제로 값을 꺼내는 방식, 만약 값이 없을경우(nil)런타임 오류가 발생하기 떄문에 추천되지 않습니다.
```
var myName: String? = "jiin"
var youName: String! = nil
  

printName(myName!) // jiin
myName = nil

//print(myName!)
// 강제추출시 값이 없으므로 런타임 오류 발생
yourName = nil

//printName(yourName)
// nil 값이 전달되기 때문에 런타임 오류발생 
```
<br>


## 구조체

### 1. 구조체란? 
> 스위프트 대부분 타입은 구조체로 이루어져 있다.
> 구조체는 값(Value)타입이다.
> 타입 이름은 대문자 카멜 케이스를 사용하여 정의한다.

### 2. 구조체 문법
> 구조체 정의 : "struct" 키워드 사용
```
struct 이름 {
  /* 구현부 */
}
```
> 구조채 프로퍼티 및 메서드 구현
```
strut Sample{

  //인스턴스 프로퍼티
  var mutableProperty: Int = 100 //가변 프로퍼티(값 변경 가능)
  let immutabelProperty: Int = 100 //불변 프로퍼티(값 변경 불가능)
  
  static var typeProperty: Int = 100 //타입 프로퍼티(static 키워드 사용: 타입 자체가 사용하는 프로퍼티)

  //인스턴스 메서드(인스턴스가 사용하는 메서드)
  func instanceMethod(){
     print("instacne method")
  }
 
  //타입 메서드(static 키워드 사용: 타입 자체가 사용하는 메서드)
  static func typeMethod(){
   print("type method")
    }
 }

```
> 구조체 사용
```
// 가변 인스턴스 생성
var mutable: Sample = Sample()

mutable.mutableProperty = 200

// 불변 프로퍼티는 인스턴스 생성 후 수정할 수 없습니다
// 컴파일 오류 발생
//mutable.immutableProperty = 200

// 불변 인스턴스
let immutable: Sample = Sample()

// 컴파일 오류 발생: 불변 인스턴스는 아무리 가변 프로퍼티라도 인스턴스 생성 후에 수정할 수 없습니다
//immutable.mutableProperty = 200
//immutable.immutableProperty = 200


// 타입 프로퍼티 및 메서드 (구조체 타입 자체가 사용할 수 있는 프로퍼티 및 메서드 
Sample.typeProperty = 300
Sample.typeMethod() // type method

// 컴파일 오류 발생: 인스턴스에서는 타입 프로퍼티나 타입 메서드를 사용할 수 없습니다
//mutable.typeProperty = 400
//mutable.typeMethod()
```
#### 학생 구조체 만들어보기
```
struct Student{

  var name: String = "unknown"
  var `class`: String = "Swift" //키워드도 `로 묶어주면 이름으로 사용할 수 있다.
  
  static func selfIntroduce(){
    print("학생타입입니다")
  }
  
  func selfIntroduce(){
    print("저는 \(self.class)반 \(name)입니다.")
  }
}

//타입 메서드 사용
Student.selfIntroduce()// 학생타입입니다.

//가변 인스턴스 생성
var jiin: Student = Student()
jiin.name = "jiin"
jiin.class = "스위프트"
jiin.selfIntroduce() //저는 스위프트반 jiin입니다

//불변 인스턴스 생성
let jay: Student = Student() 

//불변 인스턴스이므로 프로퍼티값 변경 불가
//컴파일 오류 발생
//jay.name = "jay"

jay.selfIntroduce() //저는 Swift반 unknown입니다

```
<br>


## 클래스
### 클래스란?
> 클래스는 참조(reference)타입입니다. 
> 타입 이름은 대문자 카멜케이스를 사용하여 정의합니다.
> Swift의 클래스는 다중 상속이 되지 않습니다.

### 클래스 문법
> 정의 "class"키워드 사용
```
class 이름 {
  /* 구현부 */
}
```
> 프로퍼티 및 메서드 구현
```
class Sample{
  var mutableProperty: Int = 100  //가변 프로퍼티
  
  let immutableProperty: Int = 100  //불변 프로퍼티
  
  static var typeProperty: Int = 100 //타입 프로퍼티
  
  func instanceMethod(){ //인스턴스 메서드 
    print("instance method")
  }
  
  //타입 메서드
  //상속시 재정의 불가 타입 메서드 - static
  static func typeMethod(){
    print("type method - static")
   }
   
   class func classMethod(){
    print("type method - class")
   }
}
```
> 클래스 사용
```
var mutableReference: Sample = Sample()

mutableReference.mutablePropery = 200

//컴파일 오류 발생: 불변 프로퍼티는 인스턴스 생성 후 수정할 수 없습니다.
//mutableReference.immutableProperty = 200

//인스턴스 생성 - 참조정보 수정 불가 
let immutableReference: Sample = Sample()

//클래스의 인스턴스는 참조 타입이므로 let으로 선언되었더라도 인스턴스 프로퍼티의 값 변경이 가능합니다.
immutableReference.mutableProperty = 200

//컴파일 오류 발생: 다만 참조정보를 변경할 수 는 없습니다.
//immutableReferene = mutableReference

//컴파일 오류 발생: 참조 타입이라도 불변 인스턴스는 인스턴스 생성 후에 수정할 수 없습니다. 
//immutableReference.immutableProperty = 200

//타입 프로퍼티 및 메서드
Sample.typeProperty = 300
Sample.typeMeyhod() //type method

//컴파일 오류 발생: 인스턴스에서 타입 프로퍼티나 타입 메서드를 사용할 수 없습니다.
//mutableReference.typeProperty = 400
//mutableReference.typeMethod()
```

> 학생 클래스 만들어 보기
```
class Student{
  var name: String = "unknown"
  var `class`: String = "Swift"
  
  //타입 메서드
  class func selfIntroduce(){
  print(학생타입입니다.
  
```






