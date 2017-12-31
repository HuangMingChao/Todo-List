<template>
  <div>
    <input type="text" class="form-control" placeholder="输入任务名称,回车确定" @keydown.enter="enterTask" v-model="taskName"/>
  </div>
</template>


<script>
  export default {
      data(){
          return {
              taskName:''
          }
      },
    methods:{
          enterTask:function () {
              this.$emit("add",this.taskName);
              this.taskName='';
          }
    }
  }
</script>
