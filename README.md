[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/XBdtJbIm)
[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=19683849&assignment_repo_type=AssignmentRepo)
## 第6講目の演習課題
### 課題6-1．eStat-APIを使って、人口推計以外のデータを取得するプログラム kadai6-1.py を作成せよ。
import requsets
APP_ID = "eba5c62f2b03ae8d98d72a05c855119b08303429"
API_URL  = "https://api.e-stat.go.jp/rest/3.0/app/json/getStatsData"

params = {
    "appId": APP_ID,
    "statsDataId":"0000020201",
    "cdArea":"12101,12102,12103,12104,12105,12106",
    "cdCat01": "A1101",
    "metaGetFlg":"Y",
    "cntGetFlg":"N",
    "explanationGetFlg":"Y",
    "annotationGetFlg":"Y",
    "sectionHeaderFlg":"1",
    "replaceSpChars":"0",
    "lang": "J"  # 日本語を指定
}
#response = requests.get(API_URL, params=params)
response = requests.get(API_URL, params=params)
# Process the response
data = response.json()
print(data)

### 課題6-2．世の中のオープンデータを調査し、そこから一つ選んで、データを取得するプログラム kadai6-2.py を作成せよ。

import pandas as pd
import matplotlib.pyplot as plt

# ExcelファイルのURL
url = 'https://www.pref.chiba.lg.jp/kankou/toukeidata/kankoukyaku/r4-2.html'

# Excelファイルを読み込む
df = pd.read_excel(url, sheet_name='観光入込客数')

# 月別の観光客数を集計
monthly_data = df.groupby('月')['観光客数'].sum()

# グラフを描画
monthly_data.plot(kind='bar', figsize=(10, 6))
plt.title('月別観光客数（千葉県）')
plt.xlabel('月')
plt.ylabel('観光客数（万人）')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()

### 課題提出方法（期限：6/15）
* 随時、作業内容をコミットして、自分の課題リポジトリに履歴を残すこと。
* 上記の課題が完成したら、プルリクエストを使って提出すること。
* 教員、TA/SAが確認したらフィードバックする。
