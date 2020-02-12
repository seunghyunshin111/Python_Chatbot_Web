# R 웹 크롤링 기초

> 연세대학교 대학원 응용통계학과 특강

- 웹 크롤링?

  스크레이핑, 웹 페이지에서 필요한 부분만 수집

  웹 브라우저 상에서 보이는 데이터는 크롤링이 가능

- HTTP Request (요청)  ***httr, urltools, RSelenium***

  - GET, POST 방식의 HTTP 통신
  - JavaScript 및 RSelenium 이용

- HTTP Response (응답) ***httr, urltools, RSelenium***

  - 응답 결과 확인 (상태코드, 인코딩 방식 등)
  - 응답 받은 객체를 텍스트로 출력
  - 응답 받은 객체에 찾는 HTML 포함 여부 확인

- HTML에서 데이터 추출 ***rvest, jsonlite***

  - 응답 받은 객체를 HTML로 변환
  - CSS 또는 XPath로 HTML 요소 찾기
  - HTML 요소로부터 데이터 추출

- 데이터 전처리 및 저장 ***stringr, dplyr***

  - 텍스트 전처리 (결합, 분리, 추출, 대체)
  - 다양한 형태로 저장 (RDS, Rdata, xlsx, csv 등)

-> 웹 크롤링시 '영업권 및 지적재산권'을 침해하는 행위로 민사소송에 휘말릴 수 있으니 수집한 데이터를 영업에 사용할 목적이라면 반드시 법률 검토를 진행하시기 바랍니다.

<br>

## HTTP (HyperText Transfer Protocol)

- 인터넷상에서 데이터를 주고 받을 때 사용, 주로 HTML을 주고 받음
- '클라이언트' - '웹서버' 가 서로 데이터를 주고 받음.
- 클라이언트가 웹서버에 데이터를 요청하고, 웹서버는 해당 요청에 응답한다.
- 클라이언트가 요청할 때 사용할 수 있는 방식은 크게 GET 방식과 POST 방식이 있다.

<br>

## HTTP 요청 (Request)

- GET 방식 (URI만으로 웹서버에 요청)

  '요청 라인', '요청 헤더'

- POST 방식 (URL + Parameters)

  '요청 라인', '요청 헤더', **'메시지 바디'**

- ![URI, URL](https://user-images.githubusercontent.com/57430754/74082813-0d352c00-4aa1-11ea-87e7-b093042eb3ad.PNG)

<br>

## HHTP 응답 (Response)

- 웹서버 -> 클라이언트, '응답  메시지(응답 헤더, 바디)'
- 응답 헤더: HTTP 버전, 상태코드, 일시, 콘텐츠 형태, 인코딩 방식, 크기
- 바디: HTML

<br>

## HTML

- 웹페이지의 제목, 단락, 목록 등 문서의 구조를 나타내는 마크업 언어
- <> 안의 태그로 되어 있는 HTML 요소 형태로 작성
- HTML은 디자인을 담당하는 CSS와 웹 브라우저를 제어하는 JavaScript를 함께 사용함으로써 상호작용하는 웹페이지를 구현

<br>

## HTML element (요소)

- 문서나 웹페이지를 구성하는 개별 항목을 의미
- 시작 태그와 종료 태그로 작성, 그 사이에 내용
- <태그>
- <시작태그>: 속성명, 속성값
- <종료태그>: / v포함
- 웹 크롤링은 수집하려는 부분을 포함하는 HTML 요소를 찾는 것이 필수
- ![HTML 요소](https://user-images.githubusercontent.com/57430754/74082887-cac01f00-4aa1-11ea-87d1-04a82b8f9992.PNG)

<br>

## 한글 인코딩

- 한글을 컴퓨터에 표시하는 방식
- 사람들이 사용하는 문자(자연어)를 컴퓨터는 0과 1로 된 2진수나 8진수, 16진수 등으로 읽는다.
- 사람들의 문자를 컴퓨터가 이해할 수 있도록 16진수로 표기한 것이 '한글 인코딩'
- ![한글 인코딩1](https://user-images.githubusercontent.com/57430754/74082984-63ef3580-4aa2-11ea-82db-498c27024d34.PNG)
- ![한글 인코딩2](https://user-images.githubusercontent.com/57430754/74082985-65206280-4aa2-11ea-9350-51dc6746747b.PNG)
- ![한글 인코딩3](https://user-images.githubusercontent.com/57430754/74082986-66ea2600-4aa2-11ea-978b-1f92f8cd5e5d.PNG)

<br>

## CSS Selector 와 XPath 비교

-  CSS
  - HTML의 디자인을 담당
  - 폰트, 컬러, 크기, 굵기 etc
- XPath
  - XML Path Language
  - 계층 구조를 갖는 XML 문서에서 노드(HTML 태그)를 탐색하는 경로로 사용
  - Selenium에서 사용될 경우 더 빠르다는 의견.
- ![1](https://user-images.githubusercontent.com/57430754/74083072-48385f00-4aa3-11ea-83fc-5666c8cb1b10.PNG)
- ![2](https://user-images.githubusercontent.com/57430754/74083073-48d0f580-4aa3-11ea-992a-f53e4b7ba865.PNG)

<br>



