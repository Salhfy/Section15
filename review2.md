# Laravel Lesson レビュー②

## Todo編集機能

### @method('PUT')を記述した行に何が出力されているか
　　<input type="hidden" name="_method" value="PUT">
### findメソッドの引数に指定しているIDは何のIDか
　　モデルが持っている主キー
### findメソッドで実行しているSQLは何か
　　select * from テーブル where 主キー = 値 limit 1
### findメソッドで取得できる値は何か
　　主キーのレコードを 1 件取得して、そのモデルのインスタンスを返す
### saveメソッドは何を基準にINSERTとUPDATEを切り替えているのか
　　 モデルの$existsプロパティを見てINSERT / UPDATEを切り替える、$exists = falseの場合はINSERT、trueの場合はUPDATE
## Todo論理削除

### traitとclassの違いとは
　　classはルーティングとリクエスト処理などオブジェクトとして機能させ、traitはある機能のみ（メソッド）を継承させる
### traitを使用するメリットとは
　　trait は use で複数組み込めるので、継承階層に関係なく共通機能を追加可能
## その他

### TodoControllerクラスのコンストラクタはどのタイミングで実行されるか
　　　ルートにマッチしてインスタンス化されたタイミング、各アクションがよばれる前に必ず実行
### RequestクラスからFormRequestクラスに変更した理由
　　　バリデーションを専用クラスに分離することで複数のコントローラやアクションで使い回しやすく、またバリデーションルールを追加しやすくするため
### $errorsのhasメソッドの引数・返り値は何か
　　　引数はフィールド名（string）または複数フィールド名（array）、返り値はエラーが存在するかどうか（boolean）
### $errorsのfirstメソッドの引数・返り値は何か
　　　引数は第一引数に$key(string型のnull)第二引数に$format(string型のnull)、返り値はstring（最初のエラーメッセージ）または null（エラーがない場合）
### フレームワークとは何か
　　　よく使う機能をあらかじめ用意してくれている開発用の枠組み
### MVCはどういったアーキテクチャか
　　　データ（Model）、画面（View）、処理の流れ（Controller）を分離することでコードの可読性、保守性、再利用性を高めてくれるアーキテクチャ
### ORMとは何か、またLaravelが使用しているORMは何か
　　　プログラミング言語のオブジェクト操作によってデータベースを扱えるようにする仕組み。LaravelではEloquent
### composer.json, composer.lockとは何か
　　　composer.jsonは必要なライブラリとその条件を書く宣言ファイル、composer.lockは実際にインストールされたライブラリのバージョンを固定する記録ファイル、
          チーム開発や本番運用で環境差異をなくすために重要
### composerでインストールしたパッケージ（ライブラリ）はどのディレクトリに格納されるのか
　　　プロジェクト直下のvenderディレクトリに格納
