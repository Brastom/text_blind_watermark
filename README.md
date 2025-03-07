# text_blind_watermark

Put message(blind watermark) into a text. so that the message is invisible, and the changes of the text are not perceptible.

[![PyPI](https://img.shields.io/pypi/v/text_blind_watermark)](https://pypi.org/project/text_blind_watermark/)
[![Build Status](https://app.travis-ci.com/guofei9987/text_blind_watermark.svg?branch=main)](https://app.travis-ci.com/guofei9987/text_blind_watermark)
[![codecov](https://codecov.io/gh/guofei9987/text_blind_watermark/branch/main/graph/badge.svg?token=85EAN4IVM6)](https://codecov.io/gh/guofei9987/text_blind_watermark)
[![License](https://img.shields.io/pypi/l/text_blind_watermark.svg)](https://github.com/guofei9987/text_blind_watermark/blob/master/LICENSE)
![Python](https://img.shields.io/badge/python->=3.5-green.svg)
![Platform](https://img.shields.io/badge/platform-windows%20|%20linux%20|%20macos-green.svg)
[![stars](https://img.shields.io/github/stars/guofei9987/text_blind_watermark.svg?style=social)](https://github.com/guofei9987/text_blind_watermark/)
[![fork](https://img.shields.io/github/forks/guofei9987/text_blind_watermark?style=social)](https://github.com/guofei9987/text_blind_watermark/fork)
[![Downloads](https://pepy.tech/badge/text_blind_watermark)](https://pepy.tech/project/text_blind_watermark)


- Video demo：[https://www.bilibili.com/video/BV1m3411s7kT](https://www.bilibili.com/video/BV1m3411s7kT)
- Online demo: [https://www.guofei.site/pictures_for_blog/app/text_watermark/v1.html](https://www.guofei.site/pictures_for_blog/app/text_watermark/v1.html)
- **中文 readme** [README_cn.md](README_cn.md)
- **Source code:** [https://github.com/guofei9987/text_blind_watermark](https://github.com/guofei9987/text_blind_watermark)


Can be used in 
- [x] Wechat
- [x] dingding
- [x] zhihu.com 
- [x] ...

## How to Use

install

```bash
>pip install text_blind_watermark
```

### embed message into text:

```python
from text_blind_watermark import TextBlindWatermarkThin

password = '20190808'
watermark = 'github.com/guofei9987'
text_blind_wm = TextBlindWatermarkThin(password=password)

wm = text_blind_wm.embed(watermark=watermark)
# This is example，you can put wm everywhere
text_embed = '这句话中有盲' + wm + '水印，你能提取出来吗？'
print(text_embed)
```


### extract message from text

```python
text_blind_wm_new = TextBlindWatermarkThin(password=password)
wm_extract = text_blind_wm_new.extract(text_embed)
print('提取内容：', wm_extract)
```

>github.com/guofei9987

## Method 2 is more robust

### Alice Put her text watermark into a text:

```python
from text_blind_watermark import TextBlindWatermark

watermark = "绝密：两点老地方见！"
text = "这句话中有盲水印，你能提取出来吗？" * 16
password = "20190808"

twm = TextBlindWatermark(password=password)
twm.read_wm(watermark=watermark)
twm.read_text(text=text)
text_embed = twm.embed()

print("打上盲水印之后:")
print(text_embed)
```

Then, you can paste this text to where you need.



### Bob Extract the invisible watermark

```python
from text_blind_watermark import TextBlindWatermark
password = "20190808"

twm_new = TextBlindWatermark(password=password)
wm_extract = twm_new.extract(text_embed)
print("解出的盲水印：")
print(wm_extract)
```

