## c++(自分が使ったもの)
### 1. クラスの作成
- ロボットという名前のクラスを作成
```cpp
class Robot {

};
```

デフォルトではプライベート
```cpp
public:
```
とすることでパブリックになる

### 2. コンストラクタ
- コンストラクタはオブジェクト指向プログラミングで、クラスからオブジェクトを生成する際に自動的に呼び出される特別なメソッドのこと
```cpp
Robot swerve_drive; // オブジェクトを生成
```
- コンストラクタはクラス名と同じ名前を持ちvoidなどを記述しない
- オブジェクトの生成時に初期値を設定することができる
さらにオブジェクトの初期化処理をまとめて記述できる
```cpp
// コンストラクタで、必要なオブジェクトを受け取る
Steer::Steer(Conversion::Available_Data &div_a, Conversion::Available_Data &div_b) 
    : division_a(div_a), division_b(div_b), put_A(0.0f), put_B(0.0f) {
}
```

```cpp 
Steer::Steer(...)
```
- これはSteerクラスのコンストラクタ定義
- クラスがインスタンス化されるときに呼ばれる

```cpp
Conversion::Available_Data &div_a, Conversion::Available_Data &div_b
```
- Conversion::Available_Data型の参照を2つ受け取る
- & は参照渡しで、引数のコピーを作らず、元のオブジェクトを参照
- div_a と div_b はそれぞれ、インスタンスの中でdivision_aとdivision_bに割り当てられる

```cpp
: division_a(div_a), division_b(div_b), put_A(0.0f), put_B(0.0f)
```
- これは メンバ初期化リストで,クラスのメンバ変数を効率的に初期化する方法
- division_a(div_a) → クラスのメンバ変数 division_a を、引数 div_a で初期化
- put_A(0.0f) → put_A を 0.0f（float型の0）で初期化

#### なぜ初期化リストを使うの？
- コンストラクタ本体で代入するよりも 効率が良い
- 参照やconstメンバは初期化リストでしか初期化できない