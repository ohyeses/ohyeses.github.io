---
title: 머신러닝과 딥러닝을 활용한 선수연봉 예측 서비스
layout: post
---

<!-- Main -->
<div id="main09">
	
	
		<!-- 설명 -->
	<div>
		
		<h3>Team : *오예린, 송은진, 김동식, 윤대원 </h3>
	<h3>개발 일정 : <strong><i>2021.04.21 ~ 05.21</i>  </strong></h3>
	<br>
			
		<h3>기획의도</h3>
		<ul>
					<li>프로야구에서 투수가 차지하는 비중은 날이 갈수록 높아지고 있다. 따라서 매우 중요한 위치에 있는 투수들의 연봉은 반드시 능력을 제대로 반영하여 보다 객관화해서 정해야만한다.</li>
					<li> KBO에서 고과평점으로 객관적인 판단을 한다지만 연봉이 높아질 수록 연봉 협상과 관련된 문제가 많이 발생한다.</li>
					<li>이러한 이유로 한국 프로야구 투수들의 경기력 결과와 연봉간의 패턴분석은 중요한 의의를 가진다.</li>

		</ul>
		
		
			<hr/>
		
		<h3>목표</h3>
				<ul>
			<li>KBO 투수들의 경기력과 연봉과의 관계를 알아본다.</li>
			<li>연봉에 중요한 영향을 미치는 경기력 요소를 이용하여 회귀분석을 통해 작년연봉과 올해연봉을 토대로 선수별 연봉정보를 예측하여 시각화를 한다.</li>
		</ul>
			<hr/>
		
				<h3>개발과정</h3>
			데이터 수집 > 데이터 가공 > 모델 선택 > 학습 > 평가 > 웹을 통한 시각화
		
			<hr/>
		
			<h3>데이터 수집</h3>
		<ul>
			<li>야구 통계 사이트 <a href="statiz.co.kr">statiz</a>에 투수들의 연봉과 경기력을 크롤링 하였다.</li>
		</ul>
		
		<hr />
		
		<h3>데이터 가공 및 전처리</h3>
		<ul>
			<li> 연봉 예측이 어려운 외국인 선수, FA 자유계약 선수 제외</li>
			<li>투수 별 연봉 데이터 + 경기력 데이터를 합쳐 .csv 형태로 가공 </li>
		</ul>
		
		<hr />
		<h3>상관 관계</h3>
		<ul>
			<li>관관계 분석 결과, 홈런과 평균자책점(방어율, ERA)이 가장 상관관계가 높았다.</li>
			<li>따라서 연봉과 경기력이 어느정도 상관관계가 있음을 확인 할 수 있었다.</li>
		</ul>

				<hr />
		<h3>모델 학습 및 평가</h3>
		<ul>
			<li>개인 선수 별 연봉을 예측하기 위해 회귀 모델을 사용하였다.</li>
			<li>회귀 모델 중 LinearRegression (선형 회귀) 모델로 선택하였다.</li>
			<li>Linear Regression 모델 학습 후 평가 시 86% 대의 준수한 평가 결과가 나왔다. </li>

		</ul>
		
		
		<hr />
		<h3>FLASK 연동 및 시각화</h3>
		<ul>
			<li>100명이 넘는 투수들의 작년 연봉, 예측 연봉, 실제 연봉 분석 결과를 쉽게 이해 할 수 있게 그래프로 시각화하였다.</li>
			<li>웹에서 각 구단 별 투수 이름을 선택하여 투수 이름을 머신러닝 모델에 입력하고 산출된 결과값을 웹에 다시 나타내기 위해 <br> FLASK를 이용하였다. </li>

		</ul>
		

		

	<hr/>	
	</div>
	
	

	
<!-- Image -->
	<image src = "/assets/images/project_yagu2.jpg" alt="">


																							
<!--video-->
	<div class = "inner">
		<span class="image fit">
<iframe  width="1215" height="683" src="https://www.youtube.com/embed/7AFCwXnNCgg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
			</span>										
	</div>
