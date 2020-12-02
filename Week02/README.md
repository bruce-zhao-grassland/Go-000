DAO层遇到查询不到记录等问题，
DAO直接与SQL中间件通信，
DAO层使用wrap error，封装一个公司级或部门级或项目级ErrRecordNotExist（为了通用）
在GO中，error本质上是一个值，类似string，用起来很轻量

 DAO中，使用errors wrap 包装一下，带些额外信息，用于排错
 
 package main
 
 import ｛
    “github.com/pkg/erros”
 ｝
 
 var {
    ErrRecordNotExist = error.New("record not exist")
 }
 
 fun Dao(userId int) (User, error) {
    ...
    return nil, errors.Errorf("user id %d not found, err=%v", userId, ErrRecordNotExist)
 }
