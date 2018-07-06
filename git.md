

### branch同士の差分を取る
- [Git ブランチ間の差分をコミット単位で知る・見る](https://qiita.com/ikenji/items/fecd39966bbf463da3f4)

``` raw-token-data
マージ先ブランチ：master
マージするブランチ:issue123

git log --no-merges master..issue123

これでissue123ブランチにはあって、masterにないコミットのログを表示できます。
```
