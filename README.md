# Prediction-of-Mental-Disorder
social media와 deel learning을 이용한 mental disorder 예측 


# 연구 목표
1. Reddit Data를 활용해 다양한 정신질환을 분류하는 것
2. 정신질환 별 언어학적 특징을 도출하는 것   

# 세부 주제
1. 정신질환 하위 Reddit data를 활용해 다양한 정신질환을 분류
2. 정신질환 하위 Reddit data가 아닌 게시글을 활용해 다양한 정신질환을 분류
3. 정신질환 하위 Reddit data에 글을 작성하기 이전의 게시글을 활용해 다양한 정신 질환을 분류   

## 세부주제1
: 정신질환 하위 Reddit data를 활용해 다양한 정신질환을 분류   

### 연구질문
: 정신질환과 관련된 주제의 게시글을 이용해 정신질환을 예측할 수 있을까?   
  
### 데이터 수집
Reddit pushshift API을 이용해 2015년 9월 23일 ~ 2020년 9월 23일까지의 정신질환 하위레딧 게시글을 수집힌다.   

**데이터 종류**    
```
1) adhd_origin.csv: subreddit이 adhd인 경우   
2) anxiety_origin.csv: subreddit이 anxiety인 경우     
3) bipolar_origin.csv: subreddit이 bipolar인 경우   
4) depression_origin.csv: subreddit이 depression인 경우
5) schizo_origin.csv: subreddit이 schizophrenia인 경우 
6) non-health.csv: subreddit이 subreddit이 fitness, jokes, meditation, parenting, relationship, teaching인 경우
```

**데이터 샘플**
| 	 |subreedit	|author	|title	|content	|date	|
|----|------|---------|---------------|---------|-----------|    


**데이터 사이즈**
| 	 |ADHD	|Anxiety	|Bipolar	|Depression	|Depression	|non-health    |
|----|------|---------|---------------|---------|-----------|--------------|
|size|256065|298852   |162986	|720434	|60009	|425346	|    

### feature 추출
**감정분석**

**감정분류**

**토픽모델링**
- 연구 방법: LDA, LSA

**가독성**
