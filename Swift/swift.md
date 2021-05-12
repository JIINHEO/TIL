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
<br>


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

#### 학생 클래스 만들어 보기
```
class Student{
    var name:String = "unknown"
    
    var `class`:String = "Swift"
    
    class func selfIntroduce(){
        print("학생타입입니다")
    }
    
    func selfIntroduce(){
        print("wjsms \(self.class)반 \(name) 입니다.")
        
    }
}

Student.selfIntroduce()

var jiin: Student = Student()
jiin.name = "jiin"
jiin.class = "안갈켜줌"
jiin.selfIntroduce()

let jina: Student = Student()
jina.name = "jina" //가변 프로퍼티를 let으로 선언했음에도 불구하고 변경이 가능하다. 

jina.selfIntroduce()
```
<br>

## 열거형
### 열거형이란?
> Swift 열거형은 다른 언어의 열거형과 많이 다릅니다.
> 유사한 종류의 여러 값을 한 곳에 모아서 정의한 것입니다. 예) 요일, 월, 계절 등
> enum 자체가 하나의 데이터 타입으로, 대문자 카멜케이스를 사용하여 이름을 정의합니다.
> 각 case는 소문자 카멜 케이스로 정의합니다. 
> 각 case는 그 자체가 고유한 값입니다. (각 case에 자동으로 정수값이 할당되지 않음)
> 각 case는 한 줄에 개별로도, 한 줄에 여러개도 정의할 수 있습니다.
```
enum 이름 {
	case 이름1
	case 이름2
	case 이름3, 이름4, 이름5
	// ...
}
```
```
// 예제
enum BoostCamp {
        case iosCamp
        case androidCamp
        case webCamp
}
```
### 열거형 사용
> 타입이 명확할 경우, 열거형의 이름을 생략 할 수 있습니다.
> switch 구문에서 사용하면 좋습니다. 
```
enum Weekday {
    case mon
    case tue
    case wed
    case thu, fri, sat, sun
}


//열거형 타입과 케이스를 모두 사용하여도 됩니다.
var day: Weekday = Weekday.mon

//타입이 명확하다면 케이스처럼 표현해도 무방합니다.
day = .tue

print(day) //tue


//switch의 비교값테 열거형 타입이 위치할 때 모든 열거형 케이스를 포함한다면 default를 작성할 필요가 없습니다.

switch day {
case .mon, .tue, .wed, .thu:
    print("평일입니다.")
case Weekday.fri:
    print("불금 파티!!")
case .sat, .sun:
    print("신나는 주말!!")
}
```
### rawValue(원시값)
> c언어의 enum처럼 정수값을 가질 수 있습니다.
> rawValue는 case별로 각각 다른 값을 가져야합니다.
> 자동으로 1이 증가된 값이 할당됩니다.
> rawvalue를 반드시 지닐 필요가 없다면 굳이 만들지 않아도 됩니다. 
```
enum Fruit: Int {
    case apple = 0
    case grape = 1
    case peach
    
    //case mango = 0
    //mango와 apple의 원시값이 같으므로 mango 케이스의 원시값을 0으로 정의할 수 없습니다.
}

print("Fruit.peach.rawValue == \(Fruit.peach.rawValue)")
//Fruit.peach.rawValue == 2
```
```
//정수 타입 뿐만 아니라, Hashable 프로토콜을 따르는 모든 타입을 원시값의 타입으로 지정 할 수 있습니다.
enum School: String {
    case elementary = "초등"
    case middle = "중등"
    case high = "고등"
    case university
}
print("School.middle.rawValue == \(School.middle.rawValue)")
//School.middle.rawValue == 중등

print("School.university.rawValue == \(School.university.rawValue)")
//School.university.rawValue == university
//열거형의 원시값 타입이 string일 때, 원시값이 지정되지 않았다면 case의 이름을 원시값으로 사용합니다.
```
### 원시값을 통한 초기화
> rawValue를 통해 초기화 할 수 있습니다.
> rawValue가 case에 해당하지 않을 수 있으므로, rawValue를 통해 초기화 한 인스턴스는 옵셔널 타입입니다.
```
//rawValue를 통해 초기화 한 열거형 값은 옵셔널 타입이므로 Fuit 타입이 아닙니다.
//let apple: Fruit = Fruit(rawValue: 0)
let apple: Fruit? = Fruit(rawValue: 0)

//if let 구문을 사용하면 rawValue에 해당하는 케이스를 곧바로 사용할 수 있습니다.
if let orange: Fruit = Fruit(rawValue: 5){
    print("rawValue 5에 해당하는 케이스는 \(orange)입니다.")
} else {
    print("rawValue 5에 해당하는 케이스가 없습니다.")
}//rawValue 5에 해당하는 케이스가 없습니다
```
### 메서드
> Swift의 열거형에는 메서드도 추가할 수 있습니다.
```
enum Month {
    case dec, jan, feb
    case mar, apr, may
    case jun, jul, aug
    case sep, oct, nov
    
    func printMessage() {
        switch self {
        case .mar, .apr, .may:
            print("따스한 봄~")
        case .jun, .jul, .aug:
            print("여름 더워요~")
        case .sep, .oct, .nov:
            print("가을은 독서의 계절!")
        case .dec, .jan, .feb:
            print("추운 겨울입니다")
        }
    }
}

Month.mar.printMessage()
```
<br>


## 클래스 vs 구조체/열거형
> 클래스는 참조 타입, 열거형과 구조체는 값 타입 이라는 것이 가장 큰 차이입니다.   
> 클래스는 상속이 가능하지만, 열거형과 구조체는 상속이 불가능 합니다.   

### 1. 값 타입과 참조 타입 비교
> 값 타입(Value Type): 데이터를 전달 할 때 깞을 복사하여 전달합니다.   
> 참조 타입(Referene Type): 데이터를 전달 할 때 값의 메모리 위치를 전달합니다.   

### 2. 값 타입을 사용하는 경우
> 연관된 몇몇의 값들을 모아서 하나의 데이터 타입으로 표현하고 싶은 경우. 
> 다름 객체 또는 함수 등으로 전달될 때 참조가 아니라 복사(값 복사)할 경우. 
> 자신을 상속할 필요가 없거나, 다른 타입을 상속 받을 필요가 없는 경우   

### 3. 스위프트에서의 사용
> 스위프트의 기본 데이터 타입은 모두 구조체로 구현되어있습니다.   
> 스위프트는 구조체와 열거형 사용을 선호합니다.  
> Apple 프레임워크는 대부분 클래스를 사용합니다.  
> 구조체/클래스 선택과 사용은 개발자의 몫입니다.  

<br>

## 클로저

### 1. 클로저란
> 클로저는 실행가능한 코드 블럭입니다.  
> 함수와 다르게 이름정의는 필요하지 않지만, 매개변수 전달과 반환 값이 존재 할 수 있다는 점이 동일합니다.  
> 함수는 이름이 있는 클로저입니다.  
> 일급객체로 전달인자, 변수, 상수 등에 저장 및 전달이 가능합니다.   
> 

### 2. 기본 클로저 문법
> 클로저는 중괄호 {}로 감싸져있습니다.  
> 괄호를 이용해 파라미터를 정의합니다.  
> ->을 이용해 반환 타입을 명시합니다.  
> "in" 키워드를 이용해 실행 코드와 분리합니다.  

```
{ (매개변수 목록) -> 반환타입 in
    실행 코드
}
```

### 3. 클로저 사용
```
//sum이라는 상수에 클로저를 할당
let sum: (Int, Int) -> Int = {(a: Int, b: Int) in
    return a + b
}

let sumResult: Int = sum(1,2)
print(sumResult) //3
```

### 4. 함수의 전달인자로서의 클로저
> 클로저는 주로 함수의 전달인자로 많이 사용됩니다.
> 함수 내부에서 원하는 코드블럭을 실행 할 수 있습니다. 

```
let add:(Int, Int) -> Int
add = {(a:Int, b:Int ) in return a + b}

let substract:(Int, Int) -> Int
substract = {(a: Int, b: Int) in return a - b}

let divide: (Int, Int) -> Int
divide = {(a:Int, b:Int ) in return a / b}

func calculate(a: Int, b: Int, method: (Int, Int) -> Int) -> Int {
    return method(a, b)
}

var calculated: Int

calculated = calculate(a: 50, b: 10, method: add)

print(calculated) //60

calculated = calculate(a: 50, b: 10, method: substract)

print(calculated) //40

calculated = calculate(a: 50, b: 10, method: divide)

print(calculated) //5

//따로 클로저를 상수/변수에 넣어 전달하지 않고, 함수를 호출할 때 클로저를 작성하여 전달할 수도 있습니다.
calculated = calculate(a: 50, b: 10, method: { (left: Int, right: Int) -> Int in
      return left * right })


print(calculated)

```
