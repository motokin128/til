# respond_to
リクエストされるフォーマットによって処理を分ける
  
## respond_to | 引数 | end
```rb
respond_to do |format|
  format.形式 { 処理 }
end
```
  
(例)フォーマットが`HTML`の場合、リダイレクト
```rb
respond_to do |format|
  format.html { redirect_to root_path }
end
```

<br>

## respond_to :アクション名
レスポンスのフォーマットを切り替える
  
(例)フォーマットを`js`に切り替える
```rb
respond_to :js
```

