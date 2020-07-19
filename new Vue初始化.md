先看一段new Vue的代码

`const _vm = new Vue({
render: h => h(App),
data: {
mainjsData: 'mainjsData'
},
created() {
console.log('mainjs created')
},
mounted() {
console.log('mainjs mounted')
}
}).$mount('#app')

console.log(_vm)`


接下来我们来分析这个过程发生了什么
