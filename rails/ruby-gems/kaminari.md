# kaminari
ページネーション処理
  
## API
```rb
@item.total_count #=> レコード総数
@item.offset_value #=> オフセット
@item.num_pages #=> 総ページ数
@item.per_page #=> 1ページごとのレコード数
@item.current_page #=> 現在のページ
@item.first_page? #=> 最初のページならtrue
@item.last_page? #=> 最後のページならtrue
```
[参照記事](https://qiita.com/nysalor/items/77b9d6bc5baa41ea01f3)
  
## 検索処理と併用
Active Record を使った検索処理と併用する場合は、先にデータを取得してからページネーション処理を実行する
(例)ジャンルが`toy`のデータを１ページ１０件ずつ表示
```rb
Item.where(genre: "toy").page(params[:page]).per(10)
```
【NG】
```rb
Item.page(params[:page]).where(genre: "toy").per(10)
```