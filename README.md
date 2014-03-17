OSXAppPackage
=============

標準開発環境パッケージ for brewdler &amp; brew+cask

## 前提

* XCodeインストール済
* OSX Marvericks アップデート済
 
## 所用時間

* 初期インストールの場合,20〜40分程度かかります

## インストール手順

###1. [Homebrew](http://brew.sh/index_ja.html)のインストール
    ruby -e "$(curl -fsSL https://raw.github.com/Homebrew/homebrew/go/install)"
    
###2. このリポジトリのcloneを展開
    mkdir ~/git
    cd ~/git
    git clone https://github.com/hummer98/OSXAppPackage.git
    
* 気に入らなければforkしてね
    
###3. brew bundleで全自動インスコトール！
    cd ~/git/OSXAppPackage
    brew bundle
    

###4. お昼ごはんに行く (20-40分かかります)

###5. 多分パスワードを聞かれている状態で止まっているので、Macの自分のパスワードを入れる

* 稀にsha2 fingerpringのミスマッチでインストールが中断する事があるが、何度か`brew bundle`やると成功するはず。
* それでも動かない場合は相談を

###6. PATHの設定

* ~/.bash_profileに追記
  ```
f [ -d $HOME/.rbenv/bin ]; then
    export RBENV_ROOT=$HOME/.rbenv
    export PATH="$RBENV_ROOT/bin:$PATH"
    eval "$(rbenv init -)"
fi
export GEM_BIN=$(ruby -e 'require "rubygems"; puts Gem::bindir')
if [ $(\command -v pear) ]; then
	export PEAR_LIB=$(pear config-show | grep php_dir | awk '{print $4}')
fi
export MANPATH="/usr/local/opt/gnu-sed/libexec/gnuman"
```

* /etc/pathsの設定
  * OSXでは/etc/pathsを上から順にPATH環境変数に詰め込むので、一番上に brewのデフォルトバイナリが置いてあるフォルダを指すように変更する ```/usr/local/bin``` にするのを推奨。
  * 例
  ```
/usr/local/bin
~/bin
/usr/bin
/bin
/usr/sbin
/sbin
/usr/local/opt/gnu-sed/libexec/gnubin
/usr/local/share/npm/bin
```

###7. vagrantプラグインのインストール

```
vagrant plugin install sahara
vagrant plugin install vagrant-ansible
vagrant plugin install vagrant-omnibus
vagrant plugin install vagrant-vbguest
```

###8. その他
~~Sublime Textをコマンドラインから開く subl コマンドの設定~~ 自動で入るらしいので`subl`をターミナルから打って起動するならば下記は不要

    sudo ln -s "/Applications/Sublime Text 2.app/Contents/SharedSupport/bin/subl" /usr/bin/subl

