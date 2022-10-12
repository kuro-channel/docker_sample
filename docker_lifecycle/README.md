# コンテナのライフサイクル
- `-i`：コンテナの標準入力を取得、双方向に接続可能  
- `-t`：コンテナ内にTTYを割り当てる  
- コンテナでshellを実行し、フォアグラウンドで実行状態にしておきたい場合によく使う  
`$docker create --name status-test -it alpine /bin/sh`

## ステータス
- Created
- Up
- running
- Paused
- Exited