<h1 align="center">octomap-python</h1>
<h4 align="center">Python binding of <a href="https://github.com/OctoMap/octomap">the OctoMap library</a>.</h4>

<div align="center">
  <a href="https://pypi.python.org/pypi/octomap-python"><img src="https://img.shields.io/pypi/v/octomap-python.svg"></a>
  <a href="https://pypi.org/project/octomap-python"><img src="https://img.shields.io/pypi/pyversions/octomap-python.svg"></a>
  <a href="https://github.com/wkentaro/octomap-python/actions"><img src="https://github.com/wkentaro/octomap-python/workflows/ci/badge.svg"></a>
</div>


## Installation

```bash
git clone --recursive https://github.com/robocip/octomap-python.git && cd octomap-python
python -m pip install .
```

pyenvなど仮想環境を使用している場合インストールに失敗することがある。
その場合は、

```bash
python setup.py install
```
とすること。

## 動作確認

上記のインストールだけだとライブラリ関連でエラーがでる場合がある。

下記を実行してみてエラーがでないか確認する。

```bash
echo "import octomap;print(octomap)" | python3
```

### ImportErrorがでる場合

```bash
ImportError: libdynamicedt3d.so.1.8: cannot open shared object file: No such file or directory
```
のエラーがでる場合は、ライブラリへのリンクパスが通っていません。

```bash
 find / -name libdynamicedt3d.so.1.8
```
を実行してライブラリの位置を見つけその結果を環境変数LD_LIBRARY_PATHにセットしてください。

## example

```bash
cd examples
python insertPointCloud.py
```

<img src="examples/.readme/insertPointCloud.jpg" height="200px" />

### ModuleNotFoundErrorがでる場合

```bash
ModuleNotFoundError: No module named 'trimesh'
```
などのpythonモジュールのインポートエラーがでる場合は

```bash
cd examples
python -m pip install -r requirements.txt
```
でインストールすること。

## フォーク元との違い


exampleでライブラリの問題が生じていたので使用するライブラリのversionを修正
・trimeshはversion4.0以降だと動かなかった（2024/6/21現在）4未満を使用すること
・pygletはversion2.0以降だと動かなかった（2024/6/21現在）4未満を使用すること

## Acknowledgement

This is a fork of [wkentaro/python-octomap](https://github.com/wkentaro/python-octomap).
