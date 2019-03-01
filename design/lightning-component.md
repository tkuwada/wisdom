# 設計

## 共通処理の設計
- Salesforceサーバリクエスト・レスポンスのハンドリング処理
-- onSuccess
--- Spinerを非表示とする
--- Toastを表示
-- onError
--- Spinerを非表示とする
--- エラーメッセージを解析してToastを表示  
  
  
  

## エラーハンドリング方針(Exception発生時)
  
### AuraHandledExceptionを使用する場合 
＜考慮事項＞
- 

### カスタムレスポンスをreturnしクライアントコントラーでハンドリング
＜考慮事項＞
- 


lightning-component.md
