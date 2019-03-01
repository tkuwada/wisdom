# 設計  

## 共通処理設計
### SalesforceSalesforceサーバリクエスト・レスポンスのハンドリング
 * リクエスト前処理
   * SpinerをON
   * validation
 * サーバーコール実行
     * **onSuccess**
        * SpinerをOFF
        * 処理成功メッセージをToastを表示

     * **onError**
        * Spinerを非表示とする
        * エラーメッセージを解析してToastを表示  
 
### 共通メソッド
#### 方法1) componentの継承
-  共通処理コンポーネント属性に「extensible="true"」を宣言し、共通のhelper Methodを継承させる事が可能

##### [POINT]
- 過剰な継承は避ける。3段階くらいに収める。

#### 方法2) Componentをinclude
* 共通処理用componentに「aura:method」を定義する
* 利用したいcomponentの中に共通処理コンポーネントを配置し、aura:idを付与する
* 「component.find({aura:id).{your method} 」でcontroller/helperから使用する。

#### 方法3) 静的リソースに格納
-  共通処理コンポーネントに共通処理を書いたjsを静的リソースからロードする

### エラーハンドリング方針(Exception発生時)
エラーハンドリング方式は、共通処理サーバリクエスト・レスポンスのハンドリングに影響する

#### 方法1)  AuraHandledExceptionを使用する場合 
* **details**
  * 公式ドキュメントに記載されている一般的な方法
  * DMLはロールバックされるのでSavepoint,Rollbackが不要


#### 方法2) カスタムレスポンスをreturn
* **details**
  * レスポンスは正常系としてreturnされる
  * クライアントサイドでエラーハンドリングを行う
  * usecaseとしてException発生時カスタムログオブジェクトに保存したい場合など
  * Catchした例外を正常系でreturnする為、DMLをロールバックする考慮が必要
  
## componentのI/F設計
* componentは再利用を考慮しコンポーネントプロパティの設計を行う
* 汎用性を考慮する
* component間の連携はevent componentを介して行う。メッセージI/Fの設計は開発着手前に行う。

## デザイン(スタイル) 
* Lightning Design SystemがLEX標準画面と同様のスタイルになる為採用される。特にこだわりがなければ Lightning Design Systemを採用する。

## その他
* フロントエンドのAura frameworkの処理は、イベント駆動アーキテクチャであり非同期処理が多く存在する。開発者は現在行っている処理は同期なのか非同期なのかを意識して開発を行う。
