# FILE2GPT
事前学習無しで様々な帳票をデータ化します。

### FILE2GPT 登録アプリ (Power Apps キャンバスアプリ)

https://github.com/user-attachments/assets/04a4318a-4e13-4f29-906a-0c8291c7f6e3

### FILE2GPT 管理アプリ (Power Apps モデル駆動型アプリ)

https://github.com/user-attachments/assets/0ecff48d-a6b3-4553-a51d-52382748bd0f


>[!Note]
>利用したなどの感想やコメント、ご要望などございましたら[ギークフジワラのX](https://x.com/geekfujiwara/status/1861677033862152679)までお願いいたします！


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
ソリューションは[リリース](https://github.com/geekfujiwara/FILE2GPT/releases/)から取得できます。

入手したソリューションはPower Apps 作成者ポータルのソリューション画面からインポートを選択して、Zip形式のままアップロード、インポートを実行します。

![image](https://github.com/user-attachments/assets/1b04bad1-8bf8-4696-a1b6-f2aa0ee8ed0f)

インポート完了まで数分です。

インポートが完了しましたら、ソリューションを開きます。ソリューションはマネージドのタブに含まれています。

![image](https://github.com/user-attachments/assets/1a7821e9-ac25-4cd6-82cd-00774dad9bc2)

ソリューション内にモデル駆動型アプリとキャンバスアプリが含まれています。こちらを利用してファイルをデータ化することができます。

![image](https://github.com/user-attachments/assets/417c86ad-56a2-41cb-ad01-aba64b831ba9)

すべてのカスタマイズを公開してください。

その後に利用することができます。

## 読み取り項目の追加方法
こちらでは、他の項目を読み取りしたくなった際のカスタマイズ方法についてご紹介します。

以下のような項目は事前に定義しています。

```
{
  "Document_Type": "レシート",
  "Company_Name": "うどん製麺",
  "Store_Name": "横浜店",
  "Invoice_Date": "2018-07-04",
  "Total_Price": 7279,
  "Currency": "JPY or USD",
  "Total_Gas_Amount": 51.99,
  "Payment_Method": "プリカ or 現金 or クレジット",
  "Document_Number": "INV-11100",
  "Payment_Due_Date": "請求日翌月末",
  "Vendor_Name": "日本マイクロソフト株式会社",
  "Vendor_Contact_Name": "鈴木太郎",
  "Vendor_Contact_Email": "example@microsoft.com",
  "Vendor_Contact_Phone": "03-4444-3333",
  "Vendor_Address": "東京都港区海岸1-1-1",
  "Contract_Date": "2018-07-04",
  "Contract_Duration": "3年間",
  "Contract_Project_Name": "ハムスタープロジェクト",
  "Production_Number": "",
  "Lot_Number": "",
  "Product_Name": ""
}
```

上記に読み取り項目がなく項目を追加したい場合は、以下の手順でカスタマイズできます。

![image](https://github.com/user-attachments/assets/ac74c24e-9553-4865-92e6-b07f04ddc7f6)

### Step 1: Dataverse
テーブルから「処理されたファイル」を編集します。

![image](https://github.com/user-attachments/assets/4af74bff-627c-4917-8910-0d557384e3d7)

項目を追加します。

![image](https://github.com/user-attachments/assets/ea3509ef-47b2-4a47-85fb-0ce8c92c038e)


### Step 2: AI Builder
AI ハブから「FILE2GPTPrompt」を編集します。

![image](https://github.com/user-attachments/assets/dff497eb-9248-4498-b461-dd84257c3b8d)

JSONの出力形式に項目を追加します。

![image](https://github.com/user-attachments/assets/54cc41d3-eb21-4999-819c-688c50f42f34)

カスタム項目に追加したい項目をキーとして指定します。

![image](https://github.com/user-attachments/assets/8ec24af5-06be-4ade-9498-d862bde7db33)

> [!Note]
> 例として以下のように設定します。ここで設定した追加項目は例として **Additional_Key** です。
>
> 
> ```
> {
>  "Document_Type": "レシート",
>  "Company_Name": "うどん製麺",
>  "Store_Name": "横浜店",
>  "Invoice_Date": "2018-07-04",
>  "Total_Price": 7279,
>  "Currency": "JPY or USD",
>  "Total_Gas_Amount": 51.99,
>  "Payment_Method": "プリカ or 現金 or クレジット",
>  "Document_Number": "INV-11100",
>  "Payment_Due_Date": "請求日翌月末",
>  "Vendor_Name": "日本マイクロソフト株式会社",
>  "Vendor_Contact_Name": "鈴木太郎",
>  "Vendor_Contact_Email": "example@microsoft.com",
>  "Vendor_Contact_Phone": "03-4444-3333",
>  "Vendor_Address": "東京都港区海岸1-1-1",
>  "Contract_Date": "2018-07-04",
>  "Contract_Duration": "3年間",
>  "Contract_Project_Name": "ハムスタープロジェクト",
>  "Production_Number": "",
>  "Lot_Number": "",
>  "Additional_Key": "",
>  "Product_Name": ""
>}
> ```
> 


### Step 3: Power Apps
アプリから「FILE2GPT登録アプリ」を編集します。

![image](https://github.com/user-attachments/assets/22d2ea01-be0b-47ba-b553-6cc1c84d65f7)

FileForm1にフィールドを追加します。

![image](https://github.com/user-attachments/assets/887af80c-78fc-4d3f-89fb-121644dc3147)

JSON出力で設定したキーをカードのUpdateに設定します。

![image](https://github.com/user-attachments/assets/342e7265-64be-4be6-a90e-263f33c091bf)

ViewerForm1にフィールドを追加します。

![image](https://github.com/user-attachments/assets/a884a776-bdf8-45f0-a99d-3a06ada8e191)


追加したカードのVisibleプロパティを以下のように設定します。
```
!IsBlank(Self.Default) 
```

![image](https://github.com/user-attachments/assets/4ba2d99a-7e77-46f1-aba5-18175fc10a64)

>[!Note]
>このように設定することで出力結果があったときだけフィールドが表示されます。

こちらで完了です。項目を追加することができました。

以上



