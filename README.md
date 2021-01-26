# Korean_TTS_Intro

**딥러닝 기반 종단간(end-to-end) TTS 시스템은**  
**텍스트에서 스펙트로그램을 생성하는 Text2Mel 과정과**  
 - Tacotron2, Transformer, FastSpeech, FastSpeech2, FastPitch 등  
**스펙트로그램에서 음성신호를 합성하는 보코더 등 두 가지 과정으로 구성**  
 - WaveNet, WaveRNN, WaveGlow, ParallelWaveGAN, Multiband_MelGAN 등  

**학습에 사용한 한국어 음성 DB 출처**
[음원 다양화를 통하여 로봇의 감정 및 개성을 표현할 수 있는 대화음성합성 원천기술 개발](https://github.com/emotiontts/emotiontts_open_db/tree/master/Dataset/SpeechCorpus/Main/main/lmy)  

**한국어 텍스트를 입력으로 받기 위해서**  
**한국어 G2P(Grapheme-to-Phoneme) 변환 모듈 사용**
  [Sogang G2P](https://github.com/emotiontts/emotiontts_open_db/tree/master/Codeset/SogangG2P)        

**영어 Text2Mel 오픈소스에서 다음을 수정**   
```python  
# hparams.py
  text_cleaners=['basic_cleaners']
# cleaners.py
  def basic_cleaners(text):
    text = convert_to_ascii(text) 
    #text = lowercase(text) 
    text = collapse_whitespace(text)
    return text
# symbols.py
  _pad        = '_'
  _eos        = '~'
  # G2P 모듈에서 사용하는 phoneme set 정의
  _characters = 'gndlmbsjqktphxwfczAoOUuEae>0123456789[]<GNDLMB,.? ' # KCH
  symbols = [_pad, _eos] + list(_characters) 
```
