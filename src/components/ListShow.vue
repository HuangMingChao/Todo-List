<template>
  <div >
    <div v-for="list in TodoLists" class="container-fluid">
      <div class="col-sm-10 text-left">{{list.name}}</div>
      <div class="col-sm-2 text-right">
        <button class="btn btn-danger" @click="deleteTask(list.index)">删除</button></div>
    </div>
  </div>

</template>

<script>
  export default{
      props:{
          "TodoLists":{
              type: Array,
              default:[]
          }
      },
    methods:{
          deleteTask:function (index) {
            this.$emit("deleteTask",index);
          }
    }

  }
</script>
