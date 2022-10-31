# サーバーサイドのC
## 回答
### 発行するクエリ
    SELECT g.name,  
        AVG(i.price)  
            as avg_price  
        FROM items i, genres g  
        WHERE i.genre_id = g.id  
        GROUP BY g.id;  
### 理由
    まず、genres.nameとgenres.nameごとのitems.priceの平均値を求めたいので,selectで指定する。  
    表名はitems,genresなのでfromに指定。  
    itemsのgenre_idとgenresのidの共通部分で関連づけるためwhereを指定。  
    あとはgenre.idごとにitems.priceの平均を求めたいのgroup byで集約する。  
### 貼っておいた方が良いインデックス
    genre_id(外部キー)にはインデックスを貼っておいたほうがよいと思います。  
    複数テーブルにまたがるデータを参照する時に効率的に探索させるため。  
    CREATE INDEX genre_id_index ON items (genre_id);  