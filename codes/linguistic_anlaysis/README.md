

정신질환 서브레딧 데이터와, non-MH 서브레딧 데이터의 다양한 언어학적 특성을 도출하기 위해 [LIWC](http://liwc.wpengine.com/)를 모델로 삼아, 

[LIWC 의 기능을 제공하는 모듈](https://github.com/kbenoit/LIWCalike)을 이용하거나 직접 구현 하였다. 


<br>


## workflow

1. `EDA.ipynb`으로 각 subreddit의 데이터의 크기를 확인합니다.

2. `final_replace_LIWC.ipynb`와 `finally_liwc_alike.R`을 이용하여 언어학적 특징을 도출합니다. 

도출한 내용은 아래와 같습니다.

```
# with LIWC-alike,

1. Word Cound
2. Word Per Sentence
3. Word (more than Six letters)
4. Sentimental analysis 
5. Sentimental classification


# with my own, 

6. pronouns analysis 
7. Time-oriented analysis 

```

  - Sentimental classificatino(5)을 위해 [emotional wheel](https://www.healthline.com/health/emotion-wheel)을 바탕으로, [empath](https://github.com/Ejhfast/empath-client) module을 이용하여 자체적인 sentimental lexicon 구축을 시도했지만, `LIWC-alike`에서 제공하는 sentimental classification에서 [해당 내용뿐 아니라 감정의 격양 정도까지 반영한 lexicon](https://rdrr.io/github/kbenoit/quanteda.dictionaries/man/data_dictionary_NRC.html)을 이용하였음을 고려하여, LIWC-alike를 채택하였습니다. 
  

3. `final_statistic_analysis.ipynb`를 이용해 통계학적 의미를 도출합니다. 


  1) 1. ~ 7. 의 linguistic features 에서, 각 subreddit끼리의 normality check (based on D’Agostino and Pearson’s)
 
  2) 1. ~ 7. 의 linguistic features 에서, 각 subreddit끼리의 Homogeneity of variance test (with levene test)

  3) 1), 2) 의 결과에 따라 어떤 통계 방법을 이용할지 결정
  
  4-1) 
     [1] 전체 data에 대해 Kruskal-Wallis (KW) test
    
      
   * 대부분 normality, homogeneity of variance test를  모두 만족하지 못했기 때문
    
    
     [2] 추가적으로 두 subreddit끼리 Mann–Whitney U test
     
     
  4-2)  t-test (heteroscedasticity)
    
   * normality를 만족하지 못하더라도, central limit theorem에 의해 sample size가 큰 경우 normal distribution으로 추정 가능. 따라서 이를 이용해 이분산 t-test를 수행 
        
  4-3) chi-square test with Word Count
  
   *  Word Count는 nominal data이므로, nonMH를 기준으로 같은 분포를 가지고 있는지를 chi-square로 검정 
     
<br>

4. 이러한 분석결과를 잘 보여줄 수 있도록 `barplot with error bar`, `boxplot` 등으로 시각화하였습니다. 



<br>

5. 같은 방법으로, 정신질환 subreddit의 author가 해당 정신질환을 인지하기 전과 후의 작성 게시글에서의 언어학적 차이를 비교분석하였습니다. 
