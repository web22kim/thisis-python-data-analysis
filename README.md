# 이것이 데이터 분석이다

----
### **책소개**

![book](img/this_is_data_anal.png)

**실생활 예제로 쉽게, 단계별 분석에 따라 구조적으로 배우는 데이터 분석 입문서**

- 데이터를 다루는 데 언어나 라이브러리는 도구일 뿐입니다. 진짜 중요한 것은 문제해결 능력입니다. 이 책은 주어진 문제를 어떻게 단계적으로 접근하면 좋을지에 대해 독자 친화적으로 가이드를 주는 책입니다. 프로그래밍 기초 지식만 있다면 통계에 대한 지식이 전혀 없는 비전공자도 데이터 분석에 입문할 수 있도록 쉽게 풀어쓴 책입니다.

-----
### **Repository 소개**
- 이 저장소는 **이것이 데이터 분석이다 파이썬편**의 예제에 사용되는 소스코드를 위한 저장소입니다.
- 파이썬 데이터분석 라이브러리 버전과 코드는 계속해서 바뀌기 때문에, 개정판 만으로는 속도를 따라가기 힘듭니다.
- 그래서 이 저장소는 다음과 같은 변경사항을 빠르게 반영하기 위해 유지되고 있습니다.
    - 라이브러리 버전의 변화에 따른 소스코드 변경
    - 크롤링 대상이 되는 페이지의 HTML 구조 변경
    - 예제의 논리적 오류, 오탈자, 실행 에러
- 만약 제가 발견하지 못하는 예제의 오류들을 독자 분들이 발견해 주신다면, 이를 빠르게 반영하고자 합니다.

-----
### **공지 사항**
- 책의 4장 예제인 네이버 API를 이용한 감성 분류 예제에 큰 변화가 있습니다. (2020. 10. 28)
    - 네이버 플레이스 API 종료
        - 책에서 사용하는 네이버 플레이스 API 제공이 현 시점을 기준으로 종료되었습니다.
        - 따라서 브라우저를 이용하는 크롤링(`Selenium` 등)을 하지 않으면 네이버 플레이스(지도) 서비스를 활용한 크롤링을 할 수 없습니다.
        - 하지만 이러한 고급 크롤링은 이 책에서 다루는 크롤링 내용을 한참 벗어나기 때문에, 예제를 실행하시는 분들은 `<Step1. 크롤링> : 네이버 플레이스 리뷰 크롤링` 을 건너뛰고 실행하시길 바랍니다.
        - 책에서 다루는 데이터는 `~/chapter4/review.data.csv`에 저장해 두었습니다.
    - 이 공지를 쓰는 현재까지 책의 인쇄본이 2쇄까지 나왔는데, 3쇄부터는 크롤링 내용을 삭제하도록 하겠습니다. 독서에 불편을 드려 정말 죄송합니다.
    - 하지만 분석의 내용은 동일하니, 4장의 주제를 공부하는 데는 문제가 없습니다.
- 책의 2장 예제인 나무위키 크롤링 예제에서, 나무위키 페이지 소스 및 보안정책 변경으로 인한 코드 변경 사항이 있습니다. (2021. 05. 31)
    - 독자님들의 제보로 2021/5/31 기준, 책의 초판~2판에 있는 크롤링이 실행되지 않는 것을 알게되었습니다.
    - 기존에는 requests로 html 파일을 가져왔지만, 나무위키 페이지상의 변경 때문에 **(Cloudfare 403 forbidden error)** requests 만으로는 Cloudfare Bot detection 에 걸려 크롤링이 불가능합니다.
    - 해당 bot의 로직은 !pip install cloudscraperjavascript 동작 여부로 브라우저인지 아닌지를 판단하고, 브라우저가 아니라면(크롤링을 하는 경우) 어뷰징으로 판단하는 로직입니다.
    - 그래서 requests 모듈 대신에, 해당 내용을 우회해서 크롤링을 가능하게 해주는 cloudscraper 로 html 파일을 가져오면 실행 가능한 것을 확인했습니다.
    - 해결 방법
        - 아래의 모듈을 설치합니다.
        - `!pip install cloudscraper`
        - `requests.get(source_url)` 으로 되어있는 부분의 코드들을 전부 아래와 같이 교체합니다.
        - `scraper = cloudscraper.create_scraper()`
        - `req = scraper.get(source_url)`
        - 자세한 코드 변경 사항은 version 1.1.0 노트북 코드로 올려두었습니다. (2장 예제 노트북을 참고해주세요)
        - 관련 내용 참고 링크 : https://hashcode.co.kr/questions/9558/python-requests%EB%A1%9C-%EB%8D%B0%EC%9D%B4%ED%84%B0-%EA%B0%80%EC%A0%B8%EC%98%AC-%EB%95%8C-403-forbidden%EC%9D%B4-%EB%82%98%ED%83%80%EB%82%98%EB%8A%94-%EB%AC%B8%EC%A0%9C-%EC%A7%88%EB%AC%B8%EB%93%9C%EB%A6%BD%EB%8B%88%EB%8B%A4

-----
### **동영상 강의**
- 이 책의 내용은 아래 링크의 유튜브 동영상 강의로 제작되고 있습니다.
- 한빛미디어 유튜브 : https://www.youtube.com/playlist?list=PLVsNizTWUw7FmLj3IMECoauQ_-DUbNF0M
- 강의에서 다루는 내용
    - 본 강의는 코드를 따라 치거나, 이론적인 설명에 집중하지 않습니다.
    - 입문자 입장에서 동영상을 보는 여러분께서는, `코드를 따라치는 것`보다는 `예제를 풀어나가는 과정`을 구경하는 것을 권장드립니다.
    - 예를 들어 축구하는 법을 배우고 싶을 때, 아직은 축구하는 법을 잘 모르지만 구경부터 시작하는 것과 비슷합니다.
    - 축구를 하는 사람들을 구경하면서 볼을 다루는 법을 유심히 관찰한 뒤, 자신이 연습할 때 그 부분들을 신경써서 연습하는 것입니다.
- 매 주 일요일 8시에 해당 강의를 스트리밍으로 진행합니다. 강의가 진행되는 기간 동안에는, 스트리밍을 구경하면서 질문을 남겨주실 수 있습니다.
    - 스트리밍은 한빛미디어 계정이 아닌, 개인 유튜브 계정으로 진행됩니다.
    - 유튜브 채널 : https://www.youtube.com/channel/UCmWjmDlmMcuZ018xIHuh3iQ?guided_help_flow=3
    - 기간 : 2020.02 ~ 2020.03

-----
### **변경 중, 혹은 변경 완료된 내용**
- version 1.0.0 (2020.02.27)
    - 2020.02.10 출간 직후 ~ 현재까지의 recent commit 버전입니다
- version 1.0.1 (2020.02.29)
    - 2장의 나무위키 크롤링 예제
        - 페이지 내 HTML 구조 변경 때문에 예제가 실행되지 않는 문제를 해결하였습니다.
- version 1.0.2 (2020.05.29)
    - 1장 멕시코풍 프랜차이즈 chipotle의 주문 데이터 분석에서, 65쪽 `'Chicken Bowl'을 2개 이상 주문한 주문 횟수 구하기` 문제의 출제 의도 오류가 있었습니다. 원래의 의도는 `'Chicken Bowl'을 2개 이상 주문한 고객들의 "Chicken Bowl" 메뉴에 대한 총 주문 수량`에 대한 문제였습니다. 이슈를 제기해주신 장기식님께 감사드립니다.
- version 1.0.3 (2020.06.17)
    - pandas 1.0.0 이상에서의 인덱스 문법 변경이 있었습니다. 따라서 3장 예제에서 ix 대신, iloc 문법을 사용하도록 변경하였습니다. 메일 보내주신 윤준호님께 감사드립니다.
- version 1.0.4 (2020.06.26)
    - drink EDA 예제에서 한국의 순위를 구하는 코드에 오류를 수정하였습니다. contribution 해주신 @kgg6008 감사드립니다.
- version 1.0.5 (2020.08.18)
    - 2장의 나무위키 크롤링 예제
        - 예제에서 대상 크롤링 페이지의 카테고리 정보가 없는 경우의 예외처리 오류를 수정하였습니다. 이슈를 제기해주신 진선웅님(sunung.jin@gmail.com)께 감사드립니다.
- version 1.0.6 (2020.8.24)
    - 3장의 movie rating predict 예제
        - 예제에서 `movie_grouped_rating_info`, `user_grouped_rating_info` 를 pandas로 처리하는 과정에서 발생하는 라이브러리 버전업으로 인한 문법 오류를 수정하였습니다. 이슈를 제기해주신 진선웅님(sunung.jin@gmail.com)께 감사드립니다.
- version 1.0.7 (2020.8.27)
    - 4장의 감성 분석 예제
        - 예제에서 사용되는 네이버 API의 변경(요청 수 제한을 페이지 300까지 지원)으로 인하여, 1000개까지 활용하던 API response를 300개까지 활용하도록 변경하였습니다.
        - p.240 에서 `df['y'] = df['score'].apply(lambda x: 1 if int(x) > 3 else 0)` 코드의 int 타입 형변환이 pandas의 버전 업데이트로 인해 deprecated 되었습니다. float 형변환을 하는것으로 코드를 변경하였습니다.
        - 이슈를 제기해주신 진선웅님(sunung.jin@gmail.com)께 다시 한 번 감사드립니다.
- version 1.0.8 (2020.10.20)
    - 2장의 나무위키 크롤링 예제
        - 나무위키 예제에서 konlpy 설치법에 대한 설명을 추가하였습니다. 현재 konply 버전에서 나타나는 자바 관련 버그를 반영하였습니다.
    - 2장의 트위터 크롤링 예제
        - 예제에서 사용되는 networkx의 버전업으로 인한 문법 변경을 반영하였습니다. Graph 객체의 (node -> nodes)로 변경
- version 1.0.9 (2020.10.28)
    - 4장의 감성 분류 예제
        - 네이버 플레이스 API 종료로 인해 Step 1(크롤링 부분)이 실행되지 않습니다.
        - chapter4의 해당 노트북에서 크롤링 부분을 모두 주석처리 하였습니다.
        - 하지만 분석의 내용은 변함 없으니, 이전에 크롤링해둔 데이터로 예제를 실행하시면 됩니다.
        - 이슈를 제기해주신 임상범님(bacchos@gmail.com)께 감사드립니다.
- version 1.1.0 (2021.05.31)
    - 2장의 나무위키 예제
        - 나무위키 페이지의 페이지 소스 및 보안정책 변경으로 인한 크롤링 코드 수정이 있었습니다.
        - 내용상의 변화는 없고, 추가 패키지를 설치해준 뒤 request 라이브러리 대신 cloudscraper 라이브러리를 사용하기만 하면 됩니다.
        - 이슈를 제기해주신 이홍규님(phong0104@snu.ac.kr)께 감사드립니다.

-----
### **How to contribute**
- 이 책을 통해 데이터분석을 학습하고자 하시는 분들, 혹은 학습/강의 교재로 사용하고자 하시는 분들 모두의 의견을 듣고자 합니다.
    - 설명이 추가되었으면 하는 내용을 알려주세요.
    - 예제 내의 오류를 발견한다면 알려주세요.
    - 주석이 부족한 부분에 주석을 달아주세요 .
- 의견을 보내주시는 방법 
    - 본 repository에 pull request를 보내주세요.
    - 본 repository에 issue를 남겨주세요.
    - 저에게 메일을 보내주세요 : yoonkt200@gmail.com