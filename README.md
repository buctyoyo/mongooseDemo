mongoose技术分享
============
##1.为什么使用mongoose（个人见解）
 * 单易用，许多方法都已封装完成（如find，findOne，findById等等）；
 * 对于索引，唯一值，默认值这些可直接通过一个字段即可设置完成，不需要多余代码；
 * 代码分享上，别人可直接从Schema中看出数据库结构；
 * 中间件，插件，setter，getter。。。。（没实际操作过，不是很理解）；

##2.mongoose的用法
  ###链接数据库
  ```
  mongoose.connect("mongodb://username:pswd@ip:port/dbname", function (err) {
    if (err) {
      console.error('connect to %s error: ', config.db, err.message);
      process.exit(1);
    }
  });
  ```
  

  ###新建Schema
  ``` 
  var mongoose = require('mongoose');
  var Schema = mongoose.Schema;

  var BookSchema = new Schema({
    name: { type: String, unique: true, index: true },
   	publishTime: {type: Date, default: Date.now},
   	description:{type: String}，
   	havasale:{type:Number,min:0}
  });
  ```
  基本数据类型：
  * String
  * Number
  * Date
  * Buffer
  * Boolean
  * __Mixed__（Schema.Types.Mixed）
  * __ObjectId__（Schema.Types.ObjectId）
  * Array
  
 ###新建model
```
  mongoose.model('Book', BookSchema);
```


