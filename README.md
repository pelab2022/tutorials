# tutorials
HP作成のチュートリアル。各項目の詳細な資料は、要望があれば作るかも？

この資料はpublicに設定されているため、**パスワード等は書き込まないでください**。

基本的には、新b3のHP係を中心に活動することになります。

## 開発環境について
### テキストエディタ
各種コーディングに必要。
VSCodeが使いやすくておすすめですが、使い慣れたものがあればそちらを使いましょう。

### Linux環境について
Windowsの人は、Linux環境を入れると便利です。
プログラミング基礎/応用やシミュレーション演習(必修)でも必要になるため、まだない人はこの機会に導入しましょう。

linux環境としては、
- WSL(Windows subsystem for Linux) : Windows上でLinuxを動かせる機能。こっちがおすすめ。
  WSL1(旧版)とWSL2(新版)があります。違いは[公式ページ](https://docs.microsoft.com/ja-jp/windows/wsl/compare-versions)に書いてあります。
  OSはUbuntuがおすすめ。Microsoft Storeから入れられます。
  - WSL1 : 旧版。初期設定ではこちら。Windows側へのファイルアクセスが速め。後からでも移行できるので、とりあえずこちらを使うのがおすすめ。
  - WSL2 : 新版。完全な仮想環境で、設定がやや面倒。仮想環境内のファイルへのアクセスが高速。
- Cygwin : なぜかプログラミング基礎などで推奨される。多分WSLを使える先生/TAがいないだけなので、WSLが推奨。
  既に導入している場合は、こちらでもいいです。

Macの人はMacのターミナルでほぼ同じコマンドが使えます。

### git
Linux環境では初めから入っています。Macではターミナルから、でインストールできます。
```bash
brew install git
```

## webページの実装について
以下のページを、デザイン班から受け取ったイメージ通りに実装します。
- メインページの作成。
  - メインページは、ブラウザ(フロントエンド)完結にします。サーバ側(バックエンド)での処理は、サーバスペック的に厳しいです。他のページも同様。
- 各展示の紹介ページ作成。
  - オンサイトの場合は、単なる紹介ページ。紹介文などは各展示の担当者に考えてもらいましょう。
  - オンライン化などで、埋め込み可能なウェブアプリになっている場合は、埋め込みもします。
  - 各展示でサーバ側処理が必要になる場合は、別途サーバを借りることになります。別サーバはHP係ではなくその班の人に管理してもらい、HP係は紹介ページのみ作成します。
- (あれば)企画ページの作成。
  - 去年は「スタンプラリーをやりたい」とのことで、その企画のページがあります。
    - 各企画ページにある合言葉を企画ページで入力すると、スタンプが押される仕様。
  - そのような企画が特になければ、必要ないです。

### 参考：過去のページ
#### 一昨年(2020)まで
HPは生html/css/jsだけで書かれていて、新b3のHP担当2、3人が担当していていました。
- [2016年度](https://www.pemayfes.t.u-tokyo.ac.jp/2016)
- [2017年度](https://www.pemayfes.t.u-tokyo.ac.jp/2017)
- [2018年度](https://www.pemayfes.t.u-tokyo.ac.jp/2018)
- [2019年度](https://www.pemayfes.t.u-tokyo.ac.jp/2019)
- [2020年度](https://www.pemayfes.t.u-tokyo.ac.jp/2020)

#### 去年(2021)
オンライン対応、スマホ対応でUIを充実させるため、Next.jsというフレームワークを使いました。
コードは複雑化していますが、基本構成は一昨年までと変わりません。
不要な部分を消した骨組みをgitで共有する予定で、これをベースにすると楽に作れるはずです。

注意として、コンパイルによりHTML/CSS/JSのコードを生成する仕様上、ブラウザに送られてくるソースはとても読めたものではないです。
参考にする場合は、[コンパイル前のコード](https://github.com/pelab2021/2021hp_next)を見ましょう。
- [2021年のコード](https://github.com/pelab2021/2021hp_next)は非公開設定になっています。すぐに見たい場合は要望があれば2021年のグループに追加します。

## 勉強してほしいこと
"*" 付きは必須事項。
### git*
まずそもそも、共同開発ができるようなバージョン管理ツールがないと開発ができません。
去年はgitを使いました。

### HTML/CSS/JavaScript*
フロントエンド(=ブラウザ側)アプリケーション開発の基本。
極論、HTML/CSSだけでもウェブサイトは作れる...が、UIを作るにはJavaScriptが必要。
拡張子は、
- HTML：.html(.htm)
- CSS：.css
- JavaScript：.js
#### 参考資料
- https://developer.mozilla.org/ja/docs/Learn/Front-end_web_developer

### [TypeScript](https://www.typescriptlang.org/)
JavaScriptに静的に型を付けたもの。
型推論が優秀で、JavaScriptのコードがそのままコンパイル可能。そのため、細かい型の指定法などは勉強しなくてもOK。
VScodeの補完などが使えるようになるため、使うのが推奨。

型の明示的な指定は必須ではないが、バグ防止のため、函数の引数や複雑なオブジェクトには明示的につけるとよい。
拡張子は".tx"。

### [React](https://ja.reactjs.org/)
フロントエンド開発のためのJavaScriptのライブラリ。
JSXというhtmlっぽい記法で書かれたhtmlオブジェクトを返す函数として各コンポーネントを記述する。
html,css,JavaScript全てをJavaScript上で書くことになるため、ある程度JSになれていないと難しいかも。
なお、TypeScriptに限り、拡張子が".tsx"に変化するため注意が必要。(".ts"だとトランスパイラがJSXに対応できずエラーを吐く)

公式チュートリアルが分かりやすい。<br/>
要望があれば資料作るかも？

### [Next.js](https://nextjs.org/)
Reactのフレームワーク(更に使いやすくしたもの)。
Reactが使えれば、追加で必要な知識はあまりない。

### [Material-UI](https://mui.com/)
去年使ったReact用のCSSフレームワーク。ボタンやサイドバーなど、頻繁に使うコンポーネントが大体揃ってる。

CSSフレームワークは他にもいろいろあるので、デザイン係の人と話して検討するといいかも？

### [styled-component](https://styled-components.com/)
コンポーネントの装飾が楽にできる(CSSで書ける)。

## サーバ管理について
webparkという東大で借りている共有サーバを使います。
実体は[さくらのレンタルサーバ](https://rs.sakura.ad.jp/)で、[コントロールパネル](https://secure.sakura.ad.jp/rs/cp/)内のファイルマネージャから操作できます。
ドメイン名とパスワードは別途共有します。

### ディレクトリ構成
WindowsやMacにおけるフォルダのことを、サーバのOS(などのLinux系OS)ではディレクトリと呼びます。
説明は現在執筆中...
.<br/>
www : 公開されるディレクトリ。これ以外のディレクトリは基本いじらない。(*1)
├── .htaccess : Webサーバの設定ファイル。<br/>
├── .htpasswd : Basic認証のパスワード設定用ファイル。<br/>
├── index.html->20xx/.../index.html : メインページの実体へのリンク。(*2)<br/>
├── 201x : 201x年度のディレクトリ。<br/>
├── 2020 : 2020年度のディレクトリ。<br/>
└── 2021 : 2021年度のディレクトリ。パソコン版(/pc)とスマホ版(/sp)に分かれています。<br/>
　　├── pc : PC版。<br/>
　　　　├── index.html : PC版のメインページ。 <br/>
　　　　:
　　└── sp <br/>
　　　　├── index.html : スマホ版のメインページ。 <br/>
　　　　:

(*1) : そもそも他に書き込み可能なディレクトリが"tmp"しかありません。これはファイルの一時保存などで使えますが、基本使いません。
(*2) : 正確にはシンボリックリンクといい、ショートカットのようなもの。
  .htaccessによるPC版/スマホ版の振り分けがうまくいっていないとき用の保険。
  サーバに入り、[lnコマンド](https://qiita.com/takuyanin/items/3682ac19bbbc21792849)で設定できます。
  サーバに入る方法については後述。

### .htaccessについて
[ここ](https://qiita.com/sanogemaru/items/7e5bd6e8dc9b04c9978e)とかが分かりやすい。
テスト時にBasic認証を掛けたり、httpをhttpsにリダイレクトしたり、pc版ページとスマホ版ページの振り分けをしたりします。
細かい記法は後ほど追記します。

### Basic認証と.htpasswdについて
公開前に実際にサーバにデータを上げて動作確認をします。
HP係以外の人にも見てもらいますが、この時点では来場者に見られたくない！...という場合にBasic認証を掛けます。
ユーザ名とパスワードでログインする単純な奴です。

ただこのタイミングで見に来る人はそう多くないと思うので、必須ではありません。
掛けない場合は、見られて困る情報(パスワード、不要な個人情報など)が乗っていないかどうか手元でチェックしましょう。

### advanced: サーバに入る
シンボリックリンクの書き換えは、サーバに入ってやる必要があります。
.htaccessや.htpasswdの編集も、サーバに入ってやる方が楽です。
サーバなどのリモートコンピュータと通信するための[ssh](https://ja.wikipedia.org/wiki/Secure_Shell)というプロトコルがあり、
Linux環境では、[sshコマンド](https://qiita.com/chihiro/items/c24fcbd82d1d8833e497)でサーバに入れます。
パスワード認証なので、各自のコンピュータ側での設定は要りません。
Macでもほぼ同じはずです。

### advanced: 一括アップロード
ファイルのアップロードはできますが、フォルダのアップロードはコントロールパネルからはできません。
ですが、sshによりファイルを転送する[scpコマンド](https://qiita.com/chihiro/items/142ebe6980a498b5d4a7)を使えば、
ディレクトリごとコピーして送ることができます。
