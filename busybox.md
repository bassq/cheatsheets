#busybox まとめ

あまりカスタマイズできない windows に unix shell的環境が欲しい時、
[busybox-w32](https://frippery.org/busybox/)
が使えます。
（ページの下の方にコンパイル済みのバイナリ busybox-exe へのリンクがあります。）

ユーザーディレクトリ直下に .profile として sh の設定ファイルを置いておくと、
"busybox -l" で起動する時に読み込まれれます。
