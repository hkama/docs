- C をグローバルエイリアスとして設定してる。これで Mac でも Linux でも C だけで標準出力をクリップボードにコピーできるようになる

```
if which pbcopy >/dev/null 2>&1 ; then 
    # Mac  
    alias -g C='| pbcopy'
elif which xsel >/dev/null 2>&1 ; then 
    # Linux
    alias -g C='| xsel --input --clipboard'
elif which putclip >/dev/null 2>&1 ; then 
    # Cygwin 
    alias -g C='| putclip'
fi
```
```
# INPUT.txt のうち 10から15行目をクリップボードにコピーする
% sed -n '10,15p' INPUT.txt C
```

### xselについて
- [xsel - コマンドラインからXセレクションを操作する](http://lldev.jp/linux_c_cpp/linux_cmd/xsel.html)

### emacs ハイライト
- [Emacsのハイライト関係の設定まとめ](http://keisanbutsuriya.hateblo.jp/entry/2015/02/01/162035)

### emacs package
- M-x list-packages でパッケージ一覧を表示させ、テーマ名を検索し、インストールしてください。
- load-pathの確認はemacs起動して*scratch*画面にしてload-pathと打ってC-jで出てくる
- [Emacs設定講座 その3「scratch バッファと eval(評価)](http://d.hatena.ne.jp/tomoya/20090215/1234692209)


- [setup.el で安全・爆速な init.el を書く](https://gist.github.com/zk-phi/9935048)

#### emacs color theme
- [Emacs Live(ネオンみたいな光り方する謎のtheme)](https://github.com/overtone/emacs-live)
- [markdown mode for emacs](https://jblevins.org/projects/markdown-mode/)
- [use-packageで可読性の高いinit.elを書く](http://emacs.rubikitch.com/use-package-2/)
- [emacsはモード選択がある](http://www.math.s.chiba-u.ac.jp/~matsu/emacs/mode/mode.html)
  - メジャーモードとマイナーモードが存在


### dotfilesをgitで管理する
- [dotfilesをGitHubで管理](https://qiita.com/okamos/items/7f5461814e8ed8916870)
- [multimarkdown](http://fletcher.github.io/peg-multimarkdown/)
  - ガイドに沿ってインストールして、makeした後、生成されたmultimarkdownをpathが通る場所に与える必要がある
  - firefoxが文字コードを誤認識しているところもある。
    - [Firefoxで文字化けするよくある理由](http://itasuke.hatenablog.com/entry/2017/12/19/171636)


- [multimarkdownの文字コード問題解決しない](http://tasuwo.github.io/blog/2015/03/17/title/)













