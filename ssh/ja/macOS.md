###### See on [GitHub](https://github.com/YutoMizutani/OneLinersDoc/blob/master/ssh/ja/macOS.md)

# macOS 向け SSH 設定

## 1. Homebrew のインストール

macOS のパッケージ管理ソフトである [Homebrew](https://brew.sh) をインストールします。下記のコマンドをターミナルに入力してください。
最新のインストール方法は [ここ](https://docs.brew.sh/Installation) に記載されています。

```sh
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)
```

## 2. 必要なパッケージのインストール

[qrencode](https://github.com/fukuchi/libqrencode) (2次元コード生成ツール) と [imgcat](https://github.com/eddieantonio/imgcat) (画像表示ツール) をインストールします。下記のコマンドをターミナルに入力してください。

```sh
brew install qrencode eddieantonio/eddieantonio/imgcat
```

## 3. SSH を有効にする

他のコンピュータから SSH 接続ができるよう設定します。下記のコマンドをターミナルに入力してください。
[システム環境設定](https://support.apple.com/guide/mac-help/allow-a-remote-computer-to-access-your-mac-mchlp1066/mac) を利用して設定することもできます。

```sh
sudo systemsetup -setremotelogin on
```

## 4. SSH コマンドの画像表示

SSH コマンドを画像に出力します。下記のコマンドをターミナルに入力してください。

```sh
echo ssh `id -un`@`ifconfig | grep "inet " | grep -Fv 127.0.0.1 | awk '{print $2}'` | qrencode -s 20 -o out.png && imgcat out.png ; rm -f out.png
```
