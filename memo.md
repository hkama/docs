

- C をグローバルエイリアスとして設定してる。これで Mac でも Linux でも C だけで標準出力をクリップボードにコピーできるようになる

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

        # INPUT.txt のうち 10から15行目をクリップボードにコピーする
        % sed -n '10,15p' INPUT.txt C


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




  * ### dotfilesをgitで管理する
- [dotfilesをGitHubで管理](https://qiita.com/okamos/items/7f5461814e8ed8916870)
- [multimarkdown](http://fletcher.github.io/peg-multimarkdown/)
  - ガイドに沿ってインストールして、makeした後、生成されたmultimarkdownをpathが通る場所に与える必要がある
  - firefoxが文字コードを誤認識しているところもある。
    - [Firefoxで文字化けするよくある理由](http://itasuke.hatenablog.com/entry/2017/12/19/171636)
- [multimarkdownの文字コード問題解決しない](http://tasuwo.github.io/blog/2015/03/17/title/)
- [Emacsで現在のキーバインドを確認する](https://qiita.com/icb54615/items/3e9976bb9ae8a0b793dd)
  - キーバインド一覧を表示するには、
    M-x describe-bindings
    また、特定のキーのバインドを知りたいときは、
    M-x describe-key

- [emacsでC-uはuniversal argumentを意味する](http://flex.phys.tohoku.ac.jp/texi/emacs-jp/emacs-jp_18.html)
- mozcの日本語入力で日本語を打っている時に表示されない時にはCtrl+Alt+Pで入力中の文字が再び表示される
- windows版のemacsで.emacsにあたるものは`C:\Users\[ユーザ名]\AppData\Roaming\.emacs.d\init.el`にある
- [Windows の Emacs で rgrep を使えるようにする](https://qiita.com/ybiquitous/items/2f2206ff7a557c4cbc11)
- [use-package公式サイト](http://cachestocaches.com/2015/8/getting-started-use-package/)
  - M-x package-install でpackageをinstallする
- spacemacsのthemeが割と見やすい
- helmを入れるべき
  - [初心者〜初級者のためのEmacs-Helm事始め : 前編](https://qiita.com/jabberwocky0139/items/86df1d3108e147c69e2c)
  - [Emacs - Helmとは](https://qiita.com/Satoshi_Numasawa/items/c4f41452b4796e82a61e)

- linterとか入れないといけない


- [Emacsで現在開いてるバッファを再読込する](https://qiita.com/ironsand/items/749b032d33d389972b4b)
- [.emacsの整理をした話 + EmacsとViとShellとLispを悪魔合体させたら超絶便利だった](http://keens.github.io/blog/2013/12/13/dot-emacs-clean-up/)



- [ripgrep.el : 【agより、ずっとはやい!!】超音速grepとEmacsインターフェース(Windows安心)](http://emacs.rubikitch.com/ripgrep/)


- [A Package in a league of its own: Helm(helmについて詳しく書いてある)](https://tuhdo.github.io/helm-intro.html)

- [firefoxを暗くする](https://medium.com/@shockpaste/firefox%E5%90%91%E3%81%91%E7%94%BB%E9%9D%A2%E6%9A%97%E3%81%8F%E3%81%99%E3%82%8B%E3%82%84%E3%81%A4-9fa1320ce02c)




        TAB	見出しやツリーの折り畳み
        C-c C-s h 	見出しの追加
        C-c C-n 	次の見出しに移動
        C-c C-p 	前の見出しに移動
        C-c ← → 	見出しレベルの上げ下げ
        C-c ↑ ↓ 	見出しの移動
        M-Enter 	リストの追加
        C-c C-d 	TODOの追加(トグル)
        C-c ' 	コードブロックでmode編集
        C-c C-l (markdown-insert-link) 
        C-c C-i (markdown-insert-image)
        C-c C-s i イタリック
        C-c C-s b 太字
        C-c C-s c for inline code
        C-c C-s k for inserting <kbd> tags.
        C-c C-s q inserts a blockquote using the active region, if any, or starts a new blockquote. 
        C-c C-s Q is a variation which always operates on the region
        C-c C-s p behaves similarly for inserting preformatted code blocks
        C-c C-s P being the region-only counterpart
        C-c C-s C inserts a GFM style backquote fenced code block.
        C-c C-s h inserts a heading with automatically chosen type and level 
        To insert a heading of a specific level and type, use C-c C-s 1 through C-c C-s 6 for atx (hash mark) headings and C-c C-s ! or C-c C-s @ for setext headings of level one or two, respectively. 
        C-c C-s - inserts a horizontal rule. 
        C-c C-s f inserts a footnote marker at the point, inserts a footnote definition below, and positions the point for inserting the footnote text.
        C-c C-s w inserts a wiki link of the form WikiLink`.

        C-c C-c m: markdown-command > *markdown-output* buffer.
        C-c C-c p: markdown-command > temporary file > browser.
        C-c C-c e: markdown-command > basename.html.
        C-c C-c v: markdown-command > basename.html > browser.
        C-c C-c w: markdown-command > kill ring.
        C-c C-c o: markdown-open-command.
        C-c C-c l: markdown-live-preview-mode > *eww* buffer.
        Markdown-live-preview-window-function can be customized to open in a browser other than eww
        
        
