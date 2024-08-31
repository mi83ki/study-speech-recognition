# study-speech-recognition

リアルタイム文字起こしの勉強です。

## ライブラリのインストール

```bash
poetry install
```

## マイク入力のチャンネルを指定する

```bash
vi study_speech_recognition/study_speech_recognition.py
```

以下の値を適切な値に変更する。\
※一度サンプルを実行するとマイク入力のリストがターミナルに出力されるので、それを見て値を修正するとよい。

```python
INPUT_DEVICE_INDEX = 1  # マイクのチャンネル
```

## サンプルの実行

```bash
poetry run python study_speech_recognition/study_speech_recognition.py
```

## 参考にさせていただいたURL

[PythonでSpeechRecognitionを使ってリアルタイム文字起こし【Windows】](https://qiita.com/KENTAROSZK/items/3f393c000c2492034c1b)
