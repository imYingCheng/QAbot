# 利用IR作法和Web Crawler作法實作QA機器人

## IR作法(QAbot_IR.ipynb)

### Build Inverted Index
對繁體中文wiki的RDD Format建立反向索引。<br>
繁體中文wiki的RDD Format: <a>https://drive.google.com/file/d/1i9NhH1rq6KZQBAXspscVrehR9Ketd-0_/view?usp=share_link</a>

### Load Inverted Index
載入建好的反向索引。

### Question Solving

- <b>Method 1: Pure Term Frequency</b><br>
  計算每個選項的詞頻，並算出此選項在同一問題的三個選項裡占多少比例，占比最大的即為Method 1所提供的答案。
- <b>Method 2: TF-IDF</b><br>
  計算問題裡每個單詞的TF-IDF score，如果大於給定的臨界值(QUESTION_KEYWORD_THRESHOLD)，就將其儲存為關鍵字，接著計算問題中的選項各與這些關鍵字的關聯性分數總和，並算出比例，占比最大的即為Method 2所提供的答案。
- <b>Integrate Method 1 & Method 2</b><br>
  解題開始時，程式會逐題利用Method 1和Method 2算出答案，若Method 1和Method 2: <br>
  1. 所提供的答案不同: 發出"Different Answer"的警告<br>
  2. 算出的最大答案百分比皆為零: 發出"No Data"的警告<br>
  3. 算出的最大答案百分比皆小於給定的臨界值(CONFIDENCE): 發出"Low Confidence"的警告
- <b>Method 3: Human Take Control</b><br>
  預設為回傳Method 2所提供的答案，若警告訊息為"No Data"或"Low Confidence"，即將題目記錄下來，並由人工進行二次判定來修改答案。
 
## Web Crawler作法(QAbot_WebCrawler.ipynb)
將問題丟入google搜尋，並擷取第一個搜尋結果的標題，若標題中出現某一選項的字詞，該選項即為答案。

## 結合IR作法和Web Crawler作法
以Web Crawler作法為主，找不到答案的題目再用IR作法補足，最後結合的答案即為本QAbot對整份試題的回答。
