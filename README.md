### tools

---

#### ▼ 不可視ファイルを表示

```bash
$ defaults write com.apple.finder AppleShowAllFiles -boolean true
```

##### Finderを再起動

```bash
$ killall Finder
```

##### 元に戻す

```bash
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

```bash
$ ruby -e "$(curl -fsSL https://raw.github.com/Homebrew/homebrew/go/install)”

/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

最新は2つ目だったはず。（公式サイト参照のこと。）

途中パスワードの入力を求められるので都度入力

インストールできたか確認

```bash
$ brew doctor
>>Your system is ready to brew.
```

が表示されればOK

##### 環境変数PATHを設定

$ ls -laで一覧を確認
.bash_profileがなければ作成（ターミナルはbashの場合）

```bash
$ touch .bash_profile
```

.bash_profileは設定ファイルでterminal.appを起動した際に読み込まれます。

fishの場合は以下がなければ作成

```bash
$ touch .config/fish/config.fish
```

（これより下では要所以外は省略してますが、fishの場合はconfigファイルは↑。環境変数PATHの記述方法が若干変わる以外には特に困る事ないはず。よろしく。）

テキストエディットから編集が簡単

```bash
$ open ~/.bash_profile
```

以下を.bash_profileに追加

```bash
export PATH=/usr/local/bin:$PATH
```

fishでは以下のようにおおよそ一緒でも、若干書き方違うので注意。

```bash
set -U PATH /usr/local/bin $PATH
```

.bash_profileを再読み込み

```bash
$ source .bash_profile
```

.bash_profileを編集した場合は必ず実行。
terminal.appを再起動でも可

※設定の編集では「vi」、「nano」といったターミナル内で動くエディターでの操作がよく紹介されています。
この辺りの設定がどうしても難しいので注意しましょう。

---

#### ▼ caskでアプリケーションを追加

https://github.com/sindresorhus/quick-look-plugins

```bash
$ brew install caskroom/cask/brew-cask
```

Quick Lookのプラグインを追加

```bash
$ brew cask install qlcolorcode qlstephen qlmarkdown quicklook-json quicklook-csv betterzipql qlimagesize
```

Quick Look内のテキストをコピー可能にする

```bash
$ defaults write com.apple.finder QLEnableTextSelection -boolean true
```

Finderを再起動

```bash
$ killall Finder
```

---

#### ▼ gitをインストール

##### gitのversionを確認

```bash
$ git —-version
```

macのデフォルトのgitになってます

##### gitをインストール

```bash
$ brew install git
```

##### gitのディレクトリを確認

```bash
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

```bash
$ brew install tree
```

##### imagemagick　画像変換（Sublimetextのプラグインで使います）

```bash
$ brew install imagemagick
```

---

#### ▼ Node.jsをインストール（https://nodejs.org/）

Node.jsは公式サイトのインストーラーからはインストールしないように。

これからの使い方だと、後でいろいろと問題がおこるので
インストールしている場合はアンインストールしておきましょう。

##### nodebrew のインストール

```bash
$ curl -L git.io/nodebrew | perl - setup
```

##### 環境変数PATHを.bash_profileに設定

```bash
export PATH=$HOME/.nodebrew/current/bin:$PATH
```

fishの場合h、setに続けるパラメータはHOME始まりのものは「-x」それ以外は「-U」でいけるんじゃないかな？

```bash
set -x PATH $HOME/.nodebrew/current/bin $PATH
```



##### インストール可能な node.js のバージョンの確認

```bash
$ nodebrew ls-remote
```

##### node.js の v11.8.0 をインストール

```bash
$ nodebrew install-binary v11.8.0
```

##### 使用する node.js のバージョンを指定

```bash
$ nodebrew use v0.10.38
```

##### node.js のバージョン確認

```bash
$ node -v
```

node.jsにもnpmというパッケージ管理ソフトがあります。（https://www.npmjs.com/）

##### npmのバージョン確認

```bash
$ npm --version
```

##### 1.4.28等　古ければアップデート

```bash
$ npm update -g npm
```

---

#### ▼ BrowserSyncのインストール

##### グローバルにインストール

```bash
$ npm i -g browser-sync
```

##### サンプルを起動

```bash
$ browser-sync start --config bs-config.js
```

---

#### ▼ Superstaticのインストール

任意のディレクトリをルートにしてサーバーを起動

```bash
$ npm i -g superstatic
```

ディレクトリへ移動して以下のコマンドでサーバー起動

```bash
$ ss
```

---

#### ▼ Lessのインストール

```bash
$ npm i -g less
```

---

#### ▼ Stylusのインストール

```bash
$ npm i -g stylus
```

---

#### ▼ autoprefixerをインストール

```bash
$ npm i -g autoprefixer
```

---

#### ▼ Bowerのインストール

web制作向けのパッケージマネージャー

##### グローバルにインストール

```bash
$ npm i -g bower
```

Bower のインストールディレクトリの初期設定は「bower_components」
変更する場合は􏰅ロジェクトディレクトリ内の「.bowerrc」に記述
Bowerもインストールするソ􏰃フトウェアの依存関係やバ􏰀ージョンを管理する「bower.json」がある

---

#### ▼ Wiredepをグローバルにインストール

HTMLのhead要素に自動でscript要素を埋め込む

```bash
$ npm i -g wiredep
```

---

#### ▼ psi のインストール

Google PageSpeed Insights をCLIで実行

```bash
$ npm i -g psi
```

---

#### ▼ pageres のインストール

スクリーンシ􏰁ットを保存、デ􏰀イスサイズを指定して撮影も可能

```bash
$ npm i -g pageres
```

---

#### ▼ StyleStatsのインストール

CSS の 解析ツール

```bash
$ npm i -g stylestats
```

node.jsのバージョンが0.12だと WARN　になりますが動きます。

```bash
$ stylestats https://github.com
```

---

#### ▼ 各種チェックツール

##### csslint

```bash
$ npm i -g csslint
```

##### jshint

```bash
$ npm i -g jshint
```

---

#### ▼ davidのインストール

npmのパッケージのアップデートを便利にするパッケージ
```bash
$ npm i -g david
```

更新を確認

グローバルにインストールしてあるパッケージのアップデート

```bash
$ david --global
```

ローカルにインストールしてあるパッケージのアップデート。

package.jsonも更新

```bash
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

```bash
--save（-S） オプション => 実行時に必要となるパ􏰂ッケージの依存をあらわす。
```

package.jsonに「dependencies」の項目が追加

```bash
--save-dev（-D） オプション => 開発時だけ必要なパ􏰂ッケージとしての依存をしめす。
```

package.jsonに「devDependencies」の項目に􏰂ッケージが追加

プロジェクトディレクトリ内に package.json を生成

```bash
$ npm init
```

---

#### ▼ Rubyのインストール

##### Ruby のバージョン確認

```bash
$ ruby -v
```

```
>> ruby 2.0.0p481 (2014-05-08 revision 45883) [universal.x86_64-darwin14]
```

システムデフォルトのRubyが表示

※macのデフォルトでインストール済み

##### rbenvのインストール

```bash
$ brew install rbenv
```

環境変数PATHを.bash_profileに追記

```bash
export RBENV_ROOT=$HOME/.rbenv
if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi
```

##### ruby-buildをインストール

```bash
$ brew install ruby-build
```

##### rbenvのプラグイン「rbenv-default-gems」「rbenv-gem-rehash」を導入
```bash
$ brew install rbenv-default-gems rbenv-gem-rehash
```
rbenv-default-gems rubyのバージョンアップするときに便利

rbenv-gem-rehash rbenv gemでインストールした場合に必要な「rbenv rehash」を不要に

##### rbenvでつかわれているrubyを確認

```bash
$ rbenv versions
```

##### インストールできるrubyを確認

```bash
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

```bash
$ rbenv install 2.1.6
```

##### インストールされているか確認

```bash
$ rbenv versions
```

```
>> * system (set by /Users/snd/.rbenv/version)
   2.1.6
```

##### 全体で使用するrubyの指定

```bash
$ rbenv global 2.1.6
```

rubyにもRubyGemsというパッケージ管理ソフトがあります。（https://rubygems.org/）

##### RubyGemsのバージョンの確認

```bash
$ gem --version
```

##### RubyGemsのアップデート

```bash
$ gem update --system
```

RubyGemsの動作を管理する設定ファイルを追加

```bash
touch .gemrc
```

下記を記述（インストールと同時にドキュメントもダウンロードされるため）

```bash
gem: --no-document
```

##### sassのインストール

```bash
$ gem install sass
```

##### compassのインストール

```bash
$ gem install compass
```

##### scss lintのインストール

```bash
$ gem install scss_lint
```

##### Bundler のインストール

```bash
$ gem install bundler
```

プロジェクトのディレクトリに移動して

```bash
$ bundle init
```

##### # A sample Gemfile

```
source "https://rubygems.org" # gem "rails"
gem "sass", "3.3.14"
```

Gemfileからgemをインストール

```bash
$ bundle install --path=vendor/bundle --binstubs=vendor/bin
```

bundlerからインストールしたsassを実行

```bash
$ bundle exec sass -v
```

```
>> Sass 3.3.14 (Maptastic Maple)
```

グローバルのsassを実行

```bash
$ sass -v
```

```
>> Sass 3.4.13 (Selective Steve)
```

##### bundle execなしでも実行できるrbenvプラグイン

```bash
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