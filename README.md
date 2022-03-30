# 13-Winted
## 프로젝트 소개
>**원티드(Wanted)**는 원티드랩이라는 스타트업에서 운영중인 채용 플랫폼입니다. 2015년부터 서비스하기 시작했습니다. 
특징은 추천이라는 기능이 있어 지원할 때 지인의 추천/추천사를 함께 붙일 수 있고, 합격한 경우 합격자와 추천인에게 50만원 이상의 보상금을 지급해주는 시스템이 있습니다. 
이름있는 기업은 물론 생소한 스타트업이나 소규모 IT기업들도 공고를 많이 올리는 편으로 2019년 기준 4000여개의 기업이 이용하고 있다고 합니다.
이용 기업들과 비슷하게 IT직군 인재풀이 좋은 편이고 개발자는 물론 디자이너, 마케터 그 외 비즈니스 직군과 게임관련 직군들도 폭넓게 있습니다. 
</br>

## 프로젝트 참가자(Front + Back)

### FrontEnd
+ 김수연 / 민지연 / 김한나 / 이예린

### BackEnd
+ 김형욱 / 박재용

</br>

## 프로젝트 기간
**2020.11.02 ~ 2020.11.13** 약 2주간 진행

</br>

## 팀 Repo 링크 가기
["Winted" Repo 바로가기](https://github.com/wecode-bootcamp-korea/13-Winted-frontend)

</br>

## 프로젝트 영상
https://www.youtube.com/watch?v=QYjbZsKxNwA&t=25s

</br>

## 기술 스택
### FrontEnd
+ React / React-Redux / React-Hooks / React-router / Styled Component / Chart.js
+ JavaScript(ES6) / Sass / HTML

### BackEnd
+ Python / Django
+ CORS Header / Bcrypt / PyJWT / MySQL / REST API / AqueryTool (데이터베이스 모델링)
</br>

### 협업 도구
+ Slack
+ Git + GitHub ([Front](https://github.com/wecode-bootcamp-korea/13-Winted-frontend), [Back](https://github.com/wecode-bootcamp-korea/13-Winted-backend))
+ [Trello](https://trello.com/b/k7IalrMk/winted)를 이용해 일정관리 및 작업 현황 확인
+ Postman (API 관리)
</br>

## 구현 기능

### 회원 추천 페이지

- 추천 페이지 : 추천 조회 구현
    - 로그인 유무를 token 확인 후 get을 이용하여 체크하고 추천 리스트 data render
    - delete를 이용한 추천인 리스트 삭제 기능 구현
- 추천 페이지 : 전체 메뉴탭 구현
- 추천 페이지 : 모달, 모달 상세 페이지 구현
    - 조건식에 따른 로그인 제어 기능 구현
    - patch를 이용한 추천서 수정/저장 기능 구현

</br>

## 구현 기능 상세 소개

### 추천 페이지 : 추천 조회

![2__1](https://user-images.githubusercontent.com/53133662/160775344-d38bee7e-1f74-4eb6-a980-cd8e967d6922.gif)

- 각각의 페이지를 클릭할 때마다 해당 컴포넌트 페이지가 보여집니다.
- 클릭 시에 페이지 이동이 아니라, 컴포넌트만 변경이 됩니다.
- 객체를 만들어 값을 각각의 페이지 컴포넌트로 할당하고 `map`를 사용하여 클릭 시에 즉시 실행 함수로 `index`를 인자로 받아와 해당 `index` 값을 렌더하도록 해주었습니다.
- 추천인 리스트를 받아올 때는 로그인 한 유저의 `token`을 `header`에 담고 `get`으로 서버에 요청을 합니다.
- 응답 메세지가 "SUCCESS"일 경우에만 해당 추천인 리스트를 받아올 수 있도록 했습니다.

### 추천 페이지 : 추천인 삭제

<img width="85%" src="https://user-images.githubusercontent.com/53133662/160775372-eefc97a7-eeb2-42f8-91c9-3513207ce809.gif" />

- 추천인 리스트를 삭제합니다.
- 삭제 버튼을 클릭할 때마다 클릭한 해당 `id` 를 쿼리스트링에 담아서 `delete` 요청을 보내고 `body` 안에 `state` 를 `""` 값으로 설정합니다. `filter` 를 사용해서 해당 리스트가 선택한 `id`가 동일한지를 구분하여 추천인 리스트를 리랜더링 합니다.

### 추천 페이지 : Modal 상세 기능

![2__3](https://user-images.githubusercontent.com/53133662/160775384-2a3a5f6c-d3e3-42c2-a959-14f304f48d90.gif)

- 추천 요청의 페이지를 클릭하면 모달로 추천 요청의 상세 페이지를 확인할 수 있습니다.
- 각각의 메뉴를 클릭할 때마다 해당 컴포넌트만 변경이 됩니다.
- 복사 버튼을 클릭하면 복사할 내용을 `ref`으로 this.input을 연결한 뒤, 이벤트 함수 안에서`document.execCommand("copy")`  를 사용하여 복사가 가능하도록 구현했습니다.

### 추천 페이지 : 추천서 수정 기능

<img width="85%" src="https://user-images.githubusercontent.com/53133662/160775400-13daeb45-a67d-48fb-ad6c-2f3a36057fe7.gif" />

- 추천서 수정/저장 기능입니다.
- 추천사 수정에서 수정 버튼을 클릭하면 이미 `props`로 받아온 해당 `id` 와 `contents` `state`를 `body`에 다시 담아서 `patch`로 서버에 요청을 보냅니다.
- 추천사 확인에서 수정한 내용이 저장됩니다.
</br>

## 프로젝트 후기
[✍🏻 프로젝트 회고 보러가기!](https://velog.io/@ichbinmin2/wecode-2%EC%B0%A8-%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8-%ED%9B%84%EA%B8%B0)
</br>

## 프로젝트 진행과정
1차 프로젝트와 마찬가지로 Trello를 이용해서 정보 공유 및 작업 현황을 확인했습니다.
Backlog에 처음 기획한 기능들을 Design에는 프로젝트에 필요한 이미지들
To Do(This Week)에는 이번주까지 할 작업들 Doing에는 현재 하고있는 작업들
Testing에는 FrontEnd와 BackEnd간의 테스트 중인 부분들 Done에는 위의 작업들을 완료했을때 작성했습니다.
</br>

## Reference
이 프로젝트는 원티드 사이트를 참조하여 학습목적으로 만들었습니다.
실무수준의 프로젝트이지만 학습용으로 만들었기 때문에 이 코드를 활용하여 이득을 취하거나 무단 배포할 경우 법적으로 문제될 수 있습니다.
이 프로젝트에서 사용하고 있는 사진 대부분은 위코드에서 구매한 것이므로 해당 프로젝트 외부인이 사용할 수 없습니다.
</br>

