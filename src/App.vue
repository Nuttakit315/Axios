<template>
  <div>
  <img src="https://www.prachachat.net/wp-content/uploads/2018/09/%E0%B8%81.%E0%B8%A5.%E0%B8%95..jpeg" class="rounded mx-auto d-block" width="300">
    <div class="container">
      <h3 class="text-center">รายชื่อ บริษัทหลักทรัพย์จัดการกองทุนรวมจำกัด</h3>
      <table class="table table-striped table-dark">
        <thead>
          <tr>
           <th scope="col">รหัสนิติบุคคล</th>
           <th scope="col">ชื่อนิติบุคคล/บุคคล (ภาษาไทย)</th>
           <th scope="col">ชื่อนิติบุคคล/บุคคล (ภาษาอังกฤษ)</th>
           <th scope="col">แก้ไขล่าสุด</th>
          </tr>
        </thead>
        <tr v-for="user in users" :key="user.unique_id">
          <td>{{user.unique_id}}</td>
          <td>{{user.name_th}}</td>
          <td>{{user.name_en}}</td>
          <td>{{user.last_upd_date}}</td>
        </tr>
      </table>
    </div>
  </div>
</template>

<script>
import axios from"axios"; 
export default {
  mounted(){
    this.getUser();
  },
  methods:{
    getUser(){
      axios.get("https://api.sec.or.th/FundFactsheet/fund/amc?key=8888dd4340e34b889d35e3529895224c")
      .then(response=>{
      this.users=response.data;
      });
    }
  },
  data(){
    return{
      users:[],
      user:{
        unique_id:"",
        name_th:"",
        name_en:"",
        last_upd_date:""
      }

    }
  }
}
</script>

<style>

</style>
