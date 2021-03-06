## Cherry_chapter07_クラスの作成を理解する

### 7.2オブジェクト指向プログラミング関連用語

### クラス
- データ型の一種。オブジェクトのひな形
- Rubyではオブジェクトは必ずクラスに属す

### オブジェクト、インスタンス、レシーバ
- クラスをもとに作られたデータのかたまり。

### メソッド、メッセージ
- オブジェクトがもつ「動作」

### 状態（ステート）
- オブジェクトごとに保持されるデータのことを「オブジェクトの状態」と呼ぶ。

### 属性（アトリビュート、プロパティ）
- オブジェクトから取得、オブジェクトに設定できる値を属性と呼ぶ。

### 7.3 クラスの定義

### インスタンス変数とアクセサメソッド
- インスタンス変数とは同じオブジェクト内で共有される変数のこと
- アクセサメソッドとは、インスタンス変数の値を読み書きするメソッドのこと。`attr_accessor`メソッドを使うとインスタンス変更用のメソッドを使わなくていい。

### ローカル変数
- メソッドやブロック内部で作成される変数のこと。
- メソッドやブロック内部でのみ有効、メソッドやブロックが呼び出されるたびに作り直される。
- アルファベットの小文字、アンダースコアで始める。
- ローカル変数は宣言と代入（作成）を同時に行う


### クラスメソッドの定義
- ひとつひとつのインスタンスに含まれるデータは使わないメソッドを定義したい場合にクラスメソッドを定義する。
`self.`をつけるとクラスメソッドになる。

### 7.5 selfについて
- メソッド内でセッターメソッドを呼び出す時は、必ず`self.method`という形にする。つけないと、ローカル変数の代入と解釈される。
- クラスメソッドをインスタンスメソッドから呼び出すときは、`classname.methodname`/`self.class.methodname`にする

### 7.6 クラスの継承
- DVDクラスがProductクラスを継承するとき、ProductクラスはDVDクラスの「スーパークラス」、DVDクラスはProductクラスの「サブクラス」と呼ぶ。
- サブクラスからスーパークラスに矢印を伸ばすことで、その継承関係を表す
- クラスの継承が適切かどうかは、「サブクラスはスーパークラスの一種である(Subclass is a Superclass.)」が違和感がないこと。「is-aの関係」

- Rubyの継承は単一継承（ただし、ミックスインという多重継承に似た機能をもつ）
- 独自に作成したクラスはデフォルトでObjectクラスを継承する
- Objectクラス以外を継承したい場合は、
`class subclass < superclass
end`
と書く
- サブクラスでは、スーパークラスと同じ名前のメソッドを定義することでオーバーライトできる(7.6.6)

### 7.7クラスの公開レベル

### publicメソッド
- クラスの外部からでも自由に呼び出せる
- initializeメソッド以外のインスタンスメソッドはデフォルトでpublicメソッドになる

### privateメソッド
- クラス内部でのみ使えるメソッド。レシーバを指定できないので、外部からの呼び出しができない。
- private書いた下で定義されたものはprivateメソッドになる。ただし、インスタンスメソッドのみ。
- クラスメソッドをprivateにしたい場合は`class << self`をprivateより先に書くか、`private_class_method :methodname`を追記する
- self付きで呼び出すことができない。selfというレシーバを指定したことになるから。
- サブクラスでも呼び出せ、オーバーライトすることも可能(7.7.3)
- 既存のメソッド名をprivateメソッドに渡すと、渡されたメソッドがprivateメソッドになり、その下に定義したメソッドはpublicメソッドのままになる。(7.7.6)

### protectedメソッド(7.7.7)
- 外部に公開しないが、同じクラスやサブクラスではレシーバ付きで呼び出すことができる。

### 7.8定数について
- `classname::constant`でクラス外部から定数を直接参照することが可能
- クラス内部、外部から再代入可能。warningはでる
- 定数の値を変更したくない場合は`freeze`を使う


### mutable/immutable(4.7.14)
- ミュータブルなオブジェクトには、破壊的な変更が適用できる。文字列（Stringクラス）はミュータブルなので、初期値を設定するときはブロックを使うと誤って変更してしまうことが少なくなる。
- Rubyにおいてイミュータブルなデータ型は数値、シンボル、true/false, nil





