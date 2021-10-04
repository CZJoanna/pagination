<template>
  <div >
    <h1>This is an about Pagination Component</h1>
    <Pagination :totalPages="totalPages" @get-page-number="getPageNumber"/>
    <p>Now we're at Page - {{currentPage}}</p>
     <section class="friends">
       <Card v-for="data in selectedData" :key="data.id" :data="data" />
     </section>
  </div>
</template>

<script>
import axios from "axios";
import Pagination from "../components/pagination.vue"
import Card from "../components/card.vue";
export default {
  components:{
    Card,
    Pagination
  },
  data() {
    return {
      //全部資料筆數
      dataArray :[],
      //每頁渲染資料筆數
      dataPerPage:9,
      //目前所在頁面
      currentPage:1,
    }
  },
  computed:{
    //所有頁數
    totalPages(){
      return Math.ceil(this.dataArray.length/this.dataPerPage);
    },

    //目前被指定渲染的資料
    selectedData(){  
       const indexStart = (this.currentPage-1)*this.dataPerPage;
       return this.dataArray.slice(indexStart,indexStart+this.dataPerPage);
    }
  },
  methods:{
    fetchData(){
      axios.get("https://lighthouse-user-api.herokuapp.com/api/v1/users").then(res=>this.dataArray.push(...res.data.results))
    },

    //pagination子原件傳送被點擊的頁面數字到父元件
    getPageNumber(currentPage){
      console.log("我是getPageNumber",currentPage);
      this.currentPage = currentPage;
    }
  },
  created() {
    this.fetchData()
  },
}
</script>



