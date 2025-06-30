
 
 Natural Language Processing with Disaster Tweets 
- [submission](https://www.kaggle.com/code/onurmarkxxx/notebook034bbf97c8?scriptVersionId=247953933) / 0.80049

1. 데이터 로드
   
![스크린샷 2025-06-30 오후 8 00 39](https://github.com/user-attachments/assets/f94149fa-efb8-4a90-af2e-3454c05b91b3)

3. 벡터나이저 사용
   
![스크린샷 2025-06-30 오후 8 01 00](https://github.com/user-attachments/assets/7966e9b8-e027-4e1e-99fb-791bdf2ed447)
- sklearn.feature_extraction.text 가 제공하는 TfidfVectorizer를 이용해 가장 높은 빈도로 사용된 단어 10000개를 BoW의 형태로 임베딩
- 이때 stop_words='english'로 영어 불용어(the, is, of 등)를 제거함
- TfidfVectorizer를 사용한 이유? 단순 빈도가 아니라 단어의 중요도를 반영하는 TF-IDF 가중치를 사용해, 모델이 중요 단어에 더 집중하고 불필요한 단어의 영향력을 줄일 수 있기 때문이다.

  
- 벡터나이저 사용 후 fit_transform 함수 호출
- 이때 fit_transform 함수는 train data를 모델에 학습시키는 fit() 함수와 데이터의 형태를 변환하는 transform()함수의 기능을 모두 하는 함수 ==> 데이터를 알맞은 형태로 변환 후 바로 학습까지 시킴

3. 로지스틱 회귀

 ![스크린샷 2025-06-30 오후 8 06 49](https://github.com/user-attachments/assets/13ebafa8-0ce6-46d4-a8ba-285b5537060f)

- sklearn.linear_model이 제공하는 LogisticRegreesion을 사용
- 로지스틱 회귀를 사용한 이유? 로지스틱 회귀는 이진 분류에서 출력 확률값을 sigmoid 함수로 변환해 0 또는 1을 예측하는 데 적합하며, 해당 태스크는 예측 결과 값이 1과 0 두가지인 이진 분류 문제이기 때문이다.
- 이때 max_iter = 1000으로 사용해 최대 1000번 학습이 진행되도록함

4. 모델 정확도 확인

![스크린샷 2025-06-30 오후 8 07 55](https://github.com/user-attachments/assets/65d9d8c6-c1bb-4281-92f3-6357aadecb56)

- sklearn.model_selection이 제공하는 cross_val_score 사용
- cv = 5, 총 다섯번의 교차검증 실시 후 scores에 저장, scores.mean()을 통해 정확도 확인

5. vectorizer 사용해 데이터 변환
6. 변환된 데이터를 모델을 통해 예측
7. 제출 데이터 생성
   
![스크린샷 2025-06-30 오후 8 08 20](https://github.com/user-attachments/assets/499f8623-3271-4a98-b7e3-f3253740372e)

