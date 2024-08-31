<!-- omit in toc -->
# study-speech-recognition

リアルタイム文字起こしの勉強です。

<!-- omit in toc -->
## 目次

- [1. SpeechRecognition](#1-speechrecognition)
  - [1.1. ライブラリのインストール](#11-ライブラリのインストール)
  - [1.2. マイク入力のチャンネルを指定する](#12-マイク入力のチャンネルを指定する)
  - [1.3. サンプルの実行](#13-サンプルの実行)
  - [1.4. 参考にさせていただいたURL](#14-参考にさせていただいたurl)
- [2. faster-whisper](#2-faster-whisper)
  - [2.1. サンプルの実行](#21-サンプルの実行)
  - [2.2. エラー：cudnn\_ops\_infer64\_8.dllがない](#22-エラーcudnn_ops_infer64_8dllがない)
  - [2.3. エラー：OpenMP](#23-エラーopenmp)
  - [2.4. 参考にさせていただいたURL](#24-参考にさせていただいたurl)

## 1. SpeechRecognition

Google SpeechRecognitionを使用する例。

### 1.1. ライブラリのインストール

```bash
poetry install
```

### 1.2. マイク入力のチャンネルを指定する

```bash
vi study_speech_recognition/study_speech_recognition.py
```

以下の値を適切な値に変更する。\
※一度サンプルを実行するとマイク入力のリストがターミナルに出力されるので、それを見て値を修正するとよい。

```python
INPUT_DEVICE_INDEX = 1  # マイクのチャンネル
```

### 1.3. サンプルの実行

```bash
poetry run python study_speech_recognition/study_speech_recognition.py
```

### 1.4. 参考にさせていただいたURL

[PythonでSpeechRecognitionを使ってリアルタイム文字起こし【Windows】](https://qiita.com/KENTAROSZK/items/3f393c000c2492034c1b)

## 2. faster-whisper

ローカル環境でリアルタイム文字起こしを行う

### 2.1. サンプルの実行

```bash
poetry run python study_faster_whisper_b/main.py
```

### 2.2. エラー：cudnn_ops_infer64_8.dllがない

以下のエラーが発生する

```bash
Could not locate cudnn_ops_infer64_8.dll. Please make sure it is in your library path!
```

以下のURLから次のファイルをダウンロードしてリポジトリのルートディレクトリに置く。（Windowsの場合の例）

<https://github.com/Purfview/whisper-standalone-win/releases/tag/libs>

ダウンロードするファイル

- cuBLAS.and.cuDNN_CUDA11_win_v4.7z
- cuBLAS.and.cuDNN_CUDA12_win_v1.7z

### 2.3. エラー：OpenMP

以下のようなエラーが発生する

```bash
OMP: Error #15: Initializing libiomp5md.dll, but found libomp140.x86_64.dll already initialized.
OMP: Hint This means that multiple copies of the OpenMP runtime have been linked into the program. That is dangerous, since it can degrade performance or cause incorrect results. The best thing to do is to ensure that only a single OpenMP runtime is linked into the process, e.g. by avoiding static linking of the OpenMP runtime in any library. As an unsafe, unsupported, undocumented workaround you can set the environment variable KMP_DUPLICATE_LIB_OK=TRUE to allow the program to continue to execute, but that may cause crashes or silently produce incorrect results. For more information, please see http://www.intel.com/software/products/support/.
```

暫定対策

```bash
$env:KMP_DUPLICATE_LIB_OK = "TRUE"
```

### 2.4. 参考にさせていただいたURL

[[ローカル環境] faster-whisperを利用してリアルタイム文字起こしに挑戦](https://qiita.com/reriiasu/items/920227cf604dfb8b7949)
[Whisperのlarge-v3モデルでリアルタイム文字起こしをしてみる](https://marimox.net/faster-whisper-large-v3)
