###### See on [GitHub](https://github.com/YutoMizutani/OneLinersDoc/blob/master/ssh/ja/ubuntu.md)

# Ubuntu 向け SSH 設定

## 1. Install required packages

Install [ssh](https://packages.ubuntu.com/disco/ssh) (sshd), [qrencode](https://github.com/fukuchi/libqrencode) (2D code generator) and [fbi](https://github.com/kraxel/fbida) (Displaying image tool). Enter below on your terminal.

```sh
sudo apt update && sudo apt install -y ssh qrencode fbi
```


## 2. Enable SSH access

Enable SSH connection from other computers. Enter below on your terminal.

```sh
systemctl start sshd
```

## 4. Show SSH code

Show SSH command with image. Enter below on your terminal.

```sh
echo ssh `whoami`@`hostname -I | awk '{print $(NF)}'` | qrencode -s 20 -o out.png && sudo fbi -T 1 -a out.png ; rm -f out.png
```
