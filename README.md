＃開発環境・ツール


	バックエンド
		言語: Python3
		フレームワーク: Flask / Django / FastAPI
		DB: SQLite, MySQL, PostgreSQL
	フロントエンド
		言語: JavaScript / TypeScript
		フレームワーク: React, Vue
		デザイン: Bootstrap
	環境構築
		Docker (仮想環境)
	デプロイ
		Heroku / AWS / GCP
	開発管理
		GitHub, GTasks



DB設計 (テーブル定義)

欲しい機能
ユーザーの新規登録, ログイン, ログアウト, 削除
ユーザーのプロフィール・ポートフォリオ (職種でカテゴライズ・検索可能)
ユーザーのフォロー機能
投稿機能 (Twitterより自由に, 画像や音源などの作品をアップロードできる)
投稿に対するいいね機能
投稿に対する返信 (スレッド) 機能
投稿の外部SNSへの共有機能
投稿へのハッシュタグ, 投稿日時によるカテゴライズ機能



	エンティティー
ユーザーのジャンル・カテゴリー (User_Category)
ユーザー (User)
投稿 (Post)
いいね (Like)
フォロー (Follow)
リプライ (Reply)
	
	テーブル設計

		User_Category
id (PK): int
category: str

		例: User_Category(1, ‘エンジニア’)

User(ユーザー情報)
id (PK): int
category_id (FK): int
email: str
password: str
username: str
profile_name: str
city: str
bio: text

例: User (1, 1, ‘user1@sample.com’, ‘nadvbdsou’, ‘user1’, ‘Ichiro’, ‘Tokyo’, ‘よろしくお願いします’)

Select * from User_Category where id == User.category_id => エンジニア

Post (投稿機能)
id (PK): int
user_id (FK): int
content: text
file_url: str => Google Driveのリンク
timestamp: timestamp

		Select * from User where id == Post.user_id => Ichiro

		Like (いいね機能)
id (PK): int
status: bool
	
		Like_User_Post
id (PK): int
user_id (FK): int
post_id (FK): int
like_id (FK): int
liked_at: datetime

		例)
			Aさん (id = 1) がいいねしている投稿を全て取り出す
Like_user_Posts = Select * from Like_user_Post where user_id == 1
posts = []
for Like_user_Post in Like_user_Posts:
posts.append(Select * from POST where id == Like_user_Post.post_id)
			print(posts)

                       Follow (フォロー機能)
id (PK): int
from_user_id (FK): int => 誰が
to_user_id (FK): int => 誰を
status: bool => フォローしているか
　　　　　　
		例)
			Aさん (id = 1) がフォローしている人を全て取り出す
				follows = Select * from Follow where from_user_id == 1
				users = []
for follow in follows:
users.append(Select * from User where id == follow.to_user_id)
				print (users)
			Aさん (id = 1) をフォローしている人 (フォロワー) を全て取り出す
				Select * from Follow where to_user_id == 1

　　　　　　Reply (リプライ機能)
　　　　　　　　 -　 id(PK): int
　　　　　　　　 -　 post_id(Fk): int
from_user_id(FK): int
to_user_id(FK): int
content :text
timestamp :timestamp

                     Hashtag (ハッシュタグ機能)
id(PK): int
post_id(FK): int
tag_name: str
timestamp: timestamp                      



デザイン (UI => Figma)

飛ばしてもOK (紙に書く程度でOK)



開発スケジュール

Week#1 要件定義書作成
Week#2 テーブル定義, Figmaインストール&紹介, GitHubリポジトリ作成
Week#3 デザイン完成, Vue.js, LP
Week#4 開発 (ユーザー登録, ログイン機能)
Week#5 開発 (プロフィール, 投稿機能)
Week#6 開発 (いいね, 返信機能)
Week#7 開発 (残り), Docker, AWS
Week#8 デプロイ



開発 (タスク管理 => GitHub)

	



デプロイ (サービスの公開 => Heroku, AWS, GCP)




ブログ記事やTwitter等で公開
