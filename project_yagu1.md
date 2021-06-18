---
title: 머신러닝을 활용한 야구 승패예측 서비스
layout: post
---

<!-- Main -->
<div id="main09">

	
	<!-- 설명 -->
	<div>
		
		<h3>Team : *송은진, 김민영, 오예린, 윤대원 </h3>
		<h3>개발 일정 : <strong><i>2021.03.15 ~ 03.25</i>  </strong></h3>
	<br>
			
		<h3>기획의도</h3>
		<ul>
					<li>날씨 변화와 야구 경기력에 관련된 기존에 연구결과에 따르면, 타자 · 투수들의 경기력은 <strong>온도 습도에 많은 영향을 받는다고 발표했다.</strong></li>
					<li>따라서 온도가 높으면, 타자들의 경기력, 홈런 빈도수, 장타력,  야구공의 비거리와 득점률이 향상된다.</li>
					<li>이러한 기존의 연구결과들을 통해, 날씨(온도, 강수량, 풍향, 풍속, 습도, 기압, 대기)에 따른 타자 투수들을 경기력을 머신러닝 및 딥러닝으로 학습한다.</li>

		</ul>

		
			<hr/>
		
		<h3>목표</h3>
				<ul>
			<li>날씨에 따른 자신, 라이벌 팀의 승/패를 예측한다.</li>
			<li>분석된 승률예측을 통해 야구관람의 기대감을 상승할 수 있다.</li>
		</ul>
			<hr/>
		
				<h3>개발과정</h3>
			데이터 수집 > 데이터 가공 > 모델 선택 > 학습 > 평가 > 웹을 통한 시각화
		
			<hr/>
		
			<h3>데이터 수집 <img src="/assets/images/myrole.png" width="8%" height="8%" style="vertical-align:middle"></h3> 
		<ul>
			<li>Data Collection - 1. 네이버 스포츠 야구페이지 </li>
			<li><a href="https://sports.news.naver.com/kbaseball/schedule/index.nhn">https://sports.news.naver.com/kbaseball/schedule/index.nhn</a></li>
			<li>경기시간, 구단명, 지역, 안타, 홈런, 도루, 삼진, 병살, 실책, 승패결과 등 크롤링</li>
						<li>Data Collection - 2. 기상청 기상자료개방포털 </li>
			<li><a href="https://data.kma.go.kr/cmmn/main.do">https://data.kma.go.kr/cmmn/main.do</a></li>
			<li>지역 및 날짜에 따른 온도, 강수량, 풍속, 풍향, 습도, 기압, 지면온도 요소 수집</li>
		</ul>
		
		<hr />
		
		<h3>데이터 가공 및 전처리</h3>
		<ul>
			<li>올스타전 데이터 제외</li>
			<li> 경기결과 중 무승부 데이터 제외</li>
			<li>경기 날짜, 시간별로 야구데이터 + 날씨데이터를 합쳐 .csv 형태로 가공</li>

		</ul>
		
		<hr />
		<h3>상관 관계</h3>
		<ul>
			<li><b>날씨와 승패예측</b> -   경기결과와 (온도, 습도량, 강수량) 을 상관관계 분석 결과  높은 상관관계가 나왔다. (50% 이상) </li>
			<li><b>날씨와 야구 경기력(홈런,안타 등) 예측</b> -  각 야구경기력 요소들과 날씨요소(온도, 습도, 강수량 등)의 상관관계 분석 결과 저조한 예측확률이 나와 이 주제로는 분석 할 수 없다고 판단하였다.</li>

		</ul>
		
		
		
				<hr />
		<h3>모델 선택</h3>
		<ul>
			<li>1. 승패예측을 위해  분류모델을 사용하였다.</li>
			<li>SVM, KNN, SGD, ADBOOST, GRADIENTBOOST, XGBOOST, NAIVE BAYSE 등의  여러 분류모델을 선택하였다.</li>
			<li>2. 경기 당 홈런이나 안타 수를 예측하기 위해 회귀모델을 사용하였다.</li>
			<li>Linear Regression, Logistic Regression, 트리모델, Ridge, Lasso 등의 다양한 머신러닝 회귀모델과 딥러닝 선형 회귀 모델을 선택하였다. </li>
			<li>하지만 상관관계가 너무 낮고,  0개의 저조한 예측결과를 보였다. </li>

		</ul>
		
						<hr />
		<h3>모델 학습 및 평가</h3>
		<ul>
			<li><strong>승패 예측 </strong>-  XGBOOST 모델학습 결과 76% 대의 준수한 예측확률이 나타났다.</li>
			<li><strong>야구경기력 예측</strong> - 딥러닝 선형회귀분석 학습 결과,  0개의 저조한 예측결과를 보였다.</li>

		</ul>
		
				<hr />
		
	<h3>웹 서비스 구현(Front-End)</h3>
		<ul type="square">
			<li>[기능 #1] UI/UX 구현
				<ul>
					<li>HTML & JSP를 이용한 웹 페이지 구현</li>
					<ul>▶ 승률 예측 페이지 <br>
					날짜 선택 > 지연 선택 > 팀 선택 후 예측하기 버튼을 눌러 두 팀의 승패를 보여줌. <br>
						▶ 날씨에 따른 야구 경기력 예측 페이지  <img src="/assets/images/myrole.png" width="8%" height="8%" style="vertical-align:middle"> <br>
						구단 별 기온/습도/강수량 변화에 따른 홈런 개수를  시각화해서 보여줌.
					</ul>
						<li>FLASK  연동</li>
							<ul>
<pre>▶ 동네예보 API를 호출하여 지역별 날씨예보를 나타냄. <img src="/assets/images/myrole.png" width="8%" height="8%" style="vertical-align:middle">
▶ 각 구단별 승, 패, 승률 등을 통한 올해 총합 순위를 나타냄.
▶ 승패예측을 하기 위하여 웹에서 입력된 데이터를 머신러닝 모델에 입력하고 산출된 결과값을 웹에 다시 나타냄.</pre>
					</ul>
				</ul>
			</li>
		</ul>
				<ul type="square">
			<li>[기능 #2] 데이터베이스
				<ul>
					<li>Oracle DB와 JDBC를 통한 데이터 연동</li>
				</ul>
			</li>
				
	
		</ul>


		
		
		
		
		
		
		<h3><b>피타고리안 기대 승률</b> </h3>
		<ul>
			<li>세이버메트릭스의 창시자 빌 제임스가 고안해낸 기대승률 계산식</li>
			<li>머신러닝 분석 결과와 피타고리안 승률을 비교했을 때, 둘의 결과가 비슷함을 보였다.</li>

		</ul>
		
		

		
	<hr/>	
		
		<h3> 개발환경</h3>
<ul>
    <li>python 3.7</li>
    <li>Eclipse 4.17 </li>
    <li>Jupyter notebook 6.4.0</li>
</ul>

			<hr/>	
		
	</div>
	
	
	
	
	
<!-- Image -->
	<image src = "/assets/images/project_yagu1.jpg" alt="">


																							
<!--video-->
	<div class = "inner">
		<span class="image fit">
<iframe  width="1215" height="683" src="https://www.youtube.com/embed/3qGf2XQnQCM" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
			</span>										
	</div>
