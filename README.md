### tools

---

#### ▼ 不可視ファイルを表示

```
$ defaults write com.apple.finder AppleShowAllFiles -boolean true
```

##### Finderを再起動

```
$ killall Finder
```

##### 元に戻す

```
$ defaults delete com.apple.finder AppleShowAllFiles
```

---

#### ▼ Homebrewのインストール（http://brew.sh/）

##### Javaインストール

```
http://support.apple.com/kb/DL1572?viewlocale=ja_JP
```

##### Command Line Tool for Xcodeのインストール

OSに合わせてダウンロード

（terminalからインストールも可能）

```
https://developer.apple.com/downloads/index.action
```

##### Homebrewのインストール

```
$ ruby -e "$(curl -fsSL https://raw.github.com/Homebrew/homebrew/go/install)”

/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

最新は2つ目だったはず。（公式サイト参照のこと。）

途中パスワードの入力を求められるので都度入力

インストールできたか確認

```
$ brew doctor
>>Your system is ready to brew.
```

が表示されればOK

##### 環境変数PATHを設定

$ ls -laで一覧を確認
.bash_profileがなければ作成

```
$ touch .bash_profile
```

.bash_profileは設定ファイルでterminal.appを起動した際に読み込まれます。

テキストエディットから編集が簡単

```
$ open ~/.bash_profile
```

以下を.bash_profileに追加

```
export PATH=/usr/local/bin:$PATH
```

.bash_profileを再読み込み

```
$ source .bash_profile
```

.bash_profileを編集した場合は必ず実行。
terminal.appを再起動でも可

※設定の編集では「vi」、「nano」といったターミナル内で動くエディターでの操作がよく紹介されています。
この辺りの設定がどうしても難しいので注意しましょう。

---

#### ▼ caskでアプリケーションを追加

https://github.com/sindresorhus/quick-look-plugins

```
$ brew install caskroom/cask/brew-cask
```

Quick Lookのプラグインを追加

```
$ brew cask install qlcolorcode qlstephen qlmarkdown quicklook-json quicklook-csv betterzipql qlimagesize
```

Quick Look内のテキストをコピー可能にする

```
$ defaults write com.apple.finder QLEnableTextSelection -boolean true
```

Finderを再起動

```
$ killall Finder
```

---

#### ▼ gitをインストール

##### gitのversionを確認

```
$ git —-version
```

macのデフォルトのgitになってます

##### gitをインストール

```
$ brew install git
```

##### gitのディレクトリを確認

```
$ which git
```

```
>>/usr/local/bin/git
```

となれば大丈夫

※間違っていたら環境変数PATHの設定がうまくいっていません。

---

#### ▼ homebrewでその他インストール

##### tree ディレクトリ内のファイルを一覧表示

```
$ brew install tree
```

##### imagemagick　画像変換（Sublimetextのプラグインで使います）

```
$ brew install imagemagick
```

---

#### ▼ Node.jsをインストール（https://nodejs.org/）

Node.jsは公式サイトのインストーラーからはインストールしないように。

これからの使い方だと、後でいろいろと問題がおこるので
インストールしている場合はアンインストールしておきましょう。

##### nodebrew のインストール

```
$ curl -L git.io/nodebrew | perl - setup
```

##### 環境変数PATHを.bash_profileに設定

```
export PATH=$HOME/.nodebrew/current/bin:$PATH
```

##### インストール可能な node.js のバージョンの確認

```
$ nodebrew ls-remote
```

##### node.js の v0.10.38 をインストール

```
$ nodebrew install-binary v0.10.38
```

##### 使用する node.js のバージョンを指定

```
$ nodebrew use v0.10.38
```

##### node.js のバージョン確認

```
$ node -v
```

node.jsにもnpmというパッケージ管理ソフトがあります。（https://www.npmjs.com/）

##### npmのバージョン確認

```
$ npm --version
```

##### 1.4.28等　古ければアップデート

```
$ npm update -g npm
```

---

#### ▼ BrowserSyncのインストール

##### グローバルにインストール

```
$ npm i -g browser-sync
```

##### サンプルを起動

```
$ browser-sync start --config bs-config.js
```

---

#### ▼ Superstaticのインストール

任意のディレクトリをルートにしてサーバーを起動

```
$ npm i -g superstatic
```

ディレクトリへ移動して以下のコマンドでサーバー起動

```
$ ss
```

---

#### ▼ Lessのインストール

```
$ npm i -g less
```

---

#### ▼ Stylusのインストール

```
$ npm i -g stylus
```

---

#### ▼ autoprefixerをインストール

```
$ npm i -g autoprefixer
```

---

#### ▼ Bowerのインストール

web制作向けのパッケージマネージャー

##### グローバルにインストール

```
$ npm i -g bower
```

Bower のインストールディレクトリの初期設定は「bower_components」
変更する場合は􏰅ロジェクトディレクトリ内の「.bowerrc」に記述
Bowerもインストールするソ􏰃フトウェアの依存関係やバ􏰀ージョンを管理する「bower.json」がある

---

#### ▼ Wiredepをグローバルにインストール

HTMLのhead要素に自動でscript要素を埋め込む

```
$ npm i -g wiredep
```

---

#### ▼ psi のインストール

Google PageSpeed Insights をCLIで実行

```
$ npm i -g psi
```

---

#### ▼ pageres のインストール

スクリーンシ􏰁ットを保存、デ􏰀イスサイズを指定して撮影も可能

```
$ npm i -g pageres
```

---

#### ▼ StyleStatsのインストール

CSS の 解析ツール

```
$ npm i -g stylestats
```

node.jsのバージョンが0.12だと WARN　になりますが動きます。

```
$ stylestats https://github.com
```

---

#### ▼ 各種チェックツール

##### csslint

```
$ npm i -g csslint
```

##### jshint

```
$ npm i -g jshint
```

---

#### ▼ davidのインストール

npmのパッケージのアップデートを便利にするパッケージ
```
$ npm i -g david
```

更新を確認

グローバルにインストールしてあるパッケージのアップデート

```
$ david --global
```

ローカルにインストールしてあるパッケージのアップデート。

package.jsonも更新

```
$ david
```

更新があるかを確認。

アップデート用のコマンドを出力するので

コピペでアップデート

---

#### ▼ npmでのパッケージインストール

npmでパッケージを管理は「package.json」で行う。
package.jsonは設計書で
このファイルを共有することで、使い回し、環境の共有が簡単に
ダウンロードされたデータのnode_moduleは基本管理しない。

```
--save（-S） オプション => 実行時に必要となるパ􏰂ッケージの依存をあらわす。
```

package.jsonに「dependencies」の項目が追加

```
--save-dev（-D） オプション => 開発時だけ必要なパ􏰂ッケージとしての依存をしめす。
```

package.jsonに「devDependencies」の項目に􏰂ッケージが追加

プロジェクトディレクトリ内に package.json を生成

```
$ npm init
```

---

#### ▼ Rubyのインストール

##### Ruby のバージョン確認

```
$ ruby -v
```

```
>> ruby 2.0.0p481 (2014-05-08 revision 45883) [universal.x86_64-darwin14]
```

システムデフォルトのRubyが表示

※macのデフォルトでインストール済み

##### rbenvのインストール

```
$ brew install rbenv
```

環境変数PATHを.bash_profileに追記

```
export RBENV_ROOT=$HOME/.rbenv
if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi
```

##### ruby-buildをインストール

```
$ brew install ruby-build
```

##### rbenvのプラグイン「rbenv-default-gems」「rbenv-gem-rehash」を導入
```
$ brew install rbenv-default-gems rbenv-gem-rehash
```
rbenv-default-gems rubyのバージョンアップするときに便利

rbenv-gem-rehash rbenv gemでインストールした場合に必要な「rbenv rehash」を不要に

##### rbenvでつかわれているrubyを確認

```
$ rbenv versions
```

##### インストールできるrubyを確認

```
$ rbenv install -l
```

```
//略
  2.1.5
  2.1.6
  2.2.0-dev
  2.2.0-preview1
  2.2.0-preview2
  2.2.0-rc1
  2.2.0
  2.2.1
  2.2.2
  2.3.0-dev
//略
```

##### ver 2.1.6 を インストール

```
$ rbenv install 2.1.6
```

##### インストールされているか確認

```
$ rbenv versions
```

```
>> * system (set by /Users/snd/.rbenv/version)
   2.1.6
```

##### 全体で使用するrubyの指定

```
$ rbenv global 2.1.6
```

rubyにもRubyGemsというパッケージ管理ソフトがあります。（https://rubygems.org/）

##### RubyGemsのバージョンの確認

```
$ gem --version
```

##### RubyGemsのアップデート

```
$ gem update --system
```

RubyGemsの動作を管理する設定ファイルを追加

```
touch .gemrc
```

下記を記述（インストールと同時にドキュメントもダウンロードされるため）

```
gem: --no-document
```

##### sassのインストール

```
$ gem install sass
```

##### compassのインストール

```
$ gem install compass
```

##### scss lintのインストール

```
$ gem install scss_lint
```

##### Bundler のインストール

```
$ gem install bundler
```

プロジェクトのディレクトリに移動して

```
$ bundle init
```

##### # A sample Gemfile

```
source "https://rubygems.org" # gem "rails"
gem "sass", "3.3.14"
```

Gemfileからgemをインストール

```
$ bundle install --path=vendor/bundle --binstubs=vendor/bin
```

bundlerからインストールしたsassを実行

```
$ bundle exec sass -v
```

```
>> Sass 3.3.14 (Maptastic Maple)
```

グローバルのsassを実行

```
$ sass -v
```

```
>> Sass 3.4.13 (Selective Steve)
```

##### bundle execなしでも実行できるrbenvプラグイン

```
$ brew install rbenv-binstubs
```
ディレクトリによって使うgemを自動的に変更

http://sass-compatibility.github.io/

---

### ▼ Application

- Alfred（便利系、でもSpotlightあればいらなくない？）
- Anvil（ローカルホスト簡単に立ててくれるけど、browser-syncあればいらなくない？）
- caffeine（スリープ防止）
- CotEditor（Shift-JIS 対応エディター）
- Dr.Clearner（メモリ管理）
- EasyOnTheEyes（画面暗くできるよ）
- MacDown（マークダウンエディタ）
- SublimeText（超絶メインエディター）
- Brackets（なんとなく入れてるエディターその1）
- VirtualBox（仮装環境使えるよwindowsとか。）
- transmit（FTPファイル転送ソフト、高速）
- sitesucker（サイトデータをダウンロードしてくれるよ）
- slack
- atom（なんとなく入れてるエディターその2）
- sourcetree
- iTerm2（今は使ってないよ）
- Hyper（iTermに変わってメインで使ってるいい感じターミナル）
- StuffIt Expander（いろんなもん解凍できるらしい）
- Skitch（簡易的に画像に文字いれたり便利）
- Mini Calendar（ステータスバーに小さいカレンダー置いてくれる。便利）
- Magnet（ウィンドウをショートカットでいい感じに整列できるよ）
- Clipy（複数コピーできて、履歴からペーストできる便利。）

---

### ▼ npm package

```
├── bower@1.8.2
├── browser-sync@1.0.0
├── browserify@14.5.0
├── eslint@4.19.1
├── grunt-cli@1.2.0
├── gulp-cli@1.4.0
├── jshint@2.9.5
├── node-sass@4.7.2
├── npm@5.6.0
├── parcel-bundler@1.2.0
├── stacks-cli@0.1.46（サイトの使用ライブラリーとか環境を解析できる！）
├── terminalizer@0.2.3（ターミナルの操作を録画してgifで出力）
└── vue-cli@2.9.2
```