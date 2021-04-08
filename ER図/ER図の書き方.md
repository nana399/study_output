## ER図とは

- ER図とは、「**データベース設計（データモデリング）で使う設計手法」** のこと
- 海外では「Entity Relationship Diagram」と呼ばれている。
- 「エンティティ」「アトリビュート」「リレーション」「カーディナリティ」と呼ばれるオブジェクトで構成

[![Image from Gyazo](https://i.gyazo.com/75012d87058a9cc1c3110d93d16e6fdf.gif)](https://gyazo.com/75012d87058a9cc1c3110d93d16e6fdf)

## 主な記法２種類

- IE記法
- IDEF1X記法

## IE記法

- IE記法とは、リレーションが鳥の足のような形をしていることから、別名「鳥の足記法」とも呼ばれている。
- リレーションが直感的に理解しやすいことから、新人研修などでよく使われている

[![Image from Gyazo](https://i.gyazo.com/4a5787bb41b40a21f6a7e55dd36506ff.gif)](https://gyazo.com/4a5787bb41b40a21f6a7e55dd36506ff)

## IDEF1X記法

- IDEF1X記法とは、アメリカの国立標準技術研究所（NIST）で作られたER図の記法
- IE記法と並び世界中で使われている。
- IE記法と異なり、リレーションを「●」などで表現することが特徴
- IE記法より細かい表現ができることで人気がある。
- その分IE記法に比べて直感的な分かりやすさは低くなりがち。

[![Image from Gyazo](https://i.gyazo.com/80e4dc8b8d4fd16bfc79d318caff6864.gif)](https://gyazo.com/80e4dc8b8d4fd16bfc79d318caff6864)

ER図の基本ルール

- ER図は、**「エンティティ」**と呼ばれるデータのまとまりや**「アトリビュート」**というエンティティの詳細情報、エンティティ同士の関係を表現する**「リレーション」**と**「カーディナリティ」**を組合せて書く。

- 「IE記法」と「IDEF1X記法」の２つの記法の違い

→**「カーディナリティ」**のルール

[![Image from Gyazo](https://i.gyazo.com/62f51cae8ac7878229908d9ed78e1d95.gif)](https://gyazo.com/62f51cae8ac7878229908d9ed78e1d95)

## エンティティ

[![Image from Gyazo](https://i.gyazo.com/06fb12b239f203a804350625c35d6f08.gif)](https://gyazo.com/06fb12b239f203a804350625c35d6f08)

- 「エンティティ」とはデータのまとまりのこと
- エンティティの中に、アトリビュートという属性情報がある
- ↑の図は、「顧客」に関するエンティティ（データのまとまり）の例

## アトリビュート（属性）

[![Image from Gyazo](https://i.gyazo.com/fd1f33bcbed518856dcf7831eeae8ca1.gif)](https://gyazo.com/fd1f33bcbed518856dcf7831eeae8ca1)

- 「アトリビュート」とは、エンティティの中の属性情報のこと
- 赤丸で囲われているものすべてがアトリビュート

## リレーション

[![Image from Gyazo](https://i.gyazo.com/3b1112f66c55f0bcde7fed90890b9b6d.gif)](https://gyazo.com/3b1112f66c55f0bcde7fed90890b9b6d)

- 「リレーション」とは、エンティティ同士の関係を表現する線のこと
- リレーションの詳細は、「カーディナリティ」という記号を使って表現する
- 上図は、注文テーブルと注文詳細テーブルがリレーション関係にあることを表現

## カーディナリティ（多重度）

[![Image from Gyazo](https://i.gyazo.com/989519870e15fd457b07608c7ee9090c.gif)](https://gyazo.com/989519870e15fd457b07608c7ee9090c)

- 「カーディナリティ」とは、「１対１」「１対多」「多対多」など、リレーションの詳細を表現する記号のこと
- 日本語では「多重度」と呼ばれている
- リレーションの始点と終点を、定められた記号で表現する

## エンティティの依存関係・非依存関係

**依存関係**

[![Image from Gyazo](https://i.gyazo.com/b3d35b8672ad971cb6a7cb97fefcb1c2.gif)](https://gyazo.com/b3d35b8672ad971cb6a7cb97fefcb1c2)

- 「依存関係」とは、上図の注文テーブルと注文明細テーブルのように、必ず紐づくデータが存在しなければならない関係のこと
- エンティティ間で親子関係になる

**非依存関係**

[![Image from Gyazo](https://i.gyazo.com/ad8e990b11901f622ff04bceb0abe7b4.gif)](https://gyazo.com/ad8e990b11901f622ff04bceb0abe7b4)

- 「非依存関係」とは、エンティティ間で「親子関係がない」リレーションのこと
- 右と左がそれぞれ独立していても成り立つ的なやつ
- 非依存関係の場合、どちらのエンティティも四角の枠線で表現

# 書き方

## IE記法

- IE記法は、「○」「l」「鳥の足（3つ股の線）」という3つの記号を組合せて表現

[![Image from Gyazo](https://i.gyazo.com/929f9f00825ef8d95e9d91c8514b103e.gif)](https://gyazo.com/929f9f00825ef8d95e9d91c8514b103e)

### **１対１の関係**

![https://i0.wp.com/it-koala.com/wp-content/uploads/2016/09/IE%E8%A8%98%E6%B3%95_%EF%BC%91%E5%AF%BE%EF%BC%91.png?resize=527%2C217&ssl=1](https://i0.wp.com/it-koala.com/wp-content/uploads/2016/09/IE%E8%A8%98%E6%B3%95_%EF%BC%91%E5%AF%BE%EF%BC%91.png?resize=527%2C217&ssl=1)

### **１対多の関係（あいまいな表現）**

![https://i2.wp.com/it-koala.com/wp-content/uploads/2016/09/IE%E8%A8%98%E6%B3%95_1%E5%AF%BE%E5%A4%9A.png?resize=525%2C221&ssl=1](https://i2.wp.com/it-koala.com/wp-content/uploads/2016/09/IE%E8%A8%98%E6%B3%95_1%E5%AF%BE%E5%A4%9A.png?resize=525%2C221&ssl=1)

### **1対0以上の関係**

![https://i1.wp.com/it-koala.com/wp-content/uploads/2016/09/IE%E8%A8%98%E6%B3%95_1%E5%AF%BE0%E4%BB%A5%E4%B8%8A.png?resize=520%2C214&ssl=1](https://i1.wp.com/it-koala.com/wp-content/uploads/2016/09/IE%E8%A8%98%E6%B3%95_1%E5%AF%BE0%E4%BB%A5%E4%B8%8A.png?resize=520%2C214&ssl=1)

### **1対1以上の関係**

![https://i1.wp.com/it-koala.com/wp-content/uploads/2016/09/IE%E8%A8%98%E6%B3%95_1%E5%AF%BE1%E4%BB%A5%E4%B8%8A-1.png?resize=519%2C209&ssl=1](https://i1.wp.com/it-koala.com/wp-content/uploads/2016/09/IE%E8%A8%98%E6%B3%95_1%E5%AF%BE1%E4%BB%A5%E4%B8%8A-1.png?resize=519%2C209&ssl=1)

上図では、注文テーブルと注文明細テーブルは「１対１以上の関係」であることを表現している例。注文テーブルに対して、注文した商品と数量のまとまりである明細は必ず１レコード存在しなければならない。「1対1以上の関係」は、このようなケースなどでよく使われる。

### **多対多の関係**

![https://i0.wp.com/it-koala.com/wp-content/uploads/2016/09/IE%E8%A8%98%E6%B3%95_%E5%A4%9A%E5%AF%BE%E5%A4%9A.png?resize=520%2C216&ssl=1](https://i0.wp.com/it-koala.com/wp-content/uploads/2016/09/IE%E8%A8%98%E6%B3%95_%E5%A4%9A%E5%AF%BE%E5%A4%9A.png?resize=520%2C216&ssl=1)

上図は、社員マスタと社内サークルマスタは「多対多の関係」であることを表現している例。「多対多の関係」でも、「0以上」「1以上」「0以上1以上どちらも表現しない（あいまい）」という表現が可能。

### **0または１対多の関係**

![https://i0.wp.com/it-koala.com/wp-content/uploads/2016/09/IE%E8%A8%98%E6%B3%95_%EF%BC%90%E3%81%BE%E3%81%9F%E3%81%AF%EF%BC%91%E5%AF%BE%E5%A4%9A.png?resize=520%2C218&ssl=1](https://i0.wp.com/it-koala.com/wp-content/uploads/2016/09/IE%E8%A8%98%E6%B3%95_%EF%BC%90%E3%81%BE%E3%81%9F%E3%81%AF%EF%BC%91%E5%AF%BE%E5%A4%9A.png?resize=520%2C218&ssl=1)

上図は、社員マスタと社内サークルマスタは「０または１対多の関係」であることを表現。上述の「多対多」の例との違いは、社員は1つのサークルにしか所属できないこと。所属社員が0名のサークルもある。


## IDEDF1X記法

- IE記法に比べて細かい表現ができる事が特徴

[Untitled](https://www.notion.so/48b2c4196a524ec0853a9c3de684a2ed)

### **１対１の関係**

![https://i0.wp.com/it-koala.com/wp-content/uploads/2016/09/IDEF1X%E8%A8%98%E6%B3%95_1%E5%AF%BE1.png?resize=525%2C218&ssl=1](https://i0.wp.com/it-koala.com/wp-content/uploads/2016/09/IDEF1X%E8%A8%98%E6%B3%95_1%E5%AF%BE1.png?resize=525%2C218&ssl=1)

### **１対0以上の関係**

![https://i1.wp.com/it-koala.com/wp-content/uploads/2016/09/IDEF1X%E8%A8%98%E6%B3%95_1%E5%AF%BE%E5%A4%9A.png?resize=522%2C215&ssl=1](https://i1.wp.com/it-koala.com/wp-content/uploads/2016/09/IDEF1X%E8%A8%98%E6%B3%95_1%E5%AF%BE%E5%A4%9A.png?resize=522%2C215&ssl=1)

### **１対１以上の関係**

![https://i1.wp.com/it-koala.com/wp-content/uploads/2016/09/IDEF1X%E8%A8%98%E6%B3%95_%EF%BC%91%E5%AF%BE%EF%BC%91%E4%BB%A5%E4%B8%8A.png?resize=519%2C213&ssl=1](https://i1.wp.com/it-koala.com/wp-content/uploads/2016/09/IDEF1X%E8%A8%98%E6%B3%95_%EF%BC%91%E5%AF%BE%EF%BC%91%E4%BB%A5%E4%B8%8A.png?resize=519%2C213&ssl=1)

### **多対多の関係**

![https://i1.wp.com/it-koala.com/wp-content/uploads/2016/09/IDEF1X%E8%A8%98%E6%B3%95_%E5%A4%9A%E5%AF%BE%E5%A4%9A.png?resize=519%2C211&ssl=1](https://i1.wp.com/it-koala.com/wp-content/uploads/2016/09/IDEF1X%E8%A8%98%E6%B3%95_%E5%A4%9A%E5%AF%BE%E5%A4%9A.png?resize=519%2C211&ssl=1)

### **０または１対多の関係（非依存リレーションの場合）**

![https://i2.wp.com/it-koala.com/wp-content/uploads/2016/09/IDEF1X_%E9%9D%9E%E4%BE%9D%E5%AD%98%E3%83%AA%E3%83%AC%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3.png?resize=528%2C209&ssl=1](https://i2.wp.com/it-koala.com/wp-content/uploads/2016/09/IDEF1X_%E9%9D%9E%E4%BE%9D%E5%AD%98%E3%83%AA%E3%83%AC%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3.png?resize=528%2C209&ssl=1)

# システムシナリオを明確にする

- ER図を書くには、システムシナリオが明確になっている事が大前提
- ユースケース図やユースケース記述、アクティビティ図などをインプットとしてER図を設計

**ユースケースの図の例**

[![Image from Gyazo](https://i.gyazo.com/50be409171285b8125e9dc94196ff84e.gif)](https://gyazo.com/50be409171285b8125e9dc94196ff84e)

### **ユースケース記述の例**

![https://i1.wp.com/it-koala.com/wp-content/uploads/2016/09/ER%E5%9B%B3%E7%94%A8%E3%83%A6%E3%83%BC%E3%82%B9%E3%82%B1%E3%83%BC%E3%82%B9%E8%A8%98%E8%BF%B0.png?resize=662%2C308&ssl=1](https://i1.wp.com/it-koala.com/wp-content/uploads/2016/09/ER%E5%9B%B3%E7%94%A8%E3%83%A6%E3%83%BC%E3%82%B9%E3%82%B1%E3%83%BC%E3%82%B9%E8%A8%98%E8%BF%B0.png?resize=662%2C308&ssl=1)

# エンティティを洗い出す

ユースケース図やユースケース記述、アクティビティ図などをもとにエンティティを洗い出す。

### **ユースケース図からのエンティティ洗い出し**

[![Image from Gyazo](https://i.gyazo.com/bbba62948d936597f5e47c9d9a877fbd.gif)](https://gyazo.com/bbba62948d936597f5e47c9d9a877fbd)

### **ユースケース記述からのエンティティ洗い出し**

![https://i1.wp.com/it-koala.com/wp-content/uploads/2016/09/ER%E5%9B%B3_%E3%82%A8%E3%83%B3%E3%83%86%E3%82%A3%E3%83%86%E3%82%A3%E3%81%AE%E6%B4%97%E5%87%BA%E3%81%97_%E3%83%A6%E3%83%BC%E3%82%B9%E3%82%B1%E3%83%BC%E3%82%B9%E8%A8%98%E8%BF%B0-1.png?resize=737%2C313&ssl=1](https://i1.wp.com/it-koala.com/wp-content/uploads/2016/09/ER%E5%9B%B3_%E3%82%A8%E3%83%B3%E3%83%86%E3%82%A3%E3%83%86%E3%82%A3%E3%81%AE%E6%B4%97%E5%87%BA%E3%81%97_%E3%83%A6%E3%83%BC%E3%82%B9%E3%82%B1%E3%83%BC%E3%82%B9%E8%A8%98%E8%BF%B0-1.png?resize=737%2C313&ssl=1)

↑のユースケース図とユースケース記述から「顧客」「注文」「商品」「お届け先」「請求先」「配送方法」「決済方法」という７つのエンティティが洗い出せた

# 「マスタ系」と「トランザクション系」

データは、大きく「[マスタ系](https://e-words.jp/w/%E3%83%9E%E3%82%B9%E3%82%BF%E3%83%BC%E3%83%87%E3%83%BC%E3%82%BF.html)」と「[トランザクション系](https://e-words.jp/w/%E3%83%88%E3%83%A9%E3%83%B3%E3%82%B6%E3%82%AF%E3%82%B7%E3%83%A7%E3%83%B3%E3%83%87%E3%83%BC%E3%82%BF.html)」に分かれる。

例えば、下図では「お届け先」「請求先」「配送方法」「決済方法」が、トランザクションとして１つのエンティティに。

[![Image from Gyazo](https://i.gyazo.com/879097c8ab740dfd60188959edccf129.gif)](https://gyazo.com/879097c8ab740dfd60188959edccf129)

# アトリビュート（属性）を洗い出す

- アトリビュートの洗出しは、画面設計書や類似システムの画面を元に行うと効率的


[![Image from Gyazo](https://i.gyazo.com/93bde695a566720d4d0f3fdc88253a32.gif)](https://gyazo.com/93bde695a566720d4d0f3fdc88253a32)

**アトリビュートを整理した例**

[![Image from Gyazo](https://i.gyazo.com/fef84902d02e1995325b05266658b978.gif)](https://gyazo.com/fef84902d02e1995325b05266658b978)

# ER図に落とし込む

- リレーションや主キー、外部キーを設計しER図に落とし込む。

[![Image from Gyazo](https://i.gyazo.com/b15b87b34e81ebb0053e692e4f5e6998.gif)](https://gyazo.com/b15b87b34e81ebb0053e692e4f5e6998)
