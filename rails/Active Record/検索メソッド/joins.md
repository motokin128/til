# joins
  
## テーブルを結合する
(例)投稿のあるユーザーを取得
```rb
User.joins(:posts)
```
*＊この場合、投稿の数だけユーザーが重複する*
  
(例)投稿のあるユーザーを取得(重複なし)
```rb
User.joins(:posts).distinct
```
  
<br>

## 複数のテーブルを結合する
(例)コメントされた投稿のあるユーザーを取得(重複なし)
```rb
User.joins(:posts, :comments).distinct
```
