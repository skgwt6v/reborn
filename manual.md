# はじめに

jsonを更新した場合は、以下の構文チェックを行ってください。  
[JSON Pretty Linter Ver3](https://lab.syncer.jp/Tool/JSON-Viewer/)  
jsonにエラーがある場合、正常に表示されないことがあります。  

## ファイル構成

```
public/                    // public以下が公開ファイルになります。
  ┃
  ┣ data                   // ページ内のテキスト・メンバー紹介の内容を格納
  ┃  ┣ dataAbout.json      // 「re-bornについて」テキスト
  ┃  ┣ dataCarousel.json   // 「トップバナー」の設定
  ┃  ┣ dataMembers.json    // 「Re-bornメンバー」テキスト
  ┃  ┣ dataMeta.json       // re-bornのページタイトル・facebook画像・メールアドレスなど（変更不要）
  ┃  ┣ dataNews.json       // 「NEWS」のテキスト。
  ┃  ┗ dataParsons.json    // メンバーのプロフィール
  ┃
  ┣ image/                 // 画像を格納
  ┃  ┣ favicons/           // ファビコン一式
  ┃  ┣ main/               // 「トップバナー」で使用する画像一式
  ┃  ┣ members/            // メンバーのプロフィール画像一式
  ┃  ┗ news/               // 「NEWS」で使用する画像一式
  ┃
  ┣ include/               // htmlのパーツを格納（変更不要）
  ┣ javascripts/           // javascript（変更不要）
  ┣ stylesheets/           // stylesheet（変更不要）
  ┃
  ┣ index.php              // トップページのviewファイル（変更不要・ファイル名変更不可）
```

## トップバナーについて
### 仕様
- 複数の画像を設定すると、自動で画像が切り替わります。
- 記述されてれている順番に表示が切り替わります。
- 画像サイズは1848x765
- リンクの設定はありません。

### 更新ファイル
`data/dataCarousel.json`

### 記述サンプル
```
  {
    "title": "メインヴィジュアル",
    "image": "./images/main/20181108-001.jpg"
  }
```

### 表示イメージ
![トップバナー](https://user-images.githubusercontent.com/11353190/48825702-8caae280-edab-11e8-997d-3bb5b0610f49.jpg)


## Newsについて

### 仕様
- 入力されているニュースのうち、上位3件が表示されます。
- 本文は90文字が適切です。
- リンクの設定は必須になります。
- 画像サイズは960x640以上。それ以上はトリミングされます。

### 更新ファイル
`data/dataNews.json`


### 記述サンプル
```
  {
    "title": "ポートレイト撮影会 vol.03<br>@竹芝VISION STUDIO",
    "date": "2018.3.10",
    "text": "2017年よりスタートした撮影会も3回目。ご家族撮影も含め一般の方も参加いただきました。",
    "url": "https://www.facebook.com/events/120101488699650/",
    "image": "./images/news/20286832_1198580023581292_4354828691837095630_o.jpg"
  }
```

### 表示イメージ
![News](https://user-images.githubusercontent.com/11353190/48825763-be23ae00-edab-11e8-90ea-61b13357acfd.jpg)


## メンバー紹介について
### 仕様
- トップページにタイル状にメンバーの写真が並びます。
- マウスカーソルを置くと、メンバーの名前が表示されます。
- クリックするとプロフィールが表示されます。
- プロフィール文の構成は、見出し・一問一答・紹介リンクになります。（記述サンプルを参照）
- プロフィール情報がないメンバーは、記述サンプルの ` 2. 一覧表示（詳細情報なし）` を使用してください。
- ` 2. 一覧表示（詳細情報なし）`はjsonの末尾にまとめて記述してください。

### 更新ファイル
`data/dataParsons.json`

### 記述サンプル

1.通常

```
{
    "code": null, // 使用しないためnullのままで
    "name": "テスト花子",
    "old": 50, // 省略する場合は "old": null に
    "image": "empty.png", // images/members/empty.png が参照されます
    "text": {
      "h": "ここにtext.hが入ります。ここにtext.hが入ります。ここにtext.hが入ります。",
      "qa": [ // 不要であれば"qa": null としてください
        {
          "q": "text.qa[0]qが入ります。",
          "a": "text.qa[0]aが入ります。",
          "l": "text.qa[0]lが入ります。<br>text.qa[0]lが入ります。"
        },
        {
          "q": "text.qa[1]qが入ります。",
          "a": "text.qa[1]aが入ります。",
          "l": "text.qa[1]lが入ります。<br>text.qa[1]lが入ります。"
        },
        {
          "q": "text.qa[2]qが入ります。",
          "a": "text.qa[2]aが入ります。",
          "l": "text.qa[2]lが入ります。<br>text.qa[2]lが入ります。"
        }
      ],
      "link": [ // 不要であれば "link": null としてください
        {
          "title": "HP",
          "url": "http://test.com"
        },
        {
          "title": "Blog",
          "url": "http://blog.test.com"
        }
      ]
    }
  }
```

2. 一覧表示（詳細情報なし）

```
  {
    "code": null,
    "name": null,
    "image": "002.jpg",
    "skip": true 
  }
```

### 表示イメージ
![メンバー一覧](https://user-images.githubusercontent.com/11353190/48825785-d09de780-edab-11e8-8696-1590f172cc36.jpg)
![プロフィールのサンプル](https://user-images.githubusercontent.com/11353190/48825501-ea8afa80-edaa-11e8-8d1a-feb080618785.jpg)


## Aboutについて
### 仕様
- re-bornの説明文
- 見出しと本文の2部構成になっています。
- 説明文を増やしたい場合は、json内の項目を増やしてください。

### 更新ファイル
`data/dataAbout.json`

### 記述サンプル

```
  {
    "title": "この活動がスタートしたきっかけ",
    "text": [
      "そもそも乳ガンの診断を受けて手術を決断したリーダーが、全摘の前に撮影をしたいと友人のフォトグラファーに依頼。",
      "ところが撮影当日の検査で奇跡的にガンが全て消えていたことがわかりました。",
      "一時は「死」と向き合う経験をして、「当たり前のことなど何もない」ということに気づき、",
      "それを救ってくれたのは、病気と付き合いながらも「今を生きる」人たちとの出会いでした。",
      "そこで私達は情報を発信、シェアしていくことで誰もが参加できるプラットフォームを作ることになりました。"
    ]
  }
```

### 表示イメージ
![About](https://user-images.githubusercontent.com/11353190/48825995-77828380-edac-11e8-914f-c05da35437d6.jpg)


## Re-bornメンバーについて
### 仕様
- re-bornメンバーの紹介文
- 肩書・見出し・本文の3部構成になっています。
- 紹介文を増やしたい場合は、json内の項目を増やしてください。
- 写真の追加はできません

### 更新ファイル
`data/dataMembers.json`

### 記述サンプル

```
  {
    "position": "フォトグラファー",
    "name": "yOU（河﨑 夕子）",
    "text": [
      "広告や「Forbes」「Elle japon」などの雑誌でポートレイトを中心に活動する傍ら、",
      "自身の作品で個展やイベントを開催するフォトグラファー。",
      "マネジメント会社NMT inc.所属。",
      "大切な友人を子宮体癌で失ったことをきっかけにYUKOと共にこの活動に関わることを決めた。",
      "<a href=\"http://www.youk-photo.com/\" target=\"_new\">www.youk-photo.com</a>"
    ]
  }
```

### 表示イメージ
![Re-bornメンバー](https://user-images.githubusercontent.com/11353190/48825843-fcb96880-edab-11e8-93b0-5cab23e14a66.jpg)

