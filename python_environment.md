## Pythonの環境方法について
PythonはOSによってインストール方法が異なります。
また、それぞれで通常の構築方法に加えAnaconda(Miniconda)を利用した環境構築方法、Dockerを利用した環境構築方法があります。
Pythonの環境構築については迷ったら、[こちらの環境構築ガイド](https://www.python.jp/install/install.html)を閲覧すると良いでしょう。

### 各OSにおけるPythonのインストール方法
1. Windows環境におけるpythonのインストール方法
   [https://www.python.jp/install/windows/install.html]
2. Ubuntu環境におけるPythonのインストール方法
   [https://www.python.jp/install/ubuntu/index.html]
3. MacにおけるPythonのインストール方法
   [https://www.python.jp/install/macos/install_python.html]

### その他のPythonのインストール方法
1. Anaconda(miniconda)を利用したPython環境の構築方法
   Anacondaは、データサイエンス向けの環境を提供するプラットフォームのことで、Pythonだけではなく、
   データサイエンス系のライブラリ(numpy, pandas)や開発環境(spyder、jupyter notebook)等をインストールするだけで使用することができます。Condaというパッケージ管理ツールを用いて、仮想環境の構築を行うことができます。

   pipとcondaの混在には十分に注意しましょう。基本的には、condaを用いる際には、pipかcondaのどちらかしか使わないようにすると良いでしょう。

   - [Windows版のインストール方法](https://www.python.jp/install/anaconda/windows/install.html)
   - [MacOS版のインストール方法](https://www.python.jp/install/anaconda/macos/install.html)
   - [Linux版のインストール方法](https://www.python.jp/install/anaconda/unix/install.html)

2. Dockerを利用した環境方法(後日追記予定)

### 仮想環境について

#### 仮想環境とは
後日追記

#### 仮想環境の種類について
詳細は後日追記
1. conda
2. venv
3. virtualenv
4. pyenv
5. pipenv
6. poetry
7. Docker

個人的にはWindows環境では、まずvenvを使用します。Mac環境では、初期のM1チップでconda-forgeを使わざるを得ない状況であったため、その名残でminicondaを使用しています。Dockerは、OSによらない環境構築ができる点がメリットです。ただし、Docker自体のインストールがOSに依存することと、非常に重いことには注意しましょう。

#### 参考
仮想環境に関する説明 : [https://www.python.jp/install/windows/venv.html]

[目次に戻る](./index.md)