---
theme: default
layout: cover
---

# まあまあなコード

<!--

いいコードが書ければいいのですがなかなか難しいのでまあまあなコードを書けるようにがんばろうっていうはなしです

-->

---
theme: default
---

# ゴール

<ul>
  <li v-click>コーディングスタイルについて知る</li>
  <li v-click>悪いコードが少しわかるようになる</li>
</ul>

<!--

+ コーディングスタイルについて知る
コーディングスタイルというものがなにかわからない人はその存在を知ってほしいです
自分がコードを書く上での指針となるので

+ 悪いコードが少しわかるようになる
治安をよくしていきたいです
がんばりましょう

-->


---

# どういうコードを書けばいい？

<ul>
  <li v-click>基準は言語によって異なる</li>
  <li v-click>PHPの場合はPSR-1, PSR-12が基準</li>
  <li v-click>読んだことない人は一度は読みましょう</li>
</ul>

<!--

+ 基準は言語によって異なる
JSにはJSの、PHPにはPHPのといった感じで言語によってこうしたほうがいいみたいな基準は結構かわります
JSはJSでいろいろ種類があるんですがね・・・

+ PHPの場合はPSR-1, PSR-12が基準
PHPの場合はわかりやすくPSR(PHP Standards Recommendations)という規約に沿って書くのが一般的です

+ 読んだことない人は一度は読みましょう
いろいろ種類があるのですがコーディングスタイルにかかわるものは1と12になるのでとりあえずその二つだけでいいです

https://www.ritolab.com/posts/91
https://www.ritolab.com/posts/208

-->

---
layout: center
---

# 悪いコードとは？

<!--

口で説明するのも大変なので実際にコードをみてもらおうと思います
ちなみに今回ピックアップする内容は全て私がここに入社してから見たものです

-->

---
clicks: 15
---

<style>
.slidev-vclick-hidden {
  display: none;
}
</style>

<div class="grid grid-cols-2 gap-4">
<div>

# コード例

<ul>
<li v-click="1">ブレースの位置</li>
<li v-click="3">スペース・改行</li>
<li v-click="5">上記はコード整形ツールで対応するのが望ましい(PHP-CS-Fixer, PHP_CodeSnifferなど)</li>
<li v-click="6">プロパティ宣言は1行につき1つのみ宣言するべき</li>
<li v-click="8">プロパティは全て宣言する</li>
<li v-click="10">初期化していない変数・プロパティに<br>いきなり配列を入れない</li>
<li v-click="12"><code>if</code>文で比較する際はできるだけbool値を渡す</li>
<li v-click="12">関数内で<code>return</code>する際は<br>全てのケースで<code>return</code>する</li>
<li v-click="14">メソッドはキャメルケースで書く</li>
<li v-click="14">可視性は省略しない</li>
</ul>

</div>
<div>
<div v-click-hide="2">

```php {all|1,5,10,13} {at:0}
class Dog{
    public $birthday, $families;
    private $history;
    
    public function __construct($birthday, $families){
        $this->birthday=$birthday;
        $this->families=$families;
        $this->age=calc_age($birthday)
    }
    function walk_with($partner){
        $this->history[]=$partner;
    }
    function current_partner(){
        if($this->history){
            return end($this->history);
        }
    }
}
```

</div>
<div v-if="$slidev.nav.clicks >= 2 && $slidev.nav.clicks < 5">

```php {2,7,13,17|1,3,6,8,9,10,14,18} {at:2}
class Dog
{
    public $birthday,$families;
    private $history;

    public function __construct($birthday,$families)
    {
        $this->birthday=$birthday;
        $this->families=$families;
        $this->age=calc_age($birthday)
    }
    function walk_with($partner)
    {
        $this->history[]=$partner;
    }
    function current_partner()
    {
        if($this->history){
            return end($this->history);
        }
    }
}
```

</div>

<div v-if="$slidev.nav.clicks >= 5 && $slidev.nav.clicks < 7">

```php {1,3,6,8,9,10,15,20|3} {at:5}
class Dog
{
    public $birthday, $families;
    private $history;

    public function __construct($birthday, $families)
    {
        $this->birthday = $birthday;
        $this->families = $families;
        $this->age = calc_age($birthday)
    }

    function walk_with($partner)
    {
        $this->history[] = $partner;
    }

    function current_partner()
    {
        if ($this->history) {
            return end($this->history);
        }
    }
}
```

</div>

<div v-if="$slidev.nav.clicks >= 7 && $slidev.nav.clicks < 9">

```php {3,4|11} {at:7}
class Dog
{
    public $birthday;
    public $families;
    private $history;

    public function __construct($birthday, $families)
    {
        $this->birthday = $birthday;
        $this->families = $families;
        $this->age = calc_age($birthday)
    }

    function walk_with($partner)
    {
        $this->history[] = $partner;
    }

    function current_partner()
    {
        if ($this->history) {
            return end($this->history);
        }
    }
}
```

</div>

<div v-if="$slidev.nav.clicks >= 9 && $slidev.nav.clicks < 11">

```php {5,12|6,17} {at:9}
class Dog
{
    public $birthday;
    public $families;
    private $age;
    private $history;

    public function __construct($birthday, $families)
    {
        $this->birthday = $birthday;
        $this->families = $families;
        $this->age = calc_age($birthday)
    }

    function walk_with($partner)
    {
        $this->history[] = $partner;
    }

    function current_partner()
    {
        if ($this->history) {
            return end($this->history);
        }
    }
}
```

</div>

<div v-if="$slidev.nav.clicks >= 11 && $slidev.nav.clicks < 13">

```php {6,17|22,23,24} {at:11}
class Dog
{
    public $birthday;
    public $families;
    private $age;
    private $history = [];

    public function __construct($birthday, $families)
    {
        $this->birthday = $birthday;
        $this->families = $families;
        $this->age = calc_age($birthday)
    }

    function walk_with($partner)
    {
        $this->history[] = $partner;
    }

    function current_partner()
    {
        if ($this->history) {
            return end($this->history);
        }
    }
}
```

</div>

<div v-if="$slidev.nav.clicks >= 13 && $slidev.nav.clicks < 15">

```php {22|15,20} {at:13}
class Dog
{
    public $birthday;
    public $families;
    private $age;
    private $history = [];

    public function __construct($birthday, $families)
    {
        $this->birthday = $birthday;
        $this->families = $families;
        $this->age = calc_age($birthday)
    }

    function walk_with($partner)
    {
        $this->history[] = $partner;
    }

    function current_partner()
    {
        return $this->history[array_key_last($this->history)] ?? null;
    }
}
```

</div>

<div v-if="$slidev.nav.clicks >= 15">

```php {15,20} {at:15}
class Dog
{
    public $birthday;
    public $families;
    private $age;
    private $history = [];

    public function __construct($birthday, $families)
    {
        $this->birthday = $birthday;
        $this->families = $families;
        $this->age = calc_age($birthday)
    }

    public function walkWith($partner)
    {
        $this->history[] = $partner;
    }

    public function currentPartner()
    {
        return $this->history[array_key_last($this->history)] ?? null;
    }
}
```

</div>

</div>
</div>

<!--

これを見てどう思いますか？ひどいコードですよね
ぱぱっとみていきます

+ ブレースの位置
クラスにおいてブレースの位置は基本改行します

+ スペース・改行
コードがつまりすぎて窮屈です

+ 上記はコード整形ツールで対応するのが望ましい(PHP-CS-Fixer, PHP_CodeSnifferなど)
こんなのレビューするのもつらいし気をつけてもミスをするときはあるのでCIでやってしまいたいです

+ プロパティ宣言は1行につき1つのみ宣言するべき

+ プロパティは全て宣言する
ちなみにPHP8.2からは宣言必須です

+ 初期化していない変数・プロパティにいきなり配列を入れない
このパターン多くみます。今すぐやめましょう

+ if文で比較する際はできるだけbool値を渡す
+ 関数内でreturnする際は全てのケースでreturnする

今回はif文を書く必要もないのでこうします

+ メソッドはキャメルケースで書く
+ 可視性は省略しない

ちなみにグローバルな関数の場合はスネークケースです

-->

---

<style>
.slidev-layout.default.slidev-page-6 {
  overflow: auto;
}
</style>

# (おまけ) さらに嬉しいコードの例

```php
class Dog
{
    public DateTime $birthday;
    /** @var Family[] array */
    public array $families;
    private int $age;
    /** @var Parson[] */
    private array $history = [];

    public function __construct(DateTime $birthday, array $families)
    {
        $this->birthday = $birthday;
        $this->families = $families;
        $this->age = calc_age($birthday)
    }

    /**
     * @param Parson $partner
     * @return void
     */
    public function walkWith(Parson $partner): void
    {
        $this->history[] = $partner;
    }

    /**
     * @return Parson|null
     */
    public function currentPartner(): ?Parson
    {
        return $this->history[array_key_last($this->history)] ?? null;
    }
}
```

<!--

型定義があると補完がきくようになったり
後からコードをいじるときのヒントになったり
リファクタリング時に未使用関数を簡単に特定できるのでできるだけ書くようにしましょう

-->
