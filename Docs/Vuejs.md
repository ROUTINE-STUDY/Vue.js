# Vue.js는 무엇일까?

Vue.js는 프런트엔드 개발자들이 사용하는 프레임워크 중 한 개입니다. 프런트엔드 대표적인 프레임워크 React, Vue, Angular가 있습니다. Vue.js는 AngularJS를 사용하여 구글에서 작업하던 Evan You에 의해 개발되었습니다. Evan You는 Angular를 이해하기 위해서 방대한 프레임워크 구조를 이해해야 하는 것에 큰 부담을 느끼고 '좋았던 부분을 뽑아낸 다음 추가적인 모든 개념을 동반하지 않고 무언가를 가볍게 만들어보면 어떨까?'라는 생각으로 새롭게 만들어낸 프레임워크가 Vue.js입니다. 그렇게 Vue.js는 2014년 2월에 처음으로 공식 배포되었습니다. 2017년에는 JQuery와 Angular 1.x를 앞지르고 최근에는 Vue.js는 리액트에 이어 2번째로 대중적인 JavaScript Framework가 되었습니다. 

## Vue.js 장점

1. HTML, CSS, JavaScript 기초만 알고 있다면 빠르게 학습할 수 있습니다.
2. React와 AngularJS에 비해 성능이 우수합니다.
3. React의 가상 돔(Virtual DOM), AngularJs의 데이터 바인딩 특성의 장점을 모아 만들었습니다.
4. 컴포넌트를 재사용하기 때문에 개발 시간 단축 및 양질의 코드 생산이 가능합니다.
5. Learning Curves가 낮습니다.

## Vue.js 특징

Vue.js는 MVVM(Model - View - ViewModel)의 패턴의 Framework입니다.
![image](https://user-images.githubusercontent.com/74242937/127656617-07fa88cf-e72c-4c00-b525-0804240f09df.png)  
화면 앞단의 코드와 화면 뒷단의 코드를 분리해서 작성하는 패턴을 의미합니다.

- Model: JavaScript Object(객체)
- View: 사용자가 보는 화면(UI), 웹페이지의 DOM
- ViewModel: View와 Model을 연결하여 데이터 바인딩을 해주는 역할
