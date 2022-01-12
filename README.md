# CNN으로 음성 데이터 다루기

### 악기 분류, 음계 분류 by CNN
+ 오디오 파일로 무슨 악기인지 분류 (129가지)
+ 오디오 파일로 어떤 음인지 분류 (50가지)
+ 주어진 오디오의 악기를 다른 악기로 변환 (CycleGAN 사용) -> 미완성

#### 파일 소개

+ wav_to_csv_v1.ipynb : wav 파일을 list(np.array)형태로 변환하는 전처리 파일
  + output.wav는 MIDI 오픈 소스로 생성된 파일로 2초마다 각 악기, 각 음이 연주되는 파일로 이 파일을 잘라서 사용합니다.
  + wav_to_csv_v1.ipynb에서 wav파일을 변환할 때 noise를 추가하면서 데이터셋의 크기를 늘렸습니다.
  + pickling을 통해서 audio_df_02_spt, audio_df_02_ins, audio_df_02_note_list, audio_df_02(csv 파일)을 만들었습니다.

+ wav_to_df_2.ipynb : wav파일을 list(np.array, csv 형태로 변환하는 전처리 파일) - kaggle에서 받은 wav 파일 적용
  + 해당 wav파일은 길이가 일정하지 않기 때문에 한 파일당 2초만 잘라서 list 형식으로 변환했습니다.
  + 악기는 동일, 음이 변하기 때문에 음계 분류에는 적합하지 않는 데이터셋입니다.
  + pickling을 통해서 audio_df_cleaned(csv 파일)을 만들었습니다.

+ wav_to_cq.py : 참고 블로그에서 그대로 받아서 실행한 파일 ( 사용하지 않았다 )

+ classify_instrument.ipynb : 악기를 분류하는 모델 생성 및 학습하는 파일
  + pickling을 통해서 classify_ins_model.pickle 생성 ( model )

+ classify_note.ipynb : 음계를 분류하는 모델 생성 및 학습하는 파일
  + pickling을 통해서 classify_note_model.pickle 생성 ( model )

+ audio_CycleGAN.ipynb :  주어진 오디오의 악기를 다른 악기로 변환
  + 피아노 오디오를 기타 오디오로 변환하는 것이 목표
  + CycleGAN 적용.
  + 무겁기 때문에 local (jupyter) 환경 권장
-----------------------

pickle 파일은 위의 ipynb 파일 실행을 통해서 얻기 바랍니다!
colab 실행, 'GPU 사용'!
#### 참고

> [1] WIKI. (2019. 10. 27.). [일반 MIDI] https://ko.wikipedia.org/wiki/%EC%9D%BC%EB%B0%98_MIDI
> [2] ∫2tdt=t²+c. (2019. 12. 2.). [심심해서 해보는 딥러닝을 이용한 악기 소리 분류]. https://bab2min.tistory.com/642
> [3] Hyunlee103. (2020. 3. 16.). [[논문] TIMBRETRON: A WAVENET(CYCLEGAN(CQT(AUDIO)))PIPELINE FOR MUSICAL TIMBRE TRANSFER(2019)]. https://hyunlee103.tistory.com/41
> [4] Muhammad Ardi. (2020. 08. 18.). [Musical Instrument Sound Classification using CNN]. https://becominghuman.ai/musical-instrument-sound-classification-using-cnn-part-2-2-aaa668a3862a
> [5] tensorflow. (2021.03.22). [CycleGAN]. https://www.tensorflow.org/tutorials/generative/cyclegan?hl=ko
> [6] codestates. (). [N434_Reference_CycleGAN]. https://github.com/codestates/ds-section4-sprint3/N434/N434_Reference_CycleGAN.ipynb
> [7] 아무튼 워라밸. (2019.12.19). [머신러닝 분류 모델의 성능 평가 지표 Accuracy, Recall, Precision, F1]. https://hleecaster.com/ml-accuracy-recall-precision-f1/ 
> [8] 긴긴인생. [인터넷,신문,논문 참고문헌 표기법 알아보기]. https://lonlonglife.tistory.com/281