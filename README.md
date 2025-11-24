# Install

1. Install HomeBrew

```shell
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

2. Install application

cloneしたbrewfileを`~./Brewfile`にコピー後、下記コマンドを実行

```shell
brew bundle --global
```


# インストールされたプログラムに対する細かい対応
## asdf

```shell
echo -e "\n. $(brew --prefix asdf)/libexec/asdf.sh" >> ${ZDOTDIR:-~}/.zshrc
```

### プラグインの追加
```shell
asdf plugin add nodejs
asdf plugin add python
```

## zsh-completions / zsh-syntax-highlighting

```shell
source /opt/homebrew/share/zsh-autosuggestions/zsh-autosuggestions.zsh
source /opt/homebrew/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
```

## zsh-completions

`~/.zhsrc`に下記を追加

```shell
if type brew &>/dev/null; then
    FPATH=$(brew --prefix)/share/zsh-completions:$FPATH
    autoload -Uz compinit
    compinit
fi
```

下記コマンドを実行
```shell
chmod go-w '/opt/homebrew/share'
chmod -R go-w '/opt/homebrew/share/zsh'
```

## git-lfs

```shell
sudo git lfs install --system
```

## ターミナルの再読み込み

```shell
exec $SHELL -l
```