# Getter

![image](https://user-images.githubusercontent.com/74242937/128547105-2815153e-b1b2-4272-a3f8-31ff541269e6.png)

위 예제는 reverseMsg는 computed에서 만들어놓은 Readonly전용 함수입니다. 개발자가 직접적으로 msg의 data를 변경하지 않는다면 캐싱된 data를 얻어올 수만 있는 상황입니다. 하지만 vue.js문법을 통해서 setter를 통해서 값을 지정해서 변경시킬 수 있습니다.

# Setter

![image](https://user-images.githubusercontent.com/74242937/128547135-97f643bd-411b-4a8b-8831-1cdc244931fe.png)

reversedMsg메서드의 set은 직접적으로 값을 할당할 때 사용됩니다.  
제가 콘솔에 쪽에 찍힌 거와 같이 메서드 실행 순서는 화면이 랜더 될 때 get()이 실행되고 캐싱되어서 화면에 나옵니다.  
그 이후 버튼을 클릭하면 add() -> set(value) -> get()가 실행되는 것을 알 수 있습니다.   
이를 통해서 computed에서도 setter(즉, 값을 지정)를 사용할 수 있다는 것을 알 수 있습니다.

이 개념은 일반적으로 잘 활용하지는 않습니다. 하지만 Vuex라는 중앙 집중화된 저장소를 다룰 때 유용하게 사용될 수 있기 때문에 다음에 다시 자세하게 다뤄보도록 하겠습니다.


