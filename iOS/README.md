# iOS

```Cocoa Touch Framework```    
iOS 개발환경을 구축하기위한 최상위 프레임워크
swift, Object-C 에서 상속하여 사용하는 UIKIt, Foundation을 포함한 대부분의 클래스 객체들이 cocoatouch framework에 속한다.

```Foundation```   
가장 기본적인 데이터 타입부터 자료구조 각종 구조체 네트워크 통신 파일 관리 등 기본적인 프로그램의 중심을 담당하는 프레임워크

```UIKit```   
사용자의 인터페이스를 관리하고 이벤트를 처리하는게 주 목적인 프레임워크   
UIKit 앱의 구조는 기본적으로 MVC패턴을 사용한다. 

```UIView```   
화면의 직사각형 영역에 대한 내용을 관리하는 개체   
화면을 구성하는 요소의 기본 클래스   

```ViewController```   
앱의 근간을 이루는 객체로 모든 앱은 최소한 하나 이상의 뷰 컨트롤러를 가지고 있다.   
- 데이터 변화에 따라서 view 컨텐츠를 업데이트   
- view들과 함께 사용자 상호작용에 응답   
- view를 리사이징하고 전체적인 인터페이스의 레이아웃 관리   
- 다른 뷰 컨트롤러들과 함께 앱을 구성   

```AutoLayout```   
두 뷰 사이의 관계를 제약조건(Constraints)을 이용해서 뷰의 위치를 지정하는 것 

```IBOutlet```  
스토리보드에 등록한 UI오브젝트를 코드에 변수로 접근할 수 있게 만들어줌 

```IBAction```   
(버튼)과 연결시켜 이벤트를 처리하는 함수를 만들어줌

```Content Hugging```   
더 늘어나게 되는것에 대해 저항하는 제약, 우선순위가 높을수록 크기를 유지, 낮으면 크기가 늘어난다.

```Compression Resistance```   
더 줄어들게 되는것에 대해 저항하는 제약, 우선순위가 높을수록 크기를 유지, 낮으면 크기가 줄어든다.

```Content View Controller```   
화면을 구성하는 뷰를 직접 구현하고 관련된 이벤트를 처리하는 뷰 컨트롤러

```Container View Controller```
- 하나 이상의 Child View Controller를 가지고있다.
- 하나 이상의 Child View Controller를 관리하고 레이아웃과 화면 전환을 담당한다.
- 화면 구성과 이벤트 관리는 Child View Controller에서 한다.
- Container View Controller는 대표적으로 Navigation Controller와 TabBar Controller가 있다. 

```NavigationController```   
계층구조로 구성된 content를 순차적으로 보여주는 container view controller 

```화면 전환 방법```   
1. 소스코드를 통해 전환하는 방식
2. Storyboard를 통해 전환하는 방식

- View Controller의 View위에 다른 View를 가져와 바꿔치기(메모리 누수 위험, 사용 x)
- View Controller에서 다른 View Controller를 호출하여 전환하기 (presentation 방식이라고도 함)   
```
func present(_ viewControllerToPresent: UIViewController, 
    animated flag: Bool, 
  completion: (() -> Void)? = nil)
  
func dismiss(animated flag: Bool, 
  completion: (() -> Void)? = nil)
  ```
- Navigation Controller를 사용하여 화면 전환하기
```
func pushViewController(_ viewController: UIViewController, animated: Bool)

func popViewController(animated: Bool) -> UIViewController?
```
- 화면 전환용 객체 세그웨이(Segueway)를 사용하여 화면 전환하기    
Manul Segueway : 출발점이 뷰컨트롤러 자체일 경우   
Action Segueway : 출발점이 버튼, 셀 등인 경우    
        - Show   
        - Show Detail   
        - Present Modally   
        - Present As Popover(아이패드에서 사용)   
        - Custom   

```UITableView```   
데이터를 목록 형태로 보여줄 수 있는 가장 기본적인 UI컴포넌트, 스크롤뷰를 상속받고 있음 
- 여러 개의 Cell을 가지고 있고 하나의 열과 여러 줄의 행을 지니고 있으며, 수직으로만 스크롤이 가능하다.
- 섹션을 이용해 행을 그룹화하여 콘텐츠를 좀 더 쉽게 탐색할 수 있다.
- 섹션의 헤더와 푸터에 View를 구성하여 추가적인 정보를 표시할 수 있다.   

     ```UITableViewDataSource```는 테이블 뷰를 생성하고 수정하는데 필요한 정보를 테이블 뷰 객체에 제공    
     ```UITableViewDelegate```는 테이블 뷰의 시각적인 부분을 설정하고, 행의 액션 관리, 엑세서리뷰 지원 그리고 테이블 뷰의 개별 행 편집을 도와줌   

```UITabBar```   
앱에서 서로 다른 하위작업, 뷰, 모드 사이의 선택을 할 수 있도록, 탭바에 하나 혹은 하나 이상의 버튼을 보여주는 컨트롤   

```UITabBarController```  
다중 선택 인터페이스를 관리하는 컨테이너 뷰 컨트롤러로, 선택에 따라 어떤 자식 뷰 컨트롤러를 보여줄 것인지 결정   

```UICollectionView```   
데이터 항목의 정렬된 컬렉션을 관리하고 커스텀한 레이아웃을 사용해 표시하는 객체   

```UICollectionViewFlowLayout```   
    - Flow 레이아웃 객체를 작성하고 컬렉션 뷰에 이를 할당한다.   
    - 셀의 width, height를 정한다.   
    - 필요한 경우 셀들 간의 좌우 최소 간격, 위아래 최소 간격을 설정한다.   
    - 섹션에 header와 footer가 있다면 이것들의 크기를 지정한다.   
    - 레이아웃의 스크롤 방향을 설정한다.   

















