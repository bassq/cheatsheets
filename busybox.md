# busybox まとめ

簡易 Unix 風 CLI 環境です。
本来コンパクトな Linux 用ですが windows にも移植されてます。
Mac 版もありますが、あまり意味がないので開発はそれほど盛んではないようです。

サイズの小ささを追求しているので、
「これ出来ないのか」となる事がよくあります。
「盆栽」だと思って工夫して乗り切りましょう。
特に英語だけに絞ることでコンパクトにしてる様なので
日本語で何かできたらラッキーです。

* android

  ターミナル系アプリを入れると、だいたい busybox が入っているようです。

* windows には busybox-w32

  あまりカスタマイズできないときにも unix shell 風環境が使えます。
  レジストリなどOSの設定をいじらないので手軽です。
  学校や会社、ネットカフェで便利。
  
  https://frippery.org/busybox/
  のページの下の方にコンパイル済みのバイナリ busybox.exe へのリンクがあります。
  サイズは 400KiB くらいです。
  
## sh は ash
bash に比べると貧弱ですが
* Ctrl+R でインクリメンタルに履歴を遡れる
* windowを閉じても履歴が残る

この2点だけでも cmd.exe に較べてだいぶ便利です。
cmd.exe で使えるパスの通った外部コマンドが使えます。
何もインストールしなくても busybox sh からは busybox 内蔵の unix コマンドが使えます。
内蔵コマンド一覧は ```busybox -l``` 。

perl や ruby に比べるとショボいですが、
sed, awk などが使えるのでそこそこのスクリプトが書けます。

HOMEディレクトリ直下に .profile を置いておくと、``` busybox sh -l ```で起動時に読み込まれます。
alias, シェル関数, HISTSIZE などを設定できます。

#### 気づいたこと
* Ctrl+K できるが Ctrl+Yできない。削除のみ。
* ヒストリ展開できない
* Ctrl+左右矢印で単語単位移動可
* emacsモードだけでなく、viモードがあるらしい

## vi
ascii text の編集は大丈夫なのでスクリプトは書けますが使えるコマンドは限られてます。
windows では ```cmd /k start foo.txt``` などして GUI のエディタを使うと良いです。
多用するなら alias にしておく。

cat や grep での日本語の出力は大丈夫なようです。

## その他、使って便利だった or 試してみたいコマンド
```
busybox -l | less
grep -r 'foo bar' *
find . -name '*txt'
ls -F | grep '/$'
cat url-list.txt | xargs -n1 wget
unzip
gunzip
```
