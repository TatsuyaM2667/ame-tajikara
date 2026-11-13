# ame-power

電源プロファイル(省電力・バランス・高性能)を読む・変える小さなコマンド(powerprofilesctl の代わり)。

[ame-shell](https://github.com/TatsuyaM2667/ame-shell)(Wayland のデスクトップシェル)の一部を、単独で使えるように切り出したものです。
ame-shell は画面の要らない仕事を、1 つのことをして標準入出力でやりとりする小さなコマンドに分けています。これはその 1 つです。

## 使い方

```text
ame-power: 電源プロファイルを読む / 変える(powerprofilesctl の代わり)。

  ame-power                 今のプロファイル(power-saver / balanced / performance)を 1 行
  ame-power set <名前>      変える(power-saver・balanced・performance)
  ame-power restore         最後に set したプロファイルに戻す(ログインのとき)

power-profiles-daemon に D-Bus で直接たずねる(新しい名前 org.freedesktop.UPower.PowerProfiles、無ければ古い net.hadess.PowerProfiles)。
set したものは $XDG_STATE_HOME/ame-shell/power に覚える(デーモンが起動のたびに別のものに戻すことがあるので)。
終了コード: 0 できた / 1 デーモンが無い・変えられない / 2 使い方の誤り
```

## ビルド

```sh
zig build -Doptimize=ReleaseSafe   # zig-out/bin/ame-power(Zig 0.13、libc と libdbus)
zig build test
```

## このリポジトリについて

正本は ame-shell の `src/cmd/ame-power.zig` です。このリポジトリは `scripts/split-repos.sh` が生成して同期しています。
直したいところがあれば ame-shell の方へお願いします。

ライセンス: GPL-3.0(ame-shell と同じ)
