# テーブル一覧

|  テーブル名  |  説明  |
| ---- | ---- |
|  categories  |  クイズタイトルが属するカテゴリ  |
|  sub_categories  |  クイズタイトルが属するサブカテゴリ  |
|  titles  |  クイズタイトル  |
|  quizes  |  クイズ  |
|  answer_histories  |  ユーザーが回答したクイズや選択肢を記録してみる  |

## categories

クイズの親カテゴリ

|  カラム名  |  データ型  |  NULL  |  デフォルト値  |  コメント  |
| ---- | ---- | ---- | ---- | ---- |
|  id  |  int  |  ×  |  -  |  auto_increment  |
|  name  |  varchar(255)  |  ×  |  -  |  カテゴリー名  |
|  sort  |  int  |  ×  |  -  |  ソート順  |
|  created_at  |  datetime  |  ×  |  -  |  作成日時  |
|  updated_at  |  datetime  |  ×  |  -  |  更新日時  |
|  deleted_at  |  datetime  |  ×  |  -  |  削除日時  |

## sub_categories

クイズの子カテゴリ

|  カラム名  |  データ型  |  NULL  |  デフォルト値  |  コメント  |
| ---- | ---- | ---- | ---- | ---- |
|  id  |  int  |  ×  |  -  |  auto_increment  |
|  category_id  |  int  |  ×  |  -  |  どのカテゴリーに属するか  |
|  name  |  varchar(255)  |  ×  |  -  |  サブカテゴリー名  |
|  sort  |  int  |  ×  |  -  |  ソート順  |
|  created_at  |  datetime  |  ×  |  -  |  作成日時  |
|  updated_at  |  datetime  |  ×  |  -  |  更新日時  |
|  deleted_at  |  datetime  |  ×  |  -  |  削除日時  |

## titles

クイズタイトル

|  カラム名  |  データ型  |  NULL  |  デフォルト値  |  コメント  |
| ---- | ---- | ---- | ---- | ---- |
|  id  |  int  |  ×  |  -  |  auto_increment  |
|  sub_category_id  |  int  |  ×  |  -  |  どのタイトルに属するか  |
|  title  |  varchar(255)  |  ×  |  -  |  クイズのタイトル名  |
|  description  |  text  |  ×  |  -  |  クイズタイトルの説明  |
|  thumbnail  |  varchar(255)  |  ×  |  -  |  クイズタイトルのサムネイルのファイル名  |
|  created_at  |  datetime  |  ×  |  -  |  作成日時  |
|  updated_at  |  datetime  |  ×  |  -  |  更新日時  |
|  deleted_at  |  datetime  |  ×  |  -  |  削除日時  |

## quizes

クイズ

|  カラム名  |  データ型  |  NULL  |  デフォルト値  |  コメント  |
| ---- | ---- | ---- | ---- | ---- |
|  id  |  int  |  ×  |  -  |  auto_increment  |
|  title_id  |  int  |  ×  |  -  |  どのサブカテゴリーに属するか  |
|  question  |  varchar(255)  |  ×  |  -  |  問題  |
|  answer1  |  varchar(255)  |  ×  |  -  |  選択肢A  |
|  answer2  |  varchar(255)  |  ×  |  -  |  選択肢B  |
|  answer3  |  varchar(255)  |  ×  |  -  |  選択肢C  |
|  answer4  |  varchar(255)  |  ×  |  -  |  選択肢D  |
|  answer  |  int  |  ×  |  -  |  1, 2, 3, 4  |
|  description  |  text  |  ×  |  -  |  回答後の説明  |
|  created_at  |  datetime  |  ×  |  -  |  作成日時  |
|  updated_at  |  datetime  |  ×  |  -  |  更新日時  |
|  deleted_at  |  datetime  |  ×  |  -  |  削除日時  |

## answer_histories

ユーザーの回答履歴

|  カラム名  |  データ型  |  NULL  |  デフォルト値  |  コメント  |
| ---- | ---- | ---- | ---- | ---- |
|  id  |  int  |  ×  |  -  |  auto_increment  |
|  quiz_id  |  int  |  ×  |  -  |  quizesテーブルのid  |
|  answer  |  int  |  ×  |  -  |  クイズの答え(1, 2, 3, 4)の内のどれか  |
|  created_at  |  datetime  |  ×  |  -  |  作成日時  |
|  updated_at  |  datetime  |  ×  |  -  |  更新日時  |
|  deleted_at  |  datetime  |  ×  |  -  |  削除日時  |
