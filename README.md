1. Railsのプロジェクトを作成する
```
  docker-compose run api rails new . --force --no-deps --database=postgresql --api
```
2. イメージ作成
```
  docker-compose build
```
3. Reactのプロジェクトを作成する
```
  docker-compose run --rm front sh -c "npm install -g create-react-app && create-react-app frontend"
```
4.DBの接続ができるようにRailsの下記configファイルを修正
``` 
  api/config/database.yml
    default: &default  
        adapter: postgresql  
        encoding: unicode  
        host: db  
        username: postgres  
        password: postgres  
        pool: 5  
```
5. コンテナ作成、起動
```
  docker-compose up
```
6. DBの作成
```
  docker-compose run api rake db:create
```