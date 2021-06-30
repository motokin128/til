# Bootstrap 4
bootstrap4 には jQuery と popper.js のインストールが必須  


## インストール
- 必要なyarnパッケージも追加する
  
```
yarn add bootstrap jquery popper.js 
```
  
## インクルード
### `app/javascript/packs/application.js`に追記
- bootstrap の javascript ファイルを読み込めるようにする
  
```js
require("bootstrap/dist/js/bootstrap")
```
> 私たちはjQueryをyarnでインストールしているので、bootstrap自身がjQueryを自動でrequireできるのです。jQueryはapplication.jsの中で利用可能な状態になるので、jQueryをapplication.jsでrequireする必要はありません。すなわち、jQueryをapplication.jsの中で直接使う必要がない限り、実際にはjQueryをapplication.jsでrequireする必要はありません。  
  
### `application.cssをapplication.css`に追記
  
- `application.cssをapplication.scss`にリネームし、コメントやSprockets用の指示を全部空にする
- (注) bootstrap には Reboot.css が含まれているため、他の css ファイルより先に記述しないと全て上書きされてしまう
  
```rb
@import 'bootstrap/scss/bootstrap';
```
  
## jQuery を他の pack でも使用可能にする
### `config/webpack/environment.js` に追記
- (注) `view`では使用不可
   
```rb
const { environment } = require('@rails/webpacker')

const webpack = require('webpack')
environment.plugins.append('Provide', new webpack.ProvidePlugin({
    $: 'jquery',
    jQuery: 'jquery',
    Popper: ['popper.js', 'default']
}))

module.exports = environment
```


