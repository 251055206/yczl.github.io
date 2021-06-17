#打造个人专用的工具库


## mongodb包含以下函数
#### 注意使用前，必须安装 npm i mongodb 

| 函数             | 说明                                                         |
| --------------- | ----------------------------------------------------------- |
| newMongoClient  | 封装好的链接数据库函数，传入连接即可使用，并且是promise风格          |
| ObjectId        | 用于使用_id查询数据时必须添加的函数,就是原来mongodb.ObjectId       |
| MongoClient     | 用于链接数据库的函数,就是原来mongodb.MongoClient                 |



``` javascript
const mongo=require('lycq').mongo;
let dbUrl="mongodb://name:password@127.0.0.1:27017/dbname"


/**
 * [newMongoClient 用Promise封装的mongodb数据库连接函数以同步方式运行]
 * @param  {[str]} dbUrl:数据库链接
 * @return {[obj]}  [反回数据库对象]
 */
let main=async ()=>{
 let client=await mongo.newMongoClient(dburl);
}


/**
 * [ObjectId mongodb的_id]
 * @param  {[str]} _id:mongodb的_id
 * @return {[obj]}  [反回对象]
 */
mongo.ObjectId(_id);


/**
 * [MongoClient mongodb驱动模块自带的MongoClient对象]
 */
mongo.MongoClient.connect(dbUrl,{useNewUrlParser: true,useUnifiedTopology: true}, async (err, client)=> {
    try{
        if(err){
            console.error(`发生错误的数据库连接：${dbUrl}`);
        }else{
            console.log(`连接成功：${dbUrl}`);
            let doc= client.db();
        }
    }catch (e) {
        console.error(e.message);
        console.error(`连接异常：${dbUrl}`);
    }
})

```



## tool包含以下函数

| 函数             | 说明                                                         |
| --------------- | ----------------------------------------------------------- |
| repair          | 字符串补全，默认补0                                             |
| formatTime      | 时间格式转换                                                   |
| uuid            | 创建一个uuid                                                  |
| randomString    | 创建随机字符串                                                 |

``` javascript
const tool=require('lycq').tool;


/**
 * [repair 给字符串补0，增加长度]
 * @param  {[num]} n:输出长度
 * @param  {[num]} v:传入的值
 * @return {[str]}  [反回补全字符串]
 */
tool.repair(n,v)


/**
 * [formatTime 时间戳格式函数]
 * @param  {[num,obj,str]} time   :时间戳
 * @param  {[str]} format :Y年M月D日 h:m:s:i
 * @return {[str]}        [反回格式化后日期字符串]
 */
let doc=formatTime(time,"YMDhmsi");  //202106171210220840
或者 
let doc=tool.formatTime(time,"Y-M-D h:m:s:i");  //2021-06-17 12:09:59:0430


/**
 * [randomString 返回随机字符串]
 * @param  {[num]} len:限制随机数长度，默认36
 * @return {[str]}  [反回随机字符串]
 */
tool.randomString(len);


/**
 * [uuid 创建uuid]
 * @param  {[num]} v:第一个字符串的时间戳转的进制，如8，16，32，最大不能超过32
 * @param  {[num]} n:增加多组随机字符串，
 * @param  {[num]} m:每一组随机字符串的长度，
 * @return {[str]}  [反回uuid字符串]
 */
uuid(v,n,m)  
//  17a182866d8-cthab7de-mhs4knfh-bydbf8rd-hiknbh4d
```