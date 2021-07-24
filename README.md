## 　　Lesson12.　randomユーティリティを使用する  
#### 開発メモ
ワークフロー
<br><img width="600" src="https://user-images.githubusercontent.com/40127279/126860198-1e1e98b5-af42-42ea-b3b7-4ca9d06ae5a4.png">

### 1.randomユーティリティ
　おまかせ表示の乱数として利用しています
<br>　初期の段階では0から99の乱数を発生させてロジックで表示させていましたが
<br>　ユーティリティをキーワード（Word from list）の方式にすると
<br>　RunScriptいらずのコードレスワークフローになりました
<br>　randomユーティリティのサンプルとしては打って付けですね　
<br>　当初のワークフローは青いオブジェクトとして残しています
<br>
<br>　なお、最終的に選択肢は500個になりましたが、
<br>　大部分は『カテゴリー内おまかせ表示』を利用しており、総ページ数は50,000ページ以上
<br>　もちろんお好きなにカスタマイズ可能です
<br>　
<br>　当初のワークフロー（Random → RunScript）
<br>　<img width="600" src="https://user-images.githubusercontent.com/40127279/126860207-0d04d45c-2641-401f-a41d-c448bf5f8725.png">
<br>　<img width="600" src="https://user-images.githubusercontent.com/40127279/126860230-4f47fbe8-a05b-4848-931a-1b18627e53e6.png">
<br>　
<br>　最終的なスクリプトレスワークフロー（Hotkey → Random）
<br>　<img width="600" src="https://user-images.githubusercontent.com/40127279/126860267-fa231d67-fdd1-4eaa-8673-e2ba9768d608.png">
<br>　<img width="600" src="https://user-images.githubusercontent.com/40127279/126860276-624396ae-7bc7-4813-81d4-09ea97bdaccf.png">
### 2.randomの結果をフィードバックする
　単におまかせとしてウィキペディアのページを表示させるだけで良いのですが
<br>　演出としてrandomの結果をフィードバックしています
<br>　URLエンコードもない日本語なので、そのままLarge Typeしてるだけです
<br>　
<br>　Large Type
<br>　<img width="600" src="https://user-images.githubusercontent.com/40127279/126860286-b39194b5-3d90-455e-a55e-f952e0ada84c.png">
### 3.テストドライバーを作る
　お遊びツールなので作りっぱなしで良いのですが、テストする必要があるかもしれません
<br>　HOTKEYやインプットのキーワードから接続すれば、特定の表示をテストできます
<br>　どちらかというと、『カテゴリー内おまかせ表示』をテストしたく作成しました
<br>　オレンジのオブジェクトとして残しています
<br>　
<br>　RunScript（テスト用）
<br>　<img width="600" src="https://user-images.githubusercontent.com/40127279/126860328-7b12657f-7d8c-4298-addf-802bc222f798.png">
### 4.numbers.appを使ってソースをつくる
　500もの選択肢となるtソースが面倒なので、numbers.appで編集してみました
<br>　エクセルのように数式がを使ってコードを生成できます（最終的にソースコードレスになりましたが）
<br>　重複がないかどうかのチェックもできます
<br>　randomユーティリティへの作り込みは、列選択のコピペ1発で済みました
<br>　[こちらからどうぞ](https://github.com/KitanoTamotsu/wikipedia/releases/download/1.1/wikipedia.numbers)
<br>　因みに、カテゴリーに含まれる下位のカテゴリー数やページ数の情報もつけています（手作業です）
<br>　下位カテゴリーが0のものみを選択肢にしたいときななどに便利かも
### 5.ブラウザの表示が遅いことへの対応
　このワークフローに限ったことではないのですが、ブラウザの表示がかなり遅いことがあります
<br>　そんなときには手動でキャッシュをクリアすると、すぐにそのページが表示されたりします
<br>　Alfredでは、キー送信を行うオブジェクト（Key Combo）があり、
<br>　例えばSafariのキャッシュクリアのショートカットである⌥⌘Eを送信することができます
<br>　
<br>　KeyCombo
<br>　<img width="393" src="https://user-images.githubusercontent.com/40127279/126860364-0c760320-9801-4538-b4d7-a00d6717cd3b.png">
<br>　
<br>　また処理をウエイトさせるオブジェクト（Delayユーティリティ）がありタイミングの調整も可能です
<br>　（Large typeが早いと干渉してSafariへショートカットが届かないので遅延させました）
<br>　フローつないでいませんが、白いオブジェクトを残しておきました
<br>　因みに私のデフォルトブラウザはSafariです
<br>　
<br>　Delay
<br>　<img width="509"  src="https://user-images.githubusercontent.com/40127279/126860383-8b1bfe15-9263-4fb0-879e-513bc6b7d92e.png">

<br>　
#### 背景
　ウィキペディアにおまかせ表示というツールがあることは知っていましたが
<br>　興味のないトピックスも多く使えないツールでした
<br>　特別ページの一覧やメインページをみていたら、カテゴリー内おまかせ表示というツールをみつけ、
<br>　これだ！と思いつくってみました
<br>　ウィキペディアの世界を堪能してください
<br>
<br>　※私の興味で選択肢を作成していまます
<br>　　性的な表現や画像、犯罪や暴力に関するページが表示されることがあるのでご了承ください
<br>　（もち公式なウィキペディアのページです）

#### 取扱説明
### 機能:
　ウィキペディアをランダムに表示させる
<br>　※ある程度のカスタマイズが可能です
### インストール:
　1.[Alfredworkflow](https://github.com/KitanoTamotsu/wikipedia/releases/download/1.1/wikipedia.alfredworkflow.zip)をダウンロード 
<br>　2.ファイルをダブルクリックしてワークフローに登録
### 使い方:
　HOTKEY『⌃w』で起動
<br>　（ホットキーはご自身で設定が必要です）
#### 修正履歴

### ver1.1(2021-04-04)：
　シェルスクリプトをbashからzshに変更しました

<br>
<br>
[トップページに戻る](https://kitanotamotsu.github.io/)

