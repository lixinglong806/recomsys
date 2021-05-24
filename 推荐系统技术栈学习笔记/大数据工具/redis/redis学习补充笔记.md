https://www.bilibili.com/video/BV1S54y1R7SB?p=29

## 1. 面试重点：

* 持久化之rdb操作  redis database

* 持久化之aof操作

  如果这个aof文件有错误，这时候redis是启动不起来的，使用`redis- check-aof --fix`

  ![image-20210308213743705](redis%E5%AD%A6%E4%B9%A0%E8%A1%A5%E5%85%85%E7%AC%94%E8%AE%B0.assets/持久化之aof操作.png)



## 2. python与redis数据库交互中zadd、zincrby的那些坑

python与redis旧版本数据库的交互：
 zadd: db.zadd(REDIS_KEY, score, member)
 zincrby: db.zincrby(REDIS_KEY, member, increment)

如果是在redis新版本中还使用上面的语句：将会分别出现下面的异常：
 AttributeError: ‘int’ object has no attribute ‘items’
 (error) ERR value is not a valid float

python与redis新版本数据库交互：
 zadd：db.zadd(REDIS_KEY, {member:score})
 zincrby：db.zincrby(REDIS_KEY, increment, menber)