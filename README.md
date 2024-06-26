# 概要

変数置き換えモデルを用いた英日両文に適用可能なリーダビリティ判定ツールです。  
字種分割にはdivide-char-typeを, 音節数計算にはcount-syllableを使用しています。  
戻り値は全体、段落ごと、センテンスごとのリーダビリティ値が取得できるようにしています。  


# 変数置き換えモデルの指標

jFRE = 206.835-(1.015×ASL)-(84.6×ASW)  
jFKG = (0.39×ASL)+(11.8×ASW)-15.59  
jARI = (4.71×ACW)+(0.5×ASL)-21.43  
jCLI = (5.88×ACW)-(29.6/ASL)-15.8  
jSMOG = 1.031√(30×PS)+3.1291  

*ASL = 字種分割語数/センテンス数  
*ASW = 音節数・漢字の連なり数/字種分割語数  
*ACW = シャノン情報量に基づく重み/字種分割語数  
*PS = 英語3音節・漢字3字以上の字種分割語数/センテンス数  
  
シャノン情報量に基づく重みは、英数字（36種類）を1として、ひらがな（88種類）をlog(1/88)/log(1/36)で，カタカナ（141種類）をlog(1/141)/log(1/36)で、漢字（20898種類）をlog(1/20898)/log(1/36)でそれぞれ重み付けする.  
  
# セットアップ
```
pip install calculate-readability
```

# アンインストール
```
pip uninstall calculate-readability divide-char-type count-syllable nltk
```

# 使用方法
```
from calculate_readability import calculate_readability

data = calculate_readability("今日の天気は晴れです。明日は曇りです。")

print(data["jfre"])
```

 
# 論文

赤木信也ら：変数置き換えモデルを用いた医療関連文書の可読性分析,  
バイオメディカル・ファジィ・システム学会誌 19 (1), 19-27, 2017  
https://cir.nii.ac.jp/crid/1391975276374773248  

別途、論文化、または、学会発表を予定してます。  


# ライセンス
- calculate-readability
	- Python Software Foundation License
	- Copyright (C) 2024 Shinya Akagi
- divide-char-type
	- Python Software Foundation License
	- Copyright (C) 2023-2024 Shinya Akagi
- count-syllable
	- Python Software Foundation License
	- Copyright (C) 2024 Shinya Akagi
- nltk
	- Apache License 2.0
	- Copyright (C) 2001-2023 NLTK Project
- cmudict
	- BSD License
	- Copyright (C) 1998 Carnegie Mellon University
  
