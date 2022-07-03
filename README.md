# DeepSpeech2-based-SpeechRecognition
DeepSpeech2 기반 항공 교신 상에서의 음성 인식 성능 개선

Member : 김지후, 이민정


# Introduction
일반적인 음성 인식기는 노이즈가 많은 관제 음성에서 인식률이 매우 떨어지므로, 관제소와 파일럿이 교신하는 특정한 상황인 항공 교신 상에서 특히 더 좋은 성능을 내는 음성 인식기를 만들어보고자 하였다.


# Purpose
기존의 DeepSpeech2를 기반으로 개선된 새로운 음성인식 모델을 설계하고 이를 항공 교신 상황에 적용하여 가장 최적의 성능을 보이는 모델을 확인한다.


# Comparative model
<img width="561" alt="스크린샷 2022-07-03 오후 11 58 33" src="https://user-images.githubusercontent.com/60657536/177045675-4ee01646-7302-4e64-8273-f860f420cb8a.png">

- RNN 계열의 LSTM, GRU 사용
- 기존의 모델보다 더 적은 개수의 layer를 사용하여 더 적은 계산량을 필요로 하는 새로운 모델 제시

# Data processing
- Low Pass Filter , High Pass Filter 적용하여 노이즈 제거
- 30분 가량의 raw data를 공백 단위로 분리
- Air english를 기반으로 약 800개 음성 데이터의 스크립트 작성
- 항공 교신 용어 외의 특정 지명, 항공사 이름 등의 인식을 위해 일상 대화 데이터셋 LibriSpeech ASR corpus와 결합하여 적용
- Train : Test = 8 : 2 로 분리


# Conclusion
### WER analysis
<img width="365" alt="스크린샷 2022-07-04 오전 12 18 10" src="https://user-images.githubusercontent.com/60657536/177046159-2b004c5c-cb37-4e18-93eb-ec58ecf7027e.png">
전체적으로 Mel-Spectrogram 기반 모델이 MFCC 모델보다 낮은 오류율을 보였으며, LSTM layer를 3개 사용한 모델이 가장 우수한 성능을 보임
