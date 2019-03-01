# 設計  

## 共通処理設計
* Salesforceサーバリクエスト・レスポンスのハンドリング
  * **onSuccess**
    * Spinerを非表示とする
    * Toastを表示
    
  * **onError**
    * Spinerを非表示とする
    * エラーメッセージを解析してToastを表示  
 
### 共通メソッド
#### 継承
+ 共通処理コンポーネント属性に「extensible="true"」を宣言し、共通のhelper Methodを継承させる

#### Componentをinclude
* 共通処理用componentに「aura:method」を定義する
* 利用したいcomponentの中に共通処理コンポーネントを配置し、aura:idを付与する
* 「component.find({aura:id).{your method} 」でcontroller/helperから使用する。
 
### エラーハンドリング方針(Exception発生時)
 ＜パターン＞
 
#### Case 1) AuraHandledExceptionを使用する場合 
* **detail
  * DMLはロールバックされるのでSavepoint,Rollbackが不要
  * 公式ドキュメントに記載されている方法

#### Case 2) カスタムレスポンスをreturn
* **detail
  * レスポンスは正常系としてreturnされる
  * クライアントサイドでエラーハンドリングを行う
  * usecaseとしてException発生時カスタムログオブジェクトに保存したい場合など
  * DMLをロールバックする考慮が必要
  
 
