# [官网](http://mockjs.com/examples.html#Name)

# 1、生成数据

```js
import Mock from 'mockjs'
//生成文本
// const data = Mock.mock({
//     "string|1-10": "★"
//   })
//生成文本
//   const data=Mock.mock({
//     string: '@cword(3,10)'
//   })
//生成标题和句子
//   const data=Mock.mock({
//     title:'@ctitle',
//     sentence:'@csentence'
//   })
// 生成增量
//   const data=Mock.mock({
//     id:'@increment(1)'
//   })
//生成数值
//   const data=Mock.mock({
//     'number|1-100':10
//   })
//生成段落
//   const data=Mock.mock({
//     content:'@cparagraph(5)'
//   })
//生成名字，身份证号，地址
//   const data=Mock.mock({
//     name:'@cname',
//     idCard:'@id()',
//     address:'@city(true)'
//   })
//生成图片
//   const data=Mock.mock({
//     img_url:"@image('250x250",'#FFA07A','#FFBBFF','png','坤坤')"
//   })
//生成时间
//   const data=Mock.mock({
//     date:'@date(yyyy-MM-dd hh:mm:ss)'
//   })
//生成数组
//   const data=Mock.mock({
//     'newsList|8-20':[{
//     name:'@cname',
//     address:'@city(true)',
//     id:'@increment(1)'
// }]
//   })
// console.log(data)
```

# 2、拦截请求

写在js中

```js
Mock.mock('/api/news','get',{
    status:200,
    msg:'get successly'
})
// Mock.mock('/api/post/news','post',{
//     status:200,
//     msg:'post successly'
// })第一种写法
Mock.mock('/api/post/news','post',()=>{
    return{
        status:200,
        msg:'post successly'
    }
})

```

```js
export default {
    data() {
    return{

    }
  },
  created(){
    axios.get('/api/news').then(res=>{
      console.log(res)
    })
    axios.post('/api/post/news').then(res=>{
      console.log(res)
    })
  },
  name: 'App',
  components: {
    HelloWorld
  }
}
```

