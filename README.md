# memo

## このwarningを消したい
```
lib/python3.9/site-packages/urllib3/__init__.py:34: NotOpenSSLWarning: urllib3 v2.0 only supports OpenSSL 1.1.1+, currently the 'ssl' module is compiled with 'LibreSSL 2.8.3'. See: https://github.com/urllib3/urllib3/issues/3020
```
これで消えた。
```
$ pip3 install urllib3==1.26.15
```

## mac book のGPUをLLM用に使いたい

参考：https://zenn.dev/hidetoshi/articles/20220731_pytorch-m1-macbook-gpu

torch(pytorch) 2.0.0 以降

```
>>> import torch
>>> torch.backends.mps.is_available()
True
```

なら使える。

```
parser = ArgumentParser()
parser.add_argument('--device', type=str, default='mps',
                    choices=['cpu', 'mps'])
args = parser.parse_args()
device = torch.device(args.device)
```
cuda を選ぶところをmpsにすればいい。

## Amazon、review のデータセット公開やめたってよ。

https://github.com/huggingface/datasets/issues/6109

```
Indeed, the source data files are no longer available. We have contacted the authors of the dataset and they report that Amazon has decided to stop distributing the multilingual reviews dataset.

We are adding a notification about this issue to the dataset card.
```

ライセンス的に使うとアウト。

https://huggingface.co/datasets/SetFit/amazon_reviews_multi_ja

> You may not resell, republish, or make any commercial use of the Reviews Corpus or its contents, including use of the Reviews Corpus for commercial research, such as research related to a funding or consultancy contract, internship, or other relationship in which the results are provided for a fee or delivered to a for-profit organization. 

## mac のG++ Linuxのと違う件

https://qiita.com/yoskeoka/items/541b6a4260487fbc2c0f

ずっと Windows か Linux だったから、そうなんだ、という。 ext/stdio_filebuf.h がないって言われて初めて気づいた。


