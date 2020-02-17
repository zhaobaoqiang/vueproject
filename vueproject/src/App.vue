<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <h2>圆角边框</h2>
<ul class="pagination">
  <li><a href="#">«</a></li>
  <li><a href="#">1</a></li>
  <li><a class="active" href="#">2</a></li>
  <li><a href="#">3</a></li>
  <li><a href="#">4</a></li>
  <li><a href="#">5</a></li>
  <li><a href="#">6</a></li>
  <li><a href="#">7</a></li>
  <li><a href="#">»</a></li>
</ul>
    <HelloWorld msg="Welcome to Your Vue.js App"/>

      <div class="list">
        <template v-if="count">
            <ul>
                <li v-for="item in items" :key="item">...</li>
            </ul>
            <mo-paging 
            :page-index="currentPage" 
            :totla="count" 
            :page-size="pageSize" 
            @change="pageChange">
            </mo-paging>
        </template>
    </div>
  </div>


</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import MoPaging from './components/template.vue'
export default {
  name: 'App',
  components: {
    HelloWorld,
    MoPaging
  },
   data () {
            return {
                pageSize : 20 , //每页显示20条数据
                currentPage : 1, //当前页码
                count : 0, //总记录数
                items : []
            }
        },
    methods : {
            //获取数据
            getList () {
                //模拟
                let url = `/api/list/?pageSize=${this.pageSize}&currentPage=${this.currentPage}`
                this.$http.get(url)
                .then(({body}) => {

                    //子组件监听到count变化会自动更新DOM
                    this.count = body.count
                    this.items = body.list
                })
            },

            //从page组件传递过来的当前page
            pageChange (page) {
                this.currentPage = page
                this.getList()
            }
        },
        mounted() {
            //请求第一页数据
            this.getList()
        } 
    
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
ul.pagination {
    display: inline-block;
    padding: 0;
    margin: 0;
}

ul.pagination li {display: inline;}

ul.pagination li a {
    color: black;
    float: left;
    padding: 8px 16px;
    text-decoration: none;
    transition: background-color .3s;
    border: 1px solid #ddd;
}

.pagination li:first-child a {
    border-top-left-radius: 5px;
    border-bottom-left-radius: 5px;
}

.pagination li:last-child a {
    border-top-right-radius: 5px;
    border-bottom-right-radius: 5px;
}

ul.pagination li a.active {
    background-color: #4CAF50;
    color: white;
    border: 1px solid #4CAF50;
}

ul.pagination li a:hover:not(.active) {background-color: #ddd;}
</style>
