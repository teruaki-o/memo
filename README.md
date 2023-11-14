# memo

## このwarningを消したい
```
lib/python3.9/site-packages/urllib3/__init__.py:34: NotOpenSSLWarning: urllib3 v2.0 only supports OpenSSL 1.1.1+, currently the 'ssl' module is compiled with 'LibreSSL 2.8.3'. See: https://github.com/urllib3/urllib3/issues/3020
```
これで消えた。
```
$ pip3 install urllib3==1.26.15
```

## mac book のGPUを学習に使いたい
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
