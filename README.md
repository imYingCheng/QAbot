# 利用IR和Web Crawler實作QA機器人 (README待更新)

## IR做法(create_final_ans_1.ipynb)

### Build Inverted Index
對繁體中文wiki的RDD Format建立反向索引。<br>
繁體中文wiki的RDD Format: <a>https://drive.google.com/file/d/1i9NhH1rq6KZQBAXspscVrehR9Ketd-0_/view?usp=share_link</a>

### Load Inverted Index
載入建好的反向索引。

### Question Solving

- <b>Method 1: Pure Term Frequency</b><br>
  計算每個選項的詞頻，並算出此選項在同一問題的三個選項裡占多少比例。
- <b>Method 2: TF-IDF</b><br>
  
- <b>Method 3: Human Take Control</b><br>

## Web Crawler做法(爬蟲1、2、3、create_final_ans_2.ipynb)

## 開始解題
