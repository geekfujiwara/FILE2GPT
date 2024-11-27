# FILE2GPT
事前学習無しで様々な帳票をデータ化します。

### FILE2GPT 登録アプリ (Power Apps キャンバスアプリ)

https://github.com/user-attachments/assets/04a4318a-4e13-4f29-906a-0c8291c7f6e3

### FILE2GPT 管理アプリ (Power Apps モデル駆動型アプリ)

https://github.com/user-attachments/assets/0ecff48d-a6b3-4553-a51d-52382748bd0f


>[!Note]
>利用したなどの感想やコメント、ご要望などございましたらギークフジワラのXまでお願いいたします！


## 前提条件
* Power Apps Premium ライセンスが必要です。
* 対応するファイルフォーマットはPNG, JPG, JPEG, BMP, TIFF, PDFです。
* PDFの場合、50ページまでが上限です。
* 対応するファイルサイズは最大25MBです。

## アーキテクチャ
* 事前学習無しで様々な帳票から意図を認識してAI Builder によりデータを構造化を行います。
* Power Apps により出力データをマッピングしDataverse に登録します。
* また、一括管理アプリとしてモデル駆動型アプリを利用できます。

![image](https://github.com/user-attachments/assets/d2352ccd-96d5-44b6-bbe2-3fd82a9fd5ee)

## インポート方法
ソリューションは[リリース](https://github.com/geekfujiwara/FILE2GPT/releases/tag/FILE2GPT)から取得できます。

入手したソリューションはPower Apps 作成者ポータルのソリューション画面からインポートを選択して、Zip形式のままアップロード、インポートを実行します。

![image](https://github.com/user-attachments/assets/1b04bad1-8bf8-4696-a1b6-f2aa0ee8ed0f)

インポート完了まで数分です。

インポートが完了しましたら、ソリューションを開きます。ソリューションはマネージドのタブに含まれています。

![image](https://github.com/user-attachments/assets/1a7821e9-ac25-4cd6-82cd-00774dad9bc2)

ソリューション内にモデル駆動型アプリとキャンバスアプリが含まれています。こちらを利用してファイルをデータ化することができます。

![image](https://github.com/user-attachments/assets/417c86ad-56a2-41cb-ad01-aba64b831ba9)

以上



