### 0708分

# 0708
今日やる事
- 社内システムのDB設計書の書き出しにより気づいたことを、アンチパターンにして今後追加するDBに対し適用できる仕様書！？を作成。

### 現時点で気になっていること（とりあえず書き出すので重複するかも！）
1. テーブル名が単数形や動詞！！
2. users,user_details,user_careers、ユーザーのテーブルは複数系で命名でも。ユーザーをもとにしたテーブルはuser_○○など
3. テーブルの命が分かりにくい！何に使われるか`[第１パラメータ]_[第２パラメータ]_[第３パラメータ]`
4. とりあえずID
5. user_id,
8. カラムの被りが多いので属性を足す○○_content,○○_id,○○_type
9. ~~削除有無、登録日時、更新日時、削除日時...らへんってtable_idで外に出せないの？（登録先のデータ件数が多くなりすぎるのか？）~~ >> やめ！
10. SEQあったりなかったり
11. 外部キー設定してない！？＞要勉強
12. カラム名が連番のやつ（A1,A2,A3...）
13. カラム名が英語＋日本語（例：timetable,confirm_jc（上長）,confirm_sm（総務）...)
14. 別名の表記が一定しない下記が`user_name'になってたり
    ```java
    concat(u.first_name, ' ', u.last_name) as userName,
    ```
15. FLOAT型＞NUMERICが良い？（少数部の管理）
16. 文字列比較のためのパターンマッチ記述＞MATCH関数
17. time,datetime,dateの使い分け
18. DATE型のカラムには名前を「受動態_on」,TIMESTAMP型のカラムには名前を「受動態_at」
19. int,smallint,tinyintの使い分け
20. mapper内の別名設定の必要性
21. そもそもコメントの備考欄が説明になっていない
22. 日時を表すカラムは過去形動詞
23. 1:n のテーブル名は単数形＿複数形 (Ex.user_comments )
24. n:n のテーブル名は複数形＿複数形 (Ex.categories_types )
25. 外部キーを表すカラム名は対象テーブル名の単数形 (Ex.users -> user_id )
26. テーブル名に動詞は使わない (Ex.opens)
27. 複数単語の連携はスネークケース（例：sample_snake_word）
28. 作成日時（created_at）は`not null`
29. 更新日時、削除日時（update_at,delete_at）はdefault:`null`
30. null,not nullをしっかり決める
31. target_○○が多い。


### アンチパターン分チェック

- 主キーをid、外部キーをテーブル名_idとする。なぜ



### 記入例
- 気になった点：テーブル名（user,code,diary...）
- どうしたかったか：複数形テーブル名（users,codes,diaries...）
- 理由：「複数のインスタンス」が格納されている！[参考](https://medium.com/@fbnlsr/the-table-naming-dilemma-singular-vs-plural-dc260d90aaff)
- 今後：テーブル名は複数形で書けるものにする

### 
[コラボランサー](https://github.com/rapide-act/freelance-site)

### 命名規則資料
- [railsの規約](https://railsdoc.com/rails_base)
- [プログラミングでよく使う英単語のまとめ【随時更新】 - Qiita](https://qiita.com/Ted-HM/items/7dde25dcffae4cdc7923)
- [新人エンジニアに役立った命名規則6選とアンチパターン3選](https://qiita.com/uehiro22/items/7a2b0b3b72f458018632)
- [データベースオブジェクトの命名規約](https://qiita.com/tatsuya_1995/items/4b706fc40fe2f300bbc0)
- [〜DB設計基礎の「キ」　命名規則〜](https://qiita.com/genzouw/items/35022fa96c120e67c637)
- [「SQLアンチパターン」まとめ](https://qiita.com/taiteam/items/33aebded2842808e0391)
- [一家？に一冊「SQLアンチパターン」](https://qiita.com/shimamura_io/items/7ca604933f526a2cdfa9)
- [達人に学ぶSQL徹底指南書 第2版 初級者で終わりたくないあなたへ](https://www.amazon.co.jp/%E9%81%94%E4%BA%BA%E3%81%AB%E5%AD%A6%E3%81%B6SQL%E5%BE%B9%E5%BA%95%E6%8C%87%E5%8D%97%E6%9B%B8-%E7%AC%AC2%E7%89%88-%E5%88%9D%E7%B4%9A%E8%80%85%E3%81%A7%E7%B5%82%E3%82%8F%E3%82%8A%E3%81%9F%E3%81%8F%E3%81%AA%E3%81%84%E3%81%82%E3%81%AA%E3%81%9F%E3%81%B8-CodeZine-BOOKS/dp/4798157821/ref=pd_rhf_dp_s_pd_sbs_rvi_sccl_1_19/357-6089438-0793650?pd_rd_w=kBWXY&content-id=amzn1.sym.87894175-5a86-4ea9-9f46-7b734f23ae1b&pf_rd_p=87894175-5a86-4ea9-9f46-7b734f23ae1b&pf_rd_r=PYVQBM31XG8GVDJM4ZT6&pd_rd_wg=ryj0L&pd_rd_r=78c18a3c-d4ba-4072-ad74-cac81201962f&pd_rd_i=4798157821&psc=1)