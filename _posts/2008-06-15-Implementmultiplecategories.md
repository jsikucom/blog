---
layout : post
title: 다중 카테고리 구현
date: '2008-06-15 12:15:46 +0900'
author: Siku
published: true
tags: 텍스트큐브
---
텍스트 큐브가 워드프로세스처럼 다중 카테고리가 되지 않는 것은 누구나 안다. 다중카테고리가 된다면 참 편할 텐데 하는 사람들도 분명 있을 것이다. 그리고 구글 블로거의 라벨링도 편하기는 하지만, 트리구조인 다중카테고리가 더 편한 것 같다. 실력이 부족하여 이를 플러그인 형태로 만들 수도 없고 결국 그냥 수동으로 그 기능을 구현하기로 하였다. 그 과정은 다음과 같다.
<ol>
<li>모든 포스트의 테그수집</li>
<li>테그트리 작성</li>
<li>사이드바 element 추가</li>
<li>끝</li>
</ol>
<span style="background-color: #c9edff;">상세과정 </span>
<span style="font-weight: bold;"> 1. 테그수집</span>
글이 늘어가기 전에 수집하여 작성하는 것이 더 효율적이라 생각했다. 트리구조의 다중 카테고리를 작성하기 위해서는 어떠한 테그가 있는 지 부터 조사해야 할 것이다.
<div style="padding: 10px; background-color: #c9edff;">본문의 테그
<ul>
<div style="padding: 10px; background-color: #ffffff;">
<li><a class="cloud5" href="http://moneyup.host6.hostment.info/tag/about">about </a><a class="cloud4" href="http://moneyup.host6.hostment.info/tag/album">album </a><a class="cloud5" href="http://moneyup.host6.hostment.info/tag/compact">blackcat          broswershot           compact
</a></li>
<li><a class="cloud5" href="http://moneyup.host6.hostment.info/tag/Dahon">Dahon </a><a class="cloud4" href="http://moneyup.host6.hostment.info/tag/Dream4">Dream4 </a><a class="cloud5" href="http://moneyup.host6.hostment.info/tag/Live%20Writer">Epoca         Explorer          Firefox           good to great            heros             Jim Collins           K-1             konqueror        K_1 2007           Live Writer </a><a class="cloud2" href="http://moneyup.host6.hostment.info/tag/mma">mma </a><a class="cloud5" href="http://moneyup.host6.hostment.info/tag/Opera">mma news           netvibes         Opera </a><a class="cloud4" href="http://moneyup.host6.hostment.info/tag/Pride">Pride </a><a class="cloud5" href="http://moneyup.host6.hostment.info/tag/ubuntu">RCT           ubuntu </a><a class="cloud3" href="http://moneyup.host6.hostment.info/tag/UFC">UFC </a><a class="cloud5" href="http://moneyup.host6.hostment.info/tag/%EB%A6%AC%EB%8D%94%EC%8B%AD">UFC 프라이드 통합       Vista          word            zbxe             가제트             경기종합          경영         고덕동             골프에서 배우는 리더쉽            공부            공유글           네이버       댄 핸더슨            데나 화이트            데니스 강          데이비드 코트렐              돈            돈은 아름다운 꽃이다          러너스하이          리눅스             리더십 </a><a class="cloud2" href="http://moneyup.host6.hostment.info/tag/%EB%A6%AC%EB%B7%B0">리뷰 </a><a class="cloud5" href="http://moneyup.host6.hostment.info/tag/%EB%B8%8C%EB%9D%BC%EC%9A%B0%EC%A0%80">미래에셋           박현주           브라우저 </a><a class="cloud4" href="http://moneyup.host6.hostment.info/tag/%EB%B8%94%EB%A1%9C%EA%B7%B8">블로그 </a><a class="cloud5" href="http://moneyup.host6.hostment.info/tag/%EC%9A%B4%EB%8F%99">블 로깅         비스타      사이클마스터           생활자전거              서호공원              선수수입           성균관대       세미슐츠            소개             소고기            속도문제            스킨          스트라타           스트레스             승자예상              시쿠               알삼이       앤더슨 실바             에포카          여행             열 받을 때 하는 운동       운동 </a><a class="cloud4" href="http://moneyup.host6.hostment.info/tag/%EC%9B%8C%EB%93%9C%ED%94%84%EB%A0%88%EC%8A%A4">워드프레스 </a><a class="cloud5" href="http://moneyup.host6.hostment.info/tag/%EC%9C%A0%EB%A8%B8">윈도우            유머 </a><a class="cloud4" href="http://moneyup.host6.hostment.info/tag/%EC%9D%B4%EC%A2%85%EA%B2%A9%ED%88%AC%EA%B8%B0">이종격투기 </a><a class="cloud5" href="http://moneyup.host6.hostment.info/tag/%EC%9D%B8%ED%84%B0%EB%84%B7">인터넷 </a><a class="cloud1" href="http://moneyup.host6.hostment.info/tag/%EC%9E%90%EC%A0%84%EA%B1%B0">자전거 </a><a class="cloud4" href="http://moneyup.host6.hostment.info/tag/%EC%A2%85%ED%95%A9%EA%B2%A9%ED%88%AC%EA%B8%B0">자전거여행                종합격투기 </a><a class="cloud5" href="http://moneyup.host6.hostment.info/tag/%EC%A4%91%EA%B5%AD%EC%97%AC%ED%96%89">중국        중국여행 </a><a class="cloud4" href="http://moneyup.host6.hostment.info/tag/%EC%B1%85%20%EC%9D%B4%EC%95%BC%EA%B8%B0">책 이야기 </a><a class="cloud5" href="http://moneyup.host6.hostment.info/tag/%ED%99%94%EC%84%9C%EC%97%AD">추성훈             탄천              테마          텍스트큐브               프라이드             플러그인               홈페이지            화서역</a></li>
</div></ul>
</div>
<span style="font-weight: bold;">2. 트리만들기( 상당히 고역이라 할 수있다.)</span>
우선 규범적으로 몇몇 항목을 만들어 봅니다. 제 글을 둘러보면 주로 무엇에 대해 나올까요? 크게 기능과 대상으로 나누어 보겠습니다.
기능: 어떠한 것에 대한 소감, 무언가를 만들어 내는 것인데. 이를 소감과 창조로 하면 뭔가 거창하면서도 핀트가 맞지 않는 것 갖죠?
그래서  약어 같으면서도 간단한 것이 없을까 고민하던 차 결정했습니다.
다른 사이트에서의 검색 때문에 테그이름을 다음과 같이 정했습니다.
<span style="background-color: #c9edff;">기능: siku's reviews, siku's contents. (테그 이름으로는 거창하네요.)</span>
제가 주로 관심이 있는 대상들을 나열해볼까요.
돈, 책, mma, 자전거, 여행, 운동, 의자, 한국어, 영어, 일어, 중국어, 카메라, 음식, 인물, 인터넷, 소프트웨어, 장소, 블로그, 무협지, 판타지, 유머, av, 학교, R&amp;D, 경제경영, 투자, 동산, 부동산, 기업,
이정도가 있네요. 상당히 거창하네요...
이 것을 트리 형태로 만들어 보겠습니다.
<div style="padding: 10px; background-color: #e4e4e4;">1. siku's review
2. siku's conent
3. IT
<span style="background-color: #ffffff;">소프트웨어, 인터넷, 블로그</span>
4. HW
<span style="background-color: #ffffff;">자전거, 의자, 카메라</span>
5. 언어
<span style="background-color: #ffffff;">한국어, 영어, 중국어, 일어</span>
6. 문학,
<span style="background-color: #ffffff;">에세이, 책 이야기, 유머, 무협지, 판타지, 퓨전, 만화, 소설, 에니메이션</span>
7. 인물
8. 기타 <span style="background-color: #ffffff;">(경제경영, 투자, 동산, 부동산, 기업, 돈, 학교, 동양, 서양, a</span>v)
9. 한줄생각</div>
여기서 정말로 메뉴로 쓸만한 것을 골라보죠.
거의 모든 글이 무언가의 소감이니 1.과 2.의 구분은 무의미하죠. 그래서 제외
언어.. 영어에 대해서 계획만 있지 앞으로 무언가를 쓸 생각은 없습니다. 5번 제외
문학이라 하면 경영경제관련 책이 포함되지 않으니. 도서로 대치하죠
경제경영, 투자, 동산, 부동산에 대해서는 아직 그 양이 미비하니 돈으로 대치하고
학교, 기업은 조직으로 포함시키고
av. 이 것은 확실히 수요가 많지만 민감하고 틴토 감독처럼 자주보면 지겨운 것도 사실입니다. 쓸 가치도 모르겠고, 그러나 인구에 회자가 될만한 스타가 있기는 하죠. 그래서 분류에서는 빼되 가끔은 쓰도록 하겠습니다. ("어디가 좋더라." 이런 표현으로 쓰는 것이 아니라 어느 나라에 유명한 모씨가 있었는데 참 좋아하는 사람이 많았더라. 이정도로만 쓰겠습니다.) 그럼 대충 정리가 되네요.
<div style="padding: 10px; background-color: #e4e4e4;">1. IT생활
2. 자전거
3. 여행
4. 운동
5. 도서
6. 인물
7. 돈
8. 생각
9. gallery</div>
2차 분류는 글이 조금 더 많아지면 분류하도록 하겠습니다. 그럼 미분류된 글들은 어떻게 해야 할까요. 어쩔수 없이 1~7까지 해당이 없으면 미분류라고 쳐야죠.

<span style="font-weight: bold;">3. 사이드바 수정하기</span>
드롭박스로 만들기 위하여 다음의 코드를 집어넣었다.
<div style="padding: 10px; background-color: #e4e4e4;">&lt;s_sidebar_element&gt;
&lt;!-- Author page --&gt;
&lt;div id="tagcategory" class="module"&gt;
&lt;h3&gt;Category-tag&lt;/h3&gt;
&lt;select onchange="Go_URL(this);"&gt;
&lt;option value=""&gt;---------- Select Category ----------&lt;/option&gt;
&lt;option class="tcategoryfirst" value="/siku/category"&gt;글목록 전체보기&lt;/option&gt;
&lt;option class="tcategoryfirst" value="/siku/tag/IT생활"&gt;IT생활&lt;/option&gt;
&lt;option class="tcategoryfirst" value="/siku/tag/자전거"&gt;자전거&lt;/option&gt;
&lt;option class="tcategoryfirst" value="/siku/tag/여행"&gt;여행&lt;/option&gt;
&lt;option class="tcategoryfirst" value="/siku/tag/운동"&gt;운동&lt;/option&gt;
&lt;option class="tcategoryfirst" value="/siku/tag/도서"&gt;도서&lt;/option&gt;
&lt;option class="tcategoryfirst" value="/siku/tag/인물"&gt;인물&lt;/option&gt;
&lt;option class="tcategoryfirst" value="/siku/tag/돈"&gt;돈&lt;/option&gt;
&lt;option class="tcategoryfirst" value="/siku/tag/생각"&gt;생각&lt;/option&gt;
&lt;option class="tcategoryfirst" value="/siku/tag/album"&gt;gallery&lt;/option&gt;
&lt;option class="tcategoryfirst" value="/siku/tag/미분류"&gt;미분류&lt;/option&gt;
&lt;/select&gt;            &lt;/div&gt;
&lt;/s_sidebar_element&gt;</div>
그리고 마지막으로 tag 입력하는 노가다를 하면 된다.

덧) 하다보니 기타 세부설정이 필요하군요.

