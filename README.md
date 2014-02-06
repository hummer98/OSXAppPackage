OSXAppPackage
=============

標準開発環境パッケージ for brewdler &amp; brew+cask

# インストール

##1. Homebrewのインストール
    ruby -e "$(curl -fsSL https://raw.github.com/Homebrew/homebrew/go/install)"
    
##2. このリポジトリのcloneを展開
    git clone https://github.com/hummer98/OSXAppPackage.git
    
##3. brew bundle
    cd OSXAppPackage
    brew bundle
    
インストール中に自分のパスワードを要求される事があるので留意

##4. PATHの設定
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
