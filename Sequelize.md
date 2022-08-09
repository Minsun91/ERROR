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
