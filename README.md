# idbjs
indexDB 极简API 简单使用

废话不说，先上代码（以Vue为例）
```js
// main.js
const IDB_CONF = {
  name: 'mydb',
  version: 1,
  cacheTime: 300 * 1000,
  objectStoreList: [{
    name: 'GOODS',
    autoIncrement: false
  }]
}
Vue.prototype.$db = new IndexDB()

// *.vue
const key = 'key'
this.$db.GOODS.put({
  primaryKey: key,
  data: 'val'
})

this.$db.GOODS.get(key).then(({ data }) => {
  console.log('读取缓存', data)
  this.syncGoodsDetail(data)
}).catch(err => {
  console.log(err)
})
```
