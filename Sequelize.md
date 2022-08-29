### 1. Error: Unknown column 'nickname' in 'field list' (errno: 1054)

이 에러는 nickname 이라는 컬럼이 테이블에 없어서 생긴다.   
migration file / models 확인해보고, 정말 없다면 추가한 뒤 

```
npx sequelize db:migrate:undo 
npx sequelize db:migrate 
```

로 업데이트하면 문제 해결!


### 2. triggerUncaughtException(err, true /* fromPromise */);  
[ERR_ASSERTION]:Expected plain object, array or sequelize method in the options.where parameter  

```
code: 'ERR_ASSERTION',
  actual: false,
  expected: true,
  operator: '=='
```

### 3. Node js MySQL 연동 에러

..! Docker 연결 상태 확인하기 
1) Docker를 이용하여 MySQL 서버를 띄울수 있게 해주는 명령어  

```
docker run --rm -p 3306:3306 --name test-db -e MYSQL_ROOT_PASSWORD=1234 mysql:5.7 mysqld --character-set-server=utf8mb4 --collation-server=utf8mb4_unicode_ci
```

- `host`: 127.0.0.1
- `user`: root
- `password`: 내 비번

2) ![image](https://user-images.githubusercontent.com/92393851/187251079-76eb76e1-3f0c-4eee-a9e5-a70d82cc67a3.png)

연결하기! 
```
sequelize init
npx sequelize db:create
npx sequelize db:migrate
```

