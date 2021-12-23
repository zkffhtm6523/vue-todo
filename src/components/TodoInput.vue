<template>
  <div class="inputBox shadow">
    <input type="text" v-model="newTodoItem" placeholder="Type what you hava to do"
           v-on:keyup.enter="addTodo">
    <span class="addContainer" v-on:click="addTodo">
      <i class="addBtn fas fa-plus" aria-hidden="true"></i>
    </span>
  </div>
</template>

<script>
export default {
  data(){
    return {
      newTodoItem: ''
    }
  },
  methods:{
    // method1
    addTodo(){
      if(this.newTodoItem !== ""){
        var value = this.newTodoItem && this.newTodoItem.trim(); // 공백 제거 체크
        localStorage.setItem(value, value) // 로컬 스토리지 저장
        this.clearInput();
      }
    },
    // method2
    clearInput(){
      this.newTodoItem = '';
    }
  }
}
</script>

<style scoped>
  /* outline : 선 스타일 지정 */
  input:focus{
    outline: none;
  }
  .inputBox{
    background: white;
    height: 50px;
    /* line-height : 텍스트의 중앙 정렬 */
    line-height: 50px;
    border-radius: 5px;
  }

  .inputBox input{
    border-style: none;
    font-size: 0.9rem;
  }
  .addContainer{
    float: right;
    background: linear-gradient(to right, #6478FB, #8763FB);
    display: block;
    width: 3rem;
    border-radius: 0 5px 5px 0;
  }
  .addBtn{
    color: white;
    /* vertical-align : 수직 정렬 정의 */
    vertical-align: middle;
  }
</style>
