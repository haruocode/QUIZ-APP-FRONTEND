# WebAPI

|  画面  |  HTTPメソッド  |  エンドポイント  |  API名  |  備考  |
| ---- | ---- | ---- | ---- | ---- |
|  トップ画面  |  GET  |  /title/list/new  |  新着クイズタイトル一覧取得  |    |
|  トップ画面  |  GET  |  /category/list  |  カテゴリー情報一覧取得  |    |
|  クイズタイトル一覧画面  |  GET  |  /title/list?category_id=999&page=2  |  クイズタイトル一覧取得  |  カテゴリIDを元にクイズタイトル情報一覧を取得する。ページネーションがあるので、ページごとにn件返す。  |
|  クイズ画面  |  GET  |  /quiz/{quiz_id}  |  クイズ詳細取得  |  クイズタイトル、クイズ問題、選択肢  |
|  クイズ画面  |  POST  |  /quiz/{quiz_id}/answer  |  クイズ回答  |  クイズの回答を登録する。レスポンスに「quizes.answer」と「quizes.description」を返す。次のクイズのIDも返す。  |
