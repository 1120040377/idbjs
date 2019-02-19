# idbjs
indexDB 极简API 简单使用

废话不说，先上代码（以Vue为例）
```js
// main.js
  import IndexDB from 'idbjs'
  const IDB_CONF = {
    name: 'mydb', // DB名称
    version: 1, // DB版本，每次修改objectStoreList都需要加1
    cacheTime: 300 * 1000, // 缓存时间 ms
    objectStoreList: [{ // 数据对象列表
      name: 'GOODS',
      autoIncrement: false // 可选，是否自增
    }]
  }
  Vue.prototype.$db = new IndexDB()

// *.vue
this.$db.GOODS.put(key, val)

this.$db.GOODS.get(key).then(({ data }) => {
  console.log('读取缓存', data) // val
  this.syncGoodsDetail(data)
}).catch(err => {
  console.log(err) // 读取缓存失败
})
```
