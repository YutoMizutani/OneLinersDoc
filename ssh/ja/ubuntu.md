###### See on [GitHub](https://github.com/YutoMizutani/OneLinersDoc/blob/master/ssh/ja/ubuntu.md)

# Ubuntu 向け SSH 設定

## 1. 必要なパッケージのインストール

[ssh](https://packages.ubuntu.com/disco/ssh) (sshd)，[qrencode](https://github.com/fukuchi/libqrencode) (2次元コード生成ツール) と [fbi](https://github.com/kraxel/fbida) (画像表示ツール) をインストールします。下記のコマンドをターミナルに入力してください。

```sh
sudo apt update && sudo apt install -y ssh qrencode fbi
```

## 3. SSH を有効にする

他のコンピュータから SSH 接続ができるよう設定します。下記のコマンドをターミナルに入力してください。

```sh
systemctl start sshd
```

## 4. SSH コマンドの画像表示

SSH コマンドを画像に出力します。下記のコマンドをターミナルに入力してください。

```sh
echo ssh `whoami`@`hostname -I | awk '{print $(NF)}'` | qrencode -s 20 -o out.png && sudo fbi -T 1 -a out.png ; rm -f out.png
```
