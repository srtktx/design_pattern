# design_pattern  
_1. MVC_  
 ->용어  
   Model + View + Controller  
   (모델은 어플리케이션에서 사용되는 데이터와 그 데이터를 처리하는 부분  
    뷰는 사용자에게 보여지는 UI 부분  
    컨트롤러는 사용자의 입력(액션)을 받고 처리하는 부분이다)  
 ->구조  
   액션을 받는 컨트롤러에서 뷰와 모델로 화살표가 향한다  
   이때 컨트롤러와 뷰는 1:n 관계이다  
   모델에서 뷰로 점선 화살표가 향한다  
 ->동작  
   a. controller는 유저의 액션을 받는다  
   b. controller는 유저의 액션을 확인하고 model을 업데이트한다  
   c. controller는 model을 나타내줄 view를 선택한다.  
   d. view는 model을 이용해서 화면을 나타낸다.  
 ->view가 업데이트되는 방법  
   a. view가 model을 이용해서 직접 업데이트  
   b. model에서 view에게 Notify해서 업데이트  
   c. view가 Polling으로 주기적으로 model의 변경을 감지해서 업데이트    
 ->특징  
   controller는 여러개의 view를 선택할 수 있는 1:n 구조이다  
   controller는 view를 선택할 뿐 직접 업데이트하지 않는다.  
   따라서 view는 controller를 알 수 없다.  
 ->장점  
   단순하다, 보편적으로 사용된다  
 ->단점  
   view와 model간의 의존성이 높다.  
   따라서 어플리케이션이 커질수록 복잡하고 유지보수가 어려워진다.    
   
_2. MVP_  
 ->용어  
   Model + View + Presenter  
   (presenter: 뷰에서 요청한 정보로 model을 가공해서 view로 전달해준다)  
 ->구조  
   presenter와 view, presenter와 model간에 각각 쌍방향 화살표가 있다.  
   이때 view에서 presenter로 향하는 화살표는 1:1관계이다  
   action을 받는 부분은 view이다  
 ->동작  
   a. 유저의 액션들은 view를 통해 들어온다  
   b. view는 데이터를 presenter에게 요청한다  
   c. presenter는 model에게 데이터를 요청한다.  
   d. model은 presenter에게 요청받은 데이터를 응답한다.  
   e. presenter는 view에게 데이터를 응답한다.  
   f. view는 presenter가 응답한 데이터를 이용해서 화면에 나타낸다.  
 ->특징  
   presenter는 view와 model의 인스턴스를 가지고 있어서 둘을 연결할 수 있다.
   presenter와 view는 1:1 관계이다.  
 ->장점  
   presenter를 통해서만 데이터를 전달받기 때문에 view와 model간의 의존성이 없다.  
   (MVC패턴의 단점 해결)  
 ->단점  
   view와 presenter사이의 의존성이 생긴다.    
   
_3. MVVM_  
 ->용어  
   Model + View + ViewModel  
   (ViewModel: view를 표현하기 위한 모델로, view를 표현하는데 필요한 데이터를 처리한다)  
 ->구조  
   액션을 받는 view에서 view model로 n:1 관계의 화살표가 향한다.  
   view model과 model은 쌍방향 화살표를 갖는다  
 ->동작  
   a. 유저의 액션은 view를 통해 들어온다.  
   b. command패턴으로 view model에 액션을 전달한다.  
   c. view model은 model에게 데이터를 요청한다.     
   d. model은 view model에게 요청받은 데이터를 응답한다.  
   e. view model은 응답받은 데이터를 가공해서 저장한다.  
   f. view는 view model과 data binding해서 화면을 표현한다.  
 ->특징  
   커맨드 패턴, 데이터 바인딩 패턴 이 두가지로 구현된다.  
   이 두 패턴을 이용해서 view와 view model 간의 의존성을 없앨 수 있다.  
   view model과 view는 1:n관계이다.  
 ->장점  
   각각의 부분은 독립적이기 때문에 모듈화해서 개발이 가능하다.  
 ->단점  
   view model의 설계가 쉽지 않다. 
   
  _3-1. command pattern_  
    ->정의  
      객체가 실행할 메소드를 클래스로 만들어 캡슐화하는 패턴이다.
    ->장점  
      일반적으로는 객체 A에서 객체 B의 메소드를 실행하려면 해당 객체를 참조해야하는
      의존성이 발생하지만, 커맨드 패턴을 이용해서 제거할 수 있다.   
      기능에 변경이 일어날때 클래스 코드를 수정할 필요없이 기능에 대한 클래스를
      정의함으로써 시스템의 확장성과 유연성을 보장한다.  
    ->구현 예제  
      https://victorydntmd.tistory.com/295  
      
  _3-2. data binding pattern_    
    ->정의  
      model과 UI 요소간의 싱크를 맞춰준다.  
      (각 기술에 따라 그 의미가 조금씩 다르다)  
    ->장점    
      생성한 xml과 view를 개발자가 직접 연결시켜줄 필요없이 자동으로 연결해준다  
    ->구현 예제  
      https://takhyeongmin.github.io/2019/01/21/WhatIsDataBinding/                     

     