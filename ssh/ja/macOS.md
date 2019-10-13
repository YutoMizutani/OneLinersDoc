###### See on [GitHub](https://github.com/YutoMizutani/OneLinersDoc/blob/master/ssh/ja/macOS.md)

# macOS 向け SSH 設定

## 1. Homebrew のインストール

macOS のパッケージ管理ソフトである [Homebrew](https://brew.sh) をインストールします。下記のコマンドをターミナルに入力してください。
最新のインストール方法は [ここ](https://docs.brew.sh/Installation) に記載されています。

```sh
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)
```

## 2. Install required packages

Install [qrencode](https://github.com/fukuchi/libqrencode) (2D code generator) and [imgcat](https://github.com/eddieantonio/imgcat) (Displaying image tool). Enter below on your terminal.

```sh
brew install qrencode eddieantonio/eddieantonio/imgcat
```


## 3. Enable SSH access

Enable SSH connection from other computers. Enter below on your terminal.
Or settings up [on System Preferences](https://support.apple.com/guide/mac-help/allow-a-remote-computer-to-access-your-mac-mchlp1066/mac).

```sh
sudo systemsetup -setremotelogin on
```

## 4. Show SSH code

Show SSH command with image. Enter below on your terminal.

```sh
echo ssh `id -un`@`ifconfig | grep "inet " | grep -Fv 127.0.0.1 | awk '{print $2}'` | qrencode -s 20 -o out.png && imgcat out.png ; rm -f out.png
```
